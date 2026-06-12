---
title: "Moving Grub to New Install"
date: 2008-12-25
forum: Installation &amp; Upgrades
---

### Post by skewray on 2008-12-25
I have a machine that I am trying to migrate into the 20th century.  It has an IDE RAID array with SuSE 10.2 on it, and a SATA RAID array with Ubuntu installed.  The computer uses the Grub boot menu.lst on the SuSE 10.2 partition to run the boot loader, but of course this boot partition isn´t the one updated when Ubuntu is updated.  I assume that the master boot record that the hardware is reading is on an IDE disk.

How do I make the computer use a master boot record on one of the SATA disks?  How do I make the MBR then refer to the Ubuntu menu.lst?

Also, Ubuntu considers the IDE disks to come first, as /dev/sda, /dev/sdb, etc.  If I pull out the IDE disks, will that confuse everything?

Brian

---

### Post by caljohnsmith on 2008-12-26
> **skewray said:**
> 
How do I make the computer use a master boot record on one of the SATA disks?  How do I make the MBR then refer to the Ubuntu menu.lst?

Also, Ubuntu considers the IDE disks to come first, as /dev/sda, /dev/sdb, etc.  If I pull out the IDE disks, will that confuse everything?

Brian
That could be tricky because of your RAID array. In order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and hopefully what your problem might be.

---

### Post by skewray on 2008-12-27
Very cool script.  I just ran it from Ubuntu 8.10 off of the disk install of the install disk, since I installed from the alternate CD and don have a live version.  The script seems to mostly work anyway,

I think I attached the results.  I can´t get this web page to work in Konqueror at all, and Firefox is dicey...

Brian

---

### Post by caljohnsmith on 2008-12-27
Forum member Meiefra wrote that script and deserves the credit for it, and I agree, I think it's a really useful script. :) So you said that Grub is using the SUSE menu.lst on start up, so for that to be true, I think you must be booting the sdc drive on start up; I'm not sure because according to the script, Grub's stage2 file is supposedly located at sector 64, and I don't see how that could be possible, because that's the 2nd sector of the sdc1 partition. But the good news is you appear to have Grub correctly installed in the MBR of your sda Ubuntu drive, so if you go into your BIOS and change the boot order so that the Ubuntu sda drive boots first, you should get the Ubuntu Grub menu OK. Or if you want, you could continue to boot off the SUSE sdc drive, and then add an entry in the SUSE menu.lst like:
```
title Ubuntu Grub Menu (hd1)
root (hd1,0)
configfile /boot/grub/menu.lst

title Ubuntu Grub Menu (hd2)
root (hd2,0)
configfile /boot/grub/menu.lst

title Ubuntu Grub Menu (hd3)
root (hd3,0)
configfile /boot/grub/menu.lst
```
In other words, since I don't know which drive in your BIOS boot order the Ubuntu drive is, there are three possibilities; one of the above possibilities should work. Anyway, how about giving one of those two methods a shot and let me know how it goes.

---

### Post by skewray on 2008-12-27
Actually sda and sdb are the SuSE install, and sdc and sdd are the Ubuntu install.  I added the Ubuntu boot lines to the menu.lst on the SuSE boot partition so that I could boot into Ubuntu.

What I don´t understand is how the computer picks one MBR over another, and what software installs a MBR that points to a particular boot partition.

Brian

---

### Post by caljohnsmith on 2008-12-27
> **skewray said:**
> Actually sda and sdb are the SuSE install, and sdc and sdd are the Ubuntu install.  I added the Ubuntu boot lines to the menu.lst on the SuSE boot partition so that I could boot into Ubuntu.

What I don´t understand is how the computer picks one MBR over another, and what software installs a MBR that points to a particular boot partition.

Brian
It looks to me like your sdc1 menu.lst is an OpenSUSE menu.lst where you added the Ubuntu entries at the bottom, so is Ubuntu actually on sdd3 and sdd4 maybe? 

But to answer your question, it is your computer's BIOS boot order that determines which drive gets booted on start up; you should be able to go into your BIOS and change the boot order so you can boot whichever drive you want. And about the software that installs a boot loader to the MBR, in the case of Grub it is the "root (hdX,Y)" and "setup (hdZ)" commands that do that. Those commands assume you all ready have Grub's boot files present in the /boot/grub or /grub directory, so if you don't, you could instead use the "grub-install" command. If you want more info about those commands, a good place to start is:

[http://www.users.bigpond.net.au/hermanzone/p15.htm](http://www.users.bigpond.net.au/hermanzone/p15.htm)
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)

And also since you have a RAID array, and if Ubuntu is on sdc3/sdc4, I'm not sure the easiest way to set up your booting process to be better since I only have a little experience with RAID.

---

### Post by skewray on 2009-07-27
I am just posting a six-month-too-late thank-you note.  The problem was fixed by changing the boot order in the BIOS, as it turns out.

Brian

---

