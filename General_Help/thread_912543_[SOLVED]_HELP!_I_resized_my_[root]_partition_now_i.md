---
title: "[SOLVED] HELP! I resized my [root] partition now it wont boot."
date: 2008-09-06
forum: General Help
---

### Post by modmadmike on 2008-09-06
I resized my [root] partition now it wont boot. The partition type is ext3 and Grub is working; however, when I get to the splash screen it just keeps loading  for a while. I went into recovery mode and it gives me the Error "/dev/disk/by-uuid/(i forgot the exact name but it was like an MD5-sum) not found." then I get dropped to a Busy box prompt. I have a copy of Linux on my ipod in which i am running right now so can I just copy the UUID (the correct one because it mounted a few) from it to my main install then change grub to reflect the new UUID or is it not that simple? My sudo fdisk -l output is ```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1       29834   239641573+  83  Linux
/dev/sda3           29835       30401     4554427+  82  Linux swap / Solaris

Disk /dev/sdb: 20.0 GB, 20000267776 bytes
255 heads, 63 sectors/track, 2431 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        1161        2431    10209307+  83  Linux
/dev/sdb2               6        1160     9277537+   b  W95 FAT32

Partition table entries are not in disk order
```

---

### Post by drs305 on 2008-09-06
When you resized your partition the UUID may have changed. I am not sure from your post whether you have the current correct UUID of the root partition. I think what you were proposing was essentially correct but I'll go through the steps. This assumes you know the /dev location of the root partition and it hasn't changed (i.e. it is still the same partition number).

Boot to a command prompt if you can or use the LiveCD. 

If you can get to a prompt, use the following command to check the UUID of your root partition:
```
sudo blkid
```

You can boot to the grub menu and then hit ESC. Use the arrow keys to highlight your normal startup kernel in the menu and hit E. This will put you in the Edit mode. Use your cursor to hightlight the line with the UUID and hit E again to edit that line. Replace the UUID, hit enter, and ESC back to the main menu. You should be set. Boot.

If you have to use the LiveCD, it would be easier at this point to mount your root partition and edit menu.lst manually.
Once the LiveCD has booted, open a terminal (Applications, Accessories, Terminal) and:
```

sudo mount /dev/sd**[COLOR="Red"]XX[/COLOR]** /mnt
cd /mnt/boot/grub
sudo cp menu.lst menu.lst.092008
gksu gedit menu.lst

```

Manually edit the entry for / and make sure the UUID is correct. If you have a separate home partition check that one as well.

---

### Post by modmadmike on 2008-09-06
Thanks! :) Now i just have to reboot into the install and see if it works.

---

### Post by modmadmike on 2008-09-06
No good now its just dropping to Busybox w/o the error and locking up in recovery mode (but it still shows USB disconnects/connects), If I rename the old UUID file in /dev/disk/by-uuid to the new UUID will it work?

---

### Post by drs305 on 2008-09-06
modmadmike,

sorry it didn't work. feel free to remove the 'thanks' ;-)

i don't know if what you propose will work or not. i am about to retire for the evening. whatever you try, make a backup copy of any file you plan on changing. i would restore menu.lst.092008 to menu.lst (via livecd if necessary) as at least you got to grub earlier.

i'll check back tomorrow to see if you have this resolved. best wishes.

---

### Post by falcon61102 on 2008-09-06
It may be locking up in the recovery mode if you didn't change the UUID for that as well in the menu.lst.  Also, you are probably going to have to edit your fstab as well to reflect the new UUID's and that could be what's causing this error.

If you boot up from the LiveCD then run:
```
sudo blkid
```
That will display all your UUID's like before.  Now mount your internal drive like you did before with:
```
sudo mount /dev/sdXX /mnt
```

And bring up the fstab with:
```
gksudo gedit /mnt/etc/fstab
```

Now compare the UUID's for each partition in there and compare them with the results of the blkid command you ran a minute ago.  Since you resized your partition, it's more than likely at least one of these changed.  Save, close and reboot.

---

### Post by modmadmike on 2008-09-06
I think ill try adding the main partition to the IPOD's grub and see if that helps :)

---

### Post by falcon61102 on 2008-09-06
If that doesn't work, try the fstab.  

Any time you resize a root or home partition, you need to update the fstab as well as the menu.lst otherwise Ubuntu will not be able to mount it and that can cause the errors.

---

### Post by modmadmike on 2008-09-06
after running the command gksudo gedit /mnt/etc/fstab the file appears to be empty on both the IPOD (my "live cd") and the Main install

---

### Post by drs305 on 2008-09-06
falcon61102,

Thanks for adding that. I'd just got into bed when I realized I hadn't mentioned fstab so I came back out and fired up the computer again.

madmodmike,

if the partition uuid's changed, that must be reflected in both the normal kernel and recovery mode, as well as fstab's / entry. Run the blkid command and make sure the UUID for the root partition is correct in all three places.

I still don't quite understand what you are doing with the IPOD but if it doesn't work the solution will be to boot to the LiveCD and make the changes in the last two posts.

I'll sleep better now. Thanks again falcon.

---

### Post by modmadmike on 2008-09-06
The ipod has a full install that i use to recover or run while on a crappy windows pc.

---

### Post by falcon61102 on 2008-09-06
drs305,
Lol... no worries.  Sleep well.


modmadmike,
That file shouldn't be empty.  Check your mount points for your partitions, it's likely you accidently mounted the wrong partition on /mnt and that's why it appears empty.  If you are unsure at which one, post (again) the results from
```
sudo fdisk -l
```
And I'll take a look.  I just want to make sure nothing changed since the last time you posted that info.

---

### Post by modmadmike on 2008-09-06
The fstab file was in /etc not /mnt/etc on both installs I wonder if they changed this in hardy

---

### Post by falcon61102 on 2008-09-06
The file location didn't change, it was some confusion with your mount point.  As long as you found it, you should be able to make the changes necessary.  Just make sure you open it with a terminal using sudo so that you can save the changes.

---

### Post by modmadmike on 2008-09-06
The UUID was correct so I guess that means the file system got broken while I was resizing:(. Or the fact that it still had a UUID for my old NTFS partition which is gone (I deleted it to resize the Root partition) was what caused all the problems which means it is fixable.

---

### Post by falcon61102 on 2008-09-06
The UUID matched the one that you put in the menu.lst for your root partition?  That's odd because the fstab normally doesn't automatically update like that.

---

### Post by modmadmike on 2008-09-06
looks like I need to reinstall thanks for your help though. I tried to avoid this at all costs because it means recompiling drivers (including my wacom driver), reinstalling all my applications and hope that the installer will not kill my current /home directory which has 60gb of things that cant fit on my backup drive. 
It still wont boot I tried my server kernel-19 and the generic-19 it just drops a busybox shell even in the repair mode.

---

### Post by falcon61102 on 2008-09-06
When you install just be careful not to overwrite your home partition.  Don't specify a seperate home parition during the partition process.  Then once it's installed, edit your fstab to point to your backed up home partition and you should be good to go.

---

### Post by modmadmike on 2008-09-06
But I dont have it on a seperate partition :(

---

### Post by falcon61102 on 2008-09-06
If it's not on a seperate partition, it's going to get overwritten.  You mentioned that you resized your root partition.  If you do that again, this time making it smaller, you can create a seperate partition to back your /home partition up to.  At most you really only need a 20 gig root partition, and that's a lot.  The rest you can put on a seperate /home partition.  That way you can always keep it seperate.

---

### Post by modmadmike on 2008-09-06
But I always install alot of software lol and IDK if it will get messed up this time too. But I guess Ill try.

---

### Post by modmadmike on 2008-09-06
Deleted

---

### Post by modmadmike on 2008-09-07
Can I also mount the Home partition as /usr/ that way the programs install there too, or is that just too crazy?

---

### Post by falcon61102 on 2008-09-07
That's probably not the best idea.  If you need a larger Root partition, that's fine, but it's still best to leave enough room for a seperate /home partion.

---

### Post by modmadmike on 2008-09-07
Thanks:)

---

### Post by falcon61102 on 2008-09-07
Not a problem.

---

