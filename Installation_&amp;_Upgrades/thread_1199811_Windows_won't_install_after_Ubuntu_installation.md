---
title: "Windows won't install after Ubuntu installation"
date: 2009-06-29
forum: Installation &amp; Upgrades
---

### Post by Timeraner on 2009-06-29
I tried installing Ubuntu on my old pc to see if it would speed up, but it got worse.
I tried installing something older to see if it would be faster; I then tried to install windows 2000 on the pc, but it would not recognize the cd. It would show the Ubuntu grub menu, then boot ubuntu. I tried running the ubuntu live cd, and I formatted the hd, but i still cannot install windows. Did I mention I had windows xp installed before? The XP cd I just used on that computer to install no longer works on that pc. But it does on all my other pcs. I tried installing DSmallLinux, but just as with windows, the cd is not recognized. No bios settings have changed, and I can still boot from the Ubuntu live cd. Also, I would like to be able to fix it without disassembling the pc, as I am inexperienced with computer hardware.


**HELP!!**

---

### Post by raymondh on 2009-06-29
> **Timeraner said:**
> I tried installing Ubuntu on my old pc to see if it would speed up, but it got worse.
I tried installing something older to see if it would be faster; I then tried to install windows 2000 on the pc, but it would not recognize the cd. It would show the Ubuntu grub menu, then boot ubuntu. I tried running the ubuntu live cd, and I formatted the hd, but i still cannot install windows. Did I mention I had windows xp installed before? The XP cd I just used on that computer to install no longer works on that pc. But it does on all my other pcs. I tried installing DSmallLinux, but just as with windows, the cd is not recognized. No bios settings have changed, and I can still boot from the Ubuntu live cd. Also, I would like to be able to fix it without disassembling the pc, as I am inexperienced with computer hardware.


**HELP!!**



Here is the release notes for 8.04 LTS which is the oldest, supported version.  You may want to browse through it and compare the requirements with your system specs.

[http://www.ubuntu.com/getubuntu/releasenotes/804](http://www.ubuntu.com/getubuntu/releasenotes/804)

** I tried running the ubuntu live cd, and I formatted the hd, but i still cannot install windows.**

When you reformatted, you wiped out any existing data.  Which partition did you reformat?  Did you reformat the whole hard drive?  If so, you then deleted XP.

**The XP cd I just used on that computer to install no longer works on that pc. But it does on all my other pcs.**

Is it a original XP install disc or a recovery disc? 


Let's take a look at your disk.  In livesession mode (using liveCD... without any changes to your system), access a terminal (appplications > accessories > terminal) and type

sudo fdisk -l

that's a small L and not a number 1.

Kindly post the output. 

Thanks.

---

### Post by Timeraner on 2009-06-29
I am currently away from the computer, but I can try wednesday.
I know I got rid of XP, that was the point of installing Ubuntu.
I used the XP install disk, the same I used to install it in the first place.
And no, there are no partitions or os's on my hd. I think I may have a corrupted
MBR or something like that. I can boot using floppy disks; the Microsoft website
has floppies to install a SP0/1/2 CD, but not a SP3 disk like I have.

---

### Post by Wiebelhaus on 2009-06-29
The optical drive is obviously malfunctioning , reading some discs and not others or reading one before but not now , it's painfully obvious and they are crazy cheap now , replace it.

---

### Post by Timeraner on 2009-06-29
Also, the computer has 2 cd drives, a cdrw and a dvd rom, and neither will boot.

---

### Post by Wiebelhaus on 2009-06-30
> **Timeraner said:**
> Also, the computer has 2 cd drives, a cdrw and a dvd rom, and neither will boot.

I assumed you set the boot device in the BIOS , correct?

---

### Post by Timeraner on 2009-06-30
That was the first thing I tried. But they were the same as the last time I installed using the cds. I even tried making it check the hard drive last, which didn't help. I'm going to try one last thing; Win2k lets you boot setup from floppies, but you still have to use a cd.

---

### Post by Timeraner on 2009-07-12
It seems to be the computer will only read real cds; it read ubuntu and win98, but not my other copied cds such as winXP (i have a legit license key) or win2000 (this one too). Thank you all for trying to help, but I'm probobly trashing the computer. It's old anyway!

Or maybe I could re-install win98 and sell it on craigslist...

---

### Post by oldos2er on 2009-07-12
Before you trash it, see if there's a BIOS update. I have no idea whether or not that would help with the CD booting problems, but it's worth a try.

---

### Post by Timeraner on 2009-07-30
I found a genuine copy of the XP cd, and the installation was a sucess. For some reason it's not as slow as it was before.  Thanks for your help!

(I couldn't find a firmware/bios update, old omputer "Designed for Windows 98/ME")

---

