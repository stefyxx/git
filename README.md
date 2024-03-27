## Configurazione globale delle tue Credenziali di Gith
FACOLTATIVO, puo' servire se il PC é aziendale, e cosi' si sa chia ha fatto cosa             
Vediamo i comandi:      

    git config --global user.name "_nome e cognome_"        
    git config --global user.email "_la ltua mail_"

## New Project
### …or create a new repository on the command line
    git init
    git add *	    or  git add .       or git add README.md    -> se ho molto testo  
    git commit -m "first commit"
    git branch -M main                  -> evita di far creare la branch Master
    git remote add origin https://github.com/stefyxx/..._link_
    git push -u origin main

### …or push an existing repository from the command line
    git remote add origin https://github.com/stefyxx/git.git
    git branch -M main
    git push -u origin main

### …or legare un project ANGULAR a GitHub
Quando crei un project Angular, ha già git init.

1. entra sul tuo github online e crea un New Repository, public or private      

>**ATTENZIONE:**    
>NON cliccare su Add README, NON cliccare su Add .gitignore -> VisulaStudio o altro , PERCHé questi files sono già presenti nel tuo New Project Angular --> 'create repository'

2. apri GithBashHere net tuo Project Angular e clicca:       

        git branch -M main     
        git remote add origin https..._link_ del repo in linea     
        git add .      
        git commit -m "first commit"       
        git push -u origin main

### …or clone
    recupera il link del project da copiare     
    apri nel tuo folder sul tuo PC Gith Bach Here e scrivi:   

    git clone _link_

### git remote...
Ma su che link sto pull-push?       

    git remote -v


    git remote ste -url origil URL

Mi appare :

    origin _link_ (fetch)       
    origin _link (push)

## Add and Remove
Buona pratica é controllare che nessuno ha pushato qualcosa     
Comandi importanti da fare prima del _git push_ sono:  

    git pull        

    git status

Poi aggiungi serenamente ;)

    git add .       
    git commit -m"Spiegazione chiara di cosa stai aggiungendo"      
    git push

>add fa anche da **update** 

### Remove un file aggiunto x errore
Puoi _discard_ un cambiamento, perché magari non :vuoi fare il commit subito

    git rm <file>           -  -> rm:= removed

    opp     

    git rm --cached <file>  -  -> to unstage

Hai **cancellato** per sbaglio un file (gith memorizza tuuttooo **:O** ):  

    git restore <file>

Vuoi vedere cosa hai _modificato_ in un file da cmd:

    git diff <file>     -  -> vedi cosa hai tolto in rosso e cosa hai aggiunto in verde


## Branch and Merge
### … create a new branch on the command line
    git branch nomeBranch 			                    -> crea branch 
    git checkout nomeBranchPrincipaleDoveDeviMerger		-> ti porta sulla branch
	
    git checkout –b nomBranch  	                        -> crea e checka


### … MERGE 
> NBB prima di merge assicurati di aver fatto tutti I commit e push fino all’ultima modifica

    git checkout branchPRINCIPALE		-> checka branch DOVE devi merger
    git merge brancDEVaMerger			-> merge la branch dev NELLA tua branch checkata

SE la BRANCH brancDEVaMerger NON TI SERVE PIU’, LA PUOI **ELIMINARE**

    git branch –d brancDEVaMerger		-> ELIMINA brancDEVaMerger

### … MERGE : si genera un **conflitto**
Se in branchPRINCIPALE et in brancDEVaMerger ho modificato la stessa parte IN MODO DIVERSO nei due rami, git non é capace di scegliere tra le modifiche ; bisogna farlo alla mano

-> avro : CONFLICT (content): Merge conflict in …
	  Automatic merge failed; fix conflicts and then commit the result.

    git status		    -> x vedere quali file sono separati in qualsiasi momento dopo un conflitto di unione


vedro’: 

_……… both modified:      index.html_ -  -  -  -  -  -> (es: index.html é il file modif in entrambe le branch)       
_no changes added to commit (use "git add" and/or "git commit -a")_
	
con degli **‘indicatori’** posso entrare in ogni conflitto e per risolvere il conflitto, devi scegliere da una parte o dall'altra o unire tu stesso i contenuti.

<<<<<<<, ======= e >>>>>>> sono state completamente rimosse

    git add 	    -> Dopo aver risolto ciascuna di queste sezioni in ogni file in conflitto, esegui git add su ogni file per contrassegnarlo come risolto
    git status 	    -> per controllare che ogni conflitto é risolto 
    git commit	    -> per finalizzare il merger // ha un SMS di default, oppure ne puoi scrivere uno tu
_____
RIASSUMENDO:

_git status_

_risolvi_ ogni conflitto alla mano RIMUOVENDO <<<<<<<, ======= e >>>>>>>

o usa git merge**tool** per risolvere I conflitti con una grafica ‘piu’ leggibile’

_git add ._ per ogni conflitto

_git status_

_git commit_
_____________
### ahhhhh cmd non rispondeeee:

    Ctrl shift esc 

### … MERGE da annullare

**Git merge –abort** -  -  -> annulla il merge riportando SOLO i conflitti allo stato di pre-merge (quindi potrebbe non funzionare)

…ritornare a una versione precedente **distruggendo** tutte quelle fatte dopo su quel branch

    git log     -  -  -> appare lo storico di TUTTI i commits fatti    
    -> poi cercare il n° del commit desiderato (lo riconosco dal sms)       
    git remote n°commitDesiderato       

oppure
    git reset n°commitDesiderato --hard    

