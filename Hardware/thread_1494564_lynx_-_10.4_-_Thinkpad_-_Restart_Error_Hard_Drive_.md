---
title: "lynx - 10.4 - Thinkpad - Restart Error: Hard Drive Initialization Error"
date: 2010-05-27
forum: Hardware
---

### Post by awongh on 2010-05-27
Hi,
I have a Lenovo Thinkpad T500 (the last ones they made, very recent). with the intel graphics chip.

I installed a new (aftermarket) kingston ssd now v 64gb hard drive.

I just installed lucid lynx 10.4 and every single thing seems to work (amazing! ) - webcam, sound (havent tired the mic) and all the power options- suspend, hibernate, on battery power and not. 

BUT- when I reset it, it gives me the error: 2100: HDD0 harddrive initialization error (1)

I have tried physically replug the hd, and I have tried putting acpi=force in the grub boot settings, and it doesn't work. (a la this thread: [http://ubuntuforums.org/showthread.php?t=967210](http://ubuntuforums.org/showthread.php?t=967210) )

Could it still be an acpi issues? The machine boots so fast that I can't see any messages it might be giving me. And I really don't understand how to set grub or grub2 for that matter. 

Apparetly this can be an issue with thinkpads, but I haven't heard of anything with kingston drives... I really don't want to hear I need a new ssd hd!! Those things are expensive!!

thanks in advance.

---

### Post by dino99 on 2010-05-27
is hdd0 the ssd ?

sudo dpkg --configure -a

will force a fsck on next boot:

sudo shutdown -F -r now

look at .xsession-errors and system/admin/log viewer for errors

[http://ubuntuforums.org/showpost.php?p=8690795&postcount=16](http://ubuntuforums.org/showpost.php?p=8690795&postcount=16)

[http://kfsone.wordpress.com/2010/04/04/lucid-on-the-ssd-with-dialogs/](http://kfsone.wordpress.com/2010/04/04/lucid-on-the-ssd-with-dialogs/)

[http://swiss.ubuntuforums.org/showthread.php?t=1463870](http://swiss.ubuntuforums.org/showthread.php?t=1463870)

---

### Post by awongh on 2010-05-27
yes. hdd0 is the ssd, my one and only hd, it's the one that's having trouble initializing.

running shutdown -F -r now still gives the same error.

although - note that I have the boot menu up when it boots at grub- and when I reboot from this menu I don't have the same problem. Only a complete restart....

Also, if I haven't already mentioned it works fine from shutdown -> [press power button] -> power on

I looked in all the logs, but didn't see anything... although not quite sure what im looking for... 

dmesg | grep ata1 didn't come up with anything suspicious looking....

I also looked at that other thread... and I don't think my drive has any of that queueing tech in it....

---

### Post by dino99 on 2010-05-27
as this kind of hardware is recent (too) you might try with the latest kernel (i'm testing maverick with 34-4 and its fine)

add this ppa into synaptic repo:

[https://launchpad.net/~ricotz/+archive/unstable](https://launchpad.net/~ricotz/+archive/unstable)

---

### Post by awongh on 2010-05-27
cool. bedtime now! I will try it tomorrow!

---

### Post by Devillbe on 2010-05-27
I also have an Thinkpad T500.
but I do not have the same HDD as you do.
I am using it since the 8.04 distro without anny issues.
Also I went through all Upgrades posible at this time.
 
If you keep getting the same error over and over, my sugestion is try the pervious version first and check if you still have the same error (9.04 or 9.10). I know that I must sound like a Stupid guy, but I fixed ohter issues I had before on the same way.

---

### Post by awongh on 2010-06-04
I didn't actually solve this, but I just bit the bullet and bought a new intel SSD. I was able to try it in the store... and now it works perfectly fine. I'm gonna try to call Kingston and get my money back....

---

### Post by raresel on 2010-09-15
this is a hardware problem and the solution is to set the SATA to compatibility mode instead of AHCI in the BIOS.
source:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820139134](http://www.newegg.com/Product/Product.aspx?Item=N82E16820139134)

additional keywords: cold boot, warm boot, thinkpad z61t, kingston ssdnow.

---

