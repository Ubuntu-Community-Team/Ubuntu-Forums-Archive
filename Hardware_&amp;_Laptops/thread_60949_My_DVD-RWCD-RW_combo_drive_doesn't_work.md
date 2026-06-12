---
title: "My DVD-RW/CD-RW combo drive doesn't work?"
date: 2005-08-29
forum: Hardware &amp; Laptops
---

### Post by linkunderscore on 2005-08-29
I have searched the forums to no avail. I recently switched to Ubuntu about 4 weeks ago and I have completely stopped using XP Pro. I really like the way Ubuntu works. Its amazing. As weird as it sounds, I have had no need for my cdrom drive in the last 4 weeks until now. I need to play an audio cd for a class. 

That said, my combo drive does not work. From what I have read, an icon should appear on my desktop when I insert a cd/dvd/cdr. If that doesn't happen, then I should look in my /media/cdrom/ directory to see if its there. I have done this...and I got nothin  ](*,) 

Here is what my fstab looks like:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hda2       /mnt/windows1   vfat

``` 
It appears to recognized the fact that I have a cdrom drive?


What do I have to do to fix this problem?

---

### Post by linkunderscore on 2005-08-30
I just took a look into my bios and it says ATAPI device:______________

I know before I installed ubuntu it was there? But now its blank...

---

### Post by linkunderscore on 2005-08-30
Any ideas? 

I just gotmy wireless card working with ndiswrapper. The only thing that is doesn't work now, is my DVD-RW/CD-RW combo drive. If I could just get this to work, it would be the perfect Ubuntu machine.

---

### Post by linkunderscore on 2005-08-30
I really need this to work for school. I don't want to have to switch back to windows everytime I need to play a CD.  :-x 

Ubuntu isn't recognizing that I even have this device. GRRRRRRRRRR

I just don't undertand how it lets me use the drive to install ubuntu, but it doesn't show the device after its installed  :?

---

### Post by linkunderscore on 2005-08-30
bump

no one has experienced this before? no one knows how to fix this?

---

### Post by autocrosser on 2005-08-31
In your fstab--

edit 
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0

to

/dev/hdc        /media.cdrom0   auto        rw,user,noauto   0       0


And re-boot-- auto "forces" your drive to look at the media to determine the filesystem type & rw allows you to read & write with you unit.

Hope this helps---luck.

---

### Post by linkunderscore on 2005-08-31
I am going to try this right now...and if it works...im going to kiss you


tounge/no tounge--your choice

---

### Post by trash on 2005-08-31
[QUOTE=autocrosser]In your fstab--

edit 
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0

to

/dev/hdc        /media.cdrom0   auto        rw,user,noauto   0       0


And re-boot-- auto "forces" your drive to look at the media to determine the filesystem type & rw allows you to read & write with you unit.

Hope this helps---luck.[/QUOTE]

I get the same failures with 'auto' or 'udf,iso9660'

---

### Post by linkunderscore on 2005-08-31
it didn't work :( 

I don't think it is a problem mounting the cd's/dvd's. I think its a problem with linux recognizing the actual hardware device. I could be wrong, but changing my fstab did not fix the problem.


edit: at this point I don't care if it reads DVDs. I need access to CD's...desperately

---

### Post by trash on 2005-08-31
it's just wierd!
gnomebaker scans and finds my hardware at dev/sr0 but.....

kenji@bigmac:~$ mount /dev/dvd
mount: can't find /dev/scd0 in /etc/fstab or /etc/mtab
kenji@bigmac:~$ sudo vi /etc/fstab
Password:
kenji@bigmac:~$ sudo mount -a
kenji@bigmac:~$ mount /dev/scd0
mount: block device /dev/scd0 is write-protected, mounting read-only

---

### Post by linkunderscore on 2005-08-31
[QUOTE=trash]it's just wierd!
gnomebaker scans and finds my hardware at dev/sr0 but.....

kenji@bigmac:~$ mount /dev/dvd
mount: can't find /dev/scd0 in /etc/fstab or /etc/mtab
kenji@bigmac:~$ sudo vi /etc/fstab
Password:
kenji@bigmac:~$ sudo mount -a
kenji@bigmac:~$ mount /dev/scd0
mount: block device /dev/scd0 is write-protected, mounting read-only[/QUOTE]


at least gnomebaker FINDS your hardware. Ubuntu magically installed itself from this drive that it can no longer see nor recognize :?

---

### Post by trash on 2005-08-31
[QUOTE=linkunderscore]at least gnomebaker FINDS your hardware. Ubuntu magically installed itself from this drive that it can no longer see nor recognize :?[/QUOTE]

have you run the livecd from that drive and checked the fstab?

---

### Post by linkunderscore on 2005-08-31
[QUOTE=trash]have you run the livecd from that drive and checked the fstab?[/QUOTE]


do you mean check the fstab the LiveCD makes...or check my fstab now? 


If you are referring to the prior, then no I have not.

---

### Post by trash on 2005-08-31
[QUOTE=linkunderscore]do you mean check the fstab the LiveCD makes..[/QUOTE]

yup, might give you a clue... i will try it soon.

---

### Post by linkunderscore on 2005-08-31
Yea, well I am thinking maybe its something wrong with the actual HARDWARE. I went into the bios and told it from boot cd/dvdrw > saved changes >it auto restarted...and it went straight to the grub menu. 

The bios says ATAPI device: ________ with a blank. All of the other categories ie video card, chipset, etc all have their info. It seems as if my dvdrw/cdrw combo drive has disappeared from my system. 

Do you think the hardware could be malfunctioning? I think im going to try it in windows tomorrow to check and make sure.

---

### Post by trash on 2005-08-31
well i booted the live cd from my internal cd-r.
Externat dvd-rw was not writen to the fstab but when i put the Haory install cd in the external drive it mounted it within seconds..

$ mount
/devscd0 on /media/cdrecorder type hfs...

I popped in a blank dvd-r and nautilus opened up a cd/dvd creator window, I created a gedit file and tried to burn to the dvd-r, it started the burn process
'fixating on dvd' for about 5 minutes, ejected the dvd-r twice, both times closed the drawer after and proceeded to burn!

i'll post the gedit file after i reboot...5 min.

EDIT:
from the livecd...
with hoary installcd in /dev/scd0

ubuntu@ubuntu:~$ mount
/dev/mapper/casper-snapshot on / type auto (rw,noatime)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)
/dev/scd0 on /media/cdrecorder type hfs (ro,nosuid,nodev,sync,uid=1000,gid=1000)

with a blank dvd-r I was able to burn using cdrecorder from the livecd! 
mount
showed no disk before it was written

---

### Post by linkunderscore on 2005-08-31
well, im out of ideas

---

### Post by linkunderscore on 2005-08-31
I am now back on my windows partition, and my worst fears have been realized. This is a hardware issue...not a software issue. 

This kinda makes me feel better about ubuntu :) It still may be the greatest thing that has ever happened to computers. ;) 

Good thing this thing still has a warranty. I will take it to the repair store asap. Then we will realy see if Ubuntu will pick it up. Which i am completely sure it will.

edit: actually, is there anything that you guys can think of that might have caused this? Or is this just hardware going bad?

---

### Post by linkunderscore on 2005-09-10
:)  :)  :)  :)  :)  :) 

just got my new replacement optical drive...first start-up after it was replaced-WORKED!! :) 

I love ubuntu :)

---

### Post by Azerial on 2007-09-02
> **linkunderscore said:**
> I am now back on my windows partition, and my worst fears have been realized. This is a hardware issue...not a software issue. 

This kinda makes me feel better about ubuntu :) It still may be the greatest thing that has ever happened to computers. ;) 

Good thing this thing still has a warranty. I will take it to the repair store asap. Then we will realy see if Ubuntu will pick it up. Which i am completely sure it will.

edit: actually, is there anything that you guys can think of that might have caused this? Or is this just hardware going bad?

I'm having the same problem EXCEPT My drive works with my windows partition and not Ubuntu

---

