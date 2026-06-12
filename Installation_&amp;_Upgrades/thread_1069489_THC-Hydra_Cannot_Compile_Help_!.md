---
title: "THC-Hydra Cannot Compile Help !"
date: 2009-02-14
forum: Installation &amp; Upgrades
---

### Post by GGGeek on 2009-02-14
k, here's the situation: 

./configure 

```
Starting hydra auto configuration ...

Checking for openssl (libssl/ssl.h) ...
... found
Checking for Postgres (libpq) ...
... found
Checking for SVN (ibsvn_client-1 libapr-0.so libaprutil-0.so) ...
... found
Checking for SAP/R3 (librfc/saprfc.h) ...
... NOT found, module sapr3 disabled
Get it from http://www.sap.com/solutions/netweaver/linux/eval/index.asp
Checking for libssh (libssh/libssh.h) ...
... found
NOTE: ensure that you have libssh v0.11 installed!! Get it from http://0xbadc0de.be !

Hydra will be installed into .../bin of: /usr/local
(change this by running ./configure --prefix=path)

Writing Makefile.in ...

NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES NOTES
=======================================================================
ARM/PalmPilot users: please run ./configure-arm or ./configure-palm respectivly

now type "make"
```

i have downloaded openssl from openssl.org
i have downloaded libssh from 0xbadc0de.be but there was some problems, 
on make it have gived a problems so i have installed a .dev packgage so the problem was soluted... and the ./configure on the hydra have found the libssh 

but when i type # make
```

cd hydra-gtk && ./make_xhydra.sh
Trying to compile xhydra now (hydra gtk gui) - dont worry if this fails, this is really optional ...
Error: configure wasnt happy. Analyse this:
configure: error: Library requirements (gtk+-2.0 >= 2.0.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
make: [xhydra] Error 1 (ignored)

```

and when i type # make install

```

test -e hydra.exe && touch Makefile || strip hydra pw-inspector
make: [strip] Error 1 (ignored)
test -e hydra.exe && strip hydra.exe pw-inspector.exe || touch hydra
test -e xhydra && strip xhydra || touch Makefile
test -e hydra.exe && touch Makefile || cp hydra pw-inspector /usr/local/bin && cd /usr/local/bin && chmod 755 hydra pw-inspector
test -e hydra.exe && cp hydra.exe pw-inspector.exe /usr/local/bin && cd /usr/local/bin && chmod 755 hydra.exe pw-inspector.exe || touch Makefile
test -e xhydra && cp xhydra /usr/local/bin && cd /usr/local/bin && chmod 755 xhydra
make: [install] Error 1 (ignored)
root@fuzzy-desktop:/home/fuzzy/Desktop/hydra-5.3-src# gedit Makefile
No protocol specified

(gedit:8231): Gtk-WARNING **: cannot open display: :0.0
```

PLS HELP...

---

### Post by GGGeek on 2009-02-14
Can someone help?

---

