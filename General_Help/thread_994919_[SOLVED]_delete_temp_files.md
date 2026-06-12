---
title: "[SOLVED] delete temp files"
date: 2008-11-27
forum: General Help
---

### Post by potatoehead64 on 2008-11-27
Hi Folks.
I've come across a problem in the last few days regarding downloading files such as PDF or MP4. I'm getting the following error

> There is not enough room on the disc to save /tmp/uP8FDp5e.pdf.part.

Remove unnecessary files from the disc and try again, or try saving in a different location.

I'm assuming the /temp directory needs purging. Having searched several forums on this subject, I can't seem to find a definitive answer. I've done the following
sudo apt-get clean and another similar, but the error for downloading still occurs. Please help. 

ps. running 8.04 - Ubuntu Studio

---

### Post by Peter09 on 2008-11-27
In a terminal type

```
df
```

If you post the output we can see what part of your disk is full.
Also have a look in Synaptic and see if you have a lot of old Kernels lying around. 

Check you waste bin is not full.

---

### Post by potatoehead64 on 2008-11-27
Heres the output
> Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda11             9993184   8845760    643788  94% /
varrun                 1031612       116   1031496   1% /var/run
varlock                1031612         0   1031612   0% /var/lock
udev                   1031612       104   1031508   1% /dev
devshm                 1031612        48   1031564   1% /dev/shm
lrm                    1031612     39976    991636   4% /lib/modules/2.6.24-21-rt/volatile
overflow                  1024       692       332  68% /tmp
gvfs-fuse-daemon       9993184   8845760    643788  94% /home/marty/.gvfs
/dev/sdb1              1973952   1595104    378848  81% /media/disk
/dev/sda3              9074432   8977504     96928  99% /media/ACERDATA

Looking at this I'm wondering if I just need to extend the partition.

---

### Post by fooman on 2008-11-27
[COLOR="Red"]warning[/COLOR]: be wary of any posts containing the commands: "sudo rm -rf"...you can accidentally delete all your important data and leave your installation unoperable.

having said that,  i occasionally empty my /tmp file with the following command (safely and with no ill effects):

```
sudo rm -rf /tmp/*
```

like i said...careful with that "rm -rf" stuff.

---

### Post by Peter09 on 2008-11-27
yes - /home/marty seems pretty full

---

### Post by fooman on 2008-11-27
there is an app in applications > accessories called "disk usage analizer"

that will give you a nice graphical break-down of where your data is stored.

...very handy to find exactly where the build-up may be occuring.

---

### Post by potatoehead64 on 2008-11-27
> **Peter09 said:**
> yes - /home/marty seems pretty full

Ah! Thanks for that. I realize I overlooked an .iso image I had saved there. Moving it to another partition has made all the difference.

Thanks

---

