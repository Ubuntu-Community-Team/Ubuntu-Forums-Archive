---
title: "Installing a second hard drive"
date: 2007-03-17
forum: Hardware &amp; Laptops
---

### Post by Li-Golfer on 2007-03-17
Hi, 
I am a newbie to Ubuntu and the Linux world. I just setup an older computer with a 40gb hard drive, as a Master, and installed Ubuntu. That sure seems to work fine. I would like to install a second hard drive as a Slave. I formatted a 20gb hard drive, in Dos, and plugged it in with the jumper set to Slave. Ubuntu doesn't seem to see it. Would you please tell me what I have done wrong and how to fix the problem.
Thanks,
Li-Golfer

---

### Post by taurus on 2007-03-17
If you install a second harddrive, you need to mount it before you can use it.  From a terminal, post the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Li-Golfer on 2007-03-17
Taurus,
Thank you for your reply. I am not sure as to what to do exactly but I will muck around on the Ubuntu computer.I will let you know what happens ... that is unless it all explodes and you get to see the mushroom cloud.
Li-Golfer

---

### Post by taurus on 2007-03-17
Okay, if you want to search for your question.  Otherwise, I can walk you through mounting it if you just post the output of that command here so I know what device it is on and what filesystem it is using.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Li-Golfer on 2007-03-18
Dear Taurus,
Again, thank you for your reply. I am the 1st to admit that I am in over my head. I booted my Ubuntu computer, went to Applications, Accessories and then to the Terminal. A pop-up window appeared with the following:
gerald@gerald-desktop:-$
I then went to Edit and added: sudo fdisk -1 to the above sentence.
There didn't seem to be a way to save so I just closed that window and re-booted. When I examined the configuration again of course nothing had changed. I went back to that pop-up window and my added sentence was not there.
I know that I am doing something(s) incorrectly, but I have faith that I will get there some time soon. 
I want you to know that I do very much appreciate your help.
Gerald
Li-Golfer

---

### Post by taurus on 2007-03-18
The command that you would type into a terminal is

```
sudo fdisk -**l**
```
That would be lower case letter **l** as in **l**arry, not number 1.

---

### Post by Frenzy-br on 2007-03-18
im having the same problem and when i type 

> sudo fdisk -l

all i get is this 

> Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4664    37463548+  83  Linux
/dev/hda2            4665        4865     1614532+   5  Extended
/dev/hda5            4665        4865     1614501   82  Linux swap / Solaris

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14946   120053713+   7  HPFS/NTFS


a few days ago it was all working fine but then i formate my linux HD and now i cant see my other HD and i have all my movies and music there, any idea on how i would be able to see it without having to format the drive... its a 120g hd and its full to the brim with evrything i own... i kinda got lazy and didnt copy everything to dvd before installing linux .. and im also a linux newb....

---

### Post by taurus on 2007-03-18
> **Frenzy-br said:**
> im having the same problem and when i type 

all i get is this 

a few days ago it was all working fine but then i formate my linux HD and now i cant see my other HD and i have all my movies and music there, any idea on how i would be able to see it without having to format the drive... its a 120g hd and its full to the brim with evrything i own... i kinda got lazy and didnt copy everything to dvd before installing linux .. and im also a linux newb....

Did you mount /dev/hdb1 in /etc/fstab?  Can you post your /etc/fstab here?

```
cat /etc/fstab
```

---

### Post by Frenzy-br on 2007-03-18
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=96419fc5-6d81-46d6-8aec-299c914d73cb /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=e65634a8-222b-4716-bc4a-a172fa6ee43f none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by taurus on 2007-03-18
Well, you need to mount it before you can access it.  Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/hdb1   /media/hdb1   ntfs   nls=utf8,umask=0222   0   0
```
Save the chance.  Then, create a new mount point and mount it.

```
sudo mkdir /media/hdb1
sudo mount -a
df -h
```

---

### Post by Frenzy-br on 2007-03-18
thx alot it worked great...

---

### Post by IAmAnEvilTaco on 2007-10-06
so I just did all of this, and it worked and I can see my hard drive (thanks, by the way, taurus). 

I have 2 additional questions, though. 1, is it possible to permanently mount it? because I had to go through gpartition to do so. 2, how do I make it so I can upload files to it, etc...? it says owner only and I'm pretty sure I own my computer. What I'd do for a password prompt or something.

---

### Post by taurus on 2007-10-06
> **IAmAnEvilTaco said:**
> so I just did all of this, and it worked and I can see my hard drive (thanks, by the way, taurus). 

I have 2 additional questions, though. 1, is it possible to permanently mount it? because I had to go through gpartition to do so. 2, how do I make it so I can upload files to it, etc...? it says owner only and I'm pretty sure I own my computer. What I'd do for a password prompt or something.

Yes, you can mount it automatically each time you boot Ubuntu.  You just need to add an entry in /etc/fstab for it.  So, if you post the outputs of these commands from a terminal, I can walk you through the whole thing!

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

---

### Post by IAmAnEvilTaco on 2007-10-06
the fdisk list:
> Disk /dev/sda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7288    58540828+  83  Linux
/dev/sda2            7289        7476     1510110    5  Extended
/dev/sda5            7289        7476     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4865    39078081   83  Linux

the df list:
> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              55G   41G   12G  78% /
varrun                252M  112K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb            252M   92K  252M   1% /proc/bus/usb
udev                  252M   92K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   33M  219M  14% /lib/modules/2.6.20-16-generic/volatile
/dev/sdb1              37G   48M   35G   1% /storage
logickbomb@logickbomb-vertigo:~$ 


Thanks again in advance, by the way. I've had a heck of a time getting anyone's attention here, it's really appreciated. It's all pretty daunting, I was really skilled with windows' subtleties and now I feel like a total noob. I guess that comes with the territory though.

---

### Post by taurus on 2007-10-06
I assume you are talking about /dev/sdb1.  If you want it to mount to /storage each time you boot ubuntu, just add a line in /etc/fstab.

From a terminal, edit /etc/fstab with

```
gksudo gedit /etc/fstab
```
and scroll down to the end and add this line to it.

```
/dev/sdb1   /storage   ext3   defaults   0   1
```
Save the change.  Now, if you want to write to /storage without using sudo, you need to change the ownership of /storage from root to your login name.  _Assuming_ your login name is **taco** (replace taco with your actual login name, okay!), do

```
sudo chown -R **taco**:**taco** /storage
ls -la /storage
```

---

### Post by IAmAnEvilTaco on 2007-10-06
bam, problem solved. thanks a lot :). now I can dump some of this stuff off of my core hard drive and stretch linux's legs a bit.

you're awesome :).

---

### Post by taurus on 2007-10-06
You see, nobody is ignoring you.  ;)

---

### Post by IAmAnEvilTaco on 2007-10-06
totally. and this was the important bit, too. I can deal without my wireless card, and I can probably fix kubuntu's exclusionist tendencies and hatred of of the rest of linux as long as I have the space to do so. this was a big help, thanks. :)

---

