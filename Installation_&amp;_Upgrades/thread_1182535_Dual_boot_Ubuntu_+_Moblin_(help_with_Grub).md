---
title: "Dual boot Ubuntu + Moblin (help with Grub)"
date: 2009-06-09
forum: Installation &amp; Upgrades
---

### Post by linorics on 2009-06-09
Hey,

I'm trying to dual boot my new Acer Aspire One netbook into three operating systems; Windows XP, Ubuntu 9.04, and Moblin Beta 2.0.

The problem is, there are 2 boot loaders that I have tried, the Moblin boot loader (which never allows me to boot into Ubuntu) and the Ubuntu boot loader (which never allows me to boot into Moblin) 

Currently I have the netbook set up with the Ubuntu boot loader. 
It picks it up and puts it in the "Other operating systems:" area, and it comes up as:

"Moblin (2.6.29.4-6.1.moblin2-netbook) (on /dev/sda3"

But if I select it and try to boot into it it comes up with:

"Error 23: Error while parsing number"
"Press any key to continue..."

So I've tried using the Moblin boot loader and the Ubuntu one, neither of them pick up the other operating system, but both of them pick up Windows XP fine. How should I fix this? 

Any suggestions?

Thanks. :D

---

### Post by zvacet on 2009-06-09
Is [this]("http://members.iinet.net.au/~herman546/p15.html#23") of any help to you?

---

### Post by nicepat on 2009-06-10
people said I need to carefully update GRUB manually. there is no mentioning about 'what to do'. I am interested to this article, and want to see the answer of original question. have you tried to change UUID in each GRUB? do you install Moblin first?

---

### Post by Fatman_UK on 2009-06-10
I'm trying to do two-thirds of this (without XP). :) I have the Moblin beta installed correctly, AFAICT. The last task before I boot into Moblin is to edit my GRUB menu on the Ubuntu partition.

I think we can just enter the Moblin boot configuration into /boot/grub/menu.lst after the Ubuntu kernels, but I'm not sure... I'll just check with my other system's menu.lst, which dual boots Ubuntu and XP just fine...

Ok, according to my other system you can enter "other" boot configurations into menu.lst, but they **must** be *outside* the "automagic kernels list"; that is, before the "BEGIN AUTOMAGIC KERNELS LIST" line or after the "END AUTOMAGIC KERNELS LIST" line but *not* between them. If you put it in the automagic kernels list, Ubuntu might delete it when you upgrade your kernel, preventing you booting Moblin. Which would be annoying.

I'm still looking for the correct Moblin config - maybe I can get it off the install USB stick I used.

A question to any GRUB gurus: will Ubuntu automatically update the Moblin boot configuration when the Moblin kernel gets updated?

---- UPDATE ----

Google knows all. :D 

This is a Moblin boot configuration:

title Moblin 2.0 beta
uuid 5c941ab7-929e-4e91-b859-b96ae81d810d
kernel /boot/vmlinuz-2.6.29.4-6.1.moblin2-netbook ro rootdelay=8 root=/dev/sda3 ht=on hpet=disabled

Works for me.

Your UUID will be different. Look in /etc/fstab or type "blkid" in the console to find the UUID of your Moblin partition. I labelled mine "Moblin" as it happens, so it was easy to find in the output of blkid.

You will also need to make sure the bit after "root=" matches your Moblin partition, and make sure the kernel file name is correct.

I have no idea what the other options mean, but it seems to work. Now, I just need to find some nice GRUB colours... ;)

---

### Post by presence1960 on 2009-06-10
if Moblin's bootloader is installed to the Moblin partition you can chainload Moblin in Ubuntu's menu.lst just as you would chainload Windows.
My main OS is Jaunty, but I have Hardy as a backup just in case and XP (which I hardly ever use). here is the end of my menu.lst for Jaunty:

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader	+1

title           Hardy 8.04
rootnoverify    (hd0,1)
chainloader     +1

```

I have Jaunty's Grub on MBR and Hardy's GRUB on it's partition. Obviously Jaunty's GRUB menu comes up on booting. Choosing Hardy brings up Hardy's GRUB menu. From there I choose which hardy kernel to use. The advantage to this is when either OS updates their kernels the menu.lst for that OS is updated. I never have to edit a menu.lst when a kernel updates. The other way when Moblin updates a kernel you will have to edit Ubuntu's menu.lst to get the new Moblin kernel to boot.

---

### Post by linorics on 2009-06-17
Hey guys,

What I ended up doing was this:

I have 4 partitions.

___________
Moblin

Windows XP

Ubuntu 9.04
____________

So, I installed Windows XP on it's partition. Very simple.

I installed Moblin on it's partition, and I also told the boot loader to install on the same Moblin partition, instead of the MBR.

Then I installed Ubuntu 9.04 on it's partition, and told it to install it's boot loader on it's partition, instead of the MBR as well.

After I did that, I ran a Ubuntu 9.04 live CD.
Got onto firefox and downloaded GAG (a open source graphical boot loader)

Followed the instructions to install it onto the MBR.

Then booted and selected each partition, (per instructions included with download) and now it works flawlessly.

I can select any of the 3, and it will bring me to the individual boot loader.

So when I boot to go into Moblin/Ubuntu it brings me to the GAG screen, and then to the GRUB screen, and then starts ubuntu/moblin.

Just thought I'd post and tell everyone how I got it to work. :D:popcorn:

---

### Post by presence1960 on 2009-06-17
Congrats, enjoy ! Nice work too!

---

### Post by jimmidik on 2009-06-23
The chainloader +1 worked for me as the last OS option I have

title           Moblin
rootnoverify    (hd0,3) 
chainloader     +1

of course the "rootnoverify   (hd_,_) will be different 

thank you very much I screwed with this for days.  Now I have:

Acer Aspire One 150 
Tri-Boot

Windows XP
Ubuntu Netbook Remix 9.04
Moblin 2.0 Beta

---

### Post by darthbushi on 2009-07-04
@linorics:

Hey, I want to try what you did, but I'm not sure how to do it. Here's the thing: I have Ubuntu Jaunty installed and working perfectly, so I don't want to do a fresh install, and I already cleared up space for Moblin and installed it successfully. The problem is that I couldn't boot Ubuntu after installing Moblin, and after restoring Ubuntu's grub into the MBR I haven't been able to boot Moblin at all. I have tried to edit my menu.lst file without any luck, and I'm thinking that I should reinstall Moblin keeping its bootloader in its partition.

The question is: how do I tell the Moblin installer not to put the bootloader in the MBR but in the Moblin root partition?

Thanks for your help!

ED: By the way, I have Ubuntu running on a ReiserFS partition... Do you think that has anything to do with my problem?

ED2: Nevermind, I found the option on where to install the bootloader for Moblin, and I can now dualboot! Woot!

---

### Post by Scotty519 on 2009-10-10
> **Fatman_UK said:**
> I'm trying to do two-thirds of this (without XP). :) I have the Moblin beta installed correctly, AFAICT. The last task before I boot into Moblin is to edit my GRUB menu on the Ubuntu partition.

I think we can just enter the Moblin boot configuration into /boot/grub/menu.lst after the Ubuntu kernels, but I'm not sure... I'll just check with my other system's menu.lst, which dual boots Ubuntu and XP just fine...

Ok, according to my other system you can enter "other" boot configurations into menu.lst, but they **must** be *outside* the "automagic kernels list"; that is, before the "BEGIN AUTOMAGIC KERNELS LIST" line or after the "END AUTOMAGIC KERNELS LIST" line but *not* between them. If you put it in the automagic kernels list, Ubuntu might delete it when you upgrade your kernel, preventing you booting Moblin. Which would be annoying.

I'm still looking for the correct Moblin config - maybe I can get it off the install USB stick I used.

A question to any GRUB gurus: will Ubuntu automatically update the Moblin boot configuration when the Moblin kernel gets updated?

---- UPDATE ----

Google knows all. :D 

This is a Moblin boot configuration:

title Moblin 2.0 beta
uuid 5c941ab7-929e-4e91-b859-b96ae81d810d
kernel /boot/vmlinuz-2.6.29.4-6.1.moblin2-netbook ro rootdelay=8 root=/dev/sda3 ht=on hpet=disabled

Works for me.

Your UUID will be different. Look in /etc/fstab or type "blkid" in the console to find the UUID of your Moblin partition. I labelled mine "Moblin" as it happens, so it was easy to find in the output of blkid.

You will also need to make sure the bit after "root=" matches your Moblin partition, and make sure the kernel file name is correct.

I have no idea what the other options mean, but it seems to work. Now, I just need to find some nice GRUB colours... ;)

I was successful using this method with Moblin 2.1 dual booting with eeebuntu. Does anyone know, or point me to where I can find info on the ro, ht, and hpet inline commands? I tried the GRUB manual, but didn't seem to find them there.

---

### Post by mailme45 on 2009-10-10
I was having having trouble dual booting Ubuntu and Moblin (no windows). I was able to solve the issue thanks to the post by presence1960.

What I did:
Installed Ubuntu on its own partition, with the boot loader on the MBR.
Then installed Moblin on a separate partion, only this time put the Moblin boot loader on the same partion as Moblin (NOT THE MBR)
I then rebooted into Ubuntu, and opened the terminal and used gedit /boot/grub/menu.lst
All I had to do here is add:
title           Moblin 2.0 beta
rootnoverify    (hd0,2) 
chainloader     +1

I'm new and spent 3 days to figure out what to do so for anyone else who needs it, the  (hd0,2) refers to where the boot loader for Moblin is located.  The 0 here was the hard drive (the only one I have) and the 2 was the partion.

Works perfectly!

---

### Post by fileexit on 2009-11-28
i managed to get ubuntu 9.10 netbook remix to triple boot with moblin 2.1 and Windows XP on Asus eeepc 1008ha.  here is what i did

I kept the original windows that came pre-installed on the hard disk.  I first used GParted to resize the windows partition down to 30 GB, so now i have first partition for windows, and the last 2 partition for windows image (5 GB) and the boot booster partition.

I installed Moblin from a usb live image, i created a new 20 GB ext3 partition and 2 GB swap partition, but then i cleared the checkbox to install a boot loader (i.e. no boot loader at all when installing moblin).  
After moblin was installed, i rebooted but from Ubuntu 9.10 live image, and installed just normally, adding another 20GB ext4 partition and another 2G swap partition (not sure if i can use the same swap, but i understood that hibernation means copying ram to the swap partition? i.e. if ubuntu went into hibernation, moblin should not use the same swap partition).  During ubuntu installation, i choose to install the boot loader on the MBR.  Then all is done... you get the triple boot working nicely

along the way of learning to complete this triple boot, the command grub-mkconfig was very useful in saving time of editing /boot/grub/grub.cfg.

Hope that was useful

---

