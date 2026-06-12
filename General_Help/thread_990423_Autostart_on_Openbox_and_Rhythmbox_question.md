---
title: "Autostart on Openbox and Rhythmbox question"
date: 2008-11-22
forum: General Help
---

### Post by celtic426 on 2008-11-22
Hi, I have to questions...

1. With openbox, I want to autostart this python thing called gvtray which manages my volume in the panel.  I understand I have to add it to the autostart.sh file which I located, but what exactly to enter I need to know.  I tried: "Exec=python /home/tim/gvtray/gvtray.py &" but that didn't work.  What do I have to put it for it to autostart?  

2. I'm using rhythmbox for my music but every time I restart my computer rhythmbox loses all my music.  My music is on another partition and I think maybe it's not auto mounting?  I just checked under /media and my paritions are not listed there.  What do I have to do for that? 

Thanks

---

### Post by doorknob60 on 2008-11-22
1. No need for exec= or anything, simply put the command. I use autostart.sh to start a bunch of stuff :)

2. Post the output of these two commands:

```
sudo fdisk -l
```

```
less /etc/fstab
```

---

### Post by celtic426 on 2008-11-22
1. So would it just be "/home/tim/gvtray/gvtray.py &" or do i put exec in front of that?

2.
fdisk -l:
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01450145

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5554    44612473+   7  HPFS/NTFS
/dev/sda2            5555       30401   199583527+   f  W95 Ext'd (LBA)
/dev/sda5            5555       11931    51223221   83  Linux
/dev/sda6           11932       19498    60781896   83  Linux
/dev/sda7           30123       30401     2241036   82  Linux swap / Solaris
/dev/sda8           19499       30122    85337248+  83  Linux


less /etc/fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=eae454d3-e85d-4b9b-9280-f8fa9e19b3d0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=e1d9470e-9d9f-4798-b293-580815de8f50 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/etc/fstab (END)

---

### Post by doorknob60 on 2008-11-22
/home/tim/gvtray/gvtray.py &

Yeah just put that in autostart.sh Also make sure it's executable.

For the partitions, do you know which partition your music is on?

---

### Post by celtic426 on 2008-11-22
Thanks for your responses, and my music is on sda 2 I beleive.

---

### Post by doorknob60 on 2008-11-22
Try running this command:
```
sudo mkdir /media/data ; sudo echo '/dev/sda2 /media/data vfat defaults,auto,user 0 0' >> /etc/fstab
```

Back up your /etc/fstab first just incase. Also, I called it /media/data, but you can change it to whatever you want to call it, I'm simply assuming it's a data partition. After that, either run 'mount /media/data' or reboot.

---

### Post by celtic426 on 2008-11-22
I created the directory but for the second thing, it said permission denied, so I added a sudo after the arrows, and then it didn't say anything so it probably worked.  I typed mount /media/data but it couldn't find it.  Maybe I have to reboot?

Is there an easier way just to make everything auto-mount?

Thanks again for your help.

---

### Post by doorknob60 on 2008-11-22
> **celtic426 said:**
> I created the directory but for the second thing, it said permission denied, so I added a sudo after the arrows, and then it didn't say anything so it probably worked.  I typed mount /media/data but it couldn't find it.  Maybe I have to reboot?

Is there an easier way just to make everything auto-mount?

Thanks again for your help.

No, the sudo after the arrows should make it do something else (not something bad dont worry).
I don't know why the sudo echo thing didn't work, does the same thing for me :confused:
Anyways, type in this:
```
sudo -i
```
then this
```
echo '/dev/sda2 /media/data vfat defaults,auto,user 0 0' >> /etc/fstab
```

Then type exit to get out of root and try mount /media/data again.

---

### Post by celtic426 on 2008-11-22
Hmm ok the command worked, but when i tried to mount it I got:
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by doorknob60 on 2008-11-22
Let's try /dev/sda1 (just incase it's on there...), can't really think of anything else.

```
sudo nano /etc/fstab
```
Change /dev/sda2 to /dev/sda1 and change vfat to ntfs-3g

Then press ctrl+x and press y and press enter, then try mount /media/data again.

---

### Post by celtic426 on 2008-11-22
Thanks that worked!  Will that mount everytime I restart?

Also, if I wanted to change the name from data to something else, can I just change it in the fstab file or do I have to do echo step too?

Thanks for helping me!

---

### Post by doorknob60 on 2008-11-22
Yeah, it should mount on restart (that's what fstab is for). To change the name, change in it /etc/fstab and also rename the folder in /media/. Glad it worked :-)

---

