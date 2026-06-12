---
title: "Installing Jaunty along side of Vista &amp; XP"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by boarder428 on 2009-06-30
I need a little advice on Installing Jaunty.  I currently have a system that has Vista installed on the first 100 GB of a 160 GB HD and Xp Installed on the remainder.  Then the PC has a 750 GB HD that is being used as a swap drive between the 2 os's.  I'd like to install Jaunty on this PC and am wondering what the best way to do so would be so that all 3 os's will boot.

---

### Post by PlancksCnst on 2009-07-01
I would either make a partition on the 750GB drive for the whole installation or make a small partition (10GB) on the 160GB drive for Ubuntu and an additional partition on the 750GB drive for /home.

---

### Post by Mark Phelps on 2009-07-01
From my experience (multibooting several different OSs across several drives), I would recommend the following:
1) Use the 750 drive for Ubuntu
2) Create all the Ubuntu partitions on that drive
3) Disconnect the MS Windows drive
4) Boot from the Ubuntu CD with only the 750 drive connected
5) Install GRUB to the MBR of the 750 drive
6) Reconnect the MS Windows drive but change the boot order to boot into the Ubuntu drive
7) Manually add a stanza to your menu.lst file to boot into Windows.

---

### Post by boarder428 on 2009-07-02
Thanks for the input, I like both ideas. don't know exactly how to create the stanza for the bootlist though. I think I may have an idea though.  I'll have to give it a try!

---

### Post by michaelzap on 2009-07-03
> **boarder428 said:**
> Thanks for the input, I like both ideas. don't know exactly how to create the stanza for the bootlist though. I think I may have an idea though.  I'll have to give it a try!

You can usually just choose which drive to boot from in your BIOS boot menu as well, so you probably wouldn't need to mess with grub at all if you're happy doing it like that (I am).

---

### Post by boarder428 on 2009-07-04
I have a little experience with editing the menu.lst file for grub my only concern is that when I disconnect the other drive and install Ubuntu on the 750 that it will probably designate the ubuntu install to hd 0,? (? depending on how the drive is partitoned) and when I plug the other drive in how it's going to react since  currently that drive has Xp as hd 0,0 and vista as hd 0,1

I suppose I should probably just give it a try and maybe try to run the boot.info script after hooking all hd's up and see what it reveals.

---

### Post by Mark Phelps on 2009-07-06
It will not present a problem as long as you continue to boot from the Ubuntu drive after you reconnect the other drive.  That's why you will need to add a stanza to the menu.lst file as you'll be booting from a drive different from the one containing Windows.

---

