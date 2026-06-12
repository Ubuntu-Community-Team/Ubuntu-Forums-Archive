---
title: "A Newbies Question!"
date: 2008-07-21
forum: General Help
---

### Post by Newatthislol on 2008-07-21
Hey Ubuntu forums!

I have a few questions, to keep things orderly I'm going to go with a numbered format.

1. I can't get grub to recognize XP. This is what I've added to my menu.lst through terminal -

title      Windows XP Home
root       (hd0,0)
makeactive
chainloader+1
savedefault

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a4bf703e-667a-4cea-83a4-8a09c59d6270 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a4bf703e-667a-4cea-83a4-8a09c59d6270 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
makeactive
chainloader	+1


I have three hard drives, two 500gig hd's hd #1 is my primary with XP hd #2 is storage and hd #3 is an 80gig hd where linux's filesystem resides.

I thought my primary would have been (hd0,0) but Vista is installed on the same hd as linux and it is (hd0, 2). XP shows up in grub, but nothing happens when I hit enter.

So how can I get XP to be my default and actually work when I hit enter? Thanks!

---

### Post by Newatthislol on 2008-07-21
And another question - is the discussion of illegal downloads through torrents prohibited? I control + f'ed through the Code of Contact with 'Illegal down', P2P, and 'downloads' and nothing came up. 

I'm not interested in getting banned and I thought I'd ask first.

---

### Post by Scarlett on 2008-07-21
The startup manager might help with your default operating system.  Did grub launch XP before you made the changes and did you make a backup of that file?  If so, restore that file and then try it through the start up manager. Open a terminal and type:

```
sudo apt-get install startupmanager
```

Say yes if it prompts (I can't remember if it does or not) and then you can find it in System > Administartion > startupmanager. On the Boot Options tab there is a pull-down menu that will allow you to select all the operating systems recognized by the menu.ls file.


As for illegal torrents... well, I really don't know.  But there are plenty of legitimate uses for bittorrent so if you're having a problem with your torrent client it's perfectly ok to talk about that.

---

### Post by Elfy on 2008-07-21
Can you open a terminal and run these commands please

```
sudo fdisk -l
```

> I'm not interested in getting banned A bit frowned upon- you won't get banned Iassume - you might get infractions - but threads are likely to be closed.

---

### Post by Newatthislol on 2008-07-21
> **Scarlett said:**
> The startup manager might help with your default operating system.  Did grub launch XP before you made the changes and did you make a backup of that file?  If so, restore that file and then try it through the start up manager. Open a terminal and type:

```
sudo apt-get install startupmanager
```

Say yes if it prompts (I can't remember if it does or not) and then you can find it in System > Administartion > startupmanager. On the Boot Options tab there is a pull-down menu that will allow you to select all the operating systems recognized by the menu.ls file.


As for illegal torrents... well, I really don't know.  But there are plenty of legitimate uses for bittorrent so if you're having a problem with your torrent client it's perfectly ok to talk about that.


Grub never even recognized XP. I am trying to add it to the list. I never made a backup of my menu.lst. It's just that I have to switch between hard drives in the boot prority all the time. When I have it set to my 80g, grub starts, and shows Ubuntu and Vista, but not XP. To get to XP I switch the priority to my 500g which shows Vista's mbr, and from that menu Vista doesn't boot.

> **forestpixie said:**
> Can you open a terminal and run these commands please

```
sudo fdisk -l
```

A bit frowned upon- you won't get banned Iassume - you might get infractions - but threads are likely to be closed.

Alright thanks. This is what I've got.


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf03b4104

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3187    25599546    6  FAT16
/dev/sda2            3188        6374    25599577+   6  FAT16
/dev/sda3            6375        9729    26949037+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x74e274e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60800   488375968+   7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x76397639

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60801   488384001    7  HPFS/NTFS
user@computer:~$

---

### Post by Elfy on 2008-07-21
Is this a wubi installation or a real one? If you're not sure what I mean can you run

```
df -h
```please.

---

### Post by Newatthislol on 2008-07-22
> **forestpixie said:**
> Is this a wubi installation or a real one? If you're not sure what I mean can you run

```
df -h
```please.


I am led to believe it is a real one but I don't know.


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              25G  2.0G   23G   8% /
varrun               1013M  100K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M   68K 1013M   1% /dev
devshm               1013M   12K 1013M   1% /dev/shm
lrm                  1013M   38M  976M   4% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon       25G  2.0G   23G   8% /home/user/.gvfs

---

### Post by cariboo on 2008-07-22
something looks really strange when you do an fdisk -l

> /dev/sda1 * 1 3187 25599546 6 FAT16
/dev/sda2 3188 6374 25599577+ 6 FAT16

also from your listing you don't have any linux partitons so I am assuming you have a wubi install.

I'd check that hard drive to see why they show up as fat16 partitions.

Jim

---

### Post by hyper_ch on 2008-07-22
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

---

### Post by Elfy on 2008-07-22
> something looks really strange when you do an fdisk -lwhich is why I wondered if it was a wubi installation.

---

### Post by Newatthislol on 2008-07-22
So what's the solution?

---

### Post by Elfy on 2008-07-22
Can you run this and post the output 

```
mount
```

Still not sure if it's a wubi installation and I put wrong command last time. It looks as though you haven't got any linux partitions at all, mount shows how everything is mounted and will help to decipher that at least. Unforunately if it is a wubi installation I'm not sure how grub works in relation to the partitions.

---

### Post by Newatthislol on 2008-07-22
> **forestpixie said:**
> Can you run this and post the output 

```
mount
```

Still not sure if it's a wubi installation and I put wrong command last time. It looks as though you haven't got any linux partitions at all, mount shows how everything is mounted and will help to decipher that at least. Unforunately if it is a wubi installation I'm not sure how grub works in relation to the partitions.

Again, I'd like to say thanks for the help so far!

Here's what I got for you!

user@Circes:~$ mount
/dev/sdc2 on / type reiserfs (rw,relatime,notail)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/user/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=garrison)
user@Circes:~$

---

### Post by Brando569 on 2008-07-23
this is quite odd that fdisk doesnt display a linux partition and that reiserfs was the default choice when it is usually ext3 (im assuming this since you pretty much said you dont know anything about linux)

im just taking a random stab at this and it will be kind of hit or miss, copy down what locations your NTFS partitions are (/dev/sd whatever) and follow these steps:

1. when you get to the grub boot menu, highlight the choice that says windows xp and hit the 'e' key, then select the line that says "root (hd0,0)" and hit 'e' again. this will allow you to change the values of that specific line. 

2. what your going to do next is the trial and error part. your going to change the value of "root(hd0,0)" until you find one that boots your xp installation. this might get slightly confusing since the way grub numbers the drives and partitions (they start at zero instead of one) so ill explain it a little... 

the first value of zero means the first drive in your computer (/dev/sda) a one would mean the second drive in your computer (/dev/sdb) and a two would mean the third drive in your computer (/dev/sdc)

the second value of zero means the first partition on that specific drive and a one would mean the second partition on that drive and so on from there.

so (hd0,0) actually means the first partition of the first drive which is a FAT16 partition and not an NTFS partition (or a FAT32 partition for that sake) like it usually would be. so your going to change those two zero's to correspond to your NTFS partitions. the first NTFS partition on the first drive would be (hd0,2)

3. after your done changing that value i believe you have to hit enter to get back to the point where you can select other lines and then you'll hit the 'b' key 

repeat this process (pressing 'e' on the windows xp choice and then 'e' again on the line that says "root(hd0,0)", hit enter, then hit 'b') until you find the right one that boots your windows xp install

once you find the correct values, boot into linux and open up /boot/grub/menu.list as root and change that same line ( root(hd0,0)) to the value that you found that worked

---

### Post by Newatthislol on 2008-07-23
> **Brando569 said:**
> this is quite odd that fdisk doesnt display a linux partition and that reiserfs was the default choice when it is usually ext3 (im assuming this since you pretty much said you dont know anything about linux)

im just taking a random stab at this and it will be kind of hit or miss, copy down what locations your NTFS partitions are (/dev/sd whatever) and follow these steps:

1. when you get to the grub boot menu, highlight the choice that says windows xp and hit the 'e' key, then select the line that says "root (hd0,0)" and hit 'e' again. this will allow you to change the values of that specific line. 

2. what your going to do next is the trial and error part. your going to change the value of "root(hd0,0)" until you find one that boots your xp installation. this might get slightly confusing since the way grub numbers the drives and partitions (they start at zero instead of one) so ill explain it a little... 

the first value of zero means the first drive in your computer (/dev/sda) a one would mean the second drive in your computer (/dev/sdb) and a two would mean the third drive in your computer (/dev/sdc)

the second value of zero means the first partition on that specific drive and a one would mean the second partition on that drive and so on from there.

so (hd0,0) actually means the first partition of the first drive which is a FAT16 partition and not an NTFS partition (or a FAT32 partition for that sake) like it usually would be. so your going to change those two zero's to correspond to your NTFS partitions. the first NTFS partition on the first drive would be (hd0,2)

3. after your done changing that value i believe you have to hit enter to get back to the point where you can select other lines and then you'll hit the 'b' key 

repeat this process (pressing 'e' on the windows xp choice and then 'e' again on the line that says "root(hd0,0)", hit enter, then hit 'b') until you find the right one that boots your windows xp install

once you find the correct values, boot into linux and open up /boot/grub/menu.list as root and change that same line ( root(hd0,0)) to the value that you found that worked

Your correct in, I don't know too much about linux, but I'm definitely computer literate. 

I went through with your suggestion and XP did not boot.

I edited it just like you said and tried all possible combinations. Sometimes the menu would briefly flash, and other times grub would dislplay error 22. Maybe I should completely wipe the hd and start over.

---

