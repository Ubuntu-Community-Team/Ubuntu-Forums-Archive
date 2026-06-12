---
title: "2nd HDD mounted as access only- need read/write"
date: 2007-07-05
forum: Hardware &amp; Laptops
---

### Post by alextababa on 2007-07-05
Hi There u wonderful people

I have a drive from my old windows setup with all my data on it...
Mounts and reads fine under root, but only as read. If I attempt to change permissions it tells me I can't because the disk is read only.

What steps can I take to change permissions?

Alistair

---

### Post by moore.bryan on 2007-07-05
*what does the line look like that controls it in /etc/fstab?*

---

### Post by alextababa on 2007-07-05
Hi. I'm really new at linux, try three days. Getting there though. Perhaps you might be able to fill me in on which is which?

fstab:


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0e937045-459b-47e4-8736-4999ff65b950 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=4fc47c33-dde5-4f9a-a71b-afd45c4aa542 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by moore.bryan on 2007-07-05
[I]alright, your /dev/sda# is your main hard drive.  where's this second one we're talking about?
;-)
[/I]

---

### Post by alextababa on 2007-07-05
Hi Again

Yes, I was wondering. But both partitions of the other drive are on my desktop and mounted. Here's what the properties were for the whole volume, available from right clicking the icon:

(two attached png files- i hope. i haven't used this forum b4 today either....)

---

### Post by moore.bryan on 2007-07-05
[I]hey, no problem... you're doing fine! ;-)
if you look at your first thumb, you'll see the "ro" setting on the drive (circled in the attached thumb) meaning "read-only."  we can change that, but the ntfs format of the drive complicates things.
as per the [ubuntuguide]("http://www.ubuntuguide.org/"), you should:
[/I]> ** How to mount Windows partitions (NTFS) on boot-up, and allow users read and write access **

 Warning: The software you will use is still in Beta.  You should not enable it on production machines[LIST]
[*]Read [#General Notes]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#General_Notes")[/LIST][LIST]
[*]Enable universe. Read  [#How to apt-get the easy way (Synaptic)]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_apt-get_the_easy_way_.28Synaptic.29")[/LIST][LIST]
[*]Applications -> Add/Remove -> search for 'NTFS', you should find NTFS Configuration Tool, install it.[/LIST][LIST]
[*]Applications -> System Tools -> NTFS Configuration Tool -> Enable Write Support (depending on your device internal/external)[/LIST][LIST]
[*]Further troubleshooting is listed at this [comprehensive howto thread]("http://www.ubuntuforums.org/showthread.php?t=217009").[/LIST]*look through what it says and let me know if anything doesn't make sense...*

---

### Post by alextababa on 2007-07-05
Will do. Keep you posted and thanks for advancing humanity.

Alistair.

---

### Post by alextababa on 2007-07-05
OK... firstly I simply installed the ntfs config program, great, but the option for enabling read/write for *internal* was not available, only for external. 

So I'm going for the 'manual configuration' alternative now... [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

Alistair

---

### Post by alextababa on 2007-07-05
seems like i was supposed to unmount the drives before running ntfs config....

---

### Post by alextababa on 2007-07-05
All Good

Thanks for your help Bryan. 

Loving Ubuntu and those who make it possible!

---

### Post by moore.bryan on 2007-07-05
[I]you're welcome; just glad to hear you got it working!
post if you have any other issues...
[/I]

---

