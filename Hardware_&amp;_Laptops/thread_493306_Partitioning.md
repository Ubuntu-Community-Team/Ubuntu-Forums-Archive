---
title: "Partitioning"
date: 2007-07-05
forum: Hardware &amp; Laptops
---

### Post by muon on 2007-07-05
Hi all, I'm posting because of a serious problem that I've run into.  First of, let me just thank anyone
who can help me with this problem, because I've been trying to fix it myself for close to a week now.

Let me elaborate on the problem.

About a week ago I became an Ubuntu user after using Windows my entire life.  The installation when smoothly
and I was running Ubuntu soon after.  Problems started to occur when I began downloading random and not-needed packages (like for instance server stuff and edubuntu).  My computer started to run extremely slow and other stuff started to happen (like, I could no longer see the networking icon in the toolbar). 

I also happened to have a Fedora 7 dvd and decided to install that on top of Ubuntu, and it worked.  I soon missed the ease of use of Ubuntu and decided to install Ubuntu again; it didn't work!  I figured it was because of Fedora because the Ubuntu disk was scratchless.  I tried different stuff none of which worked.  I finally burned 
a program that partitions hards drives on my friends computer, it worked off the CD so I had to boot it up at startup instead of loading fedora.  

I managed to erase the partition, because I figured Fedora did something to the harddrive.  I ended up erasing the entire HDD and now Ubuntu doesn't even boot into the Live CD mode!  I've been researching and I think I 
erased the Master Boot Record or something.  I don't know how the Live CD needs the harddrive at all, but It seems It does.  

I've tried to partion the HDD in many ways: FAT, FAT32, NTSC, Ext2, Ext3, Extended, etc. nothing works!  I tried installing Windows agiain, and it worked so I don't understand why Ubuntu won't even boot into the LiveCD.  Please, if anyone can help me with this I would really appreciate it.  How do I make Ubuntu work again?  I really miss it!

My Computer Specs:
Toshiba Tecra 8200 - Laptop
Pentium 3 - 1 Ghz
300+ MB of RAM (Can't remember exactly)
20GB HDD
CD/DVD ROM Drive

---

### Post by robenroute on 2007-07-05
That Ubuntu Live CD, does that run without problems on a different system? And, what happens? What do you see when you try to boot from the Live CD?

---

### Post by loserboy on 2007-07-05
also you might make sure you have the Cdrom as the 1st boot priority in BIOS

---

### Post by muon on 2007-07-05
Well, I thought I was the CD at first so I burned a new one.  Both CDs are clean and both work on my friend's desktop computer.  

What happens exactly is this:  The cd boots into the menu that asks 5 options: install, install in graphic safe
mode, test CD, and boot from harddrive.  I then see the boot log and the configuration of the system.

the last line says: Configuring X system and then the screen goes black, and it stays black with only the blinking cursor viewable.  I left it like this for 30 minutes to see if it loads up, but it doesn't.  Originally, the first time that I tried this 2 weeks ago, it did not take 30 minutes, or even 15 minutes.  It was very quick.

---

### Post by loserboy on 2007-07-05
sounds like a video problem, what's your video card

---

### Post by muon on 2007-07-05
I doubt its the video card, as I say before Ubuntu loaded up before with no problems.  It was during the re-installation after the formatting of my harddrive that everything started to mess up.  In any case, by video card is an old Cyberblade XP from toshiba, with about 16MB of ram.

---

### Post by muon on 2007-07-06
Ok, thanks a lot for everyones help, its the thought that counts :)

I fix the problem, it seems that the problem had to do with my memory RAM chips, one of them was faulty and there wasn't sufficient 
memory to boot the system.  I debugged the problem and Ubuntu is now working just fine.  Thanks.

---

