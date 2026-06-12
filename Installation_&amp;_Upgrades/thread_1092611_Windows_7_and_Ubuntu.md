---
title: "Windows 7 and Ubuntu"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by Hogosha on 2009-03-10
I am having an issue with installing Ubuntu inside of Windows 7.

I had previously installed it inside of Vista and it worked fine. I upgraded to 7 and i could still boot to it. I decided i wanted to start over in Linux so i deleted it and now when i reinstall it it is not a boot option.

---

### Post by Neo_The_User on 2009-03-10
I'm confused. Do you have windows or linux on your HDD right now?

---

### Post by Hogosha on 2009-03-10
windows is installed and i am trying to use the ubuntu disc to install linux inside of windows

---

### Post by Silent Warrior on 2009-03-10
Are you installing Ubuntu on the same harddrive? If not, check your BIOS - you might need to set your boot-order to begin with the Linux-HD, to get GRUB. (Needless to say, if this buggers up your Win7 beta [Call that an upgrade, do you? You must have had a really interesting experience with Vista. :)] you should go back into BIOS and change the order back.)

---

### Post by Hogosha on 2009-03-10
i thought with the option to install inside of windows that is on 8.04 GRUB and LiLo were not used, it was all inside the windows boot loader. It is practically treated like a windows program with an uninstaller in the ubuntu folder in windows. That is what i used to get rid of it and now, after reinstalling, the menu for which OS to boot to is no longer appearing, it goes strait to 7.

(and no i did not have that bad of an experience with Vista, i just read the specs on 7 and saw that it used less ram and with 2GB i will take what i can get)

---

### Post by Hogosha on 2009-03-11
i have discovered that the windows 7 boot manager is slightly different than the windows vista boot manager so the installer for Ubuntu is not writing it correctly for the given manager. Is there a work around for this?

---

### Post by Hogosha on 2009-03-11
i got it. i edited the boot manager to recognize linux and moved the linux mbr menu file to the root folder and viola!

I am currently posting from linux

---

### Post by theozzlives on 2009-03-11
AOL won't install on Windows 7, it's a beta and should be reported to Microsoft.

---

### Post by martialartist81 on 2009-03-12
> **Hogosha said:**
> i got it. i edited the boot manager to recognize linux and moved the linux mbr menu file to the root folder and viola!

I am currently posting from linux

Hogosha, mind walking us through it step by step?  I'm running/testing Windows 7 and I'm jonesin' to get 8.10 working on the same PC.  I have one hdd, so I'll be dual-booting off of that.

I'm assuming that while in Windows 7, you ran the installer inside the OS.  Once it finished installing, you reboot the PC, goes straight into Windows 7 like it doesn't even see GRUB or any other boot file... at least that's what I experienced.

Let us know!  Gotta get my Ubuntu Java fix!

---

### Post by Hogosha on 2009-03-12
1. i installed it normally and rebooted. It indeed went straight to  7

2. Install Easy BCD and add linux to the mbr. Save that. There are two options here, a complicated one that could stop your computer from booting all together or an easy one, i shall use the easy one.

3. copy the wubildr.mbr and menu files  in the /ubuntu/winboot directory into the /NST folder that EasyBCD created. Change the name of the wubildr.mbr to NeoGrub.mbr

4. ...

5. Profit

Reboot and Linux should be there. It Will be labeled Neo Smart Linux unless you Change the name in EasyBCD when you first add it to the boot manager list. Name it what ever you want.

---

### Post by israa hasan on 2009-08-26
hi
i have installed ubuntu inside windows7 normaly, then i installed the Easy BCD, the os menu appeared and it had two choices between ubuntu and windows7 but when i choosed ubuntu it did not work there was an error!
please i need the solution!
thanks

---

### Post by israa hasan on 2009-08-26
hi
i have installed ubuntu inside windows7 normaly, then i installed the Easy BCD, the os menu appeared and it had two choices between ubuntu and windows7 but when i choosed ubuntu it did not work there was an error!
please i need the solution!
thanks

---

### Post by Mark Phelps on 2009-08-26
israa:

Did you see the previous posts in this thread and try the solution offered?

Wubi is NOT guaranteed to work with Windows 7.  They are working on that update but it is not available yet.

---

### Post by israa hasan on 2009-08-28
I tried the Hogosha solution, as I said I install ubuntu normaly then I installed the Easy BCD , the os menu appeared but when I choosed ubuntu, it didn't work!.
I think that there is a special version of ubuntu which work inside windows7!

---

