---
title: "Using a PATA drive for Ubuntu and a SATA that has win 7 x64 same machine"
date: 2016-07-07
forum: Hardware
---

### Post by Sn00ze on 2016-07-07
I think I have figured out how to fix the problem of having to run an older machine for linux.  I want to use one of my best machines that has the later hardware and memory and other goodies that will allow me to run some 3d software like Blender for one and others.  I have a 16.04 install running fine on an older P4 machine and had no trouble running out of the box on that install but it does balk trying to install the latest Blender release due to the old graphics card.  My answer to that is to just reformat that drive and move it to my good machine and do an install on that machine and use the boot loader to choose what system to boot up.   I get the best of everything that way ,  So the question is has anyone set up one of their machines using this mixed drive approach since I have both on the motherboard of the machine I plan on using.  I have both SATA and the IDE/PATA will the installer still be able to install as usual or should I expect some unseen problems .   Also is it best to install the boot loader on the drive that will hold the linux install. I assume I will be able to update any nVidia drivers since I am using a pretty old GeForce GT 660 or one of those series cards .  Any expert advice or tips would be nice before I jump in but I don't think I could harm anything going this route.  It's either do it this way or buy something newer but who has money 

Thanks

---

### Post by weatherman2 on 2016-07-07
This really depends on your BIOS/EFI firmware settings.  If it can allow you to set any hard drive, PATA or SATA, as a boot device, then you should have no trouble.

You can dual boot in various ways.  One way is to use the Grub boot menu to choose the OS.  Another way is to use your BIOS/EFI firmware's boot menu - which is how I often do it.  That way, you don't have to worry about the boot loader at all.  If you can do that, in that case: yes, I would install Grub on the Ubuntu drive, NOT on the Windows drive.  In fact, if you are re-installing, you might even unplug the Windows drive during the install to make sure there is no accidental use of the wrong drive.  If you are simply moving your existing PATA drive to a new machine, you shouldn't to change anything; just choose which drive you want to boot from with the boot menu.

On my laptop, I use the F12 key at boot time to choose Windows or Ubuntu.  On one desktop, it's the F11 key; on another, it's F8.  Sometimes you must enable the BIOS/firmware boot menu as a setting before you can access the boot menu.

---

### Post by oldfred on 2016-07-07
Is new machine so new it is UEFI?

I gave up on PATA/IDE drives 10 years ago. SATA drives then had dropped to about $10 more than the IDE drives. And the day I went to buy DVD I ended up with  SATA DVD. A Sony SATA DVD was twice the price, so I was going to buy PATA, but they just put out new DVDs that were again only $10 more than PATA.

Make sure mother board has IDE/PATA connector. And only use the newer 80 conductor cable not a left over DVD 40 conductor cable.
You also may have drive order issues as the IDE port may become sda.

I now use a SSD for boot drive. Smaller ones are now reasonably prices and make system very fast. I have / on SSD and data on HDD.

---

### Post by Sn00ze on 2016-07-08
Thanks, the motherboard is capable to set either or as boot, I plan on making it painless using the grub loader to allow me to choose which system to run on boot. I understand what your saying about the bios boot menu I am pretty sure it does have that feature.  Although not new it is not a dinosaur and has just about anything needed to run both win 7 on it's own drive and linux on another being the IDE/PATA.  I have a brand new ribbon cable 80wire never used so I feel pretty confident it should work ..  I will read tomorrow on the bios menu feature to make sure I chose the best to boot, I don't mind the grub loader it seems to do well every time I used it in the past.  I will remove the c drive connection completely as you recommend.   I sure don't need any headaches with all the things I have on this drive.   Now if I should go with the bios boot menu do I not install the grub boot loader or will it install anyway on the linux drive want it or not?
Thanks for the info

---

### Post by weatherman2 on 2016-07-08
Well, if you want to use the Grub boot menu to boot and not the BIOS boot menu, you'll need to leave the Windows drive plugged in, then either install Ubuntu again - or just update Grub on the Ubuntu drive and let it detect the Windows drive as a boot drive.  Then make sure the PATA drive is set as the 1st boot drive.

---

### Post by Sn00ze on 2016-07-08
Thanks for the tips, I was going to just buy a nice little WD My Passport drive but after reading up on those I see they had hidden partitions not allowing for a reformatting, later firmware was provided but I don't need more headaches than what I already have .  I thought about it and decided this reinstall to a good 64 bit machine is the way to go for what I want to do.  I'm more or less planning for the future hoping to learn linux much better than I know it now because I think I see a shift in the win monopoly with this win 10 murder.  I love that there is already some great software for 3d and even Inkscape which is just superb , Gimp I don't like so much since I have photoshop but I could learn to use it .   Too bad The Gimp don't have the nice filters and other nice add ons, it may have I just don't know about them not using it.  Thanks again, tomorrow by high noon I should have the system up and adding updates and the goodies.  I wish I had a larger hard drive but I figure I can always clone to a larger one in the future or just reinstall.

Thanks

---

### Post by Sn00ze on 2016-07-08
Ok I understand that and will make sure I have the PATA boot so it can give me the grub menu.   I plan on reading up on my bios boot menu to make the right choice before I start, I think that might be the better choice after thinking about it a while, and I can go ahead and disconnect the c drive to make sure there are no glitches in the install and I don't hose anything.  The c drive is SATA as well as one storage drive and two PATA storage drives which I plan on removing both since they are full anyway.  I'll get a cheap case enclosure to mount those when I need something from storage.    I have the 16.04 on a USB stick and can boot from that.   It will be nice to see it run on a more capable machine.  Thanks again

---

