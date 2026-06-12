---
title: "DVD Playback."
date: 2005-12-04
forum: General Help
---

### Post by LongTooth on 2005-12-04
I've search the forum high and low and can't find a solution. I'm sure its buried somewhere in the forum but I'll be damn if I can find it. So without further ado  here goes.

I'm getting this error message with I try to play DVDs: "Fail to find mountpoint for device /dev/hdd in /etc/fstab".

Here's what I have in my /etc/fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


I don't see where I'm missing anything.I used Automatix to tweak my system so I know DMA is on and I've done: 
 
sudo apt-get install libdvdread3
sudo /usr/share/doc/libdvdread3/examples/install-css.sh.

I'm lost and dont' know where to go from here. Any assistance would be greatly appreciated. 

Thanks.

---

### Post by arnieboy on 2005-12-04
[QUOTE=LongTooth]I've search the forum high and low and can't find a solution. I'm sure its buried somewhere in the forum but I'll be damn if I can find it. So without further ado  here goes.

I'm getting this error message with I try to play DVDs: "Fail to find mountpoint for device /dev/hdd in /etc/fstab".

Here's what I have in my /etc/fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


I don't see where I'm missing anything.I used Automatix to tweak my system so I know DMA is on and I've done: 
 
sudo apt-get install libdvdread3
sudo /usr/share/doc/libdvdread3/examples/install-css.sh.

I'm lost and dont' know where to go from here. Any assistance would be greatly appreciated. 

Thanks.[/QUOTE]
do the following:
```
sudo gedit /etc/hdparm.conf
```
and add the following lines at the end:
> /dev/hdd {
       dma = on
}

save and exit and reboot.

---

### Post by LongTooth on 2005-12-05
Well, thanks for the quick reply but that did not work. Still no DVD playback and I get the same error message. 'fail to find mountpoint for device /dev/hdd in /etc/fstab'. What else should I check for? 

Thanks.

---

### Post by arnieboy on 2005-12-05
[QUOTE=LongTooth]Well, thanks for the quick reply but that did not work. Still no DVD playback and I get the same error message. 'fail to find mountpoint for device /dev/hdd in /etc/fstab'. What else should I check for? 

Thanks.[/QUOTE]
try doing:
```
sudo mkdir /media/cdrom1
```
and see if that helps

---

### Post by LongTooth on 2005-12-05
Results of mkdir...:

 longtooth@microatx:~$ sudo mkdir /media/cdrom1
Password:
mkdir: cannot create directory `/media/cdrom1': File exists
longtooth@microatx:~$

Looks like I have this directory already. 


Arniboy I really appreciate your input. Why don't I start from scratch? What are the first steps to insure DVD playback. If nothing else it will help me understand what's going on in the back ground when and if it happens. Might help others as well. So, what files to check, what information to insure is there? Etc. 

Thanks for your involment.

---

### Post by markr on 2005-12-05
Not sure how a DVD player is called /dev/hdd.

Should it not be /dev/dvd or /dev/cdrom?

Mark.

---

### Post by Gray. on 2005-12-05
/dev/hda = Master on 1st IDE channel
/dev/hdb = Slave on 1st IDE channel
/dev/hdc = Master on 2nd IDE channel
/dev/hdd = Slave on 2nd IDE channel

At least that is what it is to my knowledge.

On-topic:
Maybe try doing:
```
sudo mount /dev/hdd /media/cdrom1
```
Or try setting the correct device in your DVD players Settings/Preferences menu?

---

### Post by Bandit on 2005-12-05
You do not mount the DVD for DVD playboack. The software will read the DVD without mounting the filesystem.
It however does need to be pointed in the right direction.
When you put a DVD/CD in the drive, what ever folder pops up in is the one you need to point xine or mplayer to. Example mine is /dev/hdc (Master Drive on Second IDE cable), it shows up as /media/cdrom1 on the system.
If you are still having issues download the newest verison of xine from my website and try it out. If you are trying to play commercial (encrypted) DVD's you will need to google for "libdvdcss2-1.2.9 deb package" as I cant host that software on my website here in the US. Stupid patents...
Cheers,
Joey

---

### Post by LongTooth on 2005-12-05
"When you put a DVD/CD in the drive, what ever folder pops..." I insert a DVD and do not get any kind of further prompt. I open Totem and from there try to open the DVD. I've tried using Mplayer also.   

I'll try sudo mount /dev/hdd /media/cdrom1 and take a look at the link provided by Bandit. I have installed the file libdvdcss2-1.2.9 deb package. 

Onward through the fog!

Thanks for the info.

---

### Post by LongTooth on 2005-12-06
Results of mount /dev....etc:

longtooth@microatx:~$
longtooth@microatx:~$ sudo mount /dev/hdd /media/cdrom1
Password:
mount: you must specify the filesystem type
smartjak@microatx:~$



My /etc/fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

So what's next? 

Thanks.

---

### Post by Bandit on 2005-12-06
Well its cdrom0 or cdrom1.
One or ther other..

---

### Post by LongTooth on 2005-12-06
Obviously I'm still missing some information. Using both cdrom0 and cdrom1 I'm still informed I'm missing a file system:

longtooth@microatx:~$ sudo mount /dev/hdd media/cdrom1
mount: you must specify the filesystem type
smartjak@microatx:~$

---

### Post by doitashimashite on 2005-12-06
Just my $0.02:

Is there a symbolic link for /dev/dvd?

ls -l /dev/dvd

should give you something like

lrwxrwxrwx  1 root root 3 2005-12-06 16:29 /dev/dvd -> hdc

If not, a symbolic link should be set:

ln -s /dev/hdc /dev/dvd

(change hdc into whatever drive your dvd is at)

---

### Post by LongTooth on 2005-12-06
Well, I've got that too:

longtooth@microatx:~$ ls -l /dev/dvd
lrwxrwxrwx  1 root root 3 2005-12-06 11:54 /dev/dvd -> hdd
longtooth@microatx:~$

Exactly as you stated.

Thanks to all for staying with me on this. Its open my eyes to a lot. I'll keep plugging away.

---

### Post by PokerFacePenguin on 2005-12-06
If you have the libdvdcss2 loaded up how about trying this.......

you have already identified the dvd as hdd.........

If you are trying to play this dvd in xine....

Open xine
Not sure if you are REQUIRED to change to expert mode or not, that is what works for me
Go to the settings option in xine (alt - s)
Click on the MEDIA tab
Device used for dvd playback 

  -change it to /dev/hdd instead of /dev/hda

---

### Post by LongTooth on 2005-12-06
I'm at work at the moment. I'll try that when I get home. 

Thanks.

---

