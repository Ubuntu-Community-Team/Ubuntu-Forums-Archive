---
title: "Trouble with external USB harddrive (Seagate FreeAgent) [SOLVED]"
date: 2007-07-07
forum: Hardware &amp; Laptops
---

### Post by trolav on 2007-07-07
Posting here for personal reference, and maybe save some other users some headache.
The post might need some cleanup.

**References:**
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/61235](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/61235)
[http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221)

**System:**
Ubuntu 7.04 Feisty Fawn

**Hardware:**
External USB harddrive, Seagate FreeAgent 500GB

**Symptoms**
I noticed lots of I/O errors on my nice new Seagate FreeAgent 500GB, which I first though look like filesystem errors. With JFS filesystem the dmesg error looked like this:

[INDENT]sd 6:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Additional sense: Logical unit not ready, initializing command required
end_request: I/O error, dev sde, sector 450262279
metapage_read_end_io: I/O error
[/INDENT]
Trying to reformat with EXT3 gave a little different error:

[INDENT]sd 6:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Additional sense: Logical unit not ready, initializing command required
end_request: I/O error, dev sde, sector 976767935
Buffer I/O error on device sde1, logical block 488383936
[/INDENT]

**Solution**
As described in the reference bug report:

Create a new UDEV rule (using your preferred method):

Example (type in Terminal):
[INDENT]sudo gedit /etc/udev/rules.d/85-usb-hd-fix.rules[/INDENT]
and enter
[INDENT]BUS=="scsi", SYSFS{vendor}=="WD", RUN+="/usr/bin/usbhdfix %k"[/INDENT]
and save the file.
**Note:** The vendor "WD" have to be replaced with the correct one, in my case "Seagate". Check the second reference link to find the correct one on your system.

Then create the shell script to be run when harddrive is detected:
Still in Terminal, type:
[INDENT]sudo gedit /usr/bin/usbhdfix[/INDENT]
and enter
[INDENT]#!/bin/bash
echo 1024 > /sys/block/$1/device/max_sectors
echo 1 > /sys/block/$1/device/scsi_disk:*/allow_restart[/INDENT]
and save the file.

Make the script executable:
Still in Terminal, enter
[INDENT]sudo chmod 0755 /usr/bin/usbhdfix[/INDENT]

That's it!
It solved all problems for me :)

---

### Post by reclusivemonkey on 2007-07-08
Thanks for posting your solution and for using the [SOLVED] thread tool. Glad you got it fixed =]

---

### Post by p_ano on 2007-07-11
i've been having trouble with my freeagent, but it's a little different than the problems the rest of you guys have been having.      it works fine for hours, but then one or two directories will disappear.    unmounting and remounting makes the directories reappear.     the drive worked fine in windows, so i assumed it must be a problem with linux and ntfs.   i reformatted it as fat32 and still had the same problem.    finally, i tried formatting it as ext3--still having the same problem.

trying this fix now....  fingers crossed...

---

### Post by p_ano on 2007-07-12
36 hours later and my freeagent is running like a charm.    still too early to get excited, but it seems like this fix has resolved my problems.

so, what exactly does "allow_restart" do?   my guess is that it does a quick scan to see if the drive is responding, and if it isn't, then remounts the drive.    i could be way off-base.

---

### Post by p_ano on 2007-07-14
3 days later and still no problems.      I feel confident that this issue is truly SOLVED.

thanks so much trolav.

---

### Post by LukeKendall on 2007-07-21
> **p_ano said:**
> 3 days later and still no problems.      I feel confident that this issue is truly SOLVED.

thanks so much trolav.

I'm having slightly similar problems with my Seagate Freeagent 500GB drive: the drive seems to work fine (e.g. I copied 100GB data to it), but after it goes idle, it goes into standby mode.  I can use the scsitools command 
```

scsi-spin -u /dev/sdb
# or
scsi-spin -u -f /dev/sdb
# (if scsi-spin thinks the device is properly mounted)
```
to force it to spin up out of standby mode (though the device name in /sys increments).

But my problem is that if I try to create the allow_restart file (as root) I just get "Permission denied":
```
root@potter:~# ls /sys/block/sdb/device/scsi_disk:4:0:0:0/
cache_type  device  FUA  uevent
root@potter:~# echo 1> /sys/block/sdb/device/scsi_disk:4:0:0:0/allow_restart
bash: /sys/block/sdb/device/scsi_disk:4:0:0:0/allow_restart: Permission denied
root@potter:~# ls /sys/block/sdb/device/scsi_disk:4:0:0:0/
cache_type  device  FUA  uevent
root@potter:~# echo 1 > /sys/class/scsi_disk/4\:0\:0\:0/allow_restart
bash: /sys/class/scsi_disk/4:0:0:0/allow_restart: Permission denied
```

Would this be because "allow_restart" is a feature of a newer kernel than what I'm running (2.6.17-11)?

luke

---

### Post by LukeKendall on 2007-07-21
> **LukeKendall said:**
> I'm having slightly similar problems with my Seagate Freeagent 500GB drive: the drive seems to work fine (e.g. I copied 100GB data to it), but after it goes idle, it goes into standby mode.  
... stuff deleted ...

Would this be because "allow_restart" is a feature of a newer kernel than what I'm running (2.6.17-11)?

luke

After a little more reading it seems that the allow_restart option was only available for IBM arrays at first, then for Maxtor, and only *later* permitted (or is in the process of being permitted?) for all kinds of scsi discs.  So yes, I think allow_restart needs kernel 2.6.21 or later.

For me, I can workaround by becoming root and then doing a umount/scis-spin/mount sequence like so:
```

root@potter:~# ls /data
ls: reading directory /data: Input/output error
root@potter:~# scsi-spin -u /dev/sdb
scsi-spin: device already in use (mounted partition)
root@potter:~# umount /dev/sdb1
root@potter:~# scsi-spin -u /dev/sdb
root@potter:~# mount /dev/sdb1
root@potter:~# ls /data
audio     codecs  gentoo         lost+found  old-logs  var
cdimages  emerge  linux-src      news        tmp

```

---

### Post by TKill on 2007-07-30
I don't know why trolav's solution worked for you. For me, %k evaluates to sda1 (or sdb1), and /sys/block/sda1 does not exist. However, /sys/block/sda does, so changing the line in usbhdfix to ```
echo 1 > /sys/block/${1:0:3}/device/scsi_disk:*/allow_restart
```
does the trick for me (${1:0:3} trims "sda1" down to "sda"). Just thought there might be someone else benefiting from this...

---

### Post by RobertHentosh on 2007-08-01
> **TKill said:**
> I don't know why trolav's solution worked for you. For me, %k evaluates to sda1 (or sdb1), and /sys/block/sda1 does not exist. However, /sys/block/sda does, so changing the line in usbhdfix to ```
echo 1 > /sys/block/${1:0:3}/device/scsi_disk:*/allow_restart
```
does the trick for me (${1:0:3} trims "sda1" down to "sda"). Just thought there might be someone else benefiting from this...

Actually, it will execute the script multiple times with the udev rule that is being used. In my case it excuted four times with the parameters "6:0:0:0", "sg0', "sdb" and "sdb1".  This will not really cause harm since those subdirectories don't exist under /sys/block, but it is a hack and explains the reason why it works for others, since the sdb works and the others fail with file not found. (You can verify my findings by changing the /usr/bin/usbhdfix script to include "echo >> /tmp/usbhdfix-output" and you will see 4 or more lines depending on how the usb drive was partitioned)

A better solution would be to change the udev rule in 85-usb-hd-fix.rules to:

```

BUS=="scsi",KERNEL=="sd?",SYSFS{vendor}=="Seagate",SYSFS{model}=="FreeAgentDesktop",RUN+="/usr/bin/usbhdfix %k"

```

And leave the usbhdix script as is:

```

#!/bin/bash
echo 1024 > /sys/block/$1/device/max_sectors
echo 1    > /sys/block/$1/device/scsi_disk:*/allow_restart

```

---

### Post by TKill on 2007-08-01
> **RobertHentosh said:**
> Actually, it will execute the script multiple times with the udev rule that is being used. In my case it excuted four times with the parameters "6:0:0:0", "sg0', "sdb" and "sdb1".  This will not really cause harm since those subdirectories don't exist under /sys/block, but it is a hack and explains the reason why it works for others, since the sdb works and the others fail with file not found. (You can verify my findings by changing the /usr/bin/usbhdfix script to include "echo >> /tmp/usbhdfix-output" and you will see 4 or more lines depending on how the usb drive was partitioned)


Right you are, but my rule doesn't execute the script several times:
```

BUS=="scsi", KERNEL=="sd?1", SYSFS{vendor}=="Seagate", SYSFS{model}=="FreeAgentDesktop", SYSFS{rev}=="100D", SYMLINK+="usbhd1", RUN+="/usr/local/bin/usbhdfix %k"

```
The idea was that I also wanted to create a symlink that I could enter into /etc/fstab, since the disk sometimes comes up as sda1 and sometimes sdb1. I see clearly now why it worked for everyone else, but not for me.. #-o

The most proper solution is maybe to have two udev rules then; one for executing the script and one for creating the symlink? That is:

```

BUS=="scsi", KERNEL=="sd?", SYSFS{model}=="FreeAgentDesktop", RUN+="/usr/local/bin/usbhdfix %k"
BUS=="scsi", KERNEL=="sd?1", SYSFS{model}=="FreeAgentDesktop", SYMLINK+="usbhd1"

```

By the way, why would we like to have this line in the script?
```

echo 1024 > /sys/block/$1/device/max_sectors

```
I seem to be getting a lot of disk errors (the log says "mounting disk with errors. running e2fsck is recommended", or something, when I mount it). I have not added this line in the script, but in my mind, adding it couldn't make the case better, rather the opposite. Am I right?

---

### Post by pingpongboss on 2007-09-02
thanks for the solution!

---

### Post by alexicon on 2007-09-08
nice just tried tkill's solution and seems to be working wonders. no time outs or disappearing files and folders :)

thanks guys!

---

### Post by antrixangler on 2007-10-27
> **TKill said:**
> Right you are, but my rule doesn't execute the script several times:
The idea was that I also wanted to create a symlink that I could enter into /etc/fstab, since the disk sometimes comes up as sda1 and sometimes sdb1. I see clearly now why it worked for everyone else, but not for me.. #-o


Instead of messing with symlinks, you can use the UUID property in /etc/fstab. Here's my case:
```

antrix@cellar:~$ vol_id /dev/sdc1
ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
ID_FS_UUID=07eb2c81-516d-4ec6-949d-5237e469fa2b
ID_FS_UUID_ENC=07eb2c81-516d-4ec6-949d-5237e469fa2b
ID_FS_LABEL=freeagent
ID_FS_LABEL_ENC=freeagent
ID_FS_LABEL_SAFE=freeagent
antrix@cellar:~$ grep freeagent /etc/fstab
UUID=07eb2c81-516d-4ec6-949d-5237e469fa2b /mnt/freeagent      ext3  defaults        0       2

```

---

### Post by VoyeurOne on 2007-10-27
The first solution worked great on Feisty but I just moved to Gutsy and now I get this error

/sys/block//device/scsi_disk:*/allow_restart: No such file or directory

Any Ideas?

---

### Post by VoyeurOne on 2007-10-29
interesting, the original solution worked on my first install of Feisty which was an upgrade from the previous release <edgy>.  Now I find out that none of the solutions will work on gusty, clean install, or the version of Feisty I am running now,  also a clean install.   I wonder if the patch has dependencies on  a package or a file I dragged over from Edgy when I did the Feisty upgrade ?  

At any rate the original post <patch> worked perfectly for me from day one and will no longer work on the clean install of Feisty or the clean install of Gusty, which is a bit of a laugh seeing as I returned to Feisty after realizing that I no longer controlled my external hard drives .......

Maybe my little observation will get someone thinking in a different tangent, I would really like to get my external hard drive back.

---

### Post by dn* on 2007-11-28
Can anyone confirm the status of this drive in relation to Gutsy? I'm thinking of getting one tomorrow. Also, am I right in thinking that formatting it into ext3 works fine?

---

### Post by mwshook on 2007-12-02
dn: My wife just got one of these for her XP computer. I tried plugging it in to my feisty machine, and it only recognized it as read-only. I thought "well, I've been meaning to upgrade to gutsy anyway."

When I did the upgrade, it no longer recognizes the drive at all.

---

### Post by dn* on 2007-12-03
I went ahead and got one of them and attached it to my home server, but I'm having the time-out, remounting as read-only issue now. I've found that unmounting it and mounting it again fixes the problem.

I just applied this thread's solution using the same vendor name and wotnot as I have the same drive, we'll see how it goes! :)

---

### Post by Topfs on 2007-12-09
Wonderfull! This seems to have solved all my problems with this harddrive!!
I got I/O errors in both nautilus and terminal if the harddrive spun down to powersave.
Well I haven't tried this fix or a very long time as of yet but it has spun down and flawlessly spinned up again.. Well it seems to work. 
I have NTFS on the harddrive so for those of you that see this thread it works for NTFS to.
Thank you for the fix.

---

### Post by Rukkot on 2007-12-09
IT seems something is moving into kernel part related to USB hard disks issues. I hope we'd see improvements in the following version:
[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=f09e495df27d80ae77005ddb2e93df18ec24d04a](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=f09e495df27d80ae77005ddb2e93df18ec24d04a)

---

### Post by ricemark20 on 2007-12-19
I used: ```
sudo mount /dev/sdc
```

It gives an error message, but if you go to >PLACES>COMPUTER and mount the drive from there, everything works

---

### Post by kraymore on 2008-01-26
I am not sure if this fix will work for me.  maybe you could tell me if that is the case.  

i have a seagate NCQ 500GB sata hd in a external enclosure.  i have found that i can browse and read files (alot of music files and directories) however after sometime has passed i might click into an album folder and either it cannot display its contents or the file icons for system playable sound files will turn to silver paper leafs instead of their sound icon and they will not be playable.  usuually happens after some time of browsing through my music and playing files randomly.  i dont know how long it was between when it stopped working and its previous success though.  

thank you

---

### Post by yonexFactory on 2008-01-29
Thank you! This worked perfectly.

---

### Post by wojtekz on 2008-02-24
> **VoyeurOne said:**
> The first solution worked great on Feisty but I just moved to Gutsy and now I get this error

/sys/block//device/scsi_disk:*/allow_restart: No such file or directory

Any Ideas?

I have two Seagate FreeAgent Pro drive running on Gutsy. This udev rule works for me:

SUBSYSTEM=="block",KERNEL=="sd?",SYSFS{model}=="FreeAgent Pro",RUN+="/usr/local/bin/usbhdfix %k"

My usbhdfix script looks as follows:

#!/bin/bash
echo 1 > /sys/block/$1/device/scsi_disk:*/allow_restart

Please note that it has to be a "bash" script and not "sh", otherwise "*" won't be expanded.

---

### Post by bruncio on 2008-03-14
I've tried the solution from this page:

http://www.theinquirer.net/gb/inquirer/news/2007/12/11/seagate-issues-workaround-linux"]http://www.theinquirer.net/gb/inquirer/news/2007/12/11/seagate-issues-workaround-linux

with one little change.The exact lines was:

sudo sdparm --clear STANDBY -S /dev/sdb

Note the -S option - it saves the cleared STANDBY flag as the default one.
It worked fine for me - also when connecting the drive to the other Linux system the STANDBY flag was cleared.

---

### Post by MEGAMANULTIMATE on 2008-04-09
I'm confused as to what step to follow first...I'm running Gutsy. Is there a step-by-step guide for this process? Or should I try the tips on that last internet link?

---

### Post by cyborg on 2008-04-11
Will this solution stop the restarting process?

So will this solution shut the standby mode down?
I dont want to loose this feature.

Or... can I somehow execute this command on drive errors:
sudo sdparm --command=start /dev/sdX

??

---

### Post by muximus on 2008-04-22
I have a FreeAgentDesktop 500GB. 

I also could not get the fix to work on my gutsy box, so i tried the instructions in this thread:
[http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221)

The problem was that the env. variable SYSFS does not seem to exist in gutsy. (see the output of the following command)
```
udevinfo -a -p $(udevinfo -q path -n /dev/sdX)
```

The following udev rule worked for me

/etc/udev/rules.d/85-usb-hd-fix-rules:
```


ATTRS{product}=="FreeAgentDesktop",  RUN+="/usr/bin/usbhdfix %k"


```

---

