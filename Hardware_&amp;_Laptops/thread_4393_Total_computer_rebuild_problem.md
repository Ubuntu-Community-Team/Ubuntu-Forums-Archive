---
title: "Total computer rebuild problem"
date: 2004-11-14
forum: Hardware &amp; Laptops
---

### Post by AerodynamicHair on 2004-11-14
I'm a newbie to linux, so be easy on me.

A little while ago, I installed Ubuntu on an old 450mhz P3 computer.  It ran well enough, and recognized everything I had on there, even an old off-brand name video card.  Since then, I've been using Ubuntu alot for some of my basic tasks.  Its a good OS, and I'm getting used to it though I still have a few problems.

Recently, I went to a computer show and bought a few upgrades to my computer, which basically include a new motherboard, new video card, a new processor, a cd/rw drive, and an extra hard drive.  I plugged everything up and ran it, and it all seemed to be working fine.  But, when I look in the filesystem, I can't find the extra drive or the new cd drive I installed.  They're present in the device manager, but I don't know how to get to them.  Everything else seems to be working fine, and the BIOS detected all the drives.

What do I do?

---

### Post by costoa on 2004-11-15
[QUOTE=AerodynamicHair]I'm a newbie to linux, so be easy on me.

A little while ago, I installed Ubuntu on an old 450mhz P3 computer.  It ran well enough, and recognized everything I had on there, even an old off-brand name video card.  Since then, I've been using Ubuntu alot for some of my basic tasks.  Its a good OS, and I'm getting used to it though I still have a few problems.

Recently, I went to a computer show and bought a few upgrades to my computer, which basically include a new motherboard, new video card, a new processor, a cd/rw drive, and an extra hard drive.  I plugged everything up and ran it, and it all seemed to be working fine.  But, when I look in the filesystem, I can't find the extra drive or the new cd drive I installed.  They're present in the device manager, but I don't know how to get to them.  Everything else seems to be working fine, and the BIOS detected all the drives.

What do I do?[/QUOTE]

Since the BIOS is seeing all the drives then we know it's not an IDE conflict. Do you need to do a manual mount? Assuming the new HD is hdc then:

sudo mkdir /mnt/otherdrive
sudo mount -t ext3 /dev/hdc1 /mnt/otherdrive
ls -l /mnt/otherdrive

Personally I'd:
- Put in all the parts execpt the old HD.
- Fresh install Ubuntu
- Reinstall the old HD
- Either manual mount or add to your /etc/fstab

Let us know how the manual mount goes.

---

### Post by az on 2004-11-15
No.  The problem is that you expect these things to be detected by Ubuntu and set up accordingly.

In linux, all your mountpoints are specified in /etc/fstab.  These will be mounted at boot.  On installation, you enter your partition information, select the partitions you want and mountpoints are created in fstab.  When you add hardware to your computer, you are free to create a new mountpoint (mkdir /cdwriter) and add an entry to your fstab so that they are there when you want to access them.

Ubuntu is great at detecting and mounting removable media (usb drivers and so forth) but it does not care about static devices.  I suppose it would be easy to write a script which would play around with your fstab at boot, but this is something that just has not been done. 

So, no, you do not have to reinstall.  Just read the fstab documentation and add the entries there.  Do this as root (sudo).  You can even just copy the entries that are there and modify the paramters there.  'Should take you a minute.

Then do mount -a
and then just 
mount
to see what is mounted...


Enjoy!

---

### Post by AerodynamicHair on 2004-11-15
[QUOTE=azz]No.  The problem is that you expect these things to be detected by Ubuntu and set up accordingly.

In linux, all your mountpoints are specified in /etc/fstab.  These will be mounted at boot.  On installation, you enter your partition information, select the partitions you want and mountpoints are created in fstab.  When you add hardware to your computer, you are free to create a new mountpoint (mkdir /cdwriter) and add an entry to your fstab so that they are there when you want to access them.

Ubuntu is great at detecting and mounting removable media (usb drivers and so forth) but it does not care about static devices.  I suppose it would be easy to write a script which would play around with your fstab at boot, but this is something that just has not been done. 

So, no, you do not have to reinstall.  Just read the fstab documentation and add the entries there.  Do this as root (sudo).  You can even just copy the entries that are there and modify the paramters there.  'Should take you a minute.

Then do mount -a
and then just 
mount
to see what is mounted...


Enjoy![/QUOTE]
 Thanks, went through the fstab and edited the new drive in.  Everything is working alright now, and I can get to the files on the new harddrive.

Thanks alot.

---

