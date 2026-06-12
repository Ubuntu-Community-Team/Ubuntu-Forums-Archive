---
title: "*** Cannot find kernel version in /lib/modules/2.6.18-6-686/build, is it configured?"
date: 2008-10-20
forum: General Help
---

### Post by zelekt on 2008-10-20
Hello.


I'm trying to install ndiswrapper, but I keep getting this error message when I install:

root@Ahlar ~/ndiswrapper-1.53 19:31:21  $
» make install
make -C driver install
make[1]: GÃ¥r til katalog '/root/ndiswrapper-1.53/driver'
Makefile:34: *** Cannot find kernel version in /lib/modules/2.6.18-6-686/build, is it configured?. Stop.
make[1]: Forlader katalog '/root/ndiswrapper-1.53/driver'
make: *** [install] Fejl 2


Any hints on what to do? :)

Thanks
Zelekt

---

### Post by Ayuthia on 2008-10-20
Do you have linux-headers-`uname -r` installed?  It looks like it might be missing. If you haven't already, you need to also install build-essential.

---

### Post by zelekt on 2008-10-20
It seems to be installed.

root@Ahlar ~/ndiswrapper-1.53 20:30:18  $
» uname -r
2.6.18-6-686


root@Ahlar ~/ndiswrapper-1.53 20:30:11  $
» apt-get install build-essential
Leser pakkelister ... Ferdig
Skaper oversikt over avhengighetsforhold ... Ferdig
build-essential er allerede nyeste versjon.

^ Translated : Build-essential is allready updated. <- Or something like that ;p 

Any other hits?

---

### Post by Nicsoft on 2008-12-29
Hello,

Did you get this resolved? I have similar problem. 

When I try to make ndiswrapper i get 

```
sudo make
make -C driver
make[1]: Entering directory `/home/niklas/Desktop/ndiswrapper-1.53/driver'
Makefile:34: *** Cannot find kernel version in /lib/modules/2.6.27-7-server/build, is it configured?.  Stop.
make[1]: Leaving directory `/home/niklas/Desktop/ndiswrapper-1.53/driver'
make: *** [all] Error 2
```

The headers are installed and the source to, I think. Perhaps I don't get the links correct configured? I created the link in this way:

```
sudo ln -s /usr/src/linux-source-2.6.27 /lib/modules/2.6.27-7-server/build
``` and when that is done I have the following link in /lib/modules/2.6.27-7-server/build: linux-source-2.6.27. Shouldn't it be the content for that folder that is presented there? If that was the case, then I think that kernel version should be found. 

Any ideas?

Regards,
Niklas

---

### Post by Nicsoft on 2008-12-29
Hello again,

This is what I did. I re-installed Ubuntu 8.10. Mainly because I wanted to start from a clean installation but also because I think I did install the acutal card after I installed Ubuntu before. Just to make sure I didn't do exactly in the same way again I installed the desktop version instead of the server version. 

I used the Network Manager Applet in the top-left to configure my network and unplugged the fixed cable. Voiala, not it works. 

So, I actually have no idea what all problems was, but most likely I messed up to much before and I didn't use the NM Applet before things were already destroyed. 

Best Regards,
Niklas

---

### Post by fibo.kowalsky on 2010-08-04
I am installing ndiswrapper on Qimo 2.0 for kids but there are similar problem:
```
Cannot find kernel version in lib/modules/2.6.32-21-generic/build, is it configured?
```
Qimo 2.0 is operational system build on Ubuntu 10.04 LTS
```
cat /etc/issue
Ubuntu 10.04 LTS \n \l
```
```
uname -r
linux nino-laptop 2.6.32-21-generic #32 Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
```
Also I have read some solutions of this problem about linking folders but problem is that there is no directory:
```
lib/modules/2.6.32-21-generic/build
```
and directory
```
/usr/src
```
is empty, no linux-sources there.

Can somebody tell me what is the problem?
Thank in advance

p.s. I am not experienced user of ubuntu :(

---

