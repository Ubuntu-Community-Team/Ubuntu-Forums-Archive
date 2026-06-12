---
title: "How do I retrieve files from HD?"
date: 2006-07-05
forum: Hardware &amp; Laptops
---

### Post by DiGiTY on 2006-07-05
the motherboard on my ubuntu 6.06 laptop just died. how can i get the files off that hard drive (either via linux/ubuntu, windows or mac os x)???

TIA

---

### Post by tonyr on 2006-07-05
It's not simple. I assume you have another computer. 

Get an inexpensive external IDE/USB HD enclosure.  The cheapie at the 
local place I go to is about $15US.  It came with a USB cable.
Remove the HD from the laptop. (also perhaps not simple)
Put the HD in the USB enclosure.  Plug the cable into the USB
enclosure and the USB port of your other computer (again, I'm
making an assumption here).  

Depending on the OS on your other computer, you might or might not see
disk devices when it boots up.  If the OS is a recent Linux distro, it may
mount them automatically or you may have to mount them yourself.
If the other OS is a Windows variant, and the partitions on the HD are
all Linux types,  you'll need to install **fs-driver** (read about it [here]("http://www.fs-driver.org/"))
to see the partions as disk devices.

---

### Post by DiGiTY on 2006-07-05
sweet, thanks. i'll try both my Ubuntu 6.06 desktop and my WinXP box.

thanks again

---

### Post by DiGiTY on 2006-07-05
i've tried both Ubuntu 6.06 and WinXP with fs-driver and they only mount '/boot'. in the IFS Drives control panel in Windows, I see the second partition, but it's not giving me the option to assign it a drive letter like the first partition.

the second partition does say 'LVM'... does that matter? is it possible to mount it in Ubuntu with some special commands???

any kind of help would be greatly appreciated

---

### Post by tonyr on 2006-07-05
I think LVM is critical here, it's got some special meaning which I don't know.  What does 
**fdisk** or **gparted** say on the Ubuntu side? (**sudo fdisk -l**, in a terminal, 
or **Gnome Partition Editor** under **System->Administration**; package 
**gparted** if it's not on the menu).

I'm offline for about 30 minutes now.

---

### Post by blkish on 2006-07-05
[QUOTE=DiGiTY]i've tried both Ubuntu 6.06 and WinXP with fs-driver and they only mount '/boot'. in the IFS Drives control panel in Windows, I see the second partition, but it's not giving me the option to assign it a drive letter like the first partition.

the second partition does say 'LVM'... does that matter? is it possible to mount it in Ubuntu with some special commands???

any kind of help would be greatly appreciated[/QUOTE]

LVM stands for Logical Volume Manager. This is a more advanced means of managing data stored on hard drives than traditional partitions.

It sounds like your ext3 linux partitions are stored within a Logical Volume on your laptop's disk.

i would be very suprised if the windows fs-driver can handle LVM Volumes.

most likely you will need to attach this disc to a computer running linux (same version of Ubuntu would be ideal, but anything recent should be OK). 

it should then be able to read the LVM information on the disc and allow you access to the ext3 parition(s) stored within the Logical Volumes.

perhaps this is a good time to get your other machine onto Ubuntu as well? ;)

good luck,

blkish

[Edit]: there can be problems if there are multiple Logical Volume Groups of the same name on one computer. This is often the case when you have a Logical Volumes created by an installer, which have the same default name (normally something like LogVol00). 
It could be that this is the problem you are encountering when trying to access your laptop's disk from your other Ubuntu machine (sorry, didn't see you had already tried with Ubuntu).

You might be able to get around this problem by attempting to access the laptop disk from a machine running linux, which is not using LVM on its discs.

You might have to re-install Ubuntu, instructing the installer not to use LVM, rather 'traditional' partitions to do this, unless you have access to such a box.

I'm not sure of the means to tell the Ubuntu installer how to do this off-hand, but I'm sure someone on the forum can help :)

You might also like to post a thread about 'how to mount different LVM volumes with the same name' to get more advice about that route. 

blkish

---

### Post by DiGiTY on 2006-07-05
this is the output from "sudo fdisk -l":

```

Disk /dev/hda: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1162     9333733+  83  Linux
/dev/hda2            1163        1216      433755    5  Extended
/dev/hda5            1163        1216      433723+  82  Linux swap / Solaris

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2432    19535008+   5  Extended
/dev/sda5   *           1          31      248944+  83  Linux
/dev/sda6              32        2432    19286001   8e  Linux LVM

```

the 2nd HD (20.0 GB) is the laptop drive in question (the 1st HD (10.0 GB) is the host/desktop Ubuntu 6.06 machine)

any ideas???

---

### Post by blkish on 2006-07-05
[QUOTE=DiGiTY]this is the output from "sudo fdisk -l":

```

Disk /dev/hda: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1162     9333733+  83  Linux
/dev/hda2            1163        1216      433755    5  Extended
/dev/hda5            1163        1216      433723+  82  Linux swap / Solaris

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2432    19535008+   5  Extended
/dev/sda5   *           1          31      248944+  83  Linux
/dev/sda6              32        2432    19286001   8e  Linux LVM

```

the 2nd HD (20.0 GB) is the laptop drive in question (the 1st HD (10.0 GB) is the host/desktop Ubuntu 6.06 machine)

any ideas???[/QUOTE]

can you post the output of the command:

**sudo lvdisplay**

when you run it in a terminal

thanks

blkish

---

### Post by DiGiTY on 2006-07-05
sudo lvdisplay outputs: No volume groups found.

---

### Post by blkish on 2006-07-05
[QUOTE=DiGiTY]sudo lvdisplay outputs: No volume groups found.[/QUOTE]

ok, could you try:

**sudo lvscan**

**sudo pvscan**

thanks

---

### Post by blkish on 2006-07-05
i have to go offline to bed, sorry.

it looks like your ubuntu desktop may not be recognising the LVM groups on your laptop's disks.

it would be worth posting question to this effect in the forums.

most importantly, don't try to change any partition information on the disk your are trying to recover data from.

hope it works out

blkish

---

### Post by DiGiTY on 2006-07-05
sudo lvscan gives also outputs "No volume groups found."

but sudo pvscan outputs:
```

PV /dev/sda6   VG Ubuntu   lvm2 [18.39 GB / 0    free]
Total: 1 [18.39 GB] / in use: 1 [18.39 GB] / in no VG: 0 [0   ]

```

---

### Post by DiGiTY on 2006-07-05
[QUOTE=blkish]i have to go offline to bed, sorry.

it looks like your ubuntu desktop may not be recognising the LVM groups on your laptop's disks.

it would be worth posting question to this effect in the forums.

most importantly, don't try to change any partition information on the disk your are trying to recover data from.

hope it works out

blkish[/QUOTE]

thanks for trying blkish

anybody have any other ideas???

---

### Post by linuchsan on 2006-07-05
On windows i have successfully used R-Studio file recover.

---

### Post by tonyr on 2006-07-05
I didn't know anything about LVM up to now.  I had no idea it would get this complicated. 
[Here]("http://www.tldp.org/HOWTO/LVM-HOWTO/") is the most up to date Howto I could find with a really 
brief search.  Anything I could do at this point would be
hunt and pick, highly experimental and risky.  If I were to guess, I'd say you need to create
a Volume Group that contains the Physical Volume that is your laptop drive.  Then
maybe more info could be mined about the Logical Volume structure on the Physical
Volume (all this jargon I just learned in the last 15 minutes scanning that Howto).

I second **blkish**'s suggestion about starting another thread with a new headline
that says something like **Attach an LVM PV to different machine?** and describe
the situation.

---

### Post by tonyr on 2006-07-05
...and for more self help, google **LVM PV recovery**.

---

### Post by DiGiTY on 2006-07-06
I was able to resolve the problem after finding Ocxic's post ([http://www.ubuntuforums.org/showthread.php?p=1158258#post1158258](http://www.ubuntuforums.org/showthread.php?p=1158258#post1158258))

i plugged in the USB HD enclosure and then booted off a ubuntu 6.04 i386 live cd and finally saw 'Ubuntu-root' in /dev/mapper, mounted it with Ocxic's suggested syntax and was able to access the LVM partition.

not sure if this was important, but a Ubuntu 6.04 install disc was originally used to install Ubuntu on the HD in question. then via update manager it was updated to 6.06 LTS final

hope that helps someone

thanks so much for the help folks

---

