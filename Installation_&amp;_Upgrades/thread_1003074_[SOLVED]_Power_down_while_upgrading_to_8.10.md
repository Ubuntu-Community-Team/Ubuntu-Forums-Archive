---
title: "[SOLVED] Power down while upgrading to 8.10"
date: 2008-12-05
forum: Installation &amp; Upgrades
---

### Post by pitchdiesel on 2008-12-05
I recently tried to upgrade to 8.10 from Hardy and my computer lost power and shut off in the middle of it. When I tried to restart, I got an error message on the GRUB loading saying the kernel was not syncing. I tried to use my manufaturer's recovery CD and that goes through the recovery and then on restart goes to a blank screen. When I tried to boot from the Ubuntu and recovery CD, the disc spins fine until the actual install and then it audibly skips/stutters. I don't really care anymore about data recovery, I think we're past that point here.. anyone got any ideas on how I could reinstall Ubuntu?

Thanks, much love!

---

### Post by taurus on 2008-12-05
I assume you have gone into the BIOS to see if the BIOS still detects your harddrive.  Then from the LiveCD, open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by pitchdiesel on 2008-12-08
The hard drive is being recognized in the BIOS. I can't run Ubuntu off of the LiveCD though, it will not start. I just get the splash screen and then any option I choose will not work.

---

### Post by pitchdiesel on 2008-12-08
bump

---

### Post by taurus on 2008-12-08
What's the spec of your machine?

---

### Post by pitchdiesel on 2008-12-08
Processor Name: Intel Celeron M 370
Processor Speed: 1.5 GHz
RAM: 1GB
Hard Drive Capacity: 60 GB
Graphics: ATI Mobility Radeon XPRESS 200
Primary Optical Drive: DVD-ROM/CD-RW
Wireless: 802.11g

---

### Post by pitchdiesel on 2008-12-08
I found a Windows XP CD that works, going to set up my comp to dual boot Windows and Ubuntu.

---

