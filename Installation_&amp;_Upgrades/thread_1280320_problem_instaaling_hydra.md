---
title: "problem instaaling hydra"
date: 2009-10-01
forum: Installation &amp; Upgrades
---

### Post by ramazani on 2009-10-01
hi i been trying to install hydra in ubuntu 9.04 but anytime i tried i get error i been looking on google almost two days, i could say been searching more then 10 houre to sort it out no chance anyone know how to sort out this  NOT found, module sapr3 disabled and that NOT found, module ssh2 disabled


Starting hydra auto configuration ...

Checking for openssl (libssl/ssl.h) ...
                                    ... NOT found, SSL support disabled
Get it from [http://www.openssl.org](http://www.openssl.org)
Checking for Postgres (libpq) ...
                              ... found
Checking for SVN (ibsvn_client-1 libapr-0.so libaprutil-0.so) ...
                              ... found
Checking for SAP/R3 (librfc/saprfc.h) ...
                                      ... NOT found, module sapr3 disabled
Get it from [http://www.sap.com/solutions/netweaver/linux/eval/index.asp](http://www.sap.com/solutions/netweaver/linux/eval/index.asp)
Checking for libssh (libssh/libssh.h) ...
                                      ... NOT found, module ssh2 disabled
Get it from [http://0xbadc0de.be/](http://0xbadc0de.be/) - use v0.11!

Hydra will be installed into .../bin of: /usr/local
  (change this by running ./configure --prefix=path)

Writing Makefile.in ...

NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES
=======================================================================
ARM/PalmPilot users: please run ./configure-arm or ./configure-palm respectivly

now type "make"

---

### Post by cariboo on 2009-10-01
OpenSSL is in the repositories. You can install it using:

```
sudo apt-get openssl
```

---

### Post by ramazani on 2009-10-02
> **cariboo907 said:**
> OpenSSL is in the repositories. You can install it using:

```
sudo apt-get openssl
```

when i try to install openssl it says
openssl is already the newest version.

i tried that before i been searching every page on google too many people got this problem but there is noone to fix it

---

### Post by serejj on 2009-11-25
code # sudo apt-get install libssl-dev libssh-dev libssh2-1-dev -y  "that's the right command"

note: to compile the source code you need to install to many dev libs so do this in a console:

code # sudo gedit /etc/apt/sources.list

and add this line:
deb [http://repo.offensive-security.com/dist/bt4](http://repo.offensive-security.com/dist/bt4) binary/

code # sudo apt-get update
don't worry about the gpg key error

code # sudo apt-get install hydra

to use xhydra:

code # xhydra

in some cases you must use sudo

code # sudo xhydra

give some feedback please

remember this: §erejj is your friend but google is your best friend

by §erejj

---

