---
title: "Upgrading Ubuntu 6.10 to Xubuntu 8.04.1"
date: 2008-09-02
forum: General Help
---

### Post by NeoAndersen on 2008-09-02
Hello!!

I've tried to install Xubuntu 8.04.1 i386 in a machine with AMD Duron(tm) Processor 1,20 GHz, 224 MB RAM. But there is an error...

Then I installed Ubuntu 6.10 version. And now I am trying to upgrade to 8.04.1 folowing these tips:
#

You can only directly upgrade to Ubuntu 7.04 ("Feisty Fawn") from Ubuntu 6.10 ("Edgy Eft") (see UpgradeNotes)
#

Be sure that you have all updates applied to Ubuntu 6.10 before you upgrade NOTE: edgy was removed from archives, so you need to change your apt sources.lists to point to [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)
#

The latest version of Update Manager (0.45.2) must be installed before you upgrade. Otherwise, you will receive an Authentication failed error. See here for instructions how to check if you have the required version.

The PROBLEM:
  I could not to apply any update to Ubuntu 6.10 and I don't know how to change my apt sources.lists... I couldn't upgrade my Update Manager from 0.45 to 0.45.2 version neither...

---

### Post by plucky on 2008-09-03
> **NeoAndersen said:**
> Hello!!

I've tried to install Xubuntu 8.04.1 i386 in a machine with AMD Duron(tm) Processor 1,20 GHz, 224 MB RAM. But there is an error...

Then I installed Ubuntu 6.10 version. And now I am trying to upgrade to 8.04.1 folowing these tips:
#

You can only directly upgrade to Ubuntu 7.04 ("Feisty Fawn") from Ubuntu 6.10 ("Edgy Eft") (see UpgradeNotes)
#

Be sure that you have all updates applied to Ubuntu 6.10 before you upgrade NOTE: edgy was removed from archives, so you need to change your apt sources.lists to point to [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)
#

The latest version of Update Manager (0.45.2) must be installed before you upgrade. Otherwise, you will receive an Authentication failed error. See here for instructions how to check if you have the required version.

The PROBLEM:
  I could not to apply any update to Ubuntu 6.10 and I don't know how to change my apt sources.lists... I couldn't upgrade my Update Manager from 0.45 to 0.45.2 version neither...


You cannot upgrade from "Edgy" to "Hardy" without going through "Fiesty" and "Gutsy" with all the updates.

> I've tried to install Xubuntu 8.04.1 i386 in a machine with AMD Duron(tm) Processor 1,20 GHz, 224 MB RAM. But there is an error...


**What is the error?**.

Have you verified the integrity of the CD?

It would probably be better to download the 8.04.1 Xubuntu Alternate Cd which is better for low memory installs,as it uses a text installer.

See this [link](http://cdimage.ubuntu.com/xubuntu/releases/hardy/release/)


Good Luck

---

### Post by hyper_ch on 2008-09-03
228 mb ram is not sufficient for a Desktop CD install. use alternate.

---

### Post by Zorael on 2008-09-03
I'll take this opportunity to advise you to just do a clean 8.04.1 installation. Backing up settings is less work than trying to fix all those small bugs that come from doing dist-upgrades. :<

I generally grab my home directory and my /etc/samba/smb.conf for samba settings, then leave the rest to be wiped.

---

### Post by NeoAndersen on 2008-09-05
To say the truth, my colleage computer are in a sorry state... Literally, there was dust in one piece of RAM hardware, then I just beat it in my belly to get rid of the dust and connect it again in the motherboard... Now I have about 500MB of RAM...
So I could install the live version of 
Xubuntu 8.04.1 i386. But sometimes the operational system just stops and I lose the mouse control... But I blame the sorry situation of the hardware...

He bought another computer with one 160GB HD splited in 2 partition of 80GB, in the first XP, in the second I installed Ubuntu without any problem (till now, as I choose "logical partition" and "end" without knowing what does that mean...). If you have any comments, it will help me to install Ubuntu for other friends properly here in my city.

---

### Post by NeoAndersen on 2008-09-05
Now I would like to receive another piece of advice without begin another thread for it...

I have 2 HDs, first 500GB, second 320GB.
I've installed XP in the first one in about 120GB. Now I want to install Ubuntu in the 380GB of the fist HD and Kubuntu in the 320HD or vice-versa if that is better.

I don't want lost XP again as it happens 2 months ago... I need it while I don't learn to use a homestudio software in Ubuntu...

What your advice is?

---

