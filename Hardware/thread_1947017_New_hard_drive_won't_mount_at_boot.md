---
title: "New hard drive won't mount at boot"
date: 2012-03-25
forum: Hardware
---

### Post by dj_sefault on 2012-03-25
I'm having problems geeting my Ubuntu 10.04LTS server to mount a new sata hard drive at boot time.  I've verified the drive works fine on another machine, and my server is otherwise working fine.  The motherboard is an Abit IP35 Pro with 6 sata ports.  I have hard drives on ports 1, 2, 4, and 5 (all JBOD), with a DVD drive on port 3.  I'm trying to hook up a brand new WD Caviar Black 1TB to port 6.

I realize the following part is not related to Ubuntu, but I'm trying to give all the symptoms: When I hook up the new hard drive to port 6 and reboot, the BIOS says "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER".  I tried powering the drive from another computer to see if the power supply was running out of juice, but got the same results.

Here's the Ubuntu part: I got the idea of unhooking the DVD drive from port 3 and leaving the hard drive on port 6.  When I did that, it got past the BIOS, but I then I got "/data4 is not ready, S to skip, M to manually mount".  When I pressed M to mount it, it mounted fine.

According to the logs, it saw the hard drive fine before that:
> sd 7:0:0:0: [sde] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
sd 7:0:0:0: [sde] Write Protect is off
sd 7:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
...
sde1
sd 7:0:0:0: [sde] Attached SCSI disk


After I manually mounted it, the logs had
> 
kjournald starting.  Commit interval 5 seconds
EXT3 FS on sde1, internal journal
EXT3-fs: mounted filesystem with ordered data mode.

Given it's not a power problem, and the hard drive works perfectly in another machine, what else can be the problem?  Why won't it mount automatically when it mounts fine manually seconds later?

---

### Post by simplebliss on 2012-05-24
I've got this same problem on a desktop server.
2 sata drives wont mount on cold boot but if i hit the reset button it boots strait to terminal login screen no problems.... I've searched all over the web... nothing...

---

### Post by ahallubuntu on 2012-05-24
> **dj_sefault said:**
> I realize the following part is not related to Ubuntu, but I'm trying to give all the symptoms: When I hook up the new hard drive to port 6 and reboot, the BIOS says "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER".

FYI, all that message means is that your motherboard is trying to boot from that disk first (for some reason) and there's nothing on the new drive so it reports the error.  The message makes sense if you are running DOS 6.3 back in 1993 but not much sense today - it's a legacy message...

---

### Post by ahallubuntu on 2012-05-24
Where/how are you trying to mount it?  Can you post your /etc/fstab file?  Hint: if you have a link to /media in your /etc/fstab, take that out and use /mnt instead.  Leave /media for Nautilus.

---

