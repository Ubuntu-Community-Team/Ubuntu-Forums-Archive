---
title: "can't mount ipod after upgrade v10"
date: 2010-05-05
forum: Hardware
---

### Post by MasterKush010 on 2010-05-05
[SIZE=2]Ipod mount issues ... Disk utility picks  up the ipod but gives no  option to  mount.
[/SIZE][SIZE=2]
very irritating.. don't want to use itunes software. have tried a lot   of OS software i.e Hipo [/SIZE] [SIZE=2]Ipod  manger, Banshee, Mpman.... etc.

Ran "lsusb" in terminal  

Bus 002 Device 002: ID 046d:c048 Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ac:1300 Apple, Inc. iPod Shuffle
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Ipod shows but can't mount it!! All was kinda ok before ubuntu v10 

Please help! having to use windows to load podcasts .... one day I will be happy to   delete that partition!!!  [/SIZE] [SIZE=2]

I have tried formatting ipod and resetting setting to factory etc

Cheers, Kush [/SIZE] [SIZE=2]:wink:[/SIZE]

---

### Post by hlxshady on 2010-05-06
can you give more detail of the output you got ?

Gtkpod once only recognised ipod mount at
/mnt/ipod/

So I had to manually mount it there, rather than leaving it to ubuntu's HAL(Hardware Abstract Layer, I guess this is what handles all automatical mount functionalities).

---

### Post by MasterKush010 on 2010-05-06
Cheers for quick reply..

Sorry not sure what you need info wise the Ipod is first gen i think...

---

### Post by hlxshady on 2010-05-06
Hiya,

Gtkpod is a software provides functions like itune, so you can use it to transfer your music to your ipod.

But it sometimes does not recognise the ipod automatically mount to /media/xxx, it may expects a path of /mnt/ipod.

If so, you can mount it manually to /mnt/ipod.

My ipod, quite old too, was in a format of fat32.


but ... :D
I am not sure if I'm answering your question actually ...

:P

---

### Post by MasterKush010 on 2010-05-06
Lol.... my ipod still not mounted so I guess not ;)

Please be more detailed as to how and what i need to do .... Cheers again!

---

### Post by hlxshady on 2010-05-07
Hiya,

Could you please give more detail of what you did so ... maybe I can figure out what you need to do ?

---

### Post by MasterKush010 on 2010-05-14
I plug in the ipod ... tried different USB ports, am able to load files to ipod under windows.

I have tried to use Rythembox and GTKPod to upload to it...

I even tried this script found on the web: /dev/sdc2    /media/iPod  vfat     nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000,user,defaults,noatime,iocharset=utf8     0 0

which helped once then ... no mount again

Sorry please ask me any answers you need. Just still unable to mount my ipod.

Cheers

---

### Post by FrogofTime on 2010-05-23
I am having the exact same problem with my 1st generation iPod Shuffle.
I have been able to use it without problem on the same laptop since 8.04, but now that I installed 10.04, it no longer appears on the desktop automatically.
I cannot access it through the file manager, but the Disk Utility and Gparted both show it as being connected.
Could this be an issue with the version of HAL that was shipped with the 10.04 64-bit version? It's the only thing I can think of, although my knowledge of the inner workings of Ubuntu is pretty basic.

---

### Post by quantumottle on 2010-07-25
[Another possible solution]("http://wwww.ubuntuforums.org/showthread.php?p=9636742#post9636742"), it worked for me anyway.

---

### Post by MasterKush010 on 2010-07-30
> **quantumottle said:**
> [Another possible solution]("http://wwww.ubuntuforums.org/showthread.php?p=9636742#post9636742"), it worked for me anyway.

Sorry my faulty should have closed this .... RESOLVED with auto updates long time ago.

ipod working 100% ok.

Ubuntu rocks.=D> The King is Dead, Long Live the King!

---

