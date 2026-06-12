---
title: "Dual Boot Grub2 Windows"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by liquidcable on 2009-11-01
Just installed Ubuntu 9.10 along side Windows XP (separate hard drive).  The install did not configure grub to give me a choice of OS, and does not take settings changes from Start-Up Manager.  On boot up it goes straight to ubuntu, no splash, no text.

There is no 9.10 documentation on the Ubuntu website and the grub2 site is useless.  There is no longer a /boot/grub/menu.lst file.

After some googling I found this link [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2).

Start-Up Manger appears to be completely useless, yet again I have to go to the command line to fix a problem.  What century is this :(

OMG!!  Running update-grud does NOT finds windows.  Adding entries to grub are way to complicated, and I still have found any exact instructions on how to add a windows xp entry to grub.

Anyone know how?

---

### Post by psykro on 2009-11-03
I'm not expert, but I have a similar problem, and I am going to make some educated guesses.

On 9.04 I used to use this method [http://blog.firetree.net/2005/08/26/duel-boot-windows-with-grub/]("http://blog.firetree.net/2005/08/26/duel-boot-windows-with-grub/") for dual booting with separate hard drives. It defined the menu.lst entry as 

```
title Windows
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
chainloader +1
```


Followed you link to [https://wiki.ubuntu.com/Grub2.]("https://wiki.ubuntu.com/Grub2.") and found the ubuntu community documentation link to [https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2").

Read the community documentation entry and found this link [https://help.ubuntu.com/community/Grub2#Custom%20Menu%20Entries]("https://help.ubuntu.com/community/Grub2#Custom%20Menu%20Entries") and reading a but further found this:
```

A sample entry for chainloading to another GRUB bootloader.

      menuentry "Grub 1 Bootloader" {

      set root=(hd0,8)

      chainloader +1

      }

```

So my guess is to add a custom menu entry (as described in the community documentation) with a format similar to menu.lst (as described in my first link) but added to the right place for grub 2 (adding scripts in /etc/grub.d/ directory) 

Hope this helps somehow, I am going to try it tonight myself and will post my results.

---

### Post by sliketymo on 2009-11-03
> **liquidcable said:**
> Just installed Ubuntu 9.10 along side Windows XP (separate hard drive).  The install did not configure grub to give me a choice of OS, and does not take settings changes from Start-Up Manager.  On boot up it goes straight to ubuntu, no splash, no text.

There is no 9.10 documentation on the Ubuntu website and the grub2 site is useless.  There is no longer a /boot/grub/menu.lst file.

After some googling I found this link [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2).

Start-Up Manger appears to be completely useless, yet again I have to go to the command line to fix a problem.  What century is this :(

OMG!!  Running update-grub does NOT finds windows.  Adding entries to grub are way to complicated, and I still have found any exact instructions on how to add a windows xp entry to grub.

Anyone know how?

Just a wild guess,but you may have to adjust your Bios setting to boot whichever drive you want first.

---

### Post by psykro on 2009-11-03
I didnt manage to fix it myself, but I found a fix [here]("http://ubuntuforums.org/showthread.php?t=1264151&page=2") which should help, did the trick for me.

---

### Post by etxkesa on 2010-06-14
I have the opposite problem. I used to have Ubuntu (Karmic) on the master disk, but chose to put Windows XP on that disk (as it's smaller than one of the SATA disks I have) and put Ubuntu on the larger SATA disk. Now I installed Ubuntu (Lucid) to the SATA disk OK, but nothing was done to the MBR of the master disk. I tried the Windows options for boot, but when I chose the Ubuntu disk nothing happened. How can I get Grub to set up the MBR under windows XP?

---

### Post by wilee-nilee on 2010-06-14
> **etxkesa said:**
> I have the opposite problem. I used to have Ubuntu (Karmic) on the master disk, but chose to put Windows XP on that disk (as it's smaller than one of the SATA disks I have) and put Ubuntu on the larger SATA disk. Now I installed Ubuntu (Lucid) to the SATA disk OK, but nothing was done to the MBR of the master disk. I tried the Windows options for boot, but when I chose the Ubuntu disk nothing happened. How can I get Grub to set up the MBR under windows XP?

Each problem is a little different, so start your own thread and post the script in my sig with the code tags instructions in the sig.

---

