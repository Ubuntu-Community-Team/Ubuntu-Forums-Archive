---
title: "NCTUns network simulator install error on ubuntu"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by blaivzzz on 2009-04-22
hallo, i`m getting an error when isntalling NCTUns netwrok emulator on my ubuntu 8.10 distro. i know that NCTUns is for fedora, but i found how to compile it. I`m quite new guy in linux and dont know what is wrong. this is the web from where i got all info [http://wiki.ehas.org/index.php?title=How_to_install_NCTUns_in_Debian/Ubuntu](http://wiki.ehas.org/index.php?title=How_to_install_NCTUns_in_Debian/Ubuntu) 
an in step [SIZE=2]Build NCTUns [SIZE=1]i`m getting an error :

   STATE: install new nctuns kernel or upgrade older nctuns kernel
fake_rpm
/bin/cp:[COLOR=Sienna] unable to check[/COLOR] &#8222;/boot/System.map-2.6.27.7-nctuns-20090319&#8220;: No such file or directory

   ERROR: copy System.map failed...

[COLOR=Sienna]unable to check[/COLOR] - is tranlsation from lithuanian language, becuse my distro runs on that language.
i have checked that there for sure is no file name  "[/SIZE][/SIZE][SIZE=2][SIZE=1]System.map-2.6.27.7-nctuns-20090319" . how can I get that file? If any body knows where i have done a mistake or had the same problem, please reply.
[/SIZE][/SIZE]

---

### Post by janfsd on 2009-05-04
Hi, I got past that part without problems. Make sure you modify all files exactly as it is written there. Maybe you made a small mistake.

---

### Post by blaivzzz on 2009-05-13
thanks, problem was with install.conf ;)

---

### Post by blaivzzz on 2009-05-14
ok, I installed all things that were required, everything i can get started (NCTUns GUI; dispatcher; coordinator), but when i try to simulate a network, NCTUns brakes down and turns off. Line in terminal:

Openfile:/home/kesa/NCTUns-5.0/examples/Demo31_GPRS_6_ms/Demo31_GPRS_6_ms.sim/Demo31_GPRS_6_ms.tcl----
Segmentation fault

is it working to you fine? with no errors? 

plz reply

---

### Post by janfsd on 2009-05-16
I got problems with the kernel patch, so I gave up and installed it in fedora, I got no problems there. 
Have you tried another example?

---

