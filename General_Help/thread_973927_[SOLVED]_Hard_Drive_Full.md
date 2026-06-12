---
title: "[SOLVED] Hard Drive Full"
date: 2008-11-07
forum: General Help
---

### Post by eadwacer on 2008-11-07
I am continuing to have a problem with my HDD filling up. 

I have searched the forums and followed the advice, to no avail. Originally, I noticed I was at 93% on my main partition, I went through and deleted a bunch of .mp3s and .wavs (not many - I am not a collector) and got down to 90% about a month ago. Then it climbed back to 93%, and after my last power cycle it jumped to 97%.

I have a VM set up, with WinXP as guest, not much installed (e.g. no MS Office), and two snapshots.

I have checked hidden files and logs and caches, and there's lots of stuff (dozens, not thousands of files), but all relatively small.

Running 7.04 Feisty

QUESTION: Does anyone have any suggestions?

///////////////////
UPDATE:Using gksudo nautilus, I got a look at the contents of media/disk and media/disk-1, and they look to be all backup tar files (as also indicated in the output below). I am under the impression that Simple Backup has been writing backup files to both the external HD and to a backup directory under /media/diskxxx. 

NEW QUESTION:if I delete the folders media/disk and media/disk-1, am I likely to do damage to something else on my system? I am new enough to be cautious about deleting a folder called 'disk'

//////////////////
Here's my diagnostics:
Update: using Disk Usage Analyzer, it shows capacity 142GB, used 130GB. However, in the breakdown, it shows that / has used a total of 12GB, if I am reading it correctly (about half of which is the VM). 
No indication of where the other 118GB is.
.........
 df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu-root
                      143G  131G  4.6G  97% /
varrun               1014M  220K 1013M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
procbususb           1014M  120K 1014M   1% /proc/bus/usb
udev                 1014M  120K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   15M  999M   2% /lib/modules/2.6.20-17-generic/volatile
/dev/sda1             222M   39M  172M  19% /boot
/dev/sdb1             147G   54G   87G  39% /media/disk-2

//////////////////
Based on what I found in the forums, I ran
sudo aptitude autoclean
sudo aptitude remove
sudo apt-get autoclean
sudo apt-get autoremove --purge
...which got me about 11MB
/////////////////
 sudo find / -type f -size +100000k
/proc/kcore
/sys/devices/pci0000:00/0000:00:02.0/0000:02:00.0/resource1
/sys/devices/pci0000:00/0000:00:00.0/resource0
/home/sshervais/.VirtualBox/VDI/WinXP.vdi
/home/sshervais/.VirtualBox/Machines/WinXP/Snapshots/{8e96cb34-f8ac-41cb-89e5-b0b78faf63ac}.vdi
/home/sshervais/.VirtualBox/Machines/WinXP/Snapshots/{795c6773-09e5-42fa-943e-8310ca445285}.vdi
/media/disk/backup/2008-10-08_07.35.37.168860.ubuntu.ful/files.tgz
/media/disk/backup/2008-10-09_07.35.39.679456.ubuntu.inc/files.tgz
/media/disk/backup/2008-10-10_07.35.46.733795.ubuntu.inc/files.tgz
/media/disk/backup/2008-10-11_07.35.30.608584.ubuntu.inc/files.tgz
...
/media/disk-1/backup/2008-11-04_07.35.59.279333.ubuntu.inc/files.tgz
/media/disk-1/backup/2008-11-05_07.35.37.263153.ubuntu.inc/files.tgz
/media/disk-1/backup/2008-11-06_07.35.29.502099.ubuntu.ful/files.tgz
/media/disk-1/backup/2008-11-07_01.31.34.583752.ubuntu.inc/files.tgz
/media/disk-2/backup/2008-08-13_13.32.52.043406.ubuntu.ful/files.tgz
/media/disk-2/backup/2008-09-02_07.35.33.172383.ubuntu.inc/files.tgz

Note: disk and disk-1 show as folders with no read permission when I look at them with the file browser in user mode. disk-2 is the current designator for my external drive

---

### Post by eadwacer on 2008-11-19
Just to bring some closure on this. Simple Backup for some reason was writing to the boot drive and not the backup drive. Don't know why, because it started out writing to the external drive just fine. In any event, deleting the backup files on the boot drive freed up 40GB. Of course, those were all my most recent backups. I have turned off SB and am rethinking my backup strategy.

As an aside, having a full disk meant I couldn't write the status files on shutdown, which broke parts of my Opera browser, in that it couldn't init the Mail function. I don't use the Opera mailer, but it also controls the RSS feeds. I worked with the folks over on the Opera forums and ended up renaming my mail directory so's that Opera would create a new one. Worked fine, except that I then had 3,000 feeds to go through.

---

