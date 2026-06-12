---
title: "Hardy and DVD drive eject button not working"
date: 2008-04-24
forum: Hardware
---

### Post by Payteer on 2008-04-24
Hello all, So the new Hardy is with us.  On the whole I like it and it is a lot more stable, here it comes, however, my eject button on my DVD drive now does not work.  I can eject the drive if I go to the drop down menu under Places on the top bar, however it would be nice to have the little button work also.  It only stops working on DVDs.  It is a Lenovo 3000 V100 and I am using 8.04.
Thanks, also if anyone has any info on the driver for the built in webcam for this machine would be good also, it is a ATI webcam, it didn't work in gutsy either.  Don't worry about that, I think it may still be in development, but if anyone has any news on it it would be good.

---

### Post by Payteer on 2008-04-25
Hello, anybody out there?  Someone must have an answer to this, I am sure it is really simple, just I am crap at coding etc.

---

### Post by cmtsailor on 2008-04-25
I'm sorry that I don't have any fix for you.  I am struggling with the same issue.  I will be keeping an eye on the responses to your thread.

---

### Post by jessika-kaos on 2008-04-27
I am having the same problem, but I cannot eject the DVD tray unless I reboot. I can't eject from the command line, nor from the right click menu. It works fine for a few minutes after booting though.

I also have a CD drive that is having no issues at all.


[curiously, the DVD tray ejected several times just now, a delayed reaction of maybe 15-20 minutes]

---

### Post by mgmiller on 2008-04-27
Ain't it fun?  Hardy changed the way the optical drives are seen/mounted.  I even went so far as to edit my /etc/fstab and commented out the lines for my 2 DVD drives (one is a burner) and they both still work perfectly.  I think the new kernel just supports them without any thing else fancy.

Now, on to your eject problem.

I have 2 little launchers on my top panel that I use to eject my 2 DVD drives.  I used to use the command:
```
eject cdrom0
```
and:
```
eject cdrom1
```

but, after upgrading to Hardy, they both stopped working.  I dug around a bit in /dev and discovered they are now called scd0 and scd1.

So, open a terminal and try these 2 commands:
```
eject scd0
eject scd1
```

If they work, make a launcher for your top panel.
Right click a blank area of the panel and select "Add to Panel".

From the dialog that opens, select "Custom Application Launcher"

A small dialog window will open.
Set Type to: Application
Set Name to: Eject DVD-rom (or whatever you want it to say on mouse over)
Set Command to:  eject scd0

Click on the "Icon" icon to the left of the Type: and Name: and select an icon.

Click "Close" and it should appear on the top panel.

Repeat for eject scd1 & you should be all set.

Have fun!!

---

### Post by jessika-kaos on 2008-04-27
Those commands only work for me after booting up, after a while the drive becomes nonresponsive. In fact, I was burning a CD and K3b froze about half way through, which I believe is a result of whatever is going on with the drive.

---

### Post by mgmiller on 2008-04-27
> **jessika-kaos said:**
> Those commands only work for me after booting up, after a while the drive becomes nonresponsive. In fact, I was burning a CD and K3b froze about half way through, which I believe is a result of whatever is going on with the drive.

Are you using kubuntu?  I have no real experience with it.  kde may handle the drives differently.

---

### Post by jessika-kaos on 2008-04-27
I'm not using Kubuntu, I just like K3b better than Brasero.

---

### Post by mgmiller on 2008-04-27
A few weeks ago, I was helping someone who also had intermittent weird optical drive behavior that turned out to be a bad drive.  
Do you have another drive you can try, or could you try booting off a live CD and see if the problem persists?

---

### Post by fraserj on 2008-04-30
hello all, I am having a similar issue: non-working optical drive(s).
Ubuntu Gutsy worked fine, I could burn without problems. Now, with Hardy, the eject button doesn't work, and Brasero won't recognize any optical drive at all.
fstab: 
```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

All the other entries use UUID, but I couldn't find a way to get my DVD burner's UUID.

The only change I can see, from the old (working) fstab, is that Hardy is pretending my IDE burner is something else, maybe SATA or SCSI?
I tried to change it - no success. 

Can anybody please post a working fstab from a machine that can burn DVDs??

Here's what eject says:
```
$sudo eject /media/cdrom0
eject: tried to use `/dev/scd0' as device name but it is no block device
eject: unable to find or open device for `/media/cdrom0'
```

---

### Post by fraserj on 2008-04-30
/dev shows there's no such thing as scd0 but there's an hda in there...

So I tried this in /etc/fstab
```
# /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/hda       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

Rebooted, still doesn't work.
:confused:

---

### Post by mgmiller on 2008-04-30
for the eject command try:
```
eject scd0
```

That's what works on mine.  Oddly, I commented out the line in fstab about my dvd burner and it still works fine.

I don't understand why.  Also, my DVD rom is now scd1 and I also commented that out in fstab and it also works fine.

Is it possible the optical drives are now somehow in the kernel?  I noticed when I put in a disk and it mounts up, it's not in /media/cdrom1 or 2 any more.  It makes a new entry dynamically.

---

### Post by silvagroup on 2008-05-06
This is not only a Hardy problem I am still using Gutsy and it does the same thing.
I will burn a dvd or cd it works fine then the only way I can get the drive to open is reboot, eject command does nothing at all. Also I am using Kubuntu so it appears to be something with the *buntu's in general.
Big problem here !!!

---

### Post by bml137 on 2008-05-06
I highly doubt that this is a hardware issue, as I am having the same issue.

Since going to Hardy, I tried the following:
```
# eject -s scd0
# eject -s /dev/scd0
# eject -r scd0
eject: unable to eject, last error: Input/output error
```

It all works perfectly fine after a reboot.  I can even burn 1 or two disks.  After a little bit of time (an hour or 2 or 3) it just flat out stops working.  I cannot hit the eject button; I cannot run the command line 'eject' app successfully.  In fact, the 'eject' command gives no errors, dmesg has no errors, and /var/log/messages has no errors.  No output at all in fact.

I am running Mythbuntu and my drive is a DVD/CD/DL burner

---

### Post by silvagroup on 2008-05-07
No it's not a hardware issue. I recall sometime back something similar happening with the dvd cd drive combos. At that time I had a few other linux os's I was checking out and they did not have the same issues as the Kubuntu. I am going to set up a few other os's, time permitting,on a spare partition to see if it's *buntu specific. Could be a kernel issue.

---

### Post by jessika-kaos on 2008-05-07
> **bml137 said:**
> 

It all works perfectly fine after a reboot.  I can even burn 1 or two disks.  After a little bit of time (an hour or 2 or 3) it just flat out stops working.  I cannot hit the eject button; I cannot run the command line 'eject' app successfully.  In fact, the 'eject' command gives no errors, dmesg has no errors, and /var/log/messages has no errors.  No output at all in fact.

I am running Mythbuntu and my drive is a DVD/CD/DL burner

This is exactly what happens on my system. After a while I get no response. My CD drive still works, though. If I look in the process list, eject is listed with a status of "uninterruptible."

---

### Post by mgmiller on 2008-05-07
With Hardy, the optical drives are no longer handled by fstab.  They are managed by the kernel and hal.d.  They are considered the same as USB thumb drives and are mounted and unmounted dynamically as media is inserted/removed.

In my system, I have commented out the 2 lines in fstab that reference my optical drives and they both continue to work perfectly.

If you are having problems with a desktop computer, and the drives are ATAPI (PATA) drives.  Check the jumpers on the drive.  You want to make sure they are not set to "cable select".  

They should be either master or slave, depending on where on the cable they are.  
If the problem continues, it may be the firmware of the optical drive having problems being seen by the new kernel/hal.d.  

Try a different brand of drive, if the problem clears up, it is probably brand specific.  

Maybe a firmware update for the drive would help.
Perhaps a bug report including the exact brand and firmware revision of the drive would help.  

If you have a lap top, I don't know if any of this is changeable.

---

### Post by fraserj on 2008-05-14
mgmiller, it doesn't look like optical drive firmware is preventing detection.. I can see the drive in my /dev folder as hda, but trying to write to hda doesn't work. 
The main thing that perplexes me: why would it work fine with Gutsy yet not in Hardy? I think it's a kernel bug. This new kernel doesn't work well with DVD burners.
Anyways, I had to install Windows XP again to use my burner.
Next up: Fedora 9.

---

### Post by jessika-kaos on 2008-05-14
I commented out the lines in fstab relating to the drives and I have had no problem since (crosses fingers).

---

### Post by mgmiller on 2008-05-15
> I commented out the lines in fstab relating to the drives and I have had a problem since (crosses fingers).

Do you mean you have had _no_ problem since?

I haven't had any problems with my burner since commenting it out in fstab even after several reboots.

---

### Post by jessika-kaos on 2008-05-15
Oh, yeah. No problems at all. Just not paying attention I guess. Thanks!

---

### Post by kolslorr on 2008-05-16
Is this a joke? A operatnig system that cant even eject a DVD rom?

---

### Post by jessika-kaos on 2008-05-16
I spoke too soon. It took a lot longer this time but the drive is once again not responding.

---

### Post by mgmiller on 2008-05-16
> I spoke too soon. It took a lot longer this time but the drive is once again not responding. 

Have you tried all my suggestions in post #17?  If this is a desktop computer are the jumpers on the optical drives set as master or slave rather than as cable select?

---

### Post by jessika-kaos on 2008-05-16
I did take out the drives and change the jumpers from cable select to master/slave. I have not tried updating firmware (actually don't even know how I would do something like that), but I mean, it did work fine under 7.10 and all previous releases, and the problem started the day I upgraded (clean install actually). I don't have another dvd drive to replace it with. I rebooted and it's still working after 4 hrs.

---

### Post by mgmiller on 2008-05-17
There is a change in how Hardy looks at optical drives as compared to earlier releases.  It's now done directly by hald and the kernel.  That's why you don't need an entry in fstab anymore.  Also, the cable select jumper setting changes the way the chipset on the motherboard interacts with the drive.  My guess is that the kernel can't quite figure out what is happening when the jumpers are cable select for certain motherboard/optical drive combos. 

If your system proves to be stable after making the jumper change, please file a bug report including the motherboard model and optical drive model, so maybe the kernel devs can get a handle on the problem.

Just as an aside, I have seen intermittent problems in windows boxes because of this as well.  I always avoid use of the cable select jumper settings.  My preference is to have burners jumpered as master, unless they are on the same cable as a hard drive, where the HDD would be master and the optical drive slave.  Since most systems today use SATA HDD, it's easy to have a PATA burner as master.

In many windows systems with burner problems, the fix was often to get the optical drive off the HDD cable and put it on its own cable as master.  This left the HDD alone on its cable, so the jumpers would sometimes have to be changed on the HDD as well, depending on the brand of the drive.  SATA has made all this much simpler.

There are other advantages to keeping optical drives off the same cables as PATA HDD, but that's a different lecture.

---

### Post by ddbattlefield2142 on 2009-03-15
I encountered the same problem. I realized that I wasn't able to eject my cd drive because some process was accessing it. For example, I finished burning a CD, my drive ejected, I took the CD out and closed the drive. After this, my eject function stopped working. I later realized that "finished burning" GUI dialog box was open. I closed that dialog box and eject started working again.

I saw similar behavior using VirtualBox. I have Ubuntu hardy, I installed VirtualBox and then I installed Windows XP as guest OS on VitualBox. I popped a CD in, then used it in WindowsXP, then ejected it from WindowsXP. After doing this, eject stopped working in my Ubuntu 8.04 again. So I went to VirtualBox, clicked on devices -> Unmount CD/DVD-ROM. After doing this, eject worked fine in Ubuntu again. I guess Ubuntu thought the device was busy. 

**Before** I ran VirtualBox -> Device -> Unmount CD/DVD-Rom this was the output of my "eject -v" command: - 

eject: using default device `cdrom'
eject: device name is `cdrom'
eject: expanded name is `/dev/cdrom'
eject: `/dev/cdrom' is a link to `/dev/scd0'
eject: `/dev/scd0' is not mounted
eject: `/dev/scd0' is not a mount point
eject: `/dev/scd0' is not a multipartition device
eject: trying to eject `/dev/scd0' using CD-ROM eject command
eject: CD-ROM eject command failed
eject: trying to eject `/dev/scd0' using SCSI commands
eject: SCSI eject succeeded

Although it said "eject: SCSI eject succeeded" but my drive didn't eject until I ran VirtualBox -> Device -> Unmount CD/DVD-Rom. 

By the way, I didn't change my /etc/fstab. It still looks like this: - 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=17deab40-fa19-4255-ab88-cfe34d76caf4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=b3719172-d9e8-410c-bf45-0fb8430fe701 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
#usbfs
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

Hope this helps.

---

### Post by ordealbyfire83 on 2009-09-14
I was having the same problem. After a fresh boot I could insert a CD or DVD and then eject it (by either using the physical button on the drive or by right-clicking the CD icon and clicking 'Eject') just fine. But then, the door would be locked and would not open. Therefore in order to insert another CD I would either have to either reboot or use the pinhole.

After poking around a bit, and running gnome-system-monitor (via sudo) I found that pktcdvd was running, even after a fresh boot and before I ever opened the drive door. This process is part of the udftools package and is used for reading/writing cd/dvd via packet writing (see [http://ubuntuforums.org/showthread.php?t=129093]("http://ubuntuforums.org/showthread.php?t=129093") for further info).

Stopping this process like so seems to allow proper open/close of the drive door.
```
sudo pktcdvd -d pktcdvd0
```
It's also possible to stop udftools from loading on boot (try, for example, creating a folder called 'disabled' in /etc/init.d and moving udftools into it, that way you still launch the daemon if you encounter a packet-written disk) or just remove the udftools package completely.

---

### Post by mgmiller on 2009-09-15
udftools is not part of a standard Ubuntu install.  It is in the universe repository.  It would appear you have found a bug in it.  Please file a bug report so it can be fixed properly.

---

