---
title: "Removing Other OS's"
date: 2008-10-25
forum: General Help
---

### Post by onewhokills on 2008-10-25
Hello, 

I'm in a weird situation. I have a T61, which I installed Debian in first, then opted to switch to XUbuntu. I made the switch because I had used Ubuntu before, but liked the XFCE environment much more then gnome. Anyways...

When I first installed XUbuntu I split my hard drive in half, 40 gigs were Debian, the other 40 were XUbuntu. Then of course I had other random partitions for swap and the sort.

Today I decided that I wanted to remove Debian and use that extra space to save files on...I figured it wouldn't be that difficult to do...but somewhere along the road I messed up.

I ended up opening up GParted Live, and formatted the partition where Debian's main stuff was on (the 40 gig partition) and it's swap partition (which was 2gigs). I formatted both of these to ext3...then restarted.

However, then I reached an issue with GRUB returning an Error 15. After trying the fixes that were online...I ended up installing regular Ubuntu on the 2gig partition that was previously Debians swap. This fixed Grub, and made it so I could once again boot into my beloved XUbuntu.

So after all this I decided to stop messing around until I got help from you all.

My final goal is to only have XUbuntu installed with the rest of the extra space as a partition where I can save files. How should I go about doing this?

(Sorry I release this is probably a little confusing, I will explain anything you guys want.) 

I JUST NEED HELP!

---

### Post by bryonak on 2008-10-25
The problem was probably the place where your GRUB settings were located: I suspect the Debian partition.
When you killed it, GRUB could start from the MBR of your drive, but probably didn't find any meaningful config files.

Try playing around with grub-install and grub-set-default. Or even better, wait for someone who knows better than me how to exactly fix this ;)

---

### Post by onewhokills on 2008-10-25
anyone?

---

### Post by sdowney717 on 2008-10-25
Super grub to the rescue!

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by onewhokills on 2008-10-26
ok, thats awesome thats one part of the issue.

Now I'm trying to get the 40 gig partition that used to be Debian to be a place where I can put files. 

I formatted the Drive to ext2, but I still can't access it in XUbuntu, anybody know how I could fix that?

---

### Post by sdowney717 on 2008-10-26
after you format a drive do a reboot and it should be picked up

---

### Post by onewhokills on 2008-10-26
Attached is a picture of gparted, with thunar in the background. As you can see thunar is not showing the formatted drive.

Any ideas why, I've tried rebooting but sadly that doesnt seem to do the trick.

Thanks for your help!

---

### Post by bryonak on 2008-10-26
Boot your system and try this in a terminal:
```

sudo mkdir /media/MyOtherPartition
sudo mount /dev/sda11 /media/MyOtherPartition

```

Feel free to change the folder name to something more meaningful.
If this gives you access to the partition (either as a desktop shortcut or by browsing the /media folder), you can add it into your /etc/fstab file (file system table).
```
sudo nano /etc/fstab
```
and then add this line under the others:
```
/dev/sda11     /media/MyOtherPartition  ext2    relatime    0       2

```

While we're at it, you can post the content of your /etc/fstab file here, to let us see if something went wrong. This is done easiest with the following command:
```
cat /etc/fstab
```

---

### Post by sdowney717 on 2008-10-27
cat /etc/fstab
I wonder how useful this is. I have 2 drives in my system sda and sdb
And if I show fstab it does not mention sdb at all
But it exists as an ext drive here is the picture

and for him, it should simply autodetect and mount, I did not do anything unusual to add my second drive. But it did not show up in my places until a reboot.

---

### Post by bryonak on 2008-10-27
The fstab (file system table) is the main configuration file for your computer's static file systems. This is what the partition config tools write to and where programs like mount applets get their info from.
Additionaly, the mtab (/etc/mtab) file is the main configuration file for your computer's dynamic, runtime-detected file systems (actually all mounted file systems, but in addition to the static ones, here you have USB and others too). It may be that with your system the drive at sdb is loaded dynamically, that's sometimes the case when you have some 'rather uncommon' setup (e-SATA, some kinds of RAID or similar).
Take a look at mtab to see if it's there. Also take a look at System->Administration->System Monitor->File Systems to get a nice graphical overview on what is mounted where.

Now if you simply want to have a file system always mounted, without the possibility of removing it while the system is operational (without manual umount, that is), fstab is the recommended way.
Ideally, this should be done automatically (either in fstab or mtab), but for some reason it isn't. Maybe the program responsible for this only does it flawlessly when installing Ubuntu, whereas *onewhokills* has changed his partition layout post-install. It could have any other reason though.
Still just adding it to your fstab will, while not being very user friendly, work.

EDIT: Changing the mtab file won't work, because it is permanently being rewritten by the system (at each boot and when inserting removable media)

---

