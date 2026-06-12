---
title: "HT Omega Striker"
date: 2008-08-22
forum: Hardware
---

### Post by epanic on 2008-08-22
I recently installed an HT Omega Striker sound card, but I can't figure out how to get the sound to work appropriately. Although it plays, the quality is awful. I'm dual booting with Windows XP, and it sounds great on there, but I'd like to mainly use Linux.

HT Omega gave me what they said was their linux driver, but it's a .c file and they didn't give me any instructions.

---

### Post by linux_tech on 2008-08-22
Open a file browser and go to the source code's directory, then right-click and choose "Open in Terminal". Then try ./configure

./configure

make

sudo make install

The source code usually has a configure script. If it doesn't, then check the INSTALL or readme file that comes with the program.

---

### Post by go_beep_yourself on 2008-09-28
Did you ever get the card working? I was thinking about buying that one. Where exactly did you get the .c file? Was it only one file, and why is Linux not listed under supported here [http://www.htomega.com/striker.html](http://www.htomega.com/striker.html) if you got that driver source code from the Ht Omega company?

---

### Post by mizunoX on 2008-11-10
Any more updates?

It's working out of the box with Intrepid, but I agree that it doesn't sound go great.

Wondering if there is a better way.

---

### Post by elitenoobboy on 2009-02-19
From their customer support:

[I]Hello Sir. 

There is a linux driver for Striker7.1
Linux driver is created by OSS. 
And it does not support DDL, dts or other cmedia sound effect modes.  
The driver performance level is just playing sound.

Therefore, we provide Linux driver to user who needs as his requirement is
met 
You can download the drivers below; 
[http://www.htomega.com/filedown/cmpci-2.6.15-oss.rar](http://www.htomega.com/filedown/cmpci-2.6.15-oss.rar)

And you can check ALSA page.  
[http://www.alsa-project.org/main/index.php/Matrix:Module-cmipci](http://www.alsa-project.org/main/index.php/Matrix:Module-cmipci)

And Striker driver will be installed automatically when you install SUSE.  

Thanks.
Sincerely,
HT OMEGA -Tech Support.
[/I]

If any of you happen to be able to get surround out using digital output, reply and mention it.

---

### Post by Yodu on 2009-04-01
bump.

Can't seem to get digital out working with this card, and I am at a loss as to how to install the driver mentioned above (it is simply a .c file... no install readme or configure file included)

FWIW, openSUSE does have this driver already installed, but I can't get digital to work there either.

---

### Post by elitenoobboy on 2009-04-02
> **Yodu said:**
> bump.

Can't seem to get digital out working with this card, and I am at a loss as to how to install the driver mentioned above (it is simply a .c file... no install readme or configure file included)

FWIW, openSUSE does have this driver already installed, but I can't get digital to work there either.

Have you tried the standard way of getting digital output to work?: Installing gnome-alsamixer from synaptic and then using that to mess around with the iec958 output settings?

---

### Post by Yodu on 2009-05-07
Can someone explain the above process to me?

---

### Post by westofariver on 2009-06-24
I am running 9.04 and can't get my HT Omega Striker to put out any sound at all.  I have searched all over and can't seem to find the fix.  I downloaded and unzipped the file listed above but I am unsure on what do to with the text file.  Any help would be greatly appreciated.  Thanks!

---

### Post by Yellow Pasque on 2009-06-24
> Linux driver is created by OSS.
See: [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by elitenoobboy on 2009-06-24
> **westofariver said:**
> I am running 9.04 and can't get my HT Omega Striker to put out any sound at all.  I have searched all over and can't seem to find the fix.  I downloaded and unzipped the file listed above but I am unsure on what do to with the text file.  Any help would be greatly appreciated.  Thanks!

Are you using digital output or analogue?

---

### Post by westofariver on 2009-06-26
[FONT=Courier New][SIZE=3]Analog.[/SIZE][/FONT]  [FONT=Courier New][SIZE=3]It appears that both the on board audio devices (not being used) and my sound card's chipset (C-Media CMI8770)[/SIZE][/FONT] [SIZE=3][FONT=Courier New]but not the sound card as a whole device. Any ideas on what to do?[/FONT][/SIZE]

---

### Post by elitenoobboy on 2009-06-29
> **westofariver said:**
> [FONT=Courier New][SIZE=3]Analog.[/SIZE][/FONT]  [FONT=Courier New][SIZE=3]It appears that both the on board audio devices (not being used) and my sound card's chipset (C-Media CMI8770)[/SIZE][/FONT] [SIZE=3][FONT=Courier New]but not the sound card as a whole device. Any ideas on what to do?[/FONT][/SIZE]

Assuming you already tried manually selecting which sound device to use in system > preferences > sound, try disabling the onboard sound in your bios so ubuntu just won't see it and bother to default it instead of the card add on.

---

### Post by doriard on 2009-07-14
I can't get the cmpci-2.6.15-oss.c file to build.  How do I build and install this file for the HT Omega Striker?  I'm using Kubuntu 9.04.

---

### Post by doriard on 2009-08-16
I have downloaded the .c driver file from HT Omega for the Striker card but I can't get it to compile.  How do I compile the c file? It is cmpic-2.6.15-oss.c.  I thought this was an ALSA driver but it has "oss" in the file name, so would that indicate otherwise?

---

