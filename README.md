##  **Einführung in Git und Git-Repositories**

### **Ziel der Schulung**

Der Teilnehmer soll verstehen:

-   Was Git ist
    
-   Wie Versionskontrolle funktioniert
    
-   Wie man ein Git-Repository erstellt, nutzt und verwaltet
    
-   Wie man mit GitHub (oder GitLab/Bitbucket) arbeitet
    

----------

## 1. **Einführung in Versionskontrolle**

### Inhalte:

-   Was ist Versionskontrolle?
    
-   Warum braucht man sie?
    
-   Vergleich manuelle Versionierung vs. Git
    
-   Was ist Git (verteiltes Versionskontrollsystem)?
    
-   Was ist GitHub (zentrale Plattform zum Teilen von Git-Repos)?
    

###  Beispiel-Erklärung:

> „Stell dir vor, du schreibst eine Hausarbeit. Du speicherst sie immer wieder unter neuen Dateinamen – `hausarbeit_final.docx`, `hausarbeit_final_final.docx` usw. Git macht das automatisch – und noch viel mehr.“

----------

## 2. **Grundlagen von Git**

### Begriffe:

-   Repository
    
-   Commit
    
-   Branch 
    
-   Merge 
    
-   Clone
    
-   Push / Pull
    
-   Remote vs. Local

 <img src="https://sdmntpritalynorth.oaiusercontent.com/files/00000000-10bc-6246-a942-ac8e337951e2/raw?se=2025-04-27T08%3A14%3A44Z&sp=r&sv=2024-08-04&sr=b&scid=40aef9c2-17bc-53fa-978b-483c7cd05e6c&skoid=06d77cea-897f-49c6-9d78-20f6510f72af&sktid=a48cca56-e6da-484e-a814-9c849652bcb3&skt=2025-04-27T05%3A39%3A36Z&ske=2025-04-28T05%3A39%3A36Z&sks=b&skv=2024-08-04&sig=v2MFAuwh/bCPrJgDtyv7ck8/AqEsY7HBZ9f33f9lMYw%3D" alt="Bildbeschreibung" width="200" height="300">
 
----------

## 3. **Installation & Setup**

### Voraussetzungen:

-   Git installieren: [https://git-scm.com](https://git-scm.com)
    
-   GitHub-Konto anlegen
    
-   Git konfigurieren:
    
    `git config --global user.name "Vorname Nachname"`
    `git config --global user.email "email@example.com"` 
    

----------

## 4. **Hands-on Teil: Git im Einsatz**

### Übung: Neues Projekt mit Git

#### A. **Lokales Repository anlegen**
Lege ein neues Verzeichnis an und wechsle in dieses
`mkdir my-first-git-project cd my-first-git-project`

Initialisiere das Verzeichnis mit Git
`git init` 

#### B. **Datei erstellen + Committen**
Erstelle eine neue Datei

Überprüfe den Status des Repositories
`git status`

Füge die neue Datei zum Repositorie hinzu
`git add readme.txt`

Übertrage die bereitgestellten Inhalte als einen neuen Commit-Snapshot
`git commit -m "Erster Commit: readme hinzugefügt"` 

#### C. **GitHub-Repo verbinden**

1.  Neues Repository auf GitHub anlegen (ohne README)
	- Kopiere die URL des Repos
2.  Repo verbinden:

`git remote add origin https://github.com/USERNAME/REPO-NAME.git`

3. Übertrage alle lokalen Commits in das remote repo
`git push -u origin main` 

#### D. **Änderung machen + Push**

`echo  "Zweite Zeile" >> readme.txt
git add readme.txt
git commit -m "Zweite Zeile ergänzt" git push` 

----------

## 5. **Branches & Zusammenarbeit**

### Beispiel:

`git checkout -b neue-idee`

macht zwei Dinge auf einmal:
 - Erstellt einen neuen Branch mit dem Namen, den du angibst (z.B. neuer-branchname).
 - Wechselt direkt auf diesen neuen Branch.

Du sparst dir damit zwei Schritte, die du sonst einzeln machen müsstest:

`git branch neuer-branchname   # Nur Branch erstellen`
`git checkout neuer-branchname # Danach auf den Branch wechseln`

Mit git checkout -b geht das in einem einzigen Befehl.

Anschließend alle modifikationen stagen und commiten
`git add .`
`git commit -m "Neue Funktion begonnen"` 

Wechsle zurück in den main/master Branch
`git checkout main`

Branche neue-idee mit main/master zusammenfügen
`git merge neue-idee` 

### Konflikte
Ein **Konflikt** passiert, wenn Git zwei verschiedene Änderungen an derselben Stelle einer Datei findet und nicht automatisch entscheiden kann, welche Version richtig ist.  
→ **Beispiel:** Du änderst Zeile 5 und jemand anderes auch → Konflikt.

----------

### So löst du Konflikte:

1.  **Konflikt erkennen**  
    Wenn du `git pull` oder `git merge` machst und ein Konflikt passiert, sagt Git dir:
    
    `CONFLICT (content): Merge conflict  in datei.txt` 
    
2.  **Dateien anschauen** Zeige dir die Dateien mit Konflikten an:
    
    `git status` 
    
    → Git listet die betroffenen Dateien auf.
    
3.  **Dateien bearbeiten** 
	Öffne die betroffene Datei
    
    Git markiert die Konfliktstellen.
    → Du musst diese Stellen **manuell anpassen** und die Konflikt-Markierungen (<<< === >>>) **löschen**!
    
4.  **Nach der Bearbeitung: Änderungen übernehmen** 
	
	Sage Git, dass du den Konflikt gelöst hast:
   
    `git add datei.txt` 
    
5.  **Merge abschließen** 
	
	Danach beendest du den Merge oder Rebase:
    
    `git commit` 
    
    (manchmal wird dieser Commit automatisch erzeugt, manchmal musst du ihn schreiben)

----------

## 6. **Best Practices & Tipps**

-   Häufig committen mit sinnvollen Kommentaren
    
-   Nicht direkt auf `main` arbeiten
    
-   `.gitignore` verwenden
    
-   Code nicht direkt in GitHub-Webinterface schreiben
    
-   Repos regelmäßig pullen, wenn im Team
