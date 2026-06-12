---
title: "Problem installing xubuntu 8.1"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by achaiah on 2009-03-16
Hello;

 I am having problems installing XUbuntu 8.1 (also tried Ubuntu 8.1 (for 64 bit AMD)).
I start the installation and after the Splash screen disappears the screen goes blank (I can switch to the terminal window with Ctrl-Alt-F1 (Ctrl-Alt-F7 does not show anything... the monitor goes to sleep)). I have tried "startx" in the terminal window and it states that there is a screen running at 0. I have tried "gdm" and it states that gdm is already running. I have also tried adding "acpi=off" and "noapic" to the boot parameter and still the same result. 
 I am running a Gigabyte ga-ma78 motherboard (PhenomII 940), Sata hard drive/ cdrom and a Radeon HD 4670. 
 Any help would be greatly appreciated.

Achaiah

---

### Post by zvacet on 2009-03-18
It look like video driver issue,but I can be wrong.Boot in recovery mode and backup your xorg.conf

```
 cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

then 

```
dpkg-reconfigure -phigh xserver-xorg
```

After this you should have minimal video and then you can search for your card drivers.

---

### Post by achaiah on 2009-03-18
Thank you. I will try that right away. I can't remember right now if I have tried that before (I haven't been able to install xubuntu yet, it is running off of the live cd at this point). I will update once I have tried this.

---

### Post by achaiah on 2009-03-19
I tried the  cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak and dpkg-reconfigure -phigh xserver-xorg and was still not able to get any video for the setup. I am only able to see the terminal window. 
I did some more digging and found in the kern.log (/var/log/kern.log) that for all of my SATA drives (I don't have any IDE drives anymore) there was an error message "ata## failed due to hw bug". My motherboard has an AMD 780G chipset and am wondering if there are issues with it.

---

### Post by zvacet on 2009-03-19
I have motherboard with same chipset ( Gigabyte MA78GM-S2H ) and I didn´t expirienced any problem like yours.

---

### Post by achaiah on 2009-03-19
It must have something to do with the video card then (Sapphire Radeon HD 4670). I have no problems with XP/ Vista or OSX (Lawless 10.5.4). Just to satisfy my curiosity I am going to try installing on a spare drive that I have.
How do you have your BIOS set for the Sata Hard Drive. I have tried AHCI mode and IDE mode and still no luck in getting XUbuntu installed.

---

### Post by tom4jean on 2009-03-20
I don't know if it is related, but I had issues installing on an old desktop with the installer hanging on a black screen after I tried to get into the live desktop and even though I had a good md5sum on the iso and what I thought was a good disc burned I tried burning another disc at a lower rate and it worked after that. Turned out to just be a bad installation disc.

---

### Post by jespdj on 2009-03-20
Note: There is no Ubuntu / Xubuntu version 8.1.

It is called **8.10**: 8 = 2008, 10 = October. The next version will be **9.04** (April 2009).

---

### Post by achaiah on 2009-03-20
Thanks. I will try burning the disc at a slower speed and see what happens. 
Sorry about the 8.1 I guess I forgot to include the 0 at the end.

---

### Post by achaiah on 2009-03-20
Tom4Jean... thank you for the suggestion. I burned the same iso file at a slower speed (2x) and the installation was successful. I was now able to install XUbuntu 8.10 on my system with no problems. Thanks again for the assistance.

---

