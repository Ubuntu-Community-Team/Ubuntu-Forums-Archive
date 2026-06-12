---
title: "mount.ntfs-3g - 100% cpu although only little fragmentation"
date: 2008-09-29
forum: General Help
---

### Post by eZtaR on 2008-09-29
Hello,

My problem is quite simply that mount.ntfs-3g uses 100% CPU and 'only' transfers at about 10 MB/s when i try to move over files from my computer to my external harddrive (which is the one formatted to ntfs).

I read about and someone stated that it might be a problem with fragmentation on the drive, so i defragged it with jkdefrag on a windows xp partition and got it down to 4% fragmentation, and the problem is still there.

What to do, what to do?

Picture of the default windows analysis:
[[IMG]http://img391.imageshack.us/img391/6195/fragbp8.jpg[/IMG]](http://imageshack.us)
[[IMG]http://img391.imageshack.us/img391/fragbp8.jpg/1/w640.png[/IMG]](http://g.imageshack.us/img391/fragbp8.jpg/1/)

**[COLOR="Red"]EDIT: I'm currently defragging the disc with Paragon Total Defrag 2009 (which also does ext2/3 btw), if there are no other replies in this thread by me, consider this the solution.[/COLOR]**

---

### Post by eZtaR on 2008-10-01
The problem persists after the total defrag :(

data about my ntfs-3g:
[quote=daemon.log]Oct  1 16:32:58 ezonthelap ntfs-3g[20677]: Version 1.2918SR.1 integrated FUSE 27 
Oct  1 16:32:58 ezonthelap ntfs-3g[20677]: Mounted /dev/sdc1 (Read-Write, label "", NTFS 3.1) 
Oct  1 16:32:58 ezonthelap ntfs-3g[20677]: Cmdline options: rw,nosuid,nodev,uhelper=hal,locale=en_DK.UTF-8 
Oct  1 16:32:58 ezonthelap ntfs-3g[20677]: Mount options: rw,nosuid,nodev,uhelper=hal,silent,allow_other,nonempty,relatime,fsname=/dev/sdc1,blkdev,blksize=4096 
Oct  1 16:32:58 ezonthelap hald: mounted /dev/sdc1 on behalf of uid 1000
Oct  1 16:32:58 ezonthelap ntfs-3g[20677]: Failed to build user mapping 
[/quote]

---

### Post by adieb on 2009-01-06
No solution yet? Same problem here... Intrepid 64 bit.
It sucks.
Workaround:

sudo kill "pid of ntfs.mount" (enter the pid)
sudo mount -a


Then it works without complains.

---

### Post by huntz on 2009-01-09
I'm using Intrepid 32bit and I'm experiencing the same problem.

I have found a solution: the ntfs 3g package available in deb is version 1.2506 but the last stable version is 1.5130

I have read somewhere about some speed optimization on recent ntfs 3g versions, so I have downloaded the sources of the package and builded with these commands:

[LIST]
[*]./configure
[*]make
[*]sudo make install
[/LIST]

Now everything is running more snappier :)

PS: umount the ntfs drives before updating the ntfs 3g program...

Bye

---

### Post by gaffurabi on 2009-01-09
i transfer between ntfs and ext3 about 30 mb/s
is it normal speed for a 7200 rpm/8mb cache/sata 3 gbit drive? cause i read that  theoritical speed is 300 mb/s :(

---

### Post by huntz on 2009-01-13
I have found a good workaround for this kind of problem.

Modify any .vmx file (the .vmx file is the config of any virtual machine, usually is '$VirtualMachineName'.vmx) adding this line (the bottom of the config file will be just fine...):

```

mainMem.useNamedFile=FALSE
```

---

### Post by rideick on 2009-08-25
Thanks man! It worked just fine!

---

### Post by nikink on 2009-11-08
> **huntz said:**
> I have found a good workaround for this kind of problem.

Modify any .vmx file (the .vmx file is the config of any virtual machine, usually is '$VirtualMachineName'.vmx) adding this line (the bottom of the config file will be just fine...):

```

mainMem.useNamedFile=FALSE
```

I have installed new versions of VMware (VMPlayer 3 and VMWare Server 2). The mainMem.useNamedFile does not work anymore.
I solved the problem changing working directory to a path outside the ntfs partition adding this line

```
workingDir = "../../../../var/vmware"
```

to the .vmx file. The path is relative to the .vmx file and must be writeable to the user that runs vmware.

This path is used to store temp/suspend memory images, that normally are stored in the same directory of the .vmx file.

---

