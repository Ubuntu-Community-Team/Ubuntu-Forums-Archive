---
title: "Harddrive unmounts randomly"
date: 2008-09-11
forum: General Help
---

### Post by jsnelli2 on 2008-09-11
I've got a TB hitachi external harddrive that is formatted as reiserfs.  It usually runs normally, but every once in a while it unmounts without warning.  When this happens I can't find any rhyme or reason on how to get it to remount.  I've found that with rebooting/switching usb ports etc. I can normally eventually get it to remount.  I was wondering if anyone knows why the drive would unmount and how to remedy the situation.  Any help would be appreciated.

---

### Post by fsmithred on 2008-09-12
Maybe your usb connector is loose. Try running 'sudo tail -f /var/log/messages in a terminal' and then gently wiggle the connector. You'll see messages if it disconnects.

---

### Post by gvartser on 2008-09-12
dmesg is also a nice one to use.
```
dmesg
```

/g

---

### Post by jsnelli2 on 2008-09-13
> Sep 13 16:57:02 josh-laptop kernel: [  113.800000] usb 5-5: configuration #1 chosen from 1 choice
Sep 13 16:57:02 josh-laptop kernel: [  113.800000] scsi3 : SCSI emulation for USB Mass Storage devices
Sep 13 16:57:07 josh-laptop kernel: [  118.800000] scsi 3:0:0:0: Direct-Access     Hitachi  Easy Device           PQ: 0 ANSI: 2 CCS
Sep 13 16:57:07 josh-laptop kernel: [  118.800000] sd 3:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
Sep 13 16:57:07 josh-laptop kernel: [  118.800000] sd 3:0:0:0: [sdb] Write Protect is off
Sep 13 16:57:07 josh-laptop kernel: [  118.804000] sd 3:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
Sep 13 16:57:07 josh-laptop kernel: [  118.804000] sd 3:0:0:0: [sdb] Write Protect is off
Sep 13 16:57:15 josh-laptop kernel: [  118.804000]  sdb: sdb1
Sep 13 16:57:15 josh-laptop kernel: [  126.756000] sd 3:0:0:0: [sdb] Attached SCSI disk
Sep 13 16:57:15 josh-laptop kernel: [  126.788000] sd 3:0:0:0: Attached scsi generic sg2 type 0


The Hitachi Easy Drive is the one the external drive.  I ran the command when the drive was plugged in but not mounted.  What does this mean?

---

### Post by jsnelli2 on 2008-09-17
Any ideas?

---

### Post by EmanresuusernamE on 2008-09-17
Some external hard drives automatically turn themselves off after a certain amount of inactivity.  Perhaps yours does this as well.

Open up a terminal and have your external hard drive mounted, and do the dmesg command again, (so you know where the last usb message is). Then let it sit there and go about your business as normal.  When your drive unmounts itself, go back to that terminal and run the dmesg command a second time, and post the results.

---

### Post by jsnelli2 on 2008-09-19
Thanks for th reply.  I've had this problem with two different makes of harddrives though.  I'm more tempted to think it is the USB port that is dropping the harddrive when it gets wiggled, but I haven't been able to force it to do so.

---

### Post by aurelieng on 2008-09-19
Yesterday, I noticed the same problem with a disk which used to work correctly two months ago. It is randomly unmounted from time to time. My feeling is that it is related to an upgrade which broke something, but I cannot figure out which one, as I haven't been using this disk since one months or so. Any idea ?

---

### Post by jsnelli2 on 2008-09-19
So using that assumption the disk should work fine under a clean install of ubuntu? No irratic behavior?  That would almost be worth a format.  I couldn't tell you what I've done that could have changed it, but it definitely never used to happen.

---

### Post by aurelieng on 2008-09-20
To know if it is worth a reinstall of Ubuntu, it is probaly a good idea to try the external hard disk with the Ubuntu liveCD first. Unfortunately, after a complete reinstall, the problem is likely to come back as soon as updates are installed. So we should probably wait for an update, hoping that this issue is due to a somewhat broken update. Let's use eSATA instead of USB hard drives .. :)

---

### Post by jsnelli2 on 2008-09-24
Well, I'm assuming it's not a distribution problem. I'm running Hardy.  I assume you are running Gutsy?  I think I might have come accross a possibility though.  I had a jumpdrive plugged into the port right underneath the one my hdd was plugged into and when I ejected and pulled out the jump drive an error popped up saying unsafe eject for the hdd.

---

### Post by aurelieng on 2008-09-25
My profile is not up to date, I am also running HH.

---

### Post by devcon101 on 2008-09-25
I have a Seagate external hard drive that has exhibited the same behavior.  It has been very aggravating and I feared data corruption or a failing hard drive. It would even unmount amidst a read or write operation mid way through.  It is formatted NTFS and I am using Hardy.

Recently, I decided to verify the problem was not with the disk.  Analysis utilities turned up no problems.  CHKDSK found a couple small errors, but I still suspected more with the filesystem.  Thus, I pulled all the data off my drive, and reformatted to NTFS (using GPARTED). Since, I have not had a problem with ubuntu randomly unmounting my drive.  

Since, I have also reinstalled Hardy and have not enabled backport or proposed updates. I do not know if this corresponds with the issue.

---

### Post by aurelieng on 2008-09-25
My external hard disk is ext3 formatted, and I cannot even fsck it : it stops responding during the check.

---

### Post by jsnelli2 on 2008-09-29
My harddrive was formatted ntfs when I first had problems with it.  I eventually couldn't get the thing to mount in windows either.  When I did, I had a hell of a time getting the stuff off of it without it freezing.  Mp3's had been corrupted, file tags had been lost, etc.  I sent the harddrive back for warranty replacement figuring it was the problem.  When I got the new one I immediately formatted it to reiserfs.  Didn't change anything.  I have repeatedly seen problems whenever plugging and unplugging things into the other usb ports though.

---

### Post by EmanresuusernamE on 2008-09-29
Have you tried removing the disk from the enclosure and seeing how well it works without it going through the USB interface?  If the drive works, then the USB interface of the enclosure may be damaged, or going out.

---

### Post by jsnelli2 on 2008-10-02
I'm assuming you mean plugging it directly into the computer via SATA?  I'm at school and don't have access to a desktop computer.  I've only got my laptop.  Would the usb interface on the harddrive actually be affected when plugging and unplugging other usb devices into the computer?

---

