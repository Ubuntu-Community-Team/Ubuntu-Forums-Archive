---
title: "Problem with booting"
date: 2009-04-06
forum: Installation &amp; Upgrades
---

### Post by Outrak on 2009-04-06
Hey all,
Im very new at linux and im having some issues just getting the darn thing booted. I am running a Acer aspire 6530 with amd turion 64 dual core processor, Ati radeon HD 3470 X2 video card. 3 gigs of ram and vista. I have tried burning the 64bit version to a disk and ive been able to boot with the disc, however during the actual boot-up after the loading bar it only displays a bunch of text about a sudo root command, and then ubuntu@ubuntu:

I have tried both the 64 and the 32, i have tried booting from a usb as well as burnt discs. Why cant i get to the GUI?

---

### Post by upchucky on 2009-04-06
since you did not say if ubuntu is the only os on the drive, boot with the live cd, 

then download this

[http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055) 

then do this

```
sudo bash ~/Desktop/boot_info_script*.sh

```

post the results here for booting advice.


your sys did boot to ubuntu, but only in the command-line mode.
if it has windows on it then you will get more advice on how to set up both.
in the meantime you may want to read about screen resolutions and setting up graphics displays in the xorg.conf file.

the xorg.conf is what needs to be set up to get you a graphical display.

---

### Post by Outrak on 2009-04-06
hmmm, how do i download that file when i am booting with the live cd, all i have is the command line mode.
like i said im new at this.
requesting further assistance!

---

### Post by upchucky on 2009-04-06
if the live cd is not getting to a graphic desktop then you can try downloading the alternate ubuntu live cd, it has some different detection and settings for cranky machines.

if you can find out what the vid card is in the machine you can google it to see if it is a supported card.

you still have not indicated if windows is on the machine, if it is then windows settings somewhere in the control panel will tell you what the card is.

---

### Post by Outrak on 2009-04-06
> **Outrak said:**
> Hey all,
 I am running a Acer aspire 6530 with amd turion 64 dual core processor, Ati radeon HD 3470 X2 video card. 3 gigs of ram and vista.

I am dual booting with vista, I have 2 radeon 3470 cards running with crossfire. 
I will try the alternate disc and see if it works.

ill post with the results

---

