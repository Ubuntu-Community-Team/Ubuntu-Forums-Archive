---
title: "How to find out what version of Ubuntu I am using??"
date: 2006-01-29
forum: Installation &amp; Upgrades
---

### Post by Jiketsu on 2006-01-29
Hi hi,

I know it might be a silly question, because If I download and install 5.10 then obviously I'd be using 5.10 right? But let's pretend it magically appeared and I had no idea.. how would I find out??

I originally installed 5.04 . I had a repository problem, where sudo apt-get install firestarter wouldnt work. Couldnt find the package. So while trying to find a thread to fix repositories (which I didnt find, just like I couldnt for this question) I came across the upgrade guide. So I upgraded to 5.10 using apt-get.

sudo apt-get update
sudo apt-get dist-upgrade

So it finished after a bit. But for fun I wanna check and see if it says 5.10 but where does it show up? The good news is, my repositories seem to be fixed because I can apt-get firestarter just fine now :)

Thank you for your help!

-Ji

---

### Post by az on 2006-01-29
5.10 is a release.  It is the contents of the 5.10 (breezy) repositories.  If you have dist-upgraded to those repositories and there are no packages held back, you are running breezy.

---

### Post by Jiketsu on 2006-01-29
So there isnt ever a version number posted anywhere within the distro?

---

### Post by SavageBeginner on 2006-01-29
```
cat /etc/lsb-release
```
or```
cat /etc/issue
```

---

### Post by o_fortuna on 2006-01-29
[QUOTE=Jiketsu]Hi hi,

I know it might be a silly question, because If I download and install 5.10 then obviously I'd be using 5.10 right? But let's pretend it magically appeared and I had no idea.. how would I find out??

I originally installed 5.04 . I had a repository problem, where sudo apt-get install firestarter wouldnt work. Couldnt find the package. So while trying to find a thread to fix repositories (which I didnt find, just like I couldnt for this question) I came across the upgrade guide. So I upgraded to 5.10 using apt-get.

sudo apt-get update
sudo apt-get dist-upgrade

So it finished after a bit. But for fun I wanna check and see if it says 5.10 but where does it show up? The good news is, my repositories seem to be fixed because I can apt-get firestarter just fine now :)

Thank you for your help!

-Ji[/QUOTE]
Do this in a console (Applications-->Applications-->Terminal for Breezy and type this:
```
cat /etc/issue
```
This will probably Ubuntu 5.10 if you have that installed.

Edit: Durn, beat to it! :/

---

### Post by Jiketsu on 2006-01-29
Exactly what I was looking for. Thank you both. Appreciated :)

---

