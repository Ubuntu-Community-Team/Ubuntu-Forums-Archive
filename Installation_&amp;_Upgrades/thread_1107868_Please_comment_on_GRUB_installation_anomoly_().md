---
title: "Please comment on GRUB installation anomoly (?)"
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by hkb11001 on 2009-03-27
I have an interesting scenario, I'd love to get some feedback on to learn whatever I can about why this happened:

FIRST:

I installed 8.10 onto my system:

I have WinXP on a PATA drive as master on IDE1.

I have three other SCSI drives attached via an adapter in one of the PCI slots

(I used to have Ubuntu 7.03 installed on this system)


I did a fresh install of 8.10: the intaller recognizes the three SCSI drives as sda, sdb, and sdc, while is sees 

the PATA drive (what used to be referred to as hda) as sdd.

I mapped /boot and / on sda and /home on sdc (not using of sdb at this time -- I'll wait for btrfs for that).

At the last step of installation, I clicked on the "Advanced" button to see what it was about, and noticed it had 

to do with where GRUB was to be installed; I noted it's default selection was hd0, which I interpreted to mean it 

would install in the MBR of hd0 (sdd in this case), which looked good --what I wanted.

When the installation was done, and it rebooted, the system hung with a GRUB prompt.

Hmmm....it's behaving as though GRUB didn't install into the MBR of the PATA drive as I expected.


SECOND:

I'll investigate installing GRUB to a different location ('take a look at the options under the "Advanced" button 

on the last screen of the installation.

Go through installation sequence again, only this time, in inspecting options under the "Advanced" button on the 

last screen I select sdc (not the subheadings of sdc1 or sdc2).

Result: when the system reboots, the terminal shows a continuous scrolling of "GRUB" flashing across the screen.

Action: Ctl-Alt-Del to put the system into restart and shut the PC off.


I post my question on the Ubuntu Forum regarding what to do with the outcome of the first scenario, expecting I can 

go back and do the installation AGAIN (!!) but repeat the installation of GRUB to the default hd0.


I get help on the Forum from cariboo907 pointing me to a helpful "How To". The documentation looks good, so I'll 

give that a try.


THIRD (and last):

I reinstall 8.10 just as I did the first time. THIS TIME the installer sees the PATA drive (on IDE1) as sda and the 

three SCSI drives as sdb, sdc, and sdd !! Hmmm....what's that about???

The installation goes fine; when I get to the last screen I verify that GRUB is to be installed on hd0 again.

This time the system boots fine: I get the GRUB menu with the linux kernel options as well as Windows listed as 

well. The system boots into Ubuntu by default. It works!


QUESTIONS:

1. Why the difference in how the installer saw the hard drives???

2. Why should GRUB work as expected this third time, but didn't the first time? The only difference again, between 

attempt 1 and attempt 2 was the device assignment to the hard drives.

I'm asking this simply to learn what I can from anyone who offers some feedback. Thanks!!

---

### Post by wkulecz on 2009-03-27
I've always thought the dynamic mapping of device names was evil.  I want a one to one correspondence between the hardware's physical location and its name.  I've been swimming upstream on this since the days of DOS and com and lpt ports so unfortunately its a lost battle and the powers that be seem hell bent to remove the last remnents of sanity.

I've custom software that uses two frame grabber cards.  Which is /dev/video0 and which is /dev/video1?  Sucks that whenever I setup a new system, I have to stick somthing in front of one of the cameras and reverse the cables if its wrong as keeping "Left" and "Right" camera views correct is important here!

--wally.

---

### Post by dandnsmith on 2009-03-27
I've been receiving wisdom about some of this in another thread.
Some of the anomalous behaviour may be due to difference in boot order setup - did you change it between attempts?
There is a record left in the grub directory, when the grub bootloading setup is installed, called devices.map, which relates the then linux view to the way grub interprets. If the linux view (sda, sdb, ...) changes, then grub may well not behave as intended, as the device number will have been recorded as part of the hard info that grub boot uses to find the grub directory.
This will necessitate a re-install of grub (eg using the original install CD).

---

### Post by hkb11001 on 2009-03-27
If you're talking about the boot order setup in the BIOS, no, that did not change.

---

### Post by meierfra. on 2009-03-28
> . Why the difference in how the installer saw the hard drives???

Ubuntu uses "udev" rules to make sure that drives are numbered consistently. Unfortunately, this does not always works perfectly and in some rare cases the order of the hard drives can vary  from boot to boot. 



> 2. Why should GRUB work as expected this third time, but didn't the first time? The only difference again, between
attempt 1 and attempt 2 was the device assignment to the hard drives.

The Ubuntu installer has no knowledge of the actually boot order. So it just assume that (hd0)=/dev/sda, (hd1)=/dev/sdb and so on.
So by default it installs grub to the MBR of /dev/sda.

Only then  you got lucky and ordering has changed, /dev/sda was actually the boot drive and Grub was installed correctly

---

### Post by hkb11001 on 2009-03-30
Thank-you. That was helpful.

---

