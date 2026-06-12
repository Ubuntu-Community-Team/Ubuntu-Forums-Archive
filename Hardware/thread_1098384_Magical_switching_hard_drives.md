---
title: "Magical switching hard drives"
date: 2009-03-17
forum: Hardware
---

### Post by Ryvius on 2009-03-17
Okay, this is a really long-winded problem and will seem really confusing at first, so I will write it in bullet points to make it easier to read.


[LIST]On every other restart, the drives on /dev/sda1 and /dev/sdc1 switch places (i.e. /dev/sda1 becomes /dev/sdc1 and /dev/sdc1 becomes /dev/sda1).[/LIST]
[LIST]
[*]When /dev/sdc1 becomes /dev/sda1, the 'File System' folder gets put on the desktop as '80.8 GB Media', replacing 'Internal1' (normally /dev/sda1, but is now /dev/sdc1 and won't mount).
[/LIST][LIST]
[*]Also, when /dev/sdc1 becomes /dev/sda1, it's stated as having 2 mount points in GParted (/ and /media/sda1).
[/LIST]

As I say, this is fixed by a restart, but once restarted or turned on once more after, the problem returns.

I have no idea how to explain this any better.

Anyway, let me know if you can help. Thanks in advance.

Edit: Maybe screenshots would help?

---

### Post by Ryvius on 2009-03-17
How do I "remove all uninstall softwares from [my] computer"?

---

### Post by ian dobson on 2009-03-17
Hi,

Are the 2 harddisks on the same controller? I've seen this happen on systems with two harddisk controllers. 
It seems to be caused by how quickly/hich controller is seen first and how quickly hotplug creates a device in the devfs.

Maybe you could use a custom hotplug rule to "force" the device name.

Regards
Ian Dobson

---

### Post by Ryvius on 2009-03-17
They were running fine until I renamed and re-mounted them elsewhere. I used GParted and Storage Device Manager, because I couldn't seem to get them how I wanted using the terminal. And now this has happened...

Maybe I could... if I knew how. Haha, I'm still a total novice.

---

### Post by Ryvius on 2009-03-17
Okay, I THINK I've have fixed it, but /dev/sdc1 has got an exclamation mark in GParted,

Here's a screenshot:
[IMG]http://i216.photobucket.com/albums/cc299/infiniteryvius/sdc.jpg[/IMG]

Here's an echo of etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc       /proc        proc  defaults  0  0  
#
/dev/sda1  /media/sda1  vfat  defaults  0  0 
/dev/sdb1  /media/sdb1  vfat  defaults  0  0  
/dev/sdc1  /            ext3  defaults  0  0
/dev/sdd1  /media/sdd1  vfat  defaults  0  0  
```

Any ideas?

---

### Post by Ryvius on 2009-03-17
Sorry for triple posting.

I'm just letting everyone know I've fixed the error above. It seems to me /dev/sdc1 didn't get mounted upon boot. I've tested it by restarting a few times and it seems to mount every time now.

Big thanks to those who tried to help.

---

