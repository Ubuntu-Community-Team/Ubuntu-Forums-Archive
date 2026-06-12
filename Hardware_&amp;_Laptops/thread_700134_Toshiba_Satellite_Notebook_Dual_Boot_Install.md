---
title: "Toshiba Satellite Notebook Dual Boot Install"
date: 2008-02-18
forum: Hardware &amp; Laptops
---

### Post by kenanton on 2008-02-18
I have a Toshiba Satellite Notebook Computer with Intel Pentium dual-core notebook processor T2330. It is model A205-S5814 with Windows Vista Home Premium as the OS. I would like to create a dual boot system with Ubuntu. What version of Unbuntu would be the best for this system? What is the easiest way to create a dual boot system? The notebook came with repair install disks.

Thanks in advance for your help.

---

### Post by coaltown on 2008-02-18
Any install of Ubuntu will do just fine, but I would recommend the latest stable one availabe. In my experience, dual booting works best this way:

-download and burn the latest UbuntuCD
-download and burn the latest Gparted LiveCD
-backup your valuable information
-reboot computer into Gparted live
-set up your windows partition however you like it (an ntfs partition), but leave the rest unformatted
-reboot and install windows on its partion
-reboot into Ubuntu LiveCD and install ubuntu so it fills the unpartitioned space, using the step by step guided installation

By installing windows first, you ensure that when you install Ubuntu the bootloader gets installed correctly. In my experience, if you install Ubuntu first, and then windows, Windows will hijack your bootloader and you wont be able to boot into Ubuntu.

**_Words of caution_**
-If you arent comfortable setting up partitions, and are not willing to mess it up a time or two, dont try dual-booting without assistance.

-Get a couple more opinions on how best to do it before you start formatting drives. I'm just one guy, I might be completely wrong

---

### Post by VMan on 2008-02-18
You can skip the step about the gParted live CD.
Instead, use the built-in controls in Windows Vista to resize your Vista partition.
First before doing anything, [COLOR="Red"]**Backup any important data**[/COLOR] then defrag your hard drive.  
Right click on "Computer" in the Vista menu.  Click on computer management.  Select "Storage". Right click on the C drive and choose resize (maybe shrink or something like that; it's been a long time since I did this).  You probably should reboot into Vista a few times to make sure that everything works correctly before installing Ubuntu.  That way if something went wrong, you know it did not have anything to do with the Ubuntu install.
After this, you should have plenty of free space to install Ubuntu.  I agree with the other poster, just use the most recent stable release of Ubuntu.  

If you run into problems, let us know and someone should be able to help you through it.

---

### Post by Ray Fried on 2008-02-18
Hello, I am trying to install Fiesty on a simular notebook (Toshiba A205-S5803 with Dual-Core T2330, Vista) but cannot get it to boot completely to the Live CD. It stopes with a message /bin/sh: Can't access tty; job control turned off (initromfs).

Please let me if you were successfull with the A205-S5814.

Ray

---

### Post by kenanton on 2008-02-18
This is a repost of my reply to mikeyphi post in Absolute Beginner Talk:

Thank you mikeyphi! I am posting this from my dual boot Toshiba!

Basically I followed the instructions in your post with some modifications.

First, in Vista I ran PC Decrapifier which is designed to remove a specific list of unwanted software in an unattended fashion. It is a free download from: [http://www.yorkspace.com/pc-de-crapifier/](http://www.yorkspace.com/pc-de-crapifier/).

Second, I did not do a backup as this is the second day I have owned this machine.

Third, I resized the partition with Windows Vista following the instructions given here:[http://vistarewired.com/2007/02/16/h...windows-vista/](http://vistarewired.com/2007/02/16/h...windows-vista/) .

Fourth, I did a disk cleanup and defrag in Vista.

Fifth, I used the install cd I burned for Ubuntu 7.10 64 bit.

Sixth, I rebooted in Ubuntu and waited while 186 updates downloaded and installed.

Seventh, I got into Firefox, downloaded and installed the bookmark synchronizer, logged in to this forum and started writing this reply.

Thank again mikeyphi and the others that made this possible!
__________________

---

### Post by w5cgu on 2008-02-24
Or just install to an external USB and never mind Winbloz at all....

John

---

### Post by wordman2 on 2008-06-10
Referring to the boot problem, I was out to install ubu d-boot myself on my new A205-S5803, and had the same error message, but cheated by installing Knoppix 3.6 first. What can I say...I'm a wannabe geek (so far). That reconfigured something and then the ubu boot worked and I installed Hardy. Later I got fed up with Vista freezing up, crashing, getting viruses, and trying to webmaster in Windows and did a full install of Hardy. Me very happy now! Sometimes you can cheat...

---

