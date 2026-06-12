---
title: "Sony Vaio PCG-Z505LS  + Wubi"
date: 2008-07-29
forum: Hardware
---

### Post by Socratez on 2008-07-29
I am havign trouble installing Ubuntu on my Sony Laptop. The PC has no CD-Rom or Floppy internally. CD-Rom is PCMCIA Floppy is external USB. I am curious if I can use the Wubi installer to completely replace the already existing Windows XP install on the machine. If not I am curious as to how I can get an install to run. Network install should be available but I am not sure which module to use for the PC. I know it is Intel 8225 series NIC. 


Any help would be greatly appreciated

---

### Post by Socratez on 2008-07-29
I am going to attempt to use unetbootin to solve this problem I'll keep all other Vaio Z505LS users up to date on my progress

---

### Post by Socratez on 2008-07-31
I ran throught the process as my laptop had winxp on it // I did manage to get ubuntu loaded using this solution ... I selected the netinstall option // after the install i was good to go // haven't tried using the CD-Rom yet but for me the wires PCMCIA card is working so i can't forsee an issue with the CD-Rom //

---

### Post by changeiscertain on 2009-05-15
As I scan through these threads, I notice that there are quite a few vaio users who are having as much trouble as I am with installing Ubuntu on their antiquated laptops.  Most recently, I wasted 6 days trying and trying to get this to work, with no success.

Several people have tried to help, but when instructed to 'go here and do this'... I found that 'this' wasn't in the 'here' as I was told it was..  in some cases, 'here' didn't even exist. Not to mention the problem with getting the linksys wireless card to work - or not work.

I admit that this is my first experience with any linux system, but should it be THIS difficult?  

After losing almost a weeks worth of sleep, I have given up and am putting Windows back on the old Sony.. at least it will be functional.  

I am open to any advice.. ANY!  If Ubuntu is THIS difficult to install and to simply get a wireless card to work, I would have to choose windows.. it's almost not worth it.

Someone, Anyone... HELP!

---

### Post by jfv411 on 2009-07-31
I have also been struggling to install Xubuntu 9.04 (or Ubuntu) on my Sony PCG-z505ls. I have a pcmia cd rom drive which is able to boot the disk, but it fails when trying to install or demo the OS. 

Machine has 512mb ram.
I've disabled the plug and play settings and enabled APCI OS control in the Bios.

When trying to install/run the live disk I get the following message:
[0.000000] ACPI: DMI BIOS year==0, assuming ACPI-capable machine
[6.444765] cpufreq: change to state 1 failed with new_state 2 and result 0
[6.444765] cpufreq: change to state 0 failed with new_state 2 and result 0
[9.080850] IO APIC resources could be not be allocated.
Loading, please wait...

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

I have windows 2000 pro installed on the machine and would like to set it up to dual boot and maybe eventually just linux. I haven't tried Wubi or a netinstall. As I understand it Wubi installs Ubuntu WITHIN a windows OS which is not what I want. I have a desktop running Ubuntu as well.  I've read that the cdrom drive doesn't work with some of the older Linux Kernals but should work with the most up to date one.  Therefore I haven't tried a netinstall since I have access to a cdrom drive and live disk. I'm considering trying some other distro's but don't want to waste a lot of time hitting the same road blocks.

I've tried disable ACPI, downgrading graphics, etc with no different results.

I will try Slackware or Debian this weekend as I've read others have been successful with it in the past.

Can anyone help or explain what these error messages mean?

---

### Post by scientastic on 2009-08-03
I am surprised to hear that the PCG-Z505LS can go to 512 MB.  I have only 256MB in mine, and was under the understanding that was the maximum you could put in it.  Care to elaborate?  I would love to get 512 MB on this laptop, it would boost it immensely.

By the way, I'm currently just running Windows XP on it but I would be greatly interested in putting Ubuntu on it as well.  So if anyone else sees this thread, it's not just one person who's interested. :D

Thanks!

---

### Post by jfv411 on 2009-09-14
Yes, I found a way to install 512mb here:
[http://www.feise.com/~jfeise/Linux/z505ls.php](http://www.feise.com/~jfeise/Linux/z505ls.php)
Basically there are two ram slots one on top and one underneath the mobo. I put a stick of 256mb ram in each and it boots up with bios seeing 512mb. No prob.

I had a very difficult time installing linux on it however. The laptop doesn't have a floppy or cd drive. I have a pcmia cd drive that it can read and "boot" from. It will basically boot the cd but if you try installing or running the live cd it fails. I gave up on finding a work around for this and found an alternative method. 

Since I already had windows installed i paritioned a drive and loaded and alternative .iso image on it for xubuntu. Then I added a grub boot loader in windows that would boot from the .iso image and voila, success. After much tweaking of the system. No plugnplay, acpi off... i think.  There are a few tutorials around explaining this method. 

Anyways, it worked successfully and then I went and tried resizing the windows partition from within windows (stupidly) and corrupted my mbr. So now I'm back trying to figure out a way to repair or work around the boot loader without a bootable cd or floppy drive. 

Suggestions?

I'm also considering trying Easy Peasy on the machine as I've heard it uses substaintially less resources than Xubuntu.

---

