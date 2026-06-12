---
title: "swap not active problem trying to install uswsusp"
date: 2007-10-23
forum: Hardware &amp; Laptops
---

### Post by acwspoon on 2007-10-23
I just clean installed gusty yesterday,
I have tried to use this HOWTO: [http://ubuntuforums.org/showthread.php?t=471855&highlight=suspend+gusty]("http://ubuntuforums.org/showthread.php?t=471855&highlight=suspend+gusty")

which it would work but I keep getting this during the installation

The swap file or partition that was found in uswsusp's configuration file is not active.
In most cases this means userspace software suspend will not work for you and you will need to choose (or let uswsusp choose) another swap space. 
 In some corner cases however, this can be what you want

I have tried to make it active by making my etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=dc564129-c29d-4f70-9072-d164f2ea6ad6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=C2D4BAC0D4BAB64F /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=006B-8E1D  /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=2A6D-11E8  /media/sda4     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5	swap		swap	defaults		0	0
UUID=3e281de7-92fa-4372-bdfa-21c25bfc8ab0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

I can't figure it out, if I finish the installation without an active suspend and hibernate don't work of course.
Any help would be much appreciated.

---

### Post by acwspoon on 2007-10-23
Someone please help, I usually can take care of this kind of stuff but I'm stumped.

---

### Post by kirill_igum on 2007-11-11
same problem here

---

### Post by gubemton on 2007-11-15
B-U-M-P...

Pretty please?

---

### Post by jeremija on 2007-11-19
i have the same problem :(
i am using t60p laptop and suspend no longer works after upgrading from fiesty to gutsy yesterday (64-bit, ati firegl v5250, using xgl)

---

### Post by shadyzay on 2007-12-01
Just upgraded to gusty,  hibernate was great in edgy and feisty, but now I have to restart NetworkManager after each hibernate.
Tried to install uswsusp but I had the same problem, swap not active.
I have a Gateway 4542GP

---

### Post by shadyzay on 2007-12-01
It's working now, here's everything I did, I don't know exactly what solved it, but I guess it's the reconfigure:
```
sudo apt-get remove --purge uswsusp
sudo apt-get install uswsusp
```
downloaded the 0.7 debian package from [here]("http://packages.debian.org/sid/uswsusp").
installed the new package.
until here it was not working yet.
then I run:
```
sudo dpkg-reconfigure uswsusp
```
I got the same error, but after going through the configuration (left all the defaults), I had the option to pick the swap partition again, with two choices:
  1. /dev/sda1
  2. UUID=e0a9cace-b2d8-464a-a881-e1347e90067d
( which are practically the same device .. I guess .. lol )
And I picked 1

Now s2disk works great, but s2ram doesn't ( but I guess that's another issue ).

You guys can try reconfigure first ( without installing 0.7 ), I guess it'll solve the issue.

---

### Post by peter771 on 2008-04-02
@shadyzay

I'm running Gutsy and this helped fix my suspend and hibernate!

Thank you! :-)

---

### Post by david412 on 2008-04-30
I followed all the directions on this page, and now the command s2disk and s2ram don't come up with an error. With s2disk, after the command is executed, the monitor turns off, but the computer never actually powers off. I ended up doing a hard shutdown after a couple of minutes, but the weird thing is, it actually saved the machine state. Is there any way that I can get the computer to turn itself after hibernation?

I am running 64bit Gutsy on an HP tx1000

---

