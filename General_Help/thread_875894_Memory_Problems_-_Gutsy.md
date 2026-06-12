---
title: "Memory Problems - Gutsy"
date: 2008-07-31
forum: General Help
---

### Post by Leo the Lion on 2008-07-31
Hi all,
I have been running Ubuntu 7.10 for some time now and at the time of install, I allocated about 8Gb for Ubuntu. I have a dual-boot machine.
Just recently, I've been getting "low memory" notices after Ubuntu starts up. When I try clicking on the power button, the whole task bar disapears. Also, when I look at the disk space distribution, it shows only 2.8Gb allocated for my Ubuntu partition. 
Has anybody seen this before and know what's going on?
I appreciate any help.
Cheers

---

### Post by Washer on 2008-07-31
what does it look like from gparted?

---

### Post by prshah on 2008-07-31
> **Leo the Lion said:**
> 
Just recently, I've been getting "low memory" notices after Ubuntu starts up. 
 when I look at the disk space distribution, it shows only 2.8Gb allocated for my Ubuntu partition. 


If you can open a terminal (Application -Accessories -Terminal) open it and post back the outputs to the following commands. If you cannot open a terminal, boot into recovery mode, and give the same commands, but _without_ the word "sudo" ```

df -h
free -m
swapon -s
sudo fdisk -l

```

---

### Post by Leo the Lion on 2008-07-31
Ok, this is what I got from the four different commands on terminal:

```

*******************:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             5.8G  5.5G  8.5M 100% /
varrun               1010M  112K 1009M   1% /var/run
varlock              1010M     0 1010M   0% /var/lock
udev                 1010M  104K 1009M   1% /dev
devshm               1010M     0 1010M   0% /dev/shm
lrm                  1010M   34M  976M   4% /lib/modules/2.6.22-15-generic/volatile
/dev/sda4             8.2G  6.4G  1.9G  78% /dos
/dev/sda1              97G   42G   56G  43% /windows
*******************:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2018        476       1542          0         12        232
-/+ buffers/cache:        230       1787
Swap:          997          0        997
*******************:~$ swapon -s
Filename                                Type            Size    Used    Priority
/dev/sda5                               partition       1021944 0       -1
*******************:~$ sudo fdisk -l
[sudo] password for *********:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x15441544

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12632   101463498+   7  HPFS/NTFS
/dev/sda2           12632       13397     6144000   83  Linux
/dev/sda3           13397       13524     1021952+   f  W95 Ext'd (LBA)
/dev/sda4           13525       14593     8586742+   7  HPFS/NTFS
/dev/sda5           13397       13524     1021952   82  Linux swap / Solaris

```

Thanks for the help.

---

### Post by Leo the Lion on 2008-07-31
Oh, this is what gparted looks like:

---

### Post by prshah on 2008-08-01
> **Leo the Lion said:**
> 
[CODE]
*******************:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             5.8G  5.5G  8.5M 100% /


Clearly, you've run out of space on your linux partition. Here's a couple of things you can try:

1) Move/Delete all files from your /var/cache/apt/archives/; this delete all downloaded .deb files (updates, etc). It will not affect your system; these files are not required once they have been installed.

2) Over a long term, reduce the size of your windows partition by about 5Gb and move+grow your ubuntu partition to take up that space. 

3) You can also consider creating alternate partitions for "/home" "/var/log" and so forth to save space on "/" partition.

4) If you have any large files in your "/home/username" directory, such as video/audio files, consider moving them into your windows partition; you can still access them just fine in ubuntu.

---

### Post by Leo the Lion on 2008-08-01
Thanks a lot. When I installed Ubuntu initially, it was just a trial run, hence the small allocated space. But now, it's the only system I use and apparently I do need to expand.

---

### Post by unutbu on 2008-08-01
If you click Applications>Accessories>Disk Usage Analyzer, you'll get a GUI which displays the size of the directories on your system in a pie-chart fashion.
Although I usually prefer the command-line, I really admire this program. It makes it very easy to find disk hogs.

One potential disk hog that hasn't been mentioned yet is the tracker database. You can remove the tracker cache with

```
rm -rf ~/.cache/tracker
```

---

### Post by Leo the Lion on 2008-08-03
Thank you very much! I found the culprit and it is Thunderbird. Since I have a dual boot system, how can I get Thunderbird to save/direct all my messages and what-not to a folder in my windows partition?

Thanks again.

---

### Post by prshah on 2008-08-04
> **Leo the Lion said:**
> I found the culprit and it is Thunderbird. how can I get Thunderbird to save/direct all my messages to a folder in my windows partition?


This is _highly not recommended_. 

The reason is that if Windows doesn't shutdown cleanly, the partition will not be made available in ubuntu. In this case, you will not be able to access your thunderbird mail/attachments etc at all, maybe not even if you restore access to the windows partition later on.

If you still want to do this, post back for instructions.

---

### Post by Leo the Lion on 2008-08-04
prshah, I'll take your word for it :0). How about expanding the partition that Ubuntu is on. Can it be done using gparted and how?

---

### Post by prshah on 2008-08-04
> **Leo the Lion said:**
> prshah, I'll take your word for it :0). How about expanding the partition that Ubuntu is on. Can it be done using gparted and how?

Yes, sure, you can resize with gparted.

However, you can't do it from a running system. So you have to boot off a live CD.

After booting off the live CD, ensure that your "/" partition (/dev/sda2 in your case) is unmounted; ```
sudo umount /dev/sda2
``` If fact, to be on the safe side, unmount _all_ your partitions and turn off swap if you have more than 230Mb RAM. Use umount for all partitions and for swap use ```
sudo swapoff /dev/sda5
```

At this point you have two options:

1) Quick and painless; I notice from your gparted screenshot that you have about 1Gb of space unallocated immediately following your ubuntu partition; you can merge that into your ubuntu partition without losing any data. Right click /dev/sda2, choose resize, and spread your partition into the unallocated space. You will instantly gain (about) 1Gb space.

2) Complicated and potentially dangerous but recommended; you seem to have a lot of space free on the Windows partition; resize it to reduce it by 5Gb, then move/resize (both operations) your /dev/sda2 partition, gparted will guide you.

Important point: In some cases gparted is slow when resizing partitions, to the point where it seems to have crashed. Personally, I have never had to spend more than 25 mins in any resizing operation, but there are cases where some people have reported it running for 2+ days. (That's an extreme). Don't interrupt gparted; there is a very real possibility of losing data.

Important point 2: I have done so many gparted resizes that I've lost count; and they've all concluded successfully, without any data loss (touch wood). However, your milage may vary; you do this at your own risk. Most people suggest a backup and that's good advice; but I've never run into any problems, and nowadays it has become a matter of such routine that I personally never bother with a backup.

---

### Post by Leo the Lion on 2008-08-04
Thanks again prshah!! I'll give it a shot and post back my results.
All the best.

---

### Post by Victormd on 2008-08-06
> **Leo the Lion said:**
> Thank you very much! I found the culprit and it is Thunderbird. Since I have a dual boot system, how can I get Thunderbird to save/direct all my messages and what-not to a folder in my windows partition?

Thanks again.

This is how my thunderbird profile is setup (and I access thunderbird from both windows and ubuntu and direct both installs to the same folder).

To do this, create a folder on your windows partition (i.e., tbprofile) then from the terminal type:
```
thunderbird -profilemanager
```
click on Create Account, give it a unique name, hit the "choose folder" button and point to the "tbprofile" folder you created. Hit finish, and set the newly created profile as the default. Then, you can copy your files from the current profile to the new profile folder on your windows partition, restart thunderbird and you're done. Once you've checked that everything is working fine, you can either delete or backup the old files.

---

### Post by Victormd on 2008-08-06
+1 for prshah's post. However, I'd resize the windows partition using the native vista partition manager. Gparted is known not to do so well with vista partitions...

---

### Post by Victormd on 2008-08-08
Just another thought, you can do the same for firefox using
```
firefox -profilemanager
```

---

