---
title: "Scan for and mount eSATA external hard disk after boot"
date: 2008-06-26
forum: Hardware
---

### Post by Ng Oon-Ee on 2008-06-26
Hi all,

I have an external eSATA connection hard disk which I connect by a converter to a SATA port on my motherboard. Currently I have to remember to have it turned on every time I reboot my system (currently on Hardy Heron, Ubuntu), after which I can unmount it, send it to sleep using...
```
hdparm -Y /dev/sda
```
...and then power it off. When I want to use it (its only for weekly backups and some DVD images I don't want to bother burning) I turn it on and remount it.

The reason I have to have it powered on boot is so that the kernel recognizes the hard disk initially (I assume its the kernel, actually, from reading up on google results). If I boot without having it on, I'm unable to detect the hard disk using the usual fdisk/blkid/what-have-you commands. I've tried the scsiadd available in the repos, no joy there either.

So the question I have is, is there any method allowing me to rescan for my SATA hard disks? I know that in Windows if the hard disk was not on on bootup, when I do turn it on the system freezes for half a second (I assume some type of intterupt is causing a rescan) after which I can see the partition with no problem, so I'm assuming my MB and external hard disk support this kind of usage.

Appreciate any help given:)

---

### Post by Ng Oon-Ee on 2008-06-27
Bump, any ideas?

---

### Post by Ng Oon-Ee on 2008-06-29
Bump, no-one's ever heard of this before? :)

---

### Post by Ng Oon-Ee on 2008-06-29
Ah, from some in-depth googling I've found some things that seem to work.

Firstly, to scan a scsi bus (in my case its bus 1) there's a few ways. This assumes you're logged in as root:-

```
echo "- - -" > /sys/class/scsi_host/host1/scan
```
or
```
echo "scsi add-single-device 1 0 0 0" > /proc/scsi/scsi
```

host1 and the number first number after add-single-device indicate your scsi bus number, easiest way to find it is by rebooting your system with the external hard disk plugged in and running:-

```
cat /proc/scsi/scsi
```

The first two commands assume you're logged in as root (adding sudo in front of them won't work). However, if you want to use sudo in any case, you need to pipe the commands using tee, as mentioned in [THIS THREAD]("http://ubuntuforums.org/showthread.php?t=412329").

```
echo "- - -" | sudo tee -a /sys/class/scsi_host/host1/scan
```
or
```
echo "scsi add-single-device 1 0 0 0" | sudo tee -a /proc/scsi/scsi
```

As for unplugging, I can just disable using remove-single-device instead of add-single-device above, but that works just like unplugging the drive directly, even if files are being read/written. Better way is to send it to sleep and then remove it.

```
sudo hdparm -Y /dev/sdb
echo "scsi add-single-device 1 0 0 0" | sudo tee -a /proc/scsi/scsi
```

Of course, /dev/sdb depends on where your hard disk has been mounted.

If anyone is familiar with methods of achieving the above using .sh/BASH scripts, please do share =). Kind of a pain to do this manually, though its MUCH better than rebooting to use my external.

---

### Post by Günter Burgstaller on 2008-08-19
What worked for me:

apt-get install scsitools
rescan-scsi-bus.sh

---

### Post by TheguywholikesLINUX on 2009-04-15
I also have the same problem, which can now be solved, but I would also appreciate it if someone could write a shell script that can auto mount my external hard drive without me having to type that command, and possibly run my backup program at the same time. And when the backup is complete if it could unmount and turn off (actually i don't think that is possible so sleep instead.) In fact I may be able to do it if someone knows a command or something, windows has to have some way of knowing when a drive is plugged in. 

Thanks!

---

### Post by ruehara on 2009-05-22
> **TheguywholikesLINUX said:**
> I also have the same problem, which can now be solved, but I would also appreciate it if someone could write a shell script that can auto mount my external hard drive without me having to type that command, and possibly run my backup program at the same time. And when the backup is complete if it could unmount and turn off (actually i don't think that is possible so sleep instead.) In fact I may be able to do it if someone knows a command or something, windows has to have some way of knowing when a drive is plugged in. 

Thanks!


You could try something like this.

In my system, I added my external eSata to /etc/fstab with[INDENT]/dev/sdb1 ext3 relatime,error

[/INDENT]The next step is to mount this to a mount point. Because I may not always wish to access this as root or sudo, I changed permissions on /mnt to rwxrwxrwx and created a mountpoint under this which I called u, also rwxrwxrwx and created a symbolic link to the root directory with[INDENT]ln -s /mnt/u u

[/INDENT]The script then would be something called say backupall which I can keep in my home directory and would look something like[INDENT]mount /dev/sdb1 /u                                     #mount the eSata drive
cd /                                                                                #change to the top level directory
tar zcvf /u/backup.tgz *                        #create a compressed tarball of the
                                                                                            #entire machine in the eSata drive
sync                                                                               #complete all remaining disc writes
umount /dev/sdb1                                                    #cleanly unmount external drive
telinit 0                                                                     #shut down the PC (if you want to)

[/INDENT]You can kick this script off before you go to bed and it will do your full system backup and shut down your PC when it's done. Because I do a lot of unattended transfers, I time this to happen at 1am when all my transfers are done with [INDENT]at 1am < ./backupall

[/INDENT]If it's to be a regular event, you could consider adding it into your crontab

---

### Post by TheguywholikesLINUX on 2009-05-26
Hi, thanks for your post ruehara, I think I will incorporate some of your code, I have just modded my /etc/fstab however, I have a problem in that if I turn my hdd on after boot it doesn't appear in /dev/sd* and I would like it to appear there and auto mount if I turn it on after boot.

---

### Post by gcbzzzz on 2010-10-01
> **Ng Oon-Ee said:**
> 
```
echo "- - -" | sudo tee -a /sys/class/scsi_host/host1/scan
```


Thank you Ng Oon-Ee! that did the trick perfectly.

everyone, remember that the 1 in host1 must be changed depending on your sata port, start counting from 0.

to unplug i can't use hdparm -Y or --idle-immediate or --idle-unload because my driver or my external sata enclosure does not support it. But if it worked, then you can simply remove the driver/turn it off, and re-run the scan command.

---

### Post by quartarian on 2011-09-30
> **gcbzzzz said:**
> Thank you Ng Oon-Ee! that did the trick perfectly.

everyone, remember that the 1 in host1 must be changed depending on your sata port, start counting from 0.

to unplug i can't use hdparm -Y or --idle-immediate or --idle-unload because my driver or my external sata enclosure does not support it. But if it worked, then you can simply remove the driver/turn it off, and re-run the scan command.

Thanks guys! This worked for me: 
```

sudo -i 
echo "- - - " > /sys/class/scsi_host/host9/scan

```

To help fellow noobs trouble shooting their wonky eSata mounts, here are some commands that helped me:
```

dmesg

```
This will give you a whole bunch of fun info from the kernel which lets you see the issues it is having with your drive, among a lot else I might add. This was my first real hardware troubleshooting I've needed to do so this was all new to me and very helpful to find.:)

To find the line we need within the log, use this command:
```

dmesg | grep "reset failed, giving up"

```
You should see something like this:
```
[   65.659876] ata10: reset failed, giving up
```
or in my case:
```
[   65.659876] ata10: reset failed, giving up
[  125.772638] ata10: reset failed, giving up
[  194.989927] ata10: reset failed, giving up
[  255.182343] ata10: reset failed, giving up
[ 1119.421422] ata10: reset failed, giving up
[ 1179.584068] ata10: reset failed, giving up
[ 1263.306857] ata10: reset failed, giving up

```
To get my drive to work, after each "reset failed, giving up" message, I turned off my eSata drive and ran 
```

echo "- - - " > /sys/class/scsi_host/host9/scan

```
until it mounted. (Normal sudo wasn't working for me so I used sudo -i.) This apparently forces the kernel to re-scan the drive which it gave up on.
***NOTE:** the host number = (10 - 1) from the line "ata**10**: reset failed, giving up" message.*

Lastly, to make the whole process much more exciting, use this command:
```

watch -n 1 "dmesg | tail -30"

```
This will keep refreshing dmesg every second for you and limit the lines to the last 30. See, exciting! Well, at least it will be once you get your drive working! :razz:

---

