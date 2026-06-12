---
title: "2hdd's 1 Vista 1 ubuntu?"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by WannabeFantasma on 2009-02-18
i was thinking of getting another hard disk to install ubuntu on (for my desktop)
but will it be possible? to install ubuntu on one hard disk and Vista on the second one? (and how do you do it?)

Thanks in advance.

---

### Post by night-wing on 2009-02-18
That's easy.
First install Vista (best on second hard disk). Then install Ubuntu. Ubuntu puts Vista as an boot option in Grub automatically and so you can choose every time, you boot, what operating system you want to start.

---

### Post by The Big Chow Mein on 2009-02-18
What about if you already have ubuntu on your main and want to install windows on a secondary? 
Do i just need to take out my ubuntu hard drive and place my other drive in the master and go through the installation process then put ubuntu back into the master and windows into the slave, hoping everything will work?

I had a nasty experience as last time i activated the sata for the slave drive as it changed the drive map and i couldn't get grub to go into any drive. 
Then when i tried to use my windows drive again (in the master slot) it had uninstalled its boot driver.
Using the windows recovery and the command line i reinstalled the boot loader, but when i restarted it still said it was missing.

SO main questions:
If i activate the other sata socket will it upset the grub drive map?
Do i need to remove my ubuntu drive from the master slot and put the drive for windows in there or can i install windows onto a secondary drive through the windows installer?


If this makes no sense could someone point me to a walk through?

Thanks

---

### Post by WannabeFantasma on 2009-02-18
> **night-wing said:**
> That's easy.
First install Vista (best on second hard disk). Then install Ubuntu. Ubuntu puts Vista as an boot option in Grub automatically and so you can choose every time, you boot, what operating system you want to start.

but i have vista allready installed... :D  (how to say you're on the second/first hard drive?)
so i install ubuntu and point Grub to the vista hdd? or?

---

### Post by Mark Phelps on 2009-02-18
Changing an MBR on a Vista OS drive to GRUB is not the solution I would  choose.  I chose to do the following:
1) Disconnect the Vista drive
2) Insert the Ubuntu CD and boot from it
3) Install ubuntu on its own drive -- add GRUB to the MBR of THAT drive
4) Reconnect the Vista drive but set the machine to boot from the Linux drive
5) Manually edit menu.lst on the Linux drive to add an entry for Vista

This way, if Vista ever fails to boot, you can disconnect the Linux drive, do repairs on the Vista drive -- without doing any damage to the Linux drive.

---

### Post by WannabeFantasma on 2009-02-19
> **Mark Phelps said:**
> Changing an MBR on a Vista OS drive to GRUB is not the solution I would  choose.  I chose to do the following:
1) Disconnect the Vista drive
2) Insert the Ubuntu CD and boot from it
3) Install ubuntu on its own drive -- add GRUB to the MBR of THAT drive
4) Reconnect the Vista drive but set the machine to boot from the Linux drive
5) Manually edit menu.lst on the Linux drive to add an entry for Vista

This way, if Vista ever fails to boot, you can disconnect the Linux drive, do repairs on the Vista drive -- without doing any damage to the Linux drive.


i'll try that :) just need the other hdd ^^ 

so this will not be like a dual boot than? or it will be a dual boot but than not something with the mbr? (grub) i remember when you want to go away from dual boot you need to delete the ubuntu partition and than restore the vista mbr again ( bootrec /FixMbr) on cd repair 

wow.. i'm so confused...

---

