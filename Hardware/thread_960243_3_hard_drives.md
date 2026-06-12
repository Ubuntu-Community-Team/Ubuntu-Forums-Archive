---
title: "3 hard drives"
date: 2008-10-27
forum: Hardware
---

### Post by SpikeyMike on 2008-10-27
hi, I have 2 sata hard drives in my pc, one with ubuntu the other with windows, I bought a 3rd drive and connected it to the sata 3 connection and it works fine with ubuntu, but when I try to boot into windows it just stops at the splash screen, it boots ok in safe mode though, the problem seems to be when I have more than 2 hard drives connected I think, any ideas?

Spikey

---

### Post by phidia on 2008-10-27
Which version of windows are you using and how is the drive formatted?

---

### Post by SpikeyMike on 2008-10-27
> **phidia said:**
> Which version of windows are you using and how is the drive formatted?

hi, I am using windows xp, the ubuntu drive is 80gb and is connected to sata 1, the windows drive is 300gb and is connected to
sata 2 and the new drive is 1tb connected to sata 3, if I go into the bios the drive is recognised and it is also recognised in ubuntu and in windows safe mode....

Regards

Spikey

---

### Post by SpikeyMike on 2008-10-27
> **SpikeyMike said:**
> hi, I am using windows xp, the ubuntu drive is 80gb and is connected to sata 1, the windows drive is 300gb and is connected to
sata 2 and the new drive is 1tb connected to sata 3, if I go into the bios the drive is recognised and it is also recognised in ubuntu and in windows safe mode....

Regards

Spikey

forgot to add that the new drive is ntfs

---

### Post by caljohnsmith on 2008-10-27
When you say you can't boot into Windows, are you booting Windows from Grub, or are you changing your BIOS to boot the Windows drive on start up?

---

### Post by SpikeyMike on 2008-10-28
> **caljohnsmith said:**
> When you say you can't boot into Windows, are you booting Windows from Grub, or are you changing your BIOS to boot the Windows drive on start up?

I am booting from grub, but I also tried restoring the mbr on the windows drive so I could boot directly from that drive and it still wouldn't boot with the 3 hard drives attached, when I unattached the ubuntu disk windows booted ok with just the new drive attached.....

Spikey

---

### Post by caljohnsmith on 2008-10-28
> **SpikeyMike said:**
> I am booting from grub, but I also tried restoring the mbr on the windows drive so I could boot directly from that drive and it still wouldn't boot with the 3 hard drives attached, when I unattached the ubuntu disk windows booted ok with just the new drive attached.....

Spikey
Your problem might be if you have the new SATA drive before the Windows drive in the BIOS boot order, then even though BIOS can't boot your new drive (no OSes on it), BIOS would default to booting the next drive in the boot order which could be your Windows drive; the problem though is that Windows XP insists on being booted from the first drive in the BIOS boot order on start up, unless you modify Windows XP's boot.ini file, or do something like boot Windows from Grub and use Grub's mapping technique to fool Windows into thinking it is on the first boot drive. Can you check your BIOS settings, and maybe change the boot order around to see if that helps?

Also, please post:
```
sudo fdisk -lu
```

---

### Post by dabl on 2008-10-28
The last time I had the honor of discussing my Win XP license with Microsoft technical support, they informed me that I was legally limited to a maximum of two hard drives by the license terms.  They said I would need to buy a server license to run Windows on a machine with more than two drives.

:(

That was 2+ years ago. Win XP now runs in a VMware window, on a machine with 5 hard drives.

**I win.**

:lolflag:

---

### Post by Cowzor on 2008-10-28
What only 2 hard drives? I've got dual boot on my main machine, windows doesn't complain there. And on another machine which had windows as well had 4 hard drives. Then again, both were XP professional, but 2 hard drives still seems weird.

---

### Post by GROMS on 2008-10-28
Beg your forgiveness for a newbe but,  installed the 64 bit version on a new system with a 3ware sata controller with 4 HDs. In the controller I set them as mirrored pairs. During install, Ubuntu seemed to only see and install to the first pair of drives. I tried to follow the book "Beginning Ubuntu Linux" by Thomas and Sicam but they assume you want or have MS win. I want just linux and be able to see and use the pair of mirrors for about a TB of space. Where am I going wrong?? [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by dabl on 2008-10-28
Linux does not necessarily provide drivers for the RAID chips in your SATA controller (or mine).  I don't do RAID, but "mirroring" is also known as RAID 1, and that's what you're talking about.

Google "dmraid" and "mdadmin" if you want to learn how to set up RAID in *buntu, and also search this forum on those terms. :)

---

### Post by dabl on 2008-10-28
> **Cowzor said:**
> What only 2 hard drives? I've got dual boot on my main machine, windows doesn't complain there. And on another machine which had windows as well had 4 hard drives. Then again, both were XP professional, but 2 hard drives still seems weird.


My license is also Win XP Pro.  Here's a reasonable description of the Win XP license:

[http://www.aumha.org/win5/a/wpa.php](http://www.aumha.org/win5/a/wpa.php)

but I did not see where he specifically states "2 hard drives max".  However, that is exactly what MS told me on the phone, when I called to re-activate after a crash of my two mirrored hard drives.  That little tidbit drove me to look into running Linux.

---

### Post by SpikeyMike on 2008-11-03
hi, the strange thing is it boots ok in safe mode and I can see and access the drive there.

Thing is I now have another problem, I restored the grub menu from a live cd, I installed it on the drive where ubuntu is installed. The thing is now ubuntu won't start, I see the splash screen and then after a couple of minutes I see:

[COLOR="Red"]busybox v1.1.3

..................

(initramfs)
[/COLOR]
and cannot go any further, I tried booting ubuntu recovery mode but then I see the following:

[COLOR="Red"]check root= bootarg cat /proc/cmdline
or missing modules devices: cat /proc/modules ls/dev
ALERT! /dev/disk/ by-uuid/06bde937-1412-421d-a18f-867e43559455 does not exist. Dropping to a shell!

busybox v1.1.3

.................

(initramfs)[/COLOR]

does this mean it cannot find my ubuntu installation? any help appreciated

Spikey

---

### Post by SpikeyMike on 2008-11-04
help :( :confused:

---

### Post by SpikeyMike on 2008-11-04
any advice greatly appreciated.......

---

### Post by zeroge on 2008-11-04
Do you want to be a blonde one day and a redhead the next? One way to do this is to dye your own hair and restyle it, but you can achieve the same effect with much less effort &#8722; just buy [lace wig](http://www.cosprops.com/lacewigs.html). To select a wig that would be indistinguishable from real [human hair wigs](http://www.cosprops.com/lace-human-hair-wigs-c-10.html) and become your favorite fashion accessory, though, you need to know a few insider tips. First of all, if youre worried that [full lace wigs](http://www.royalmewigs.com) will look natural on your head, never fear! A properly made wig &#8722; even the quality synthetic varieties &#8722; can look totally realistic. Which is best &#8722; synthetic or human hair wigs? Wigs can be synthetic or made from real human hair. Synthetic [front lace wigs](http://www.cosprops.com/lacewigs.html) is cheaper, but the very cheap ones you can find online dont look real enough. On the other hand, high quality synthetic [cosplay wigs](http://www.cosprops.com/cosplay-wigs-c-5.html) like Revlon, Raquel Welch or Paula Young wigs look very real. Also, synthetic wigs are easier to care for, as you dont need to restyle them every time you wash them.

---

### Post by psusi on 2008-11-06
You say you installed grub to the drive ubuntu is on?  Which drive is that?  Is that the drive your bios is set to boot from?

Post the output of sudo fdisk -l and the contents of /boot/grub/menu.lst.

---

### Post by SpikeyMike on 2008-11-07
> **psusi said:**
> You say you installed grub to the drive ubuntu is on?  Which drive is that?  Is that the drive your bios is set to boot from?

Post the output of sudo fdisk -l and the contents of /boot/grub/menu.lst.

hi, yes I installed grub on the ubuntu drive and then set the bios to boot that drive, when I boot the pc I see the grub menu and when I select ubuntu it starts to boot, I see the splash screen but then after about 2 minutes I see the output in my earlier post. unfortunately I cannot boot into ubuntu to post the output of sudo fdisk -l and /boot/grub/menu.lst :(

Spikey

---

### Post by psusi on 2008-11-07
> **SpikeyMike said:**
> hi, yes I installed grub on the ubuntu drive and then set the bios to boot that drive, when I boot the pc I see the grub menu and when I select ubuntu it starts to boot, I see the splash screen but then after about 2 minutes I see the output in my earlier post. unfortunately I cannot boot into ubuntu to post the output of sudo fdisk -l and /boot/grub/menu.lst :(

Spikey

Boot from the livecd ;)

From the livecd you should be able to mount the hard disk and get at menu.lst.

What /dev/sdX did Linux see that drive as?

---

### Post by SpikeyMike on 2008-11-08
> **psusi said:**
> Boot from the livecd ;)

From the livecd you should be able to mount the hard disk and get at menu.lst.

What /dev/sdX did Linux see that drive as?

thanks for your reply, how do I mount the disk once I have booted with the live cd?

Spikey

---

### Post by psusi on 2008-11-09
> **SpikeyMike said:**
> thanks for your reply, how do I mount the disk once I have booted with the live cd?

Spikey

sudo mkdir /media/sdX
sudo mount -t ext3 /dev/sdX /media/sdX

Where sdX is whatever the device name of the disk/partition you installed to is.

---

