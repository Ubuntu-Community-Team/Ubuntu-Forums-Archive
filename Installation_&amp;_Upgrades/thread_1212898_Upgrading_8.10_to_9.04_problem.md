---
title: "Upgrading 8.10 to 9.04 problem"
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by errolgreer on 2009-07-14
****I bought Ubuntu User mag which included a 9.04 DVD. From 8.10 I inserted the DVD. 2 windows appeared: "Upgrade volume detected, A distribution volume with software packages has been detected, Would you like to upgrade from it automatically ? The 2nd: "This medium contains software intended to be automatically started, Would you like to run it ?

If I click on "Run" (2nd window), I get "Error autorunning software, cannot find the autorun program." I clicked OK. Then clicked "run upgrade" on 1st window. Nothing happens ! I tried ignoring the 2nd window and clicked "Run upgrade" on the 1st window. NOTHING !

If I open the DVD, how do I get the upgrade to run ? I do not want to delete 8.10 and replace it with 9.04 because of all my existing settings and drivers etc. I am a fairly new  Ubuntu user.

Thanks, Errol****

---

### Post by sp00f3r on 2009-07-14
Hi errolgeer,

Don't know why that DVD doesn't work out for you, but if you want to upgrade to Jaunty (9.04) without losing your personal settings etc. use the Update Manager. You will need an internet connection btw. This worked for me. 

More detaisl can be found here: [http://www.ubuntu.com/getubuntu/upgrading]("http://www.ubuntu.com/getubuntu/upgrading")

Hope this helps,
$p00f3r

---

### Post by errolgreer on 2009-07-14
How big was the download file ? ie how many megabytes ? We have a cap on our ASDL here of only 1GB per month. Also our so-called broadband is only 384Kb, so it could take a very long time !

---

### Post by sp00f3r on 2009-07-14
I don't remember the exact download size, but I can't imagine it was larger than 300-400MB. The Ubuntu-9.04-desktop-i386.iso file on the Ubuntu website is "only" 698MB, and that is including all stuff that you will not update when you go to Jaunty: OpenOffice, GIMP, etc. 

By the way, does Uupdate Manager not give you the download size? If it doesn't than type this in a console:
```
sudo apt-get dist-upgrade
```
This should display the download size before upgrading.

(see also: [http://ubuntuguide.org/wiki/Ubuntu:Jaunty#Upgrading_Intrepid_to_Jaunty]("http://ubuntuguide.org/wiki/Ubuntu:Jaunty#Upgrading_Intrepid_to_Jaunty")

$p00f3r

---

### Post by errolgreer on 2009-07-15
Thanks, but the file is too large.

I'm sure that there must be some file on the DVD that I can execute to start an upgrade ? I see lots of folders and files but their names do not explain what they do ! So if anyone can help here I would be grateful.

Many thanks

---

### Post by LouRan on 2009-07-15
I have update manager and a broadband connection and so far I have accepted all the available updates but I've been scared silly to allow the upgrade of the OS to 9.04! Am I being ridiculous? Should I just do it and not worry that it will change any of my settings or perturb my files and life? I need encouragement or cautioning, either would be appreciated. I currently remain in stasis. :neutral:

---

### Post by sp00f3r on 2009-07-15
I guess thta really depends on what you do with your computer. Do you use Ubuntu main-stream packages or do you use exotic software that you can't live without which might give you troubles?

I have Ubuntu installed on a pretty old AMD2200+ (KT333 chipset) machine which I mainly use for playing MP3's (Audicous), Java applications (Sun Java) and I use LIRC for remote control of Audicous with an Asus DH remote. I upgraded this machine with the Update Manager from 8.04 to 8.10 and later to 9.04 without any issues!

If you make a backup before you upgrade I would say: GO!:P

---

### Post by LouRan on 2009-07-15
Thanks for the encouragement and you said what I thought I probably should do anyway if I was gonna bite the bullet and that is back things up, it's mostly data files that need backed up not applications because nothing terribly exotic is going on with my computer. I'm gonna GO FOR IT! :guitar:

impossible guitar parts ensue...

---

