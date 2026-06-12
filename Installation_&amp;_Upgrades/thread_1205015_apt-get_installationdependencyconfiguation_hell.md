---
title: "apt-get installation/dependency/configuation hell"
date: 2009-07-05
forum: Installation &amp; Upgrades
---

### Post by flying sheep on 2009-07-05
edit:solved!

in case somebody has a log like this,
just use the DEBIAN version of [FONT="DejaVu Sans Mono"]install-info[/FONT] instead of the GNU version, which is most likely in your [FONT="DejaVu Sans Mono"]PATH[/FONT], e.g. if you have installed texlive manually and created a symlink to it’s (gnu) [FONT="DejaVu Sans Mono"]install-info[/FONT] binary within /usr/local/bin/
```
$: sudo apt-get -f install
Paketlisten werden gelesen... Fertig          
Abhängigkeitsbaum wird aufgebaut              
Lese Status-Informationen ein... Fertig       
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
9 nicht vollständig installiert oder entfernt.                             
Nach dieser Operation werden 0B Plattenplatz zusätzlich benutzt.           
Richte cvs ein (1:1.12.13-12ubuntu1) ...                                   
install-info: No dir file specified; try --help for more information.      
dpkg: Fehler beim Bearbeiten von cvs (--configure):                        
 Unterprozess post-installation script gab den Fehlerwert 1 zurück         
Richte gettext ein (0.17-6ubuntu2) ...                                     
install-info: No dir file specified; try --help for more information.      
dpkg: Fehler beim Bearbeiten von gettext (--configure):                    
 Unterprozess post-installation script gab den Fehlerwert 1 zurück         
Richte gnuplot-doc ein (4.2.4-6) ...                                       
install-info: No dir file specified; try --help for more information.      
dpkg: Fehler beim Bearbeiten von gnuplot-doc (--configure):                
 Unterprozess post-installation script gab den Fehlerwert 1 zurück         
Richte groff ein (1.18.1.1-22build1) ...                                   
install-info: No dir file specified; try --help for more information.      
dpkg: Fehler beim Bearbeiten von groff (--configure):                      
 Unterprozess post-installation script gab den Fehlerwert 1 zurück         
Richte gv ein (1:3.6.5-2) ...                                              
No apport report written because MaxReports is reached already             
                                                              install-info: No dir file specified; try --help for more information.                                                       
dpkg: Fehler beim Bearbeiten von gv (--configure):                                           
 Unterprozess post-installation script gab den Fehlerwert 1 zurück                           
Richte m4 ein (1.4.11-1) ...                                                                 
No apport report written because MaxReports is reached already                               
                                                              install-info: No dir file specified; try --help for more information.                                                       
dpkg: Fehler beim Bearbeiten von m4 (--configure):                                           
 Unterprozess post-installation script gab den Fehlerwert 1 zurück                           
Richte maxima-doc ein (5.13.0-3ubuntu1) ...                                                  
No apport report written because MaxReports is reached already                               
                                                              install-info: No dir file specified; try --help for more information.                                                       
dpkg: Fehler beim Bearbeiten von maxima-doc (--configure):                                   
 Unterprozess post-installation script gab den Fehlerwert 1 zurück
Richte texi2html ein (1.78-1) ...
No apport report written because MaxReports is reached already
                                                              install-info: No dir file specified; try --help for more information.
dpkg: Fehler beim Bearbeiten von texi2html (--configure):
 Unterprozess post-installation script gab den Fehlerwert 1 zurück
Richte comerr-dev ein (2.1-1.41.4-1ubuntu1) ...
No apport report written because MaxReports is reached already
                                                              install-info: No dir file specified; try --help for more information.
dpkg: Fehler beim Bearbeiten von comerr-dev (--configure):
 Unterprozess post-installation script gab den Fehlerwert 1 zurück
No apport report written because MaxReports is reached already
                                                              Fehler traten auf beim Bearbeiten von:
 cvs
 gettext
 gnuplot-doc
 groff
 gv
 m4
 maxima-doc
 texi2html
 comerr-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

