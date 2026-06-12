---
title: "Ubuntu 14.10 takes a long time to boot"
date: 2015-03-31
forum: Hardware
---

### Post by pablo38 on 2015-03-31
Yesterday I decided to install ubuntu 14.10 on my laptop, the installation was succesful but it was at a very low resolution (640x400) so I installed nvidia drivers, version 349. When I rebooted my laptop after GRUB, screen was black and I thought I should wati. After about 10 minutes my laptop started the GUI. After starting all works fine.
I tried with different versions of nvidia drivers but the result is the same
PD: My graphic card is a NVIDIA GEFORCE GT525M

---

### Post by oldfred on 2015-03-31
If you did not purge each nVidia driver totally and xorg file, then you get conflicts and create many more issues.

Purge all nVidia and install which everyone is correct for your chip. 
Is it a dual video Ultrabook? 

       #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA
#Resolution:
xwininfo -root
#What is installed
dkms status

Some not so old nVidia cards/chips use 340.xx as legacy. Not sure what yours is:
      
 Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
Updated driver search by nVidia model
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

      
 # only reason to purge is there are several versions, if you know you have different nVidia use that:
Also must make sure parts of old install or persistence issue are not persevered as they are in use.
#To see available versions:
dpkg -l | grep -i nvidia*
#see details for version installed
sudo apt-cache policy nvidia*
dkms status
#Then for verson installed
sudo apt-cache policy nvidia-3XX-updates 


 sudo mv /etc/X11/xorg.conf /etc/X11/xorg/conf.old
Shows any file with nvidia in name, lots of files.
sudo find / -name "nvidia*"
Shows versions in repository:
sudo apt-cache search nvidia-sett*
Lists installed version, in/with your kernel:
dkms status
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*

All the conflicts may be the issue on slow boot, or it may be other unrelated issues. 
But first resolve to correct nVidia driver.

---

### Post by pablo38 on 2015-03-31
I decided to do a clean install of ubuntu and then install nvidia drivers version 340, the problem persists.

---

### Post by pablo38 on 2015-03-31
> **oldfred said:**
> If you did not purge each nVidia driver totally and xorg file, then you get conflicts and create many more issues.

Purge all nVidia and install which everyone is correct for your chip. 
Is it a dual video Ultrabook? 

       #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA
#Resolution:
xwininfo -root
#What is installed
dkms status

Some not so old nVidia cards/chips use 340.xx as legacy. Not sure what yours is:
      
 Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
Updated driver search by nVidia model
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

      
 # only reason to purge is there are several versions, if you know you have different nVidia use that:
Also must make sure parts of old install or persistence issue are not persevered as they are in use.
#To see available versions:
dpkg -l | grep -i nvidia*
#see details for version installed
sudo apt-cache policy nvidia*
dkms status
#Then for verson installed
sudo apt-cache policy nvidia-3XX-updates 


 sudo mv /etc/X11/xorg.conf /etc/X11/xorg/conf.old
Shows any file with nvidia in name, lots of files.
sudo find / -name "nvidia*"
Shows versions in repository:
sudo apt-cache search nvidia-sett*
Lists installed version, in/with your kernel:
dkms status
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*

All the conflicts may be the issue on slow boot, or it may be other unrelated issues. 
But first resolve to correct nVidia driver.

I decided to do a clean install of ubuntu and then install nvidia drivers version 340, the problem persists.

---

### Post by oldfred on 2015-03-31
Does it boot but very long time?

If so take a look at log files. 
With 14.04 it still is in /var/log/dmesg
While that can be long list, you want to look at those entries with long time stamp differences.
Post just those with very long times in code tags with # in advanced editor.

---

### Post by pablo38 on 2015-04-01
> **oldfred said:**
> Does it boot but very long time?

If so take a look at log files. 
With 14.04 it still is in /var/log/dmesg
While that can be long list, you want to look at those entries with long time stamp differences.
Post just those with very long times in code tags with # in advanced editor.
This is the log
```

```[   2.705569] Switched to clocksource tsc
```

```[   34.313944] EXT4-fs (sda7): INFO: recovery required on readonly filesystem
```

```[   34.313947] EXT4-fs (sda7): write access will be enabled during recovery
```

```[   34.455918] random: nonblocking pool is initialized
```

```[   35.041656] EXT4-fs (sda7): orphan cleanup on readonly fs
```

```[   35.041820] EXT4-fs (sda7): 11 orphan inodes deleted
```

```[   35.041822] EXT4-fs (sda7): recovery complete
```

```[   35.161245] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
```

```[   66.992437] init: ureadahead main process (238) terminated with status 5
```

```[   67.744737] Adding 5999612k swap on /dev/sda6.  Priority:-1 extents:1 across:5999612k FS

---

### Post by oldfred on 2015-04-01
It is running fsck on sda7. Is it doing that more than just once?

Try this from liveCD and see if you still get message on reboot.
 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda7 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda7
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda7

---

### Post by pablo38 on 2015-04-01
There isnt any error when I use those commands

---

### Post by pablo38 on 2015-04-01
> **oldfred said:**
> It is running fsck on sda7. Is it doing that more than just once?

Try this from liveCD and see if you still get message on reboot.
 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda7 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda7
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda7
Maybe the hard disk is damaged?

---

### Post by oldfred on 2015-04-01
IF you go into Disks and click on the tiny icon in upper right and open Smart Status does it say anything about your drive? All I know is ok or passed is good and any major issue is a new drive.

---

### Post by pablo38 on 2015-04-01
The status say passed, I think its no problem hard drive because when I use the nouveau drivers it boot quickly.

---

### Post by pablo38 on 2015-04-01
> **oldfred said:**
> IF you go into Disks and click on the tiny icon in upper right and open Smart Status does it say anything about your drive? All I know is ok or passed is good and any major issue is a new drive.

Problably is a graphics problem

---

### Post by pablo38 on 2015-04-02
> **oldfred said:**
> IF you go into Disks and click on the tiny icon in upper right and open Smart Status does it say anything about your drive? All I know is ok or passed is good and any major issue is a new drive.

I analized my hard disk with Hirens boot and there arent any error, something happens with graphics

---

### Post by pablo38 on 2015-04-05
I solved the problem by updating the bios. Now, only takes 40 seconds

---

