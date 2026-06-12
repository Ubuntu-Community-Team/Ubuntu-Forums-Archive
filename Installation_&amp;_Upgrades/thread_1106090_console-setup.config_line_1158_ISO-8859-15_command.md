---
title: "console-setup.config: line 1158: ISO-8859-15 command not found"
date: 2009-03-25
forum: Installation &amp; Upgrades
---

### Post by macsaver on 2009-03-25
Hello Forum,

every time I work with apt I got this error message and an error code 127. I removed the package and reinstalled it - generated the locales again but nothing helps - any ideas?

Thanks in advance.

macsaver

---

### Post by rjl6591 on 2009-03-25
Can you please show us exactly what you are trying to do?

Tip: you can record an interactive command-line session to a file by typing "script logfile" before the session, and typing Control-D when you've finished. If you then paste the logfile here we can see what you're doing.

---

### Post by macsaver on 2009-03-25
hi this is my last step - I removed console-setup completely with apt-get --purge remove console-setup 
This is the output of apt-get install console-setup:

apt-get install console-setup
Paketlisten werden gelesen... Fertig
Abh?ngigkeitsbaum wird aufgebaut       
Reading state information... Fertig
Die folgenden NEUEN Pakete werden installiert:
  console-setup
0 aktualisiert, 1 neu installiert, 0 zu entfernen und 10 nicht aktualisiert.
Es m?ssen noch 0B von 468kB Archiven geholt werden.
After this operation, 1294kB of additional disk space will be used.
Vorkonfiguration der Pakete ...
[COLOR="Red"]/tmp/console-setup.config.200371: line 1158: ISO-8859-15: command not found[/COLOR]
console-setup konnte nicht vorkonfiguriert werden, Exit-Status 127
W?hle vormals abgew?hltes Paket console-setup.
(Lese Datenbank ... 135643 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacke console-setup (aus .../console-setup_1.21ubuntu9_all.deb) ...
Richte console-setup ein (1.21ubuntu9) ...
/[COLOR="red"]var/lib/dpkg/info/console-setup.config: line 1158: ISO-8859-15: command not found[/COLOR]
[COLOR="red"]dpkg: Fehler beim Bearbeiten von console-setup (--configure):
 Unterprozess post-installation script gab den Fehlerwert 127 zur?ck[/COLOR]
Fehler traten auf beim Bearbeiten von:
 console-setup
E: Sub-process /usr/bin/dpkg returned an error code (1)

locale -a output is:
C
de_DE
de_DE@euro
de_DE.utf8
en_US.utf8
POSIX

Hope this helps

---

### Post by macsaver on 2009-03-25
Solved the problem by setting all Language Vars manually - after that I could reinstall console-setup and now everything is fine

Thanks anyway

---

