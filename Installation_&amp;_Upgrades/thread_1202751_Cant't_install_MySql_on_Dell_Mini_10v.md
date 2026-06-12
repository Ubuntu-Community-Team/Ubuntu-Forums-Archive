---
title: "Cant't install MySql on Dell Mini 10v"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by hgeis on 2009-07-02
Hi,

For nearly a week I've been trying to install MySql on my new Dell Mini 10v under Ubuntu 8.04/Gnome. I have again tried to install the programme by command:
**sudo apt-get -f install** after several attempts to install/uninstall the software.

This happens after downloading the packages mysql-server and mysql-client. Sorry, error messages are in German. Anybody can help?

I have also failed to cleanly uninstall both packages. Neither apt-get nor dpkg let me do that.

Cheers.

Heinrich

Hole:1 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/public
mysql-client-5.0 5.0.51a-3ubuntu5.4 [7840kB]
Hole:2 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main
mysql-server-5.0 5.0.51a-3ubuntu5.1 [27,4MB]               
Es wurden 35,2MB in 1min49s geholt
(322kB/s)                                                                                
Vorkonfiguration der Pakete ...
Wähle vormals abgewähltes Paket mysql-client-5.0.
(Lese Datenbank ... 104463 Dateien und Verzeichnisse sind derzeit
installiert.)
Entpacke mysql-client-5.0
(aus .../mysql-client-5.0_5.0.51a-3ubuntu5.4_lpia.deb) ...
Wähle vormals abgewähltes Paket mysql-server-5.0.
Vorbereiten zum Ersetzen von mysql-server-5.0 5.0.51a-3ubuntu5.1
(durch .../mysql-server-5.0_5.0.51a-3ubuntu5.1_lpia.deb) ...
/etc/lsb-base-logging.sh: line 84: INITOUTPUT: unbound variable
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: Warnung - altes pre-removal-Skript wurde mit Fehler-Status 1
beendet
dpkg - probiere stattdessen Skript aus dem neuen Paket ...
/etc/lsb-base-logging.sh: line 84: INITOUTPUT: unbound variable
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: Fehler beim Bearbeiten
von /var/cache/apt/archives/mysql-server-5.0_5.0.51a-3ubuntu5.1_lpia.deb
(--unpack):
 Unterprozess neues pre-removal-Skript gab den Fehlerwert 1 zurück
/etc/lsb-base-logging.sh: line 84: INITOUTPUT: unbound variable
invoke-rc.d: initscript mysql, action "stop" failed.
/etc/lsb-base-logging.sh: line 84: INITOUTPUT: unbound variable
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: Fehler beim Aufräumen:
 Unterprozess post-installation script gab den Fehlerwert 1 zurück
Fehler traten auf beim Bearbeiten von:
 /var/cache/apt/archives/mysql-server-5.0_5.0.51a-3ubuntu5.1_lpia.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

