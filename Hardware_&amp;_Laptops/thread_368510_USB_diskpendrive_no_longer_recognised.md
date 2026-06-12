---
title: "USB disk/pendrive no longer recognised"
date: 2007-02-23
forum: Hardware &amp; Laptops
---

### Post by danzinho on 2007-02-23
Hi

In the past couple of weeks at some point my Ubuntu machine has ceased to automatically recognise USB disks and pen-drives.  It used to just fine.  The hardware works on a Windows machine.  There is communication with the USB disk because I can hear it start up.

The relevant bit of /var/log/syslog (for a 400GB Freecom USB2.0 drive) reads like this

Feb 23 16:35:25 adenine kernel: [17181942.828000] usb 4-5: new high speed USB device using ehci_hcd and address 9
Feb 23 16:35:25 adenine kernel: [17181943.068000] usb 4-5: configuration #1 chosen from 1 choice
Feb 23 16:35:25 adenine kernel: [17181943.068000] scsi5 : SCSI emulation for USB Mass Storage devices
Feb 23 16:35:25 adenine kernel: [17181943.068000] usb-storage: device found at 9
Feb 23 16:35:25 adenine kernel: [17181943.068000] usb-storage: waiting for device to settle before scanning
Feb 23 16:35:30 adenine kernel: [17181948.068000] usb-storage: device scan complete
Feb 23 16:35:30 adenine kernel: [17181948.104000]   Vendor: SAMSUNG   Model: HD400LD           Rev: WQ10
Feb 23 16:35:30 adenine kernel: [17181948.104000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Feb 23 16:35:30 adenine kernel: [17181948.104000] SCSI device sda: 781422768 512-byte hdwr sectors (400088 MB)
Feb 23 16:35:30 adenine kernel: [17181948.108000] sda: Write Protect is off
Feb 23 16:35:30 adenine kernel: [17181948.108000] sda: Mode Sense: 03 00 00 00
Feb 23 16:35:30 adenine kernel: [17181948.108000] sda: assuming drive cache: write through
Feb 23 16:35:30 adenine kernel: [17181948.108000] SCSI device sda: 781422768 512-byte hdwr sectors (400088 MB)
Feb 23 16:35:30 adenine kernel: [17181948.108000] sda: Write Protect is off
Feb 23 16:35:30 adenine kernel: [17181948.108000] sda: Mode Sense: 03 00 00 00
Feb 23 16:35:30 adenine kernel: [17181948.108000] sda: assuming drive cache: write through
Feb 23 16:35:34 adenine udevd-event[10984]: wait_for_sysfs: waiting for '/sys/devices/pci0000:00/0000:00:1d.7/usb4/4-5/4-5:1.0/host5/target5:0:0/5:0:0:0/bus' failed
Feb 23 16:35:37 adenine udevd-event[10984]: wait_for_sysfs: waiting for '/sys/devices/pci0000:00/0000:00:1d.7/usb4/4-5/4-5:1.0/host5/target5:0:0/5:0:0:0/ioerr_cnt' failed
Feb 23 16:35:38 adenine kernel: [17181948.108000]  sda: sda1
Feb 23 16:35:38 adenine kernel: [17181955.688000] sd 5:0:0:0: Attached scsi disk sda
Feb 23 16:35:38 adenine kernel: [17181955.688000] sd 5:0:0:0: Attached scsi generic sg0 type 0

Can anyone help me interpret the error message?

Many thanks
Daniel

---

### Post by Richard Kut on 2007-02-23
Hello danzinho! 

The two error messages are odd. Maybe try another port on the machine? Also, if you are plugging into a USB hub, then try removing the hub and plugging directly into the PC instead.

If that does not work, then run the following command in a terminal:

> gnome-volume-manager

This will start the GNOME module which will recognize the new device and create an icon for it on your desktop. Now try again to insert the USB stick.

Please update this post with your results, and good luck!

---

### Post by danzinho on 2007-02-23
> **Richard Kut said:**
> Hello danzinho! 

The two error messages are odd. Maybe try another port on the machine? Also, if you are plugging into a USB hub, then try removing the hub and plugging directly into the PC instead.

If that does not work, then run the following command in a terminal:



This will start the GNOME module which will recognize the new device and create an icon for it on your desktop. Now try again to insert the USB stick.

Please update this post with your results, and good luck!
Hi Richard

Thanks for the quick reply.  I've tried all the USB ports, front and back.  None leads to recognition of the USB drive.

gnome-volume-manager didn't produce any visible result for me.  Could that be because I'm in KDE?  I still see the same error messages in /var/log/syslog.

Any more ideas?  Thanks!

Daniel

---

### Post by silentb on 2007-02-23
Does your USB drive work when booting off of the Kubuntu cd?

---

### Post by danzinho on 2007-02-23
Thanks for the reply.  I don't have immediate access to the CD (it was borrowed from a friend).  Is there any other diagnostic I could run?

Daniel

---

### Post by Richard Kut on 2007-02-23
Plug in the USB drive and then post back here the output of these commands:

sudo fdisk -l 

df -h 

cat /etc/fstab

Also, what version of Kubuntu are you using?

---

### Post by danzinho on 2007-02-26
> **Richard Kut said:**
> Plug in the USB drive and then post back here the output of these commands:

sudo fdisk -l 

df -h 

cat /etc/fstab

Also, what version of Kubuntu are you using?

Here goes

sudo fdisk -l 

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       13999   112446936   83  Linux
/dev/hda2           14000       14593     4771305    5  Extended
/dev/hda5           14000       14593     4771273+  82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       13954   112085473+  83  Linux
/dev/hdb2           13955       14593     5132767+   5  Extended
/dev/hdb5           13955       14593     5132736   82  Linux swap / Solaris

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       48641   390706232    b  W95 FAT32

df -h 

Filesystem            Size Used Avail Use% Mounted on
/dev/hda1             106G   55G   46G  55% /
varrun               1014M   92K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
procbususb             10M  140K  9.9M   2% /proc/bus/usb
udev                   10M  140K  9.9M   2% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M  8.0M 1006M   1% /lib/modules/2.6.17-11-generic/volatile
/dev/hdb1             106G   81G   19G  81% /disk2

cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=3177838e-e6e2-4ff7-8907-ebd0be01cd26 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=1b1a66c0-8a96-4ac8-a826-e94dbd18a9ac none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
# /dev/hdb1
/dev/hdb1 /disk2               ext3    defaults  0       2

My Kubuntu version is 6.10.  It has been regularly updated, although the update system seems to have got in a tangle recently.  I think the origin of that was an attempt to install some new python-related material that failed because of improper pre- or post-installation scripts.  I didn;t get to the bottom of that but, on the face of it, it seems unconnected to this issue.

Many thanks again

Daniel

---

### Post by Richard Kut on 2007-02-26
Hi Daniel. This line appears to indicate that your USB stick is recognized:

> Device Boot Start End Blocks Id System
/dev/sda1 1 48641 390706232 b W95 FAT32


Have you tried looking at the /media folder to see if there is a mount point defined there for the USB stick? If there does exist a mount point, then try to cd into that directory and ls the files there.

Also, if you have problems using apt-get then that needs to be resolved, since that might contribute in some way.

---

### Post by danzinho on 2007-02-27
> **Richard Kut said:**
> Hi Daniel. This line appears to indicate that your USB stick is recognized:



Have you tried looking at the /media folder to see if there is a mount point defined there for the USB stick? If there does exist a mount point, then try to cd into that directory and ls the files there.

Also, if you have problems using apt-get then that needs to be resolved, since that might contribute in some way.

Hi Richard

Yes, it's encouraging that the disk actually appears.  There is no entry in /media for the drive, though.  
Looking in more detail at the apt-get issue, it may be related.

apt-get upgrade
gives me

The following packages have unmet dependencies.
  libgnomevfs2-0: Depends: libgnomevfs2-common (= 2.16.1-0ubuntu7) but 2.16.1-0ubuntu6 is installed
  libgnomevfs2-extra: Depends: libgnomevfs2-common (= 2.16.1-0ubuntu7) but 2.16.1-0ubuntu6 is installed

vfs seems to be virtual file system so it makes sense

The trouble is that apt-get -f install fails

Preparing to replace libgnomevfs2-common 2.16.1-0ubuntu6 (using .../libgnomevfs2-common_2.16.1-0ubuntu7_all.deb) ...
Unpacking replacement libgnomevfs2-common ...
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/sbin/update-gconf-defaults", line 11, in ?
    import os
ImportError: No module named os
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/sbin/update-gconf-defaults", line 11, in ?
    import os
ImportError: No module named os
dpkg: error processing /var/cache/apt/archives/libgnomevfs2-common_2.16.1-0ubuntu7_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/sbin/update-gconf-defaults", line 11, in ?
    import os
ImportError: No module named os
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libgnomevfs2-common_2.16.1-0ubuntu7_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
daniel@adenine:~/teaching/Biol727_comm_skills$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
  libgnomevfs2-0: Depends: libgnomevfs2-common (= 2.16.1-0ubuntu7) but 2.16.1-0ubuntu6 is installed
  libgnomevfs2-extra: Depends: libgnomevfs2-common (= 2.16.1-0ubuntu7) but 2.16.1-0ubuntu6 is installed
E: Unmet dependencies. Try using -f.


All this seems to do with an inadequate or broken Python installation.
Any thoughts, or ideas as to where to go next for help?

Thanks again

Daniel

---

### Post by Richard Kut on 2007-02-27
Hi Daniel. I believe that you may have pinpointed the root cause of the problem! Definitely there are packages that are in distress.

It looks like the GNOME Virtual File System (VFS) is causing the grief (my best guess).

You mentioned that you are using Kubuntu 6.10. Would it be alright to remove the Ubuntu (GNOME environment) completely, and try to mount the USB stick using the Kubuntu (KDE environment) tools instead?

Don't worry, because you can always reinstall GNOME later by doing:

> sudo aptitude install ubuntu-desktop

If you are OK with dropping GNOME, then follow the directions found here:

[http://www.psychocats.net/ubuntu/purekde]("http://www.psychocats.net/ubuntu/purekde")

and then stop and restart the computer, just to be sure that all previously running GNOME daemons have stopped. Then try to insert the USB stick again. Remember to run dmesg to check the system messages after inserting the stick. Please update the post with your feedback. Good luck!

---

### Post by danzinho on 2007-02-28
> **Richard Kut said:**
> Hi Daniel. I believe that you may have pinpointed the root cause of the problem! Definitely there are packages that are in distress.

It looks like the GNOME Virtual File System (VFS) is causing the grief (my best guess).

You mentioned that you are using Kubuntu 6.10. Would it be alright to remove the Ubuntu (GNOME environment) completely, and try to mount the USB stick using the Kubuntu (KDE environment) tools instead?

Don't worry, because you can always reinstall GNOME later by doing:



If you are OK with dropping GNOME, then follow the directions found here:

[http://www.psychocats.net/ubuntu/purekde]("http://www.psychocats.net/ubuntu/purekde")

and then stop and restart the computer, just to be sure that all previously running GNOME daemons have stopped. Then try to insert the USB stick again. Remember to run dmesg to check the system messages after inserting the stick. Please update the post with your feedback. Good luck!

Dear Richard

Thanks for these ideas.  Sounds silly, but I appear to actually be running GNOME after all, despite having installed KDE at some point (early enough that I don;t remember exactly how).  I've never had the choice of KDE or GNOME when logging in (like I have before) which leads me to doubt that KDE is installed properly.  Of course, I wouldn't like to remove GNOME and be left with a dysfunctional KDE.  The trouble is that when I try to reinstall/check KDE I get the same apt-get/aptitude problems to do with the vfs libraries.  I feel like I'm stuck.

Daniel

---

### Post by Richard Kut on 2007-02-28
Hi Daniel. Alright, in that case, how about re-installing gnome-vfs?

---

### Post by danzinho on 2007-03-01
> **Richard Kut said:**
> Hi Daniel. Alright, in that case, how about re-installing gnome-vfs?

Hi Richard

Yes, but the systems for de/re/installation are broken (that's what got me in this mess!).  It seems to be an issue with Python from the 'ImportError: No module named os' errors in the output below

Any more ideas?

Thanks

Daniel

daniel@adenine: sudo aptitude reinstall gnome-vfs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Building tag database... Done      
Couldn't find package "gnome-vfs".  However, the following
packages contain "gnome-vfs" in their name:
  libgnome-vfs-dev libgnome-vfs-common libgnome-vfsmm-2.6-dev gnome-vfs-extfs libgnome-vfs0 libgnome-vfsmm-2.6-1c2a 
The following packages are BROKEN:
  libgnomevfs2-0 libgnomevfs2-extra 
The following packages have been kept back:
  apt apt-utils firefox firefox-gnome-support libgnomevfs2-common libnspr4 libnss3 
0 packages upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
Need to get 651kB of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  libgnomevfs2-0: Depends: libgnomevfs2-common (= 2.16.1-0ubuntu7) but 2.16.1-0ubuntu6 is installed and it is kept back.
  libgnomevfs2-extra: Depends: libgnomevfs2-common (= 2.16.1-0ubuntu7) but 2.16.1-0ubuntu6 is installed and it is kept back.
Resolving dependencies...
The following actions will resolve these dependencies:

Upgrade the following packages:
libgnomevfs2-common [2.16.1-0ubuntu6 (edgy-proposed, now) -> 2.16.1-0ubuntu7 (edgy-updates)]

Score is 0

Accept this solution? [Y/n/q/?] Y
The following packages have been kept back:
  apt apt-utils firefox firefox-gnome-support libnspr4 libnss3 
The following packages will be upgraded:
  libgnomevfs2-common 
1 packages upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Need to get 0B/651kB of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
(Reading database ... 140972 files and directories currently installed.)
Preparing to replace libgnomevfs2-common 2.16.1-0ubuntu6 (using .../libgnomevfs2-common_2.16.1-0ubuntu7_all.deb) ...
Unpacking replacement libgnomevfs2-common ...
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/sbin/update-gconf-defaults", line 11, in ?
    import os
ImportError: No module named os
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/sbin/update-gconf-defaults", line 11, in ?
    import os
ImportError: No module named os
dpkg: error processing /var/cache/apt/archives/libgnomevfs2-common_2.16.1-0ubuntu7_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/sbin/update-gconf-defaults", line 11, in ?
    import os
ImportError: No module named os
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libgnomevfs2-common_2.16.1-0ubuntu7_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of libgnomevfs2-extra:
 libgnomevfs2-extra depends on libgnomevfs2-common (= 2.16.1-0ubuntu7); however:
  Package libgnomevfs2-common is not installed.
dpkg: error processing libgnomevfs2-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-0:
 libgnomevfs2-0 depends on libgnomevfs2-common (= 2.16.1-0ubuntu7); however:
  Package libgnomevfs2-common is not installed.
dpkg: error processing libgnomevfs2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-bin:
 libgnomevfs2-bin depends on libgnomevfs2-0 (>= 2.15.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnomevfs2-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ekiga:
 ekiga depends on libgnomevfs2-0 (>= 2.15.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing ekiga (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgnomevfs2-extra
 libgnomevfs2-0
 libgnomevfs2-bin
 ekiga

---

### Post by Richard Kut on 2007-03-01
Hi Daniel. I am sorry to say that I am out of ideas. Maybe someone else in the forums that is a bit more experienced than me in these matters might see this post and comment. Otherwise, you could create a new post referencing this one, and that might attract attention.

I am really sorry that I could not be of more help to you. I hope that you find a solution. If you do, it would probably be a good idea to post the fix here so that this thread gets closure.

Good Luck!

---

