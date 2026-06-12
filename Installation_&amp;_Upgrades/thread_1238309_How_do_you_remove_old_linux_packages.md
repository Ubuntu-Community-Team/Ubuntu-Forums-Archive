---
title: "How do you remove old linux packages?"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by sidewalkcynic on 2009-08-12
installer gives an error saying my /boot partition is short on space, and I [found this thread discussing the problem]("http://ubuntuforums.org/showpost.php?p=3835350&postcount=1")/ solution, but it does not give the details...>  Re: Gusty Gibbon upgrade problem re /boot free space
It turns out that you can't delete old kernels manually. You have to delete them through apt-get. So remove all your old linx-image packages and you should be all set the next time you upgrade.

In my particular situation I installed the CD Hardy 08.04, upgraded to Intrepedid 08.10, and now that I want to upgrade to 09.04 I received this error message:
> The upgrade is now aborted. The upgrade needs a total of 1204M free space on disk '/'. Please free at least an additional [COLOR="Red"]840M[/COLOR] of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'. and then after cleaning-up, and running an autoremove command, I got:
> The upgrade is now aborted. The upgrade needs a total of 1204M free space on disk '/'. Please free at least an additional [COLOR="Magenta"]230M[/COLOR] of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.And, I recall that the installation of 8.10 required 610Mb of space, and that is the difference of the amount of space that was "liberated" when the apt-get clean was run.

So, what should it be, "apt-get remove hardy 08.04"

---

### Post by p2bc on 2009-08-12
Well to start you should open the man page of apt-get
```

man apt-get

```

The man page is the way to bring up the manual of any given application to see what variables you can add to change the outcome.

So I would start by:
```

sudo apt-get -autoremove
sudo apt-get -autoclean
sudo apt-get -clean

```

All that would help, if there are repository information stored on you system which is taking up room, and is no longer needed.

But to me it sounds like you just need to start clearing out space on your hard drive. You could even be better to replace the hard drive with a newer larger one, and clone the existing system onto the new drive. (Recently purchased a 500g laptop drive for $125CAD)  :) more than enough room.  Just saying.

Enjoy

---

### Post by sidewalkcynic on 2009-08-12
I'll be attempting the commands you provided. As far, as my hardrive capacity, I have been monitoring it very closely and trying different configurations of partitions to handle my expectations - I'm not a gamer, or video-type, my session are usually only web-browsing and note taking, so I have yet to use-up my partitions of saved web pages, only about 2.5 Gb. And, since my processor is ten-years-old and is only 500 Mhz, I don't think it would be of much sense to work a much larger hardrive.

---

### Post by sidewalkcynic on 2009-08-12
Nope,

those commands did not help any.

---

### Post by slakkie on 2009-08-12
Can you show me the output of 

df -kh

and also post the output of

du -sh /var/cache/apt/*

Many thanks.

Removing packages which are no longer needed:

```

# Simulate
sudo aptitude -s purge $(dpkg -l | grep "^rc" | awk '{print $2}')

# Actually do it
sudo aptitude -y purge $(dpkg -l | grep "^rc" | awk '{print $2}')


```

And maybe you can remove your old kernels as well;

```

# Simulate
sudo aptitude -s purge $(dpkg -l | grep linux-image | egrep -v "$(uname -r)|linux-image-generic" | awk '{print $2}')
# Actually remove
sudo aptitude -y purge $(dpkg -l | grep linux-image | egrep -v "$(uname -r)|linux-image-generic" | awk '{print $2}')

```

The kernels take about 100Mb, so maybe you have enough room afterwards.

---

### Post by sidewalkcynic on 2009-08-12
```
 df -kh
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             3.5G  2.4G  991M  72% /
tmpfs                 125M     0  125M   0% /lib/init/rw
varrun                125M  108K  125M   1% /var/run
varlock               125M     0  125M   0% /var/lock
udev                  125M  2.7M  122M   3% /dev
tmpfs                 125M  104K  125M   1% /dev/shm
lrm                   125M  2.2M  123M   2% /lib/modules/2.6.27-14-generic/volatile
/dev/sda3             849M   77M  730M  10% /home

```

```
$ du -sh /var/cache/apt/*
76K	/var/cache/apt/archives
792K	/var/cache/apt/pkgcache.bin
12K	/var/cache/apt/srcpkgcache.bin

```

---

### Post by zvacet on 2009-08-12
You can remove old kernels from synaptic.In search box type **linux-image **and when you find them remove ones with lower number.

---

### Post by slakkie on 2009-08-12
> **sidewalkcynic said:**
> ```
 df -kh
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             3.5G  2.4G  991M  72% /
tmpfs                 125M     0  125M   0% /lib/init/rw
varrun                125M  108K  125M   1% /var/run
varlock               125M     0  125M   0% /var/lock
udev                  125M  2.7M  122M   3% /dev
tmpfs                 125M  104K  125M   1% /dev/shm
lrm                   125M  2.2M  123M   2% /lib/modules/2.6.27-14-generic/volatile
/dev/sda3             849M   77M  730M  10% /home

```

```
$ du -sh /var/cache/apt/*
76K	/var/cache/apt/archives
792K	/var/cache/apt/pkgcache.bin
12K	/var/cache/apt/srcpkgcache.bin

```

That is not a lot of space my friend. I have a / of 20 Gb and using 14 Gb on Karmic (ok, I have almost every GUI installed..)

How big is your swap? (swapon -s)


Try removing your old kernels, that might help a lot.

---

### Post by sidewalkcynic on 2009-08-12
```
 sudo aptitude -s purge $(dpkg -l | grep "^rc" | awk '{print $2}')

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
The following packages will be REMOVED:

  bluez-audio{p} console-tools{p} cups-pdf{p} dhcdbd{p} libbind9-30{p} 
  libbluetooth2{p} libcamel1.2-11{p} libchromexvmc1{p} libchromexvmcpro1{p} 
  libdjvulibre15{p} libdns32{p} libdns35{p} libedataserver1.2-9{p} 
  libffi4{p} libgail18{p} libgmime-2.0-2{p} libgnome-desktop-2{p} 
  libgnomekbd2{p} libgnomekbdui2{p} libgnutls13{p} libgpmg1{p} 
  libgucharmap6{p} libhunspell-1.1-0{p} libisc32{p} libisc35{p} 
  libisccc30{p} libisccfg30{p} libltdl3{p} liblwres30{p} libmtp7{p} 
  libntfs-3g23{p} libopenal0a{p} libopencdk10{p} libopenexr2ldbl{p} 
  libparted1.7-1{p} libpoppler-glib2{p} libpoppler2{p} libsmbios1{p} 
  libtotem-plparser10{p} myspell-en-us{p} scrollkeeper{p} 
  xserver-xorg-video-via{p} 
0 packages upgraded, 0 newly installed, 42 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Would download/install/remove packages.

```

Swap is 1Gb

In SYNAPTIC, it appears I have three kernals:

linux-image-generic     2.6.27.14.18
linux-image-2.6.24-23.46-generic
linux-image-2.6.24-23.46-generic

So, I imagine, I can remove the bottom two, and everything will be straight?

---

### Post by slakkie on 2009-08-12
If you use the commands I gave you, first remove the kernels, then purge all the other stuff.

In this order (**I removed the simulate option**!!!!)
```

sudo aptitude -y purge $(dpkg -l | grep linux-image | egrep -v  "$(uname -r)|linux-image-generic" | awk '{print $2}')

sudo aptitude -y purge $(dpkg -l | grep '^rc' | awk '{print $2}')

```

---

### Post by sidewalkcynic on 2009-08-12
I just gave the simulate command, because I thought you wanted to review the info.

I did the commands that you gave, and it appears a lot of work took place so, I'll bet everything is in order now. And so, after upgrading to 9.04, I'll then remove what will become old kernal -right?

---

### Post by slakkie on 2009-08-12
After upgrading, yes, also include 

sudo aptitude clean

Since the upgrade will place a whole lot of packages in your cache which can be removed. That was that du -sh line.

---

### Post by sidewalkcynic on 2009-08-12
Oh, so close...

Error message came back - needs 83Mb

My system monitor says that the FireFox browser uses about 42 Mb. So, I imagine that could be part of it???

---

### Post by slakkie on 2009-08-12
That is memory (RAM) usage, so no.

If you don't care about your logs.. You could wipe some out in /var/log..


This will show you what we will remove (files which haven't been touched over a day) and how much we will remove in total.
```

sudo find /var/log -mtime +0 -exec du -ch {} +

```

Don't think it will be much, on my laptop this is only 42 Mb, on my server 90 Mb and on another server 64 Mb... 

To remove them...

```

sudo find /var/log -mtime +0 -exec rm {} +

```

If you really, really don't care about them.. but it is not something I would do this, after the removal of files older then a day...

```

sudo find /var/log -type f -exec :> {} \;

```

Which will remove the contents of all files, and setting them to 0, but this is not something I would recommend.

Maybe fireup gparted (get the livecd) and shrink your home partition (or swap) in favor of your root... That will take some time and could hurt the data on your disk. But with clonezilla you can make a backup.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
[http://www.clonezilla.org/](http://www.clonezilla.org/)


I just reminded myself that you could remove stuff from /var/tmp.. although that will probably clear 0-30 Mb at the most..

```

sudo rm -rf /var/tmp/*

```

---

### Post by sidewalkcynic on 2009-08-12
The problem I have encountered with GParted Live CD, is that if I resize the /root partition, I could not boot 8.04 - it would hang up in the "saving VESA state." I don't know what you mean by "date on the disk," but I haven't installed my applications list of note taking stuff, and have not yet installed anything in the /home that I would be concerned about losing - in fact to speed up GParted, I would just delete the /home and swap, since swap is in between them, enlarge /root, and then rebuild swap and /home. So, then I am only waiting on /root to resize.

> 12K	/var/log/fsck
0	/var/log/mail.err
40K	/var/log/bootstrap.log
0	/var/log/btmp
4.0K	/var/log/samba
4.0K	/var/log/dmesg.2.gz
0	/var/log/mail.log
4.0K	/var/log/boot
0	/var/log/mail.info
0	/var/log/lpr.log
4.0K	/var/log/apparmor
4.0K	/var/log/unattended-upgrades
0	/var/log/pycentral.log
0	/var/log/mail.warn
224K	/var/log/apt
296K	total


What's the command for learning how much will be removed for:
> sudo rm -rf /var/tmp/*using the file browser, there's nothing in /var/tmp, although, there is some 190Mb in /var/lib ,
 and 25Mb in /tmp

---

### Post by slakkie on 2009-08-12
Maybe you can use the following method to upgrade:

[https://help.ubuntu.com/community/JauntyUpgrades#Upgrading%20Using%20the%20Alternate%20CD/DVD](https://help.ubuntu.com/community/JauntyUpgrades#Upgrading%20Using%20the%20Alternate%20CD/DVD)

This will require some diskspace to burn the CD (can be removed after burning) But I don't think it will require so much diskspace like the network install. Never done it myself, so no warranty ;)

---

### Post by slakkie on 2009-08-12
> **sidewalkcynic said:**
> The problem I have encountered with GParted Live CD, is that if I resize the /root partition, I could not boot 8.04 - it would hang up in the "saving VESA state." I don't know what you mean by "date on the disk," but I haven't installed my applications list of note taking stuff, and have not yet installed anything in the /home that I would be concerned about losing - in fact to speed up GParted, I would just delete the /home and swap, since swap is in between them, enlarge /root, and then rebuild swap and /home. So, then I am only waiting on /root to resize.


date on disk was data on disk. Typo :)

I would resize you swap a little, since your home is already less then one Gb (how you manage is beyond me btw, my home is 50Gb).
You are on dual boot I assume, since the other 5 Gb is allocated to another OS..? Maybe remove some space from there??

The space from /var/log is nothing. Not even close.

sudo ls /var/tmp/*

will tell you what is in that dir, to see what you will remove with sudo rm -rf /var/tmp/*

---

### Post by joao82 on 2009-12-12
> **slakkie said:**
> If you use the commands I gave you, first remove the kernels, then purge all the other stuff.

In this order (**I removed the simulate option**!!!!)
```

sudo aptitude -y purge $(dpkg -l | grep linux-image | egrep -v  "$(uname -r)|linux-image-generic" | awk '{print $2}')

sudo aptitude -y purge $(dpkg -l | grep '^rc' | awk '{print $2}')

```

This was very helpful, thanks.

---

