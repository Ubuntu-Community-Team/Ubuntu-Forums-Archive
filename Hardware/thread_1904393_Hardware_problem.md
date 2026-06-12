---
title: "Hardware problem"
date: 2012-01-04
forum: Hardware
---

### Post by dgundling on 2012-01-04
Need some ideas regarding my UBUNTU installation effort. I have a computer which at one time was running UBUNTU 10.10, 11.04 and WIN98SE quite happily. About last July I decided to use update manager to move the 10.10 installation to 11.04 also. At that point things fell apart. Since that time nothing runs and I can't reinstall anything. I did manage to fdisk the HD using an old version of partition magic. As I sit now I have 5 UBUNTU CDROMs 10.10, 2 of 11.04, and 2 of 11.10. All 5 will boot on my other computers without a problem. None will boot on the problem computer. No start up. I have two CDROM drives for the computer I want to put UBUNTU on. Neither will take and load a UBUNTU CDROM. The only thin I have which will work at all is an old WIN98SE disk. It will install up to the very last restart in the process and go no further. The computer will only boot into safe mode. Am unable to fix, if SFC is right, user.exe because the repair that I have is 5MB of software which takes a CDROM which the computer won't read. MEMtest checks out OK as well as the Seagate HD test. Any ideas on what to try next? Thanks.

---

### Post by jerrrys on 2012-01-06
What kind of computer is this?  Is that ubuntu or windows that boots to safe mode?

---

### Post by dgundling on 2012-01-06
The computer is one made up from parts. It has an Intel D865GV mobo with an Intel pentium 4 3.2 processor. It is windows that boots to safe mode. The problem is that I can't get any of the 5 Ubuntu distros that I have to boot on the machine.

---

### Post by grahammechanical on 2012-01-06
It may be a faulty video card.

I had a problem the other year where my video card was overheating. It was a fanless type. I am only running Ubuntu. It started to boot into low resolution mode. Then it would not boot at all and for a few times I could get a live CD to load. Then none of them would load not even the 7.04 CD that I first used to install Ubuntu with. But I did manage to install Mandriva 2007 because it let me select a screen resolution.

Ubuntu gets its monitor information from the monitor but through the video card. This is why we do not need to set screen resolutions or refresh rates when installing Ubuntu. In my case the faulty video card was not passing the monitor configuration to Ubuntu so that the screen settings could be configured.

Regards.

---

### Post by dgundling on 2012-01-07
Thanks for the suggestion. The computer I am using has built in video.

---

### Post by 2F4U on 2012-01-07
What does it mean when you say the CD's don't start? Do you get to the grub boot screen or even beyond?

---

### Post by dgundling on 2012-01-07
> **2F4U said:**
> What does it mean when you say the CD's don't start? Do you get to the grub boot screen or even beyond?
 
The only thing I get is a blinking cursor. Screen is essentially blank.
 
Dave

---

### Post by 2F4U on 2012-01-07
Did you try to boot from an usb flash drive or is your computer not supporting that?

---

### Post by dgundling on 2012-01-07
I don't have a flash drive with Ubuntu on it so I haven't tried that. Thanks for the idea.

---

### Post by upchucky on 2012-01-07
I once had a client's machine come in that would not boot live cd's from either of it's cd drives, turned out that the cd master/slave jumpers were both set to cable select. Windows xp would only boot from the first cd drive, and live cd's would not do anything.
I set the first drive on the ribbon to master, the second one to slave, all was good then.

---

### Post by dgundling on 2012-01-07
> **upchucky said:**
> I once had a client's machine come in that would not boot live cd's from either of it's cd drives, turned out that the cd master/slave jumpers were both set to cable select. Windows xp would only boot from the first cd drive, and live cd's would not do anything.
I set the first drive on the ribbon to master, the second one to slave, all was good then.
 
Thanks for the comment. I have tried all possible combinations of HD placement on the cables and master/slave/ computer select without any luck. I am over 90% cetain at this point that the controller chip has gone to its final reward.

---

