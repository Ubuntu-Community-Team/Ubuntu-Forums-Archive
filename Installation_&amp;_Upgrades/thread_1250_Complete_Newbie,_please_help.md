---
title: "Complete Newbie, please help"
date: 2004-10-19
forum: Installation &amp; Upgrades
---

### Post by hpstg on 2004-10-19
I am completely new to Linux, and one of my friends convinced me to go with Ubuntu. I think he was right  :wink: 

I have a few questions though:
First:

1) How do I mount an NTFS volume? I have all my mp3's on an ntfs disk. I need to  be able to read it at least.

2) How do I install my ATi drivers? I have an nForce2 motherboard, with an ATI Radeon 9800Pro. I haven't managed to install them yet.

Please help, I am really new to this and I really like it  :cry:  :cry:  :cry:

---

### Post by im_ka on 2004-10-19
first of all, i don't use ntfs but i hope this helps (at least you can start til someone smarter than me shows up ;)

i've done some googleing for ya. [http://www.google.com/linux](http://www.google.com/linux) is generally a good place to look for answers.

to be able to acces ntfs, you probably have to apt-get at least these packages

```

libntfs-gnomevfs - NTFS GNOME virtual filesystem module
libntfs5 - Library that provides common NTFS access functions
ntfsdoc - Documentation about NTFS partitions format

```

```
sudo apt-get install packagename
```
or just run synaptic.

and maybe

```

ntfstools - Tools for doing neat things in NTFS partitions from Linux

```

you will then have to add a line to /etc/fstab. i don't know what number your partition is, but in general, this is how fstab should look like:

```
device   mountpoint     filesystem    mountoptions     0    0
```

in your case MAYBE

```
/dev/hda?     /mnt/ntfs      ntfs      defaults   0     0
```

? is the number of the hard disk. you can have a look at your partition table with parted or cfdisk.

you have to create the /mnt/ntfs (this is what i suggest, you can mount it where you want it) by doing

```
sudo mkdir /mnt/ntfs
```

you can specify mountoptions instead of defaults. mine looks like this:

```

proc            /proc           proc    defaults        0       0
/dev/hda1       /               reiserfs defaults        0       1
/dev/hda2       /home           ext3    defaults        0       2
/dev/hda3       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

ro = read only
rw = read write
user = user is able to mount
auto = automount
noauto = ...
exec = you can execute files on the partition

these are the main options, you can google up the rest.

ati...
i don't know about it, i got an nvidia card (which is known to be more linux friendly than ati). again: google/linux

good luck!

ps: don't be afraid of the command line. it's your friend, and it doesn't hide anything like gui's do  :)

---

### Post by Rancoras on 2004-10-19
Nah, everything's there by default that you need.  Create a mount point in /media for your drive, say /media/mp3 for example:

```
mkdir /media/mp3
```

Then add this line to your /etc/fstab

```
/dev/hda1   /media/mp3   ntfs   ro,uid=1000,gid=1000   0   0
```

Substitute the proper /dev entry for your partition.  Reboot and it should automount the partition and place an icon for it on your desktop.

---

### Post by hpstg on 2004-10-20
Thanks for replying guys! I did what you mentioned, and although the partition is mounted, I can't see it on the desktop icon, and I can only access it through /mnt/ntfs

That's not the only problem though. Altough the system sounds play perfectly, whenever I try to play an audio or video file, I get this : 

[img]http://users.tellas.gr/~hpstg/totemerror.jpg[/img]

I never had that kind of problems with any Knoppix Live CD.

---

### Post by ErikN on 2004-10-20
I thought your mp3's were all stored on a seperate partition? From that screenshot it looks like its trying to play it from cd?

as for the icon on the desktop, i added an ntfs partition to my fstab and it shows up fine in Computer and even created an icon on my desktop.

---

### Post by im_ka on 2004-10-20
you need to make sure that you have the permission to play your mp3's from that partition.

i would recommend using mplayer to play videos. you need to add a new deb source for that, there is a howto on the main ubuntu site on that and it has been posted on this forum a couple of times.

---

### Post by hpstg on 2004-10-21
[quote=ErikN]I thought your mp3's were all stored on a seperate partition? From that screenshot it looks like its trying to play it from cd?

as for the icon on the desktop, i added an ntfs partition to my fstab and it shows up fine in Computer and even created an icon on my desktop.[/quote]

I even tried to play it from the cd, and the error is the same as when I try to play it form the cd. My settings never created an icon on my desktop  :? 

WTF? It's surely my mistake though... How am I supposed to get the permissions I need?

---

### Post by Rancoras on 2004-10-21
I wonder if you're running up against this?

[http://ubuntuforums.org/viewtopic.php?t=321](http://ubuntuforums.org/viewtopic.php?t=321)

---

### Post by hpstg on 2004-10-21
Thank you! Thank you! Thank you! Thank you!!!!! It's almost surely the codecs, because I was able to play an ogg file. Thank you for your patience guys, and excuse my complete n00biness :)

---

### Post by im_ka on 2004-10-21
[quote=hpstg]Thank you! Thank you! Thank you! Thank you!!!!! It's almost surely the codecs, because I was able to play an ogg file. Thank you for your patience guys, and excuse my complete n00biness :)[/quote]

that's what this forum is about  :wink:

---

### Post by Rancoras on 2004-10-21
My pleasure.

---

