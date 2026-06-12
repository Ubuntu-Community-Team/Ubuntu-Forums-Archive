---
title: "ubuntu :strange boot problem"
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by notmyday on 2008-12-16
Hi guys ,here we go !
So ,i downloaded the very latest version of ubuntu, you can install it from windows so no cd is needed.
Everything went fine. 
So im almost in ubuntu .im asked for my username and password ,entered both but then nothing happens!
I tried again and again ,sometimes i just get black screens.
Then i tried this safeboot method where you could update modify and correct some things.
So i tried to update in this "safeboot" menu.
And heres another bad thing. 
ubuntu connects to some pages, but cant download the files ! 
Thats because ubuntu cant find these files or these files dont excist.
Path was something like "archive.ubuntu.de" yeah ,german =)
Anyway ,the system check was allright you can do on this safeboot menu was allright!
i hope you can understand my english

rlly thankful if you halpz me plz =(

konny

---

### Post by albinootje on 2008-12-16
> **notmyday said:**
> Hi guys ,here we go !
So ,i downloaded the very latest version of ubuntu, you can install it from windows so no cd is needed.


So you're using Wubi, right ?
> 
Then i tried this safeboot method where you could update modify and correct some things.
So i tried to update in this "safeboot" menu.
And heres another bad thing. 
ubuntu connects to some pages, but cant download the files ! 
Thats because ubuntu cant find these files or these files dont excist.
Path was something like "archive.ubuntu.de" yeah ,german =)
Anyway ,the system check was allright you can do on this safeboot menu was allright!
You booted in the "recovery mode", and then you did choose "drop to root shell" ?
If so, then try (in the root shell) : dhclient
After that do : apt-get update

(And it was probably about de.archive.ubuntu.com)

---

### Post by notmyday on 2008-12-16
yes ,its wubi
ive tried all you say ,but its still the same!
i enter my username ,my password and all i get to see is the background ,nothing more .
although the computer keeps loading for 5 seconds...

---

### Post by notmyday on 2008-12-16
so
instead of apt-get update i typed in apt-get upgrade ,which made the system work now ! hooray !

---

