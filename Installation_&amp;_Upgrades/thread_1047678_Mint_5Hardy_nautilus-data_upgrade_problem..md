---
title: "Mint 5/Hardy nautilus-data upgrade problem."
date: 2009-01-22
forum: Installation &amp; Upgrades
---

### Post by sdellysse on 2009-01-22
I just installed Linux Mint 5 x86_64 earlier today. Even though it's not officially ubuntu, since it is based off of Hardy, I thought I could get some help here.

Tried to update the the packages, and synaptic failed. Been doing a few things on my own, cleared the downloaded packages, retrying. Didn't help.

```
sdellysse@uuber ~ $ sudo apt-get update && sudo apt-get upgrade
[sudo] password for sdellysse:
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_US                                                                                       
Ign http://packages.linuxmint.com elyssa Release.gpg                                                                                                       
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US                                                                                 
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US                                                                         
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US                                                                       
Hit http://security.ubuntu.com hardy-security Release                                                                                           
Hit http://archive.ubuntu.com hardy Release.gpg                                                                 
Ign http://archive.ubuntu.com hardy/main Translation-en_US                                 
Hit http://archive.canonical.com hardy Release.gpg                                                             
Ign http://archive.canonical.com hardy/partner Translation-en_US                                               
Ign http://packages.linuxmint.com elyssa/main Translation-en_US                           
Ign http://packages.linuxmint.com elyssa/upstream Translation-en_US                       
Ign http://packages.linuxmint.com elyssa/import Translation-en_US                         
Ign http://archive.ubuntu.com hardy/restricted Translation-en_US                           
Ign http://archive.ubuntu.com hardy/universe Translation-en_US                             
Ign http://archive.ubuntu.com hardy/multiverse Translation-en_US                           
Hit http://archive.ubuntu.com hardy-updates Release.gpg                                   
Ign http://archive.ubuntu.com hardy-updates/main Translation-en_US                         
Ign http://archive.ubuntu.com hardy-updates/restricted Translation-en_US                   
Ign http://archive.ubuntu.com hardy-updates/universe Translation-en_US                     
Ign http://archive.ubuntu.com hardy-updates/multiverse Translation-en_US                   
Hit http://archive.canonical.com hardy Release                                                                   
Hit http://security.ubuntu.com hardy-security/main Packages                                                     
Hit http://packages.medibuntu.org hardy Release.gpg                                                           
Hit http://archive.ubuntu.com hardy Release                                                                                                     
Get:1 http://packages.linuxmint.com elyssa Release [7853B]                                                                                                 
Hit http://security.ubuntu.com hardy-security/restricted Packages                                                                                           
Hit http://security.ubuntu.com hardy-security/universe Packages                                                                                       
Hit http://security.ubuntu.com hardy-security/multiverse Packages                                                                                     
Hit http://archive.canonical.com hardy/partner Packages                                                                                               
Hit http://archive.ubuntu.com hardy-updates Release                                                                             
Hit http://archive.ubuntu.com hardy/main Packages                                                         
Hit http://archive.ubuntu.com hardy/restricted Packages                   
Hit http://archive.ubuntu.com hardy/universe Packages                     
Hit http://archive.ubuntu.com hardy/multiverse Packages                   
Ign http://packages.medibuntu.org hardy/free Translation-en_US           
Hit http://archive.ubuntu.com hardy-updates/main Packages                                                 
Hit http://archive.ubuntu.com hardy-updates/restricted Packages                                     
Hit http://archive.ubuntu.com hardy-updates/universe Packages                                       
Hit http://archive.ubuntu.com hardy-updates/multiverse Packages                                     
Ign http://packages.linuxmint.com elyssa/main Packages                                               
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US             
Ign http://packages.linuxmint.com elyssa/upstream Packages                     
Ign http://packages.linuxmint.com elyssa/import Packages                       
Hit http://packages.linuxmint.com elyssa/main Packages                         
Hit http://packages.medibuntu.org hardy Release                               
Hit http://packages.linuxmint.com elyssa/upstream Packages                     
Hit http://packages.medibuntu.org hardy/free Packages                         
Hit http://packages.linuxmint.com elyssa/import Packages                       
Hit http://packages.medibuntu.org hardy/non-free Packages
Fetched 7853B in 1s (4899B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up nautilus-data (1:2.22.5.1-0ubuntu1) ...
/usr/share/gconf/schemas/apps_nautilus_preferences.schemas:21962: parser error : expected '>'
rate soltato le cartelle. In caso contrario sono mostrati sia le cartelle .</li
                                                                               ^
/usr/share/gconf/schemas/apps_nautilus_preferences.schemas:21962: parser error : Opening and ending tag mismatch: long line 21962 and li
rate soltato le cartelle. In caso contrario sono mostrati sia le cartelle .</li
                                                                               ^
/usr/share/gconf/schemas/apps_nautilus_preferences.schemas:21962: parser error : Opening and ending tag mismatch: locale line 21960 and long
o le cartelle. In caso contrario sono mostrati sia le cartelle .</li file.</long
                                                                               ^
/usr/share/gconf/schemas/apps_nautilus_preferences.schemas:21963: parser error : Opening and ending tag mismatch: schema line 21770 and locale
      </locale>
               ^
/usr/share/gconf/schemas/apps_nautilus_preferences.schemas:22184: parser error : Opening and ending tag mismatch: schemalist line 2 and schema
    </schema>
             ^
/usr/share/gconf/schemas/apps_nautilus_preferences.schemas:22387: parser error : expected '>'
long>Se impostata a VERO, è presente sulla scrivania un&apos;icona .</lrimanda
                                                                               ^
/usr/share/gconf/schemas/apps_nautilus_preferences.schemas:22387: parser error : Opening and ending tag mismatch: long line 22387 and lrimanda
long>Se impostata a VERO, è presente sulla scrivania un&apos;icona .</lrimanda
                                                                               ^
/usr/share/gconf/schemas/apps_nautilus_preferences.schemas:22387: parser error : Opening and ending tag mismatch: locale line 22385 and long
è presente sulla scrivania un&apos;icona .</lrimanda alla cartella home.</long
                                                                               ^
/usr/share/gconf/schemas/apps_nautilus_preferences.schemas:22388: parser error : Opening and ending tag mismatch: schema line 22186 and locale
      </locale>
               ^
/usr/share/gconf/schemas/apps_nautilus_preferences.schemas:22629: parser error : Opening and ending tag mismatch: gconfschemafile line 1 and schema
    </schema>
             ^
/usr/share/gconf/schemas/apps_nautilus_preferences.schemas:22631: parser error : Extra content at the end of the document
    <schema>
    ^
dpkg: error processing nautilus-data (--configure):
subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of nautilus:
nautilus depends on nautilus-data (>= 1:2.22); however:
  Package nautilus-data is not configured yet.
nautilus depends on nautilus-data (<< 1:2.23); however:
  Package nautilus-data is not configured yet.
dpkg: error processing nautilus (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-sendto:
nautilus-sendto depends on nautilus-extensions-2.0; however:
  Package nautilus-extensions-2.0 is not installed.
  Package nautilus which provides nautilus-extensions-2.0 is not configured yet.
dpkg: error processing nautilus-sendto (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-share:
nautilus-share depends on nautilus (>= 2.10); however:
  Package nautilus is not configured yet.
dpkg: error processing nautilus-share (--configure):
dependency problems - leaving unconfigured
Errors were encountered while processing:
nautilus-data
nautilus
nautilus-sendto
nautilus-share
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Anyone got any ideas?

---

