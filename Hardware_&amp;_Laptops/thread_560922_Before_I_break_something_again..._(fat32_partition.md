---
title: "Before I break something again... (fat32 partition)"
date: 2007-09-27
forum: Hardware &amp; Laptops
---

### Post by Drake2k on 2007-09-27
I have these 2 sata drives, both exactly the same.  They are both partitioned (when I had windows) as Fat32.  Each drive has 2 partictions of 20 gigs each are are named as such.


Sata 1
 20Gig Partition  named ES1   (extra space 1)
 20Gig Partition  named ES2

Sata 2
 20 Gig Partition named ES3
 20 Gig Partition named ES4


Pretty simple eh? 

When I click Places then Computer, It only shows me ES2 3 & 4....not 1.


How do I even begin to troubleshoot this?

I want to get the data off of them before I reformat them as ext3.

---

### Post by Drake2k on 2007-09-27
Anyone?  A point in the right direction of where to look or how to troubleshoot this?

---

### Post by jacob01 on 2007-09-27
how are you viewing the drives? is it in windows or in ubuntu live cd or an install?

if you are in ubuntu and it is installed it might not be displayed because this might be your file system.

---

### Post by Drake2k on 2007-09-27
> **jacob01 said:**
> how are you viewing the drives? is it in windows or in ubuntu live cd or an install?

if you are in ubuntu and it is installed it might not be displayed because this might be your file system.


Purely an Ubuntu Install. Not a live CD.  I did forget to mention that there are a total of 4 drives in the computer.
hda is partitioned for dual boot linux/windows (I really only wanted linux but I'll deal with that later)

hdb is an NTFS 120 gig drive that I can read from just fine and don't need read/write access  just read and that I have.

Then there are the 2 sata drives I mentioned.   My file system is on my bood drive hda 1.  The 2 sata drives are purely for storage.

How I view them is this...
after booting I click on 'Places' then 'Computer'.  It sees and lists all by ES1 on the right.  I double click any of the ones there and it will mount it (asking me for a password)  Then I can access that drive just fine.   It's just that ES1 never shows up anywhere, yet I can see the second partition on that physical drive ES2 just fine.   Hope this helps you help me.

---

### Post by Drake2k on 2007-09-28
Any thoughts?

---

### Post by carloslosgrande on 2007-09-30
[FONT="Comic Sans MS"]When you look at your partitions thru >places>computer do you have one called filesystem?[/FONT]

---

### Post by Drake2k on 2007-09-30
> **carloslosgrande said:**
> [FONT="Comic Sans MS"]When you look at your partitions thru >places>computer do you have one called filesystem?[/FONT]


Yes, that one I do have and if I'm not mistaken that's on hda1 (my primary ide)

---

### Post by carloslosgrande on 2007-09-30
[FONT="Comic Sans MS"]Yes your filesystem is probably on (ide) hda1 and it'll show as / 
whereas the 2nd 3rd and 4th should show as /media/hdb  or sda or sdb.

Ok, have you looked with 'system monitor' and or 'storage device manager'?
I know it should show in >places>computer but its worth a try.

sata will show as sda1 and 2 and sdb1 and 2.

the attachment is from my sys monitor, my sata was originally ntfs and fat32.

Sorry I'm not more help.[/FONT]

---

### Post by Drake2k on 2007-09-30
> **carloslosgrande said:**
> [FONT="Comic Sans MS"]Yes your filesystem is probably on (ide) hda1 and it'll show as / 
whereas the 2nd 3rd and 4th should show as /media/hdb  or sda or sdb.

Ok, have you looked with 'system monitor' and or 'storage device manager'?
I know it should show in >places>computer but its worth a try.

sata will show as sda1 and 2 and sdb1 and 2.

the attachment is from my sys monitor, my sata was originally ntfs and fat32.

Sorry I'm not more help.[/FONT]

Ok, System monitor only shows the drives I have mounted.  So I took a screen shot for you.  As you can see ES2 shows up fine and it's physically located on the same drive as ES1 just two different fat partitions.

[IMG]http://www.grinbox.com/images/SSSM.png[/IMG]

---

### Post by carloslosgrande on 2007-10-01
[FONT="Comic Sans MS"]Screenshot didn't attach, try again[/FONT].
Oops, yes it did.

Alright, in terminal try this>  sudo fdisk -l this will show all the discs and partitions that is seen by the system.
Mine looks like this at the momen, (sda and sdb being the sata drives);
ramses@backroom:~$ sudo fdisk -l
Password:

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1401    11253501   83  Linux
/dev/sda2            1402       19452   144994657+   5  Extended
/dev/sda5           19069       19452     3084480   82  Linux swap / Solaris
/dev/sda6            3946       19068   121475466   83  Linux
/dev/sda7            1402        3945    20434617   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641   83  Linux

Disk /dev/sdc: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        4864    39070048+   c  W95 FAT32 (LBA)

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1          92      738958+   6  FAT16
/dev/sdd2              93       19457   155549362+  83  Linux

---

### Post by Drake2k on 2007-10-01
> **carloslosgrande said:**
> [FONT="Comic Sans MS"]Screenshot didn't attach, try again[/FONT].
Oops, yes it did.

Alright, in terminal try this this will show all the discs and partitions that is seen by the system.
Mine looks like this at the momen, (sda and sdb being the sata drives);
ramses@backroom:~$ sudo fdisk -l

Thanks for the reply.  Here's what I got.


```
drake@Mage:~$ sudo fdisk -l
Password:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       10927    87771096    7  HPFS/NTFS
/dev/hda2           10928       19103    65673720   83  Linux
/dev/hda3           19104       19457     2843505    5  Extended
/dev/hda5           19104       19457     2843473+  82  Linux swap / Solaris

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2432    19535008+   c  W95 FAT32 (LBA)
/dev/sda2            2433        4865    19543072+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2432    19535008+   c  W95 FAT32 (LBA)
/dev/sdb2            2433        4865    19543072+   c  W95 FAT32 (LBA)
drake@Mage:~$ 
```

Oh, look at that.  It sees all the partitions here.  How should I proceed now?

[edit]
Originally there was another 120 gig hd that was NTFS, it's not showing here because I took it out.  
I had to sacrifice it for another box. So it's not part of the equation, but then it never really was.

---

### Post by carloslosgrande on 2007-10-01
[FONT="Comic Sans MS"]Well, its certainly odd, at least to me.
Do you have a GParted live cd? try here; [HTML]http://gparted.sourceforge.net/[/HTML]
Comes in very handy.
You may be able to copy the partition over to another, on your ide drive, and then reformat the disc, and copy back.
It seems simplest to me, I'm hoping that the reformat will kick in the recognition, and I also don't know what else to suggest.
I'm assuming you've already tried restart.[/FONT]

---

### Post by carloslosgrande on 2007-10-01
[FONT="Comic Sans MS"]Just had to go out shopping
....Been thinking,  did you try the 'storage device manager' ? It might give it a kick. All my discs mount automatically from this.[/FONT]

---

### Post by vanadium on 2007-10-01
These are internal drives. Partitions will be automatically available only if they are (correctly) declared in /etc/fstab.

* Post the output of the "mount" command to reveal what is effectively mounted
* Post the contents of your /etc/fstab

Some tests you can do:

Run

sudo mount -a

to remount all your partitions declared in /etc/fstab and see whether an error throws up.

Try mounting your "missing" partition manually and see whether an error throws up.

---

### Post by Drake2k on 2007-10-01
> **carloslosgrande said:**
> [FONT="Comic Sans MS"]Just had to go out shopping
....Been thinking,  did you try the 'storage device manager' ? It might give it a kick. All my discs mount automatically from this.[/FONT]

I don't have anything called Storage Device Manager that I can find.  I did read your responses and Van's.  Here's what I was able to find without blowing anything up so far.

Here is a nice screen shot.
[http://www.grinbox.com/images/Screenshot.png]("http://www.grinbox.com/images/Screenshot.png")

Then when I type 
sudo mount -a

I got this
```
drake@Mage:~$ sudo mount -a
NTFS signature is missing.
Failed to startup volume: Invalid argument
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
Failed to access '/dev/hdb1': No such file or directory
drake@Mage:~$ 

```


I think my fstab is wrong.  Here's what it says.
(Keeping in mind I had a 120 Gig NTFS drive that I don't have anymore)
```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda2 :
UUID=d496d4bc-c755-41af-bbe5-351517fa8be9 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda5 :
UUID=e6e84c1d-02e5-40f1-91ac-3fef2f9642ea none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/sdb1 /media/New\040Volume ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/hdb1 /media/120 ntfs-3g defaults,locale=en_US.UTF-8 0 0
```

---

### Post by Drake2k on 2007-10-01
> **Drake2k said:**
> I don't have anything called Storage Device Manager that I can find.  I did read your responses and Van's.  Here's what I was able to find without blowing anything up so far.

Ok...Some success.

After writing this I realized there isn't much that Synaptic can't get for me so I told it to fetch Storage Device Manager.

I played around with it and saw that my drive was trying to be mounted as ntfs or something and so I went through and made sure all my Fat32 partitions were made equal.  Reboot and now here is what my FSTAB says

```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc           proc         defaults                     0  0  
# Entry for /dev/hda2 :
UUID=d496d4bc-c755-41af-bbe5-351517fa8be9  /               ext3         defaults,errors=remount-ro   0  1  
# Entry for /dev/hda5 :
UUID=e6e84c1d-02e5-40f1-91ac-3fef2f9642ea  none            swap         sw                           0  0  
/dev/hdc                                   /media/cdrom0   udf,iso9660  user,noauto                  0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto               0  0  
/dev/hdb1                                  /media/120      ntfs-3g      defaults,locale=en_US.UTF-8  0  0  
/dev/sda1                                  /media/ES1      vfat         defaults                     0  0  
/dev/sda2                                  /media/ES2      vfat         defaults                     0  0  
/dev/sdb2                                  /media/ES4      vfat         defaults                     0  0  
/dev/sdb1                                  /media/ES3      vfat         defaults                     0  0  
```

Does that not look so much better?

I have all four of my Fat32 partitions now. THANK YOU SO MUCH.

There is one small annoyance.

If you look at my fstab up there....to 'me' it looks fine....but on my desktop where it lists all my ES1-4 drives....  ES1 is labeled as ES1 (2) and ES3 is labeled as ES1.
Device manager says ES3 is ES3, but when I click the unmount button.  My ES1 vanishes.  I click mount, it comes back.  When I click on unmount for ES1, the ES1 (2) vanishes and when I remount ES1... ES1 (2) comes back.  Does this make any sense?  

I'm going to reboot and see if this clears up.

I can't find in the device manager where that's doing that.   Any thoughts?

[edit]
Nope didn't clear up.
I am learning a lot though and appreciate the help.  If we can just figure out this silly annoyance.

---

### Post by idkwot on 2007-10-01
helped for me also, thanks!

---

### Post by carloslosgrande on 2007-10-01
[FONT="Comic Sans MS"]Hi, been busy getting compiz working.
You could try renaming the drives again that may help sort it out, look here[HTML];https://help.ubuntu.com/community/RenameUSBDrive[/HTML]
By the way, you've done well.
When you reformat to ext3 that'll probably fix that little difficulty also.[/FONT]

---

### Post by Drake2k on 2007-10-02
> **carloslosgrande said:**
> [FONT="Comic Sans MS"]Hi, been busy getting compiz working.
You could try renaming the drives again that may help sort it out, look here[HTML];https://help.ubuntu.com/community/RenameUSBDrive[/HTML]
By the way, you've done well.
When you reformat to ext3 that'll probably fix that little difficulty also.[/FONT]


HAHA this is funny, watch this.

```
drake@Mage:~$ sudo mlabel -i /dev/sdb1 -s ::ES3
Password:
 Volume label is ES1        
drake@Mage:~$ 
```


at least now I can access and move the data off even if the labeling is a little screwy.  I'm going to reformat them for ext3 that way I don't have to have 2 partitions per disk.  ^^  

Wish me luck.

---

### Post by Drake2k on 2007-10-02
I just pat myself on the back.  I reformatted them using Gnome Partition Editor.  I was able to narrow things down to 1 partition per drive and are ext3 now.

I renamed them ES1 and ES2 using Storage Device Manager.  
When I rebooted they didn't mount because the fstab was screwy.  I noticed that in Storage Device Manager it stated that the drives were still vfat.  So I removed and re-added them in the manager and rebooted.  Presto, works great.

Except.... Exactly how do I take ownership of these two devices?  They're locked down and only Root can create/edit files.

After this I'll try to stop bugging you guys.  *grin*

---

### Post by carloslosgrande on 2007-10-02
[FONT="Comic Sans MS"][FONT="Comic Sans MS"]You can change ownership with[COLOR="Purple"] chown[/COLOR]
maybe something like this
[COLOR="#800080"]sudo chown drake -R /media/ES1[/COLOR]
assuming that is the right address for es1
enter[COLOR="#800080"] man chown[/COLOR] in a terminal and you'll get a long, complex, description of the functions (the manual) of this command.
Actually, [COLOR="Magenta"]man[/COLOR] before any command will give you the manual for it. Also adding[COLOR="#ff00ff"] --help[/COLOR] after a command will give some tips.
Check out[COLOR="#ff00ff"][COLOR="Red"] [http://www.psychocats.net/](http://www.psychocats.net/)[/COLOR][/COLOR]
and [COLOR="#ff0000"]https://help.ubuntu.com/7.04/ [/COLOR][/FONT] for lots more info[/FONT]:)

---

### Post by vanadium on 2007-10-02
There are two ways you can acquire permissions on a permanent drive (mounted in /etc/fstab)

1) As root, create a directory on that drive and grant yourself permissions to it as a user (obviously you -as root - may want to create a link under your user home directory for easy access to that storage space.)

2) (as told by carloslosgrande): change the ownership of the mount point.

(1) is easiest and most flexible, and certainly the way to go in a system used by multiple users.

---

### Post by Drake2k on 2007-10-03
Bingo,  chown for the win. 

Thanks for everything guys.  I'm done with this thread now and have learned a lot.  I hope someone else will too.

---

