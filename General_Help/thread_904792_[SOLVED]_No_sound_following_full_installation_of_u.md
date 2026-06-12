---
title: "[SOLVED] No sound following full installation of ubunti 8.04 LTS"
date: 2008-08-29
forum: General Help
---

### Post by Timmeh02 on 2008-08-29
Hi there, 

I recently switched to a full install of ubuntu 8.04 LTS and not only am I loving this system, but my teenage daughters are using words like "cool" and "sweet".  I thought I was going to have a battle on my hands but so far all is good.  There is one thing, when I did the complete install there is now no SOUND.  I have just installed a Sound Maker Value 5.1 PCI sound card.  There is a reference to installing the drivers in Linux but I don't know how to follow the instructions, they read like Latin to me.  I have also tried some of the step by step instructions using terminal but stumbled a bit when I was required to find files from a web site etc and use these files during that process.  Is there an easy to follow process to enable sound on my PC again.  A copy of the tar.gz is attached but installing it is the problem for me.  I'm brand new at these things. Please help, and thankyou.

---

### Post by spiderbatdad on 2008-08-29
Trying to find some good advice for you. Helping you with the commands for installing that driver looks easy enough, but I'm not sure installing that driver is the best course of action.
Ubuntu should detect the card for you and make use of existing drivers. I'm running Intrepid now, and sound has been much easier to enable.

I think you should post the output of a couple of commands, so that better assistance can be provided. From your terminal:
```
lspci
```

and

```
asoundconf list
```

---

### Post by Timmeh02 on 2008-08-29
> **spiderbatdad said:**
> Trying to find some good advice for you. Helping you with the commands for installing that driver looks easy enough, but I'm not sure installing that driver is the best course of action.
Ubuntu should detect the card for you and make use of existing drivers. I'm running Intrepid now, and sound has been much easier to enable.

I think you should post the output of a couple of commands, so that better assistance can be provided. From your terminal:
```
lspci
```

and

```
asoundconf list
```

Have followed your first steps with the results attached.  Excuse me if I don't reply immediately.  Just heading out for a while.  Thanks Tim

---

### Post by enzodad on 2008-08-29
No sound for me either i can get it to work period i put in those commands and got these results

chris@Enzo:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
chris@Enzo:~$ asoundconf list
Names of available sound cards:
ICH6
chris@Enzo:~$

---

### Post by markbuntu on 2008-08-29
Try my guide:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

It starts with the very basics of getting sound working and get complicateder and complicateder as you go along. If you follow all the links, you could spend days.. But anyway, I do not think you will need more than a few minutes. 

The AC'97 has been well and long suppported in linux/Ubuntu and the CMI cards are as well so it is probably some setup issue.

---

### Post by spiderbatdad on 2008-08-29
> **Timmeh02 said:**
> Have followed your first steps with the results attached.  Excuse me if I don't reply immediately.  Just heading out for a while.  Thanks Tim

Timmeh02,
I believe you may need to physically disconnect the other sound card from the motherboard. Then run the command:```
asoundconf set-default-card CMI8738
```then reboot.
I assume, but don't know, that you'll want to use alsa for running this sound card. Check synaptic package manager and install these packages:
alsa-base, alsaplayer-alsa, alsaplayer-common, alsaplayer-gtk, alsa-source, alsa-utils.

You may need to add backports to your software sources: use the search feature in synaptic for linux-backports-modules

Sorry if this is a pain. Just the first two instructions may get your sound card recognized. Then select Alsa from system>>preferences>>sound.
Good luck.

---

### Post by Timmeh02 on 2008-08-30
> **spiderbatdad said:**
> Timmeh02,
I believe you may need to physically disconnect the other sound card from the motherboard. 

spiderbatdad
I'm not sure what you mean by the 'other' sound card from the mother board.  I have the case open and when I look at the PCI slots there is only the new sound card and an original card from Acer which has two ports on the back with could connect to a telephone line so I'm guessing that was the card used as a modem for dial-up interenet access.  The only other thing I can see are cables running from the front headphone/mic jacks etc on to the motherboard, or else everything looks in-built on the motherboard. Timmeh02

---

### Post by Timmeh02 on 2008-08-30
> **markbuntu said:**
> Try my guide:

Thanks markbuntu,

Will try your guide now.  

Timmeh02

---

