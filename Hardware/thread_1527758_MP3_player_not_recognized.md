---
title: "MP3 player not recognized"
date: 2010-07-09
forum: Hardware
---

### Post by lile001 on 2010-07-09
I have an MP3 player ( A Sansa Clipp) that was working fine under Ubuntu 9.04.  I could plug it into a USB port, and the computer would recognize it, a window would pop up with the files, etc etc.  

I have just upgraded to 10.04.  Now when I plug in the MP3 player, nothing happens, it doesn't open a window, and doesn't show up in the file system under /media, which is where I think it should be but  I don't know a darn thing about that for sure.  

When I plug it in, the MP3 player wakes up, claims it is connected, and begins charging it's battery, so that end seems to be working.  


  How can I convince my brainbox to talk to it?

---

### Post by lile001 on 2010-07-09
Tried rebooting the computer.  This time, it sees the MP3 player, but will not mount it or open the file.  If I unplug the USB cable, and plug it back in, the computer doesn't see it at all.  How do i mount a device that refuses to be mounted?

---

### Post by lile001 on 2010-07-09
> **lile001 said:**
> Tried rebooting the computer.  This time, it sees the MP3 player, but will not mount it or open the file.  If I unplug the USB cable, and plug it back in, the computer doesn't see it at all.  How do i mount a device that refuses to be mounted?

The adjacent windows box talks to this MP3 player just fine, so it isn't the player.

---

### Post by fryem720 on 2010-08-15
I have the same mp3 player and the same problem.  Did you find a solution?  Where's the vaunted community support on this one?

---

### Post by zapcojake on 2010-08-15
I have the same issue with a Phillips GoGear

code: dmesg |tail
[   41.070186] usb 1-3: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 192 rq 1 len 1000 ret -110
[   44.250182] usb 1-3: usbfs: USBDEVFS_CONTROL failed cmd gvfsd-gphoto2 rqt 192 rq 1 len 1000 ret -110
[   63.080051] usb 1-3: reset high speed USB device using ehci_hcd and address 3
[   76.250061] usb 1-3: usbfs: USBDEVFS_CONTROL failed cmd gvfsd-gphoto2 rqt 192 rq 1 len 1000 ret -110


code: lsusb 
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0424:2514 Standard Microsystems Corp. 
Bus 001 Device 003: ID 0471:207b Philips 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


code: mount |column -t
proc              on  /proc                        type  proc                   (rw,noexec,nosuid,nodev)
none              on  /sys                         type  sysfs                  (rw,noexec,nosuid,nodev)
none              on  /sys/fs/fuse/connections     type  fusectl                (rw)
none              on  /sys/kernel/debug            type  debugfs                (rw)
none              on  /sys/kernel/security         type  securityfs             (rw)
none              on  /dev                         type  devtmpfs               (rw,mode=0755)
none              on  /dev/pts                     type  devpts                 (rw,noexec,nosuid,gid=5,mode=0620)
none              on  /dev/shm                     type  tmpfs                  (rw,nosuid,nodev)
none              on  /var/run                     type  tmpfs                  (rw,nosuid,mode=0755)
none              on  /var/lock                    type  tmpfs                  (rw,noexec,nosuid,nodev)
none              on  /lib/init/rw                 type  tmpfs                  (rw,nosuid,mode=0755)
none              on  /var/lib/ureadahead/debugfs  type  debugfs                (rw,relatime)
/dev/sda1         on  /boot                        type  ext4                   (rw)
/dev/sda4         on  /home                        type  ext4                   (rw)
/dev/sdb2         on  /Music                       type  ext4                   (rw)
/dev/sdb3         on  /data                        type  ext4                   (rw)
/dev/sdb1         on  /backtrack                   type  ext3                   (rw)
binfmt_misc       on  /proc/sys/fs/binfmt_misc     type  binfmt_misc            (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon  on  /home/jake/.gvfs             type  fuse.gvfs-fuse-daemon  (rw,nosuid,nodev,user=jake)


I am on a clean 10.04 that I installed this morning with all the updates applied.  The player appears in Rhythmbox but not as a mounted file system.  It also does not appear in gparted.  Also the player is in MTP mode.  I have tried running mtp-detect but the problem persists.

---

### Post by zapcojake on 2010-08-16
There is a bug filed against gvfs for this problem.  I installed kubuntu-desktop from the repos and am using it to drag and drop files to my player.  I don't know how wide-spread the problem is, you could try the Fedora forums to see id they are experiencing this bug.

---

### Post by lile001 on 2010-08-28
> **zapcojake said:**
> There is a bug filed against gvfs for this problem.  I installed kubuntu-desktop from the repos and am using it to drag and drop files to my player.  I don't know how wide-spread the problem is, you could try the Fedora forums to see id they are experiencing this bug.


So far no joy - has anyone found a workaround?  So far I am moving podcasts to an old windows box to talk to my MP3 player, mucho inconvienient.

---

### Post by lile001 on 2010-09-18
> **lile001 said:**
> So far no joy - has anyone found a workaround?  So far I am moving podcasts to an old windows box to talk to my MP3 player, mucho inconvienient.

Wow!  It sounds liek this is a widespread and pernicious many-hairy-legged bug!  No responses that helped, several users reporting MP3 players not recognized!  Is there anyone with technical competence paying attention to this problem?  Me, I'm not too savvy on what to do about such problems.

---

### Post by lile001 on 2010-09-18
Looks like Windows wins this one.  Sorry Ubuntu, you fail.  I'd sure like to see someone tackle this problem with an answer, or even a question.....

---

### Post by zapcojake on 2010-09-18
Fedora 13 exhibits the same issue for me.  I'd say it's a Gnome problem as Kubuntu 10.04.1 recognizes my player just fine.

---

