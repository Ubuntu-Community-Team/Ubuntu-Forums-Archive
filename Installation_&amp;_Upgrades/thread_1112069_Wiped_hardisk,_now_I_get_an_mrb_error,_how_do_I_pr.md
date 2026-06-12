---
title: "Wiped hardisk, now I get an mrb error, how do I proceed?"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by Vincenso Andolini on 2009-03-31
Hello all,

I endeavoured to flatten windows permanently on my computer. This is a process I had completed recently on another computer with no problems. On the computer in question I used Hiren's Boot Cd with Acronis Disk Director and wiped the hardisk twice over. Now when I try to boot from a cd, an Ubuntu cd, the computer (BIOS?) does not allow it and says "MBR ERROR".

I can press F12 upon startup to access Hirens Boot CD but I cannot boot from an Ubuntu disc. I want to install Ubuntu.

Does anybody know how I can fix this? I assume that the hardisk has a corruption in the master reboot file (?), but I am new to working with hardisks in this manner so I am not sure what to do.

All help is appreciated.

Vincenso

---

### Post by kpatz on 2009-03-31
Go into your BIOS settings and make sure the boot order has the CD drive before the hard drive.

If that doesn't work, and just the Ubuntu CD isn't booting (but other CDs do), you may have a bad image.  Redownload, check the MD5, and burn another disk and try again.

---

### Post by Vincenso Andolini on 2009-03-31
Thanks for your reply. 

I was in the BIOS already and my cd drive is set as boot #1, before the HDD too. Also, this cd was used two days ago to successfully install Ubuntu, so I know the .iso is a good burn.

Thanks, have anymore ideas?

Vincenso

---

### Post by kpatz on 2009-03-31
What does this "Hirens Boot CD" have on it?  Does it have a MBR repair or partitioning utility?  Try that, if you can boot from that CD but not an Ubuntu one.

Once you have a MBR perhaps the Ubuntu CD will load, though I've never seen that happen before.  Maybe the disk wipe you did wrote something other than zeros to the MBR sector and that's confusing the Ubuntu boot loader.

Another thing to try is DBAN.  Download the ISO, burn it to a CD, boot it, and overwrite your MBR, then try booting the Ubuntu CD.

---

### Post by lindsay7 on 2009-03-31
never mind you tried this already.

---

### Post by dandnsmith on 2009-03-31
A thought - have you tried a bootable CD which isn't a live distro?

I ask, because the Ubuntu liveCD (when you poke into the crevices) tells us that it can use swap on the HDD - it has to find this via the MBR block (looking at the partition entries).

My scenario would be to try a bootable CD, and, if you don't get the error, wipe the first block on that HDD.

---

### Post by Mark Phelps on 2009-03-31
Hirens CDs all too typically have old versions of utilities on them -- some of which work, some of which do not.

If you download a SystemRescueCD and boot from it, it gives you an option to replace an MBR.  Go to the distrowatch.com website. It's located on the right side of the page, about half way down as SystemRescue.

---

