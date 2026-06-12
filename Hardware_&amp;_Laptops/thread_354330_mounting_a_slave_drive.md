---
title: "mounting a slave drive"
date: 2007-02-05
forum: Hardware &amp; Laptops
---

### Post by Finkeralfl@mac.com on 2007-02-05
I just installed ubuntu and got rid of my xp os.  I have a 20 gig slave drive that worked in xp and is showing up in ubuntu under my computer.  However, If I try to access the files I have on the slave drive it says that i cannot mount this drive.  
So...How do I mount / get access to these files?
The slave drive currently has 19.4 of 20 gigs used, and I cannot afford to lose these files.
I am new to linux so please keep that in mind when anwsering this post.  Thank you.

---

### Post by Aifel on 2007-02-05
You should make sure that your BIOS has it registered as a slave drive. Also, you could try 
```
mount <device location>
```

I think that the BIOS thing will probably be the problem.

---

### Post by Finkeralfl@mac.com on 2007-02-05
The bios reads it as a master slave

if I type: mount <d:> in terminal I get..  Bash: syntax error near unexpected token 'newline'

suggestion?

---

### Post by taurus on 2007-02-05
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
Otherwise, here's a guide to mount your Windows.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by tommcd on 2007-02-06
See this about adding a new hard drive:
[https://help.ubuntu.com/community/InstallingANewHardDrive?highlight=%28drive%29%7C%28hard%29%7C%28new%29](https://help.ubuntu.com/community/InstallingANewHardDrive?highlight=%28drive%29%7C%28hard%29%7C%28new%29)
You can skip down to "Set mount point" since the drive already has data on it. If you want to have the drive mount at boot you will have to add it to your /etc/fstab.

---

### Post by Finkeralfl@mac.com on 2007-02-06
This is what I get, where do I go from here?



Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19079   153252036   83  Linux
/dev/hda2           19080       19457     3036285    5  Extended
/dev/hda5           19080       19457     3036253+  82  Linux swap / Solaris

Disk /dev/hdb: 20.8 GB, 20847697920 bytes
64 heads, 63 sectors/track, 10098 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               2       10098    20355552    f  W95 Ext'd (LBA)
/dev/hdb5               2       10098    20355520+   b  W95 FAT32
jared@Slick:~$ sudo mkdir /backup
jared@Slick:~$ sudo mount /dev/hdd1 /backup
mount: you must specify the filesystem type

---

### Post by taurus on 2007-02-06
So you want to mount /dev/hdb5.  Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/hdb5   /media/hdb5   vfat   iocharset=utf8,umask=000   0   0
```
Save it.  Now, create a new mount point and mount it.

```
sudo mkdir /media/hdb5
sudo mount -a
df -h
```

---

### Post by Finkeralfl@mac.com on 2007-02-07
all set thanks for the help!!! :KS

---

