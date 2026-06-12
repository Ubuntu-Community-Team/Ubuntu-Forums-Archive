---
title: "Lexar jump drive problem"
date: 2006-02-26
forum: Hardware &amp; Laptops
---

### Post by LadyDoor on 2006-02-26
Hi.

I've done a search on Lexar Jump Drive and USB Jump Drive & various permutations thereof, but haven't found anything that has helped me solve this problem yet. I've got (obviously) a Lexar USB Jump Drive that I used to use to transfer data from my computer to various school computers (Mac or Windows) from which I could print (not a Linux problem, an "I don't have money to buy a printer" problem). When I first started using Ubuntu a few months ago (Hoary, then) it worked fine. When I switched to Breezy, however, it stopped working.

Whenever I insert the jump drive, it does automount, and I can copy files off of it and onto my computer. However, I can't delete any of those files that have been on it for months; nor can I save new files to it--I do not, Ubuntu tells me, have permission to access this device. So I did an ls -l in /media, and it told me not only that I (i.e., my username) am the owner of the device, but also that I have 777 permissions on the drive dir. Nonetheless, anytime I try to write to the USB drive or delete anything from it, I am informed that it is a read-only filesystem (though one which, apparently, I have permission to write to).

Does anyone know how to convince my computer to allow me to use my jump drive for its intended purpose again? I would very much like to be able to depend on being able to transfer files that way, since emailing files to myself isn't really the best option for moving them from place to place (especially since my school's online mail client is really annoying now that I'm used to using an installed program on my computer).

Any help would be much appreciated. Bunches of kudos to whomever has the solution! Only slightly (VERY slightly) fewer kudos to anyone who wants to help but does not have definitive Guru-level knowledge! Only YOU hold the key to the mystery! Respond now, while supplies of kudos last!

---

### Post by mjwood0 on 2006-02-26
> Bunches of kudos to whomever has the solution! Only slightly (VERY slightly) fewer kudos to anyone who wants to help but does not have definitive Guru-level knowledge!

Lol.  :)

Sorry I'm not in front of my Linux box right now (I'm at work). 

Sounds like the device is being mounted as read-only.  This means that whatever the permissions are, you can't write to it.

To check this, go to your (i'm doing this from memory here) /etc/fstab and paste the output.  The line that mounts the /media/<your usb device> perhaps has the "ro" option.

---

### Post by LadyDoor on 2006-02-27
Hmm, thanks. Unfortunately, fstab (after I inserted the jump drive) still didn't seem to show any indication of it. Do you know of anywhere else I could look?
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /home           ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```
Thanks,
Door

---

### Post by 5-HT on 2006-02-27
[QUOTE=LadyDoor]Hmm, thanks. Unfortunately, fstab (after I inserted the jump drive) still didn't seem to show any indication of it. Do you know of anywhere else I could look?
[/quote]

Gnome-volume-manager (responsible to automounting removable media) does some magical little dance to do what it does, and likes to keep secrets from fstab.

To see what may be going on...try ```
 mount 
``` when the drive is mounted to see where it's being mounted and with what options. That may help find out what's going on as it is certainly not reflected in fstab.

Personally, I dislike automounting myself and just set up an fstab entry for removable media. If you want to try that (either for use, or just as part of the troubleshooting) append a line like this to /etc/fstab

```
<device> <mountpoint> <filesystem> defaults,user,noauto  0    0

```

For the <filesystem>, I just use 'vfat', but if the drive(s) have different filesystems then 'auto' could be used.

For the <mountpoint>, I like /media/usbdisk.

For the <device>, the best thing is (if you don't what it is) to enter:
```
 tail -f /var/log 
``` and plug in the drive.
You should see some lines about it being detected and which device name is given to it (something like /dev/sda).

Once the fstab entry is appended, and you have the proper directory made for the mountpoint, mounting and unmounting become as simple as ```
 mount/umount  <device name OR mountpoint> 
```



My apologies if you are already well aware of how to mount stuff manually, I just find doing so results in less possible headaches when problems, like your are currently experiencing, happen.

Providing the result of 'mount' though with the drive mounted should help someone identify why the permissions are as they are, and how to possibly fix them.

Hope that helps.

---

### Post by LadyDoor on 2006-02-27
Hmm, thanks for the tip...this seems to be moving in the right direction, but didn't quite solve the problem, unfortunately.

After doing all that you suggested in your post, 5-HT, this is the pertinent output from the mount command:
```

/dev/sda1 on /media/usbdisk type vfat (rw,noexec,nosuid,nodev,user=door)

```

(Nothing's different from before except that it says /media/usbdisk instead of /media/LEXAR\ MEDIA). I still can't write to it though. And here's the new last line of my modified /etc/fstab:
```

/dev/sda1       /media/usbdisk  vfat    defaults,user,noauto   0        0

```

Do you (or does anybody) have any suggestions?

Many thanks again,
Door

---

### Post by 5-HT on 2006-02-27
[QUOTE=LadyDoor]

/dev/sda1 on /media/usbdisk type vfat (rw,noexec,nosuid,nodev,user=door)

(Nothing's different from before except that it says /media/usbdisk instead of /media/LEXAR\ MEDIA). I still can't write to it though. And here's the new last line of my modified /etc/fstab:

/dev/sda1       /media/usbdisk  vfat    defaults,user,noauto   0        0


Do you (or does anybody) have any suggestions?
[/quote]

Hmm...so you get the same printout with 'mount' from both a manual mount with that fstab entry and GNOME's automount (albeit with a different mount point).

From that printout,the drive appears to be, as you said, mounted read/write and under your username.

There shouldn't be a reason why you are not allowed to delete or write files to it...yet there is.

Unfortunately, I'm really not sure what's going on but have two suggestions:

1) Try this to explicitly mount the drive as read/write for your user ( the 'default' option should include rw though)

```
 mount -w /media/usbdisk 
```

2) Have you tried to see if you could write/delete as root?

Mount the drive, and just try to write/delete a file from a terminal using 'sudo'.


Apart form that, everything, as you said, appears to be in order save that you cannot write to the drive.

There could either be something amiss with Ubuntu or the drive.
Does the drive have any issue on other OS's?

If not, and the previous doesn't help, hopefully someone better than I can help you out (if not, a bugreport may be a good idea).


Sorry for your trouble.

---

### Post by LadyDoor on 2006-02-27
Hmm, the 'mount -w' didn't help, but thanks...I've already tried both su and sudo to get access, though since an ls -l tells me I'm the owner that shouldn't be the issue...and apparently isn't since that just tells me it's mounted readonly. Hmmmmm. Well, if a person wanted to submit a bug report, where would zie submit it and what kind of info?

Also, I had no problems with this defice on Windows XP, on Mac OSX, or on Ubuntu Hoary--just Breezy. Weird, no?

Thanks, and any help anyone has is much appreciated,
Door

P.S.:  Kudos as promised to those whose suggestions have so far been useful!

---

### Post by bull on 2006-02-28
I'm using Lexar Jump Drives with Breezy and they are working fine (automount, read, and write). Hope the following will be of some help.    

I received the following from "tail -f /var/log/messages" after I insert the drive:

> Feb 28 10:07:00 edisto kernel: [6888191.600000] usb 5-3: new high speed USB device using ehci_hcd and address 6
Feb 28 10:07:00 edisto kernel: [6888191.680000] scsi6 : SCSI emulation for USB Mass Storage devices
Feb 28 10:07:00 edisto usb.agent[1381]:      usb-storage: already loaded
Feb 28 10:07:05 edisto kernel: [6888196.682000]   Vendor: LEXAR     Model: JUMPDRIVE SPORT   Rev: 1000
Feb 28 10:07:05 edisto kernel: [6888196.682000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Feb 28 10:07:05 edisto kernel: [6888196.687000] SCSI device sdb: 506880 512-byte hdwr sectors (260 MB)
Feb 28 10:07:05 edisto kernel: [6888196.689000] sdb: Write Protect is off
Feb 28 10:07:05 edisto kernel: [6888196.696000] SCSI device sdb: 506880 512-byte hdwr sectors (260 MB)
Feb 28 10:07:05 edisto kernel: [6888196.697000] sdb: Write Protect is off
Feb 28 10:07:05 edisto kernel: [6888196.697000]  /dev/scsi/host6/bus0/target0/lun0: p1
Feb 28 10:07:05 edisto kernel: [6888196.758000] Attached scsi removable disk sdb at scsi6, channel 0, id 0, lun 0
Feb 28 10:07:05 edisto scsi.agent[1429]:      sd_mod: loaded sucessfully (for disk)


And I get the following when I remove the drive (without manual umount):

> Feb 28 10:09:52 edisto kernel: [6888363.184000] usb 5-3: USB disconnect, address 6

mount gives the following :

> /dev/sdb1 on /media/LEXAR MEDIA type vfat (rw,noexec,nosuid,nodev,quiet,shortname=winnt,uid=1000,gid=1000,umask=077,iocharset=utf8 )

The drive never shows up in /etc/fstab.  I'm not sure if I installed any additional usb or scsi related libraries or drivers since I first installed breezy, so I'm not sure why its working.  Let me know if there is anything else you want me to check.  Otherwise, you could try adding a udev profile for your jump drive.

[http://www.reactivated.net/writing_udev_rules.html#example-camera](http://www.reactivated.net/writing_udev_rules.html#example-camera)

---

### Post by LadyDoor on 2006-02-28
Hi. Well, this is interesting...this is what I got from my /var/log/messages file with that command: 
```
Feb 28 13:08:19 localhost usb.agent[12614]:      usb-storage: loaded successfully
Feb 28 13:08:24 localhost kernel: [4295058.086000]   Vendor: LEXAR     Model: JUMPDRIVE         Rev: 1000
Feb 28 13:08:24 localhost kernel: [4295058.086000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Feb 28 13:08:24 localhost kernel: [4295058.231000] SCSI device sda: 506880 512-byte hdwr sectors (260 MB)
Feb 28 13:08:24 localhost kernel: [4295058.232000] sda: Write Protect is off
Feb 28 13:08:24 localhost kernel: [4295058.236000] SCSI device sda: 506880 512-byte hdwr sectors (260 MB)
Feb 28 13:08:24 localhost kernel: [4295058.238000] sda: Write Protect is off
Feb 28 13:08:24 localhost kernel: [4295058.238000]  /dev/scsi/host0/bus0/target0/lun0: p1
Feb 28 13:08:24 localhost kernel: [4295058.297000] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
Feb 28 13:08:24 localhost scsi.agent[12678]:      sd_mod: loaded sucessfully (for disk)
Feb 28 13:08:30 localhost kernel: 5000] **FAT: Filesystem panic (dev sda1)**

```
[bold added for emphasis] And here's what I get after pulling it out:
```
Feb 28 13:10:32 localhost kernel: [4295185.782000] usb 3-2: USB disconnect, address 2

```

Could the "fillesystem panic" be the cause of the problems? That really doesn't seem like a good thing. Also, I'm using Fluxbox but with the Gnome Volume Manager on...could part of the problem be that it's still automounting or something, and if so is there a way to turn that off? Does anybody know how a person would go about resolving a "filesystem panic?"

Thanks again,
Door

---

### Post by LadyDoor on 2006-02-28
I checked and it seems there were already a couple tools installed to handle FAT filesystems, so I don't know why there would be a "panic"...just in case I went ahead and installed the only other one I could find, which is in synaptic and the only package beginning with "fat"...i also installed various tools dealing with mac & windows data from the "Cross-Platform" sections, just in case exposure to other OS's was the problem...turns out it wasn't. Is there a specific thing I should have installed maybe that would allow it to be written to and not cause a "filesystem panic?"

Thanks,
Door

---

### Post by 5-HT on 2006-03-01
I've been hesitant to reply again as I am not knowledgeable about filesystem panic issues, but just wanted to add some thoughts for what they may be worth.

Yes, Ubuntu should have no problem handing FAT drives at all.
What may be going on is that there could be a minor corruption on the drive's filesystem.

While it's odd that only Linux/Ubuntu, specifically in the move to Breezy, should have problems with it as opposed to Windows/Mac...I have noticed that Linux likes to adhere strongly to specifications and can be quite picky sometimes.

It may just be a coincidence that the problem started to occur at the time of the upgrade, or the problem could very well be something else entirely.

A few things that may be of help if this is the correct problem:

i) If it's a Breezy specific issue (in your case)...maybe it's the new kernel that is a cause?

If so, there may be a way to test this. If you upgraded from Hoary to Breezy instead of a clean install of Breezy, you should still have Hoary's kernel available to boot from.

I'd try booting from Hoary's kernel to see if that helps.

ii) Have you tried another flash drive, or just the one?
If only the one doesn't work, that would lend support to a filesystem issue.
Maybe checking the filesystem (probably best to do this from Windows) and fixing any errors that may happen to come up?


About how to report a bug, there's a link in the upper right corner of the forums (Ubuntu Bugzilla). I'm not sure if this really is a bug, especially given that the same brand of drive is working for someone else, but it could be; and if you'd like that would be the easiest way to file a bug report.


Hope some of this may be of help.

---

### Post by LadyDoor on 2006-03-01
Interesting, thanks...I did not do an upgrade...or I did, but I made a mistake somewhere and broke everything and had to start all over (though luckily my "home" is on a separate partition). But thanks for the suggestion. And I will try to see if it works with other jump drives as soon as I find someone who has one. So thanks again for your help!

--Door

---

### Post by greghill on 2006-05-21
I, too have just purchased a LEXAR jump drive and am having the same problem on Ubuntu Breezy. The disk is automounted as a "read only" drive and that means you can't write to or delete any files from the drive! I did read somewhere (in another section of these forums) that it is a  quirk of Breezy. I can at least partly verify that, as the drive works flawlessly on my second box, powered by SuSE Linux 9.3. I'm hoping that Dapper will fix the problem. It's almost rediculous that a drive mounted by the user should have next to no priviledges. A portable drive, it seems to me, should be owned by the person (i.e. - user) mounting the drive, and therefore should have unlimited read/write abilities assigned automatically to the user. :-))
Greg

---

### Post by Resurrection on 2006-05-21
This is very interesting.  I saw this thread, read it and figured that since I have a Lexar 512 mB drive sitting here that I had never used on Linux, only on Windows, that I would plug it in and see what happens.

My drive worked fine.  No problems, reading, writing, executing or deleting files from the drive.  I plugged it in to the USB port, and a Nautilus window pops up showing the contents of the drive just like it was another drive in the system, except that nautilus gives it a drive icon with a little USB arrow symbol on top of it.  All of the files on my drive were either Word or Powerpoint documents.  Double clicking on them starts Open Office right up without any issues.  I am only logged in as a regular user, not as root, and I didn't have to sudo or anything.  If it means anything though I find it odd that the USB drive is detected as a type "Unknown" filesystem.  In windows XP, the same drive is a "FAT" filesystem (not 32, just fat).  I use this drive at work on Windows 2000 machines.  Perhaps the filesystem it is formatted as is why it works everywhere.

I am using Breezy on a fairly old machine.  The Lexar is auto-mounted as /dev/sda1.  It's access path is auto set to /media/LEXAR.  If I had to guess, I would think this is a kernel problem.  I am using the 2.6.12-10-386 kernel that comes as part of the base install of Breezy.  I have not tried it with my custom compiled kernel yet.  Perhaps if you are using a custom kernel, and the right modules are not compiled in?

---

