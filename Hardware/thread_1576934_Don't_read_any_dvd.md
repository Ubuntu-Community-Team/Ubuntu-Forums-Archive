---
title: "Don't read any dvd"
date: 2010-09-18
forum: Hardware
---

### Post by kapstokje78 on 2010-09-18
Hi,

In the past i use to test ubuntu and i really like the system.
I've decided to change completely to ubuntu instead of windows, but now i have a problem with dvd's

I looked for hours with google, but i don't find a solution.
I hope you can help me, i'm getting desperate........

As soon i put a dvd in my player, the system is doing nothing with it.
CD's is no problem.


I'ved seen somewher to execute the command **lshw -short -c disk**
When i execute this, the following result is showing:


```

H/W path           Device      Class       Description
======================================================
/0/100/1f.2/0      /dev/sda    disk        500GB SAMSUNG HD503HI
/0/100/1f.2/1      /dev/cdrom  disk        DVDRAM GH22NS50
/0/100/1f.2/1/0    /dev/cdrom  disk        
/0/2/0.0.0         /dev/sdb    disk        SCSI Disk
/0/2/0.0.1         /dev/sdc    disk        SCSI Disk
/0/2/0.0.2         /dev/sdd    disk        SCSI Disk
/0/2/0.0.3         /dev/sde    disk        SCSI Disk
```

After i did this, he is reading my dvd's  ???


My /etc/fstab is looking the following:

```

 / was on /dev/sda1 during installation
UUID=a194d4d0-bbaa-44b6-86de-04fd8a100bda /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=1b27ab9f-34e6-4d8b-a958-e6e1b8dabfa1 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=1b8999bd-e317-45d5-a471-6f8e5158a2af none            swap    sw              0       0

```

I'll execute the command everytime i start the computer, but i'm hoping for a solution.
My ubuntu is 10.04.

Kind regards,

A new linux user.

---

### Post by Brandel Valico on 2010-09-18
[http://ubuntuforums.org/showthread.php?t=766683&highlight=dvd+playback](http://ubuntuforums.org/showthread.php?t=766683&highlight=dvd+playback)

Try following the guide here for your version and everything should be up and running in no time

---

### Post by kapstokje78 on 2010-09-18
Well,

It finally works, even without reading your thread.

I installed libdvdread4-dev and libdvdcss packages and it reads the dvd at once (atm).

I'll try it a few times today and post my outcome

---

### Post by Brandel Valico on 2010-09-18
Yep thats pretty much what the guide tells you to do.

---

