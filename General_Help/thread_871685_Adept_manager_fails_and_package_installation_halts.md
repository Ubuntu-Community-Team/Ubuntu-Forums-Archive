---
title: "Adept manager fails and package installation halts"
date: 2008-07-27
forum: General Help
---

### Post by snirpyor on 2008-07-27
[LIST]
[*]Installation of kubuntu-restricted-packages failed
[COLOR="Silver"][*]Adept can't be started any more after this  RESOLVED [/COLOR] 
[/LIST]

Here is where it started: Installing kubuntu-restricted-packages the installation halted at sun-java6-bin. The details showed a user-agreement window for JDK. Nothing i could do there, so i was forced to exit, leaving uncommited changes.

Now the following question

**How do I remove or install the broken sun-java6-bin package?**


Apt-get fails in removing it:

```

sudo apt-get remove sun-java6-bin
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd
Reading state information... Klaar
The following packages were automatically installed and are no longer required:
  libdns32
Use 'apt-get autoremove' to remove them.
De volgende pakketten zullen VERWIJDERD worden:
  sun-java6-bin
0 pakketten opgewaardeerd, 0 pakketten nieuw geïnstalleerd, 1 te verwijderen en0 niet opgewaardeerd.
2 pakketten niet volledig geïnstalleerd of verwijderd.
After this operation, 0B of additional disk space will be used.
Wilt u doorgaan [J/n]? j
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: fout bij afhandelen van sun-java6-bin (--remove):
 Pakket is in een ernstige inconsistente status - u moet het opnieuw
 installeren alvorens het te verwijderen.
Fouten gevonden tijdens behandelen van:
 sun-java6-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

How do I get this in English?

---

### Post by snirpyor on 2008-07-27
Trying to install or remove any other package results in the following error:

```

U wilt waarschijnlijk 'apt-get -f install' uitvoeren om volgende op te lossen:  
De volgende pakketten hebben niet-voldane vereisten:                            
  sun-java6-bin: Vereisten: sun-java6-jre (= 6-06-0ubuntu1) maar het zal niet geïnstalleerd worden

```

Own translation
[I]
You would want to run 'apt-get -f install' to resolve the following:
The following packages have unresolved requirements:
 sun-java6-bin: Requirements: sun-java6-jre (= 6-06-0ubuntu1) but it will not be installed[/I]

Trying to run the install -f as suggested:
```

sudo apt-get -f install
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd
Reading state information... Klaar
Vereisten worden gecorrigeerd... Klaar
The following packages were automatically installed and are no longer required:
  libdns32
Use 'apt-get autoremove' to remove them.
De volgende extra pakketten zullen geïnstalleerd worden:
  sun-java6-bin sun-java6-jre
Voorgestelde pakketten:
  binfmt-support sun-java6-fonts sun-java6-plugin ia32-sun-java6-plugin
  ttf-wqy-zenhei
Aanbevolen pakketten:
  gsfonts-x11
De volgende NIEUWE pakketten zullen geïnstalleerd worden:
  sun-java6-jre
De volgende pakketten zullen opgewaardeerd worden:
  sun-java6-bin
1 pakketten opgewaardeerd, 1 pakketten nieuw geïnstalleerd, 0 te verwijderen en0 niet opgewaardeerd.
2 pakketten niet volledig geïnstalleerd of verwijderd.
Er moeten 0B/33,6MB aan archieven opgehaald worden.
After this operation, 96,4MB of additional disk space will be used.
Wilt u doorgaan [J/n]? j
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Instellen van libc6 (2.7-10ubuntu3) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: fout bij afhandelen van libc6 (--configure):
 subproces post-installation script gaf een foutwaarde 1 terug
Fouten gevonden tijdens behandelen van:
 libc6
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

This cannot be resolved by removing the lock in the following way:
```

sudo rm /var/lib/dpkg/lock

```

---

### Post by snirpyor on 2008-07-27
RESOLVED

reboot allowed me to do the installation again and I managed to work my way through the user agreement.

---

