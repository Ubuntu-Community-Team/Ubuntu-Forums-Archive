---
title: "Using 3 Operating Systems. Two Drives"
date: 2009-02-23
forum: Installation &amp; Upgrades
---

### Post by Abydosgater on 2009-02-23
Hi, I currently have just a winXP Pro installation on my desktops primary hard drive.

I was just wondering if it was possible if i get a internal hard drive, to install both Vista and Ubuntu on the second drive.

So i would have it:
Main HD: Full XP Drive
New HD: Half Vista/Half Ubuntu

Is it possible to do this on the new drive?
Do i just install Vista first, and then install Ubuntu as a second partition on the new harddrive?

My last question is if i do get this working, Where will GRUB be installed?
I plan on getting a new computer within the next few months, When i get my new computer i will be taking my new harddrive and putting it into the new computer. Will that still have grub to select what to boot? (vista/ubuntu)

Also if i do take the second hd out with grub, will the old computer still know to boot XP?

I hope this makes sense, thank you for your time in reading =]

Abydos

---

### Post by Pumalite on 2009-02-23
XP, Vista and Ubuntu last is ideal. Grub will be installed in sda (probably your new drive)

---

### Post by zwygart on 2009-02-23
Be sure that GRUB don't override the bootloader of XP. This way, if you take the second HD away, XP will boot normally.

When you put the drive with Vista and Ubuntu in another computer but not as the same number, then you may have to change some settings in /boot/grub/menu.lst

If you have any problem, post here and you should have a answer fast, since this is a well know problem here.

---

### Post by Pumalite on 2009-02-23
Vista will override XP which is what you want.
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)
[http://lifehacker.com/software/ubuntu/hack-attack-how-to-tripleboot-windows-xp-vista-and-ubuntu-193474.php](http://lifehacker.com/software/ubuntu/hack-attack-how-to-tripleboot-windows-xp-vista-and-ubuntu-193474.php)

---

### Post by Abydosgater on 2009-02-23
Ok thanks,

So what i should do is put in the new drive, install vista and get that working.

Then install Ubuntu which will install grub. I take it that grub will automaticly show all XP/Vista/Ubuntu in the menu.lst or will i have to add XP?.

And then when i move the drive to another computer, i just change the grub menu.lst on the new computer, and run xp's fixmbr on the old computer?

Abydos

---

### Post by Pumalite on 2009-02-23
I misunderstood you. I thought you planned on leaving that drive in the same computer. I doubt you could do it unless computers have similar hardwares.

---

### Post by caljohnsmith on 2009-02-23
If you want to be able to move the Vista/Ubuntu drive to another computer, you should make sure you install Grub to the MBR of the Vista/Ubuntu drive, and not to your XP drive. To do that, when you go through the Ubuntu installer, click the "advanced" button near the end of the installation process, and specify "/dev/sdb" (or whichever is the Ubuntu/Vista drive) as the location to install Grub to. Then you can move that HDD to another computer and it will at least be bootable, but if the hardware of the other computer is really different, you may have problems booting Ubuntu or Vista.

---

### Post by Abydosgater on 2009-02-23
Well yes i will be leaving it in the same computer.

But in a few months i plan on getting a new computer. Then i will take the harddrive out and put it in the new computer. I will have to reconfigure Grub to work on the new computer as the HD order/numbers will change? Do i have that right? :P

Sorry for the nooby questions, im a software developer, great once a computer is started but getting it all set up with drives on the inside isnt something im experienced at.

> **caljohnsmith said:**
> If you want to be able to move the Vista/Ubuntu drive to another computer, you should make sure you install Grub to the MBR of the Vista/Ubuntu drive, and not to your XP drive. To do that, when you go through the Ubuntu installer, click the "advanced" button near the end of the installation process, and specify "/dev/sdb" (or whichever is the Ubuntu/Vista drive) as the location to install Grub to. Then you can move that HDD to another computer and it will at least be bootable, but if the hardware of the other computer is really different, you may have problems booting Ubuntu or Vista.

Update sorry: Yeah i understand now thanks =] so install grub to vista/ubuntu drive so i can boot it. =]

---

