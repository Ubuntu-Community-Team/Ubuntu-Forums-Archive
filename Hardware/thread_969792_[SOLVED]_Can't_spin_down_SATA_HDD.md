---
title: "[SOLVED] Can't spin down SATA HDD"
date: 2008-11-03
forum: Hardware
---

### Post by ghjf345 on 2008-11-03
I have a SATA harddisk which is used up entirely as a TrueCrypt container. I use it very rarely, so I want to spin it down (of course after having dismounted it).

I tried two ways to do that:

```
# sudo hdparm -y /dev/sdd
/dev/sdd:
 issuing standby command
```

and

```
# sudo sdparm -C stop /dev/sdd
    /dev/sdd: ATA       SAMSUNG HD642JJ   1AA0
```

Not only do I not hear anything, but I also ask hdparm's opinion

```
# sudo hdparm -C /dev/sdd

/dev/sdd:
 drive state is:  active/idle
```

and it agrees that the HDD is still spinning.

Does anybody have any idea why I cannot spin it down? Or maybe another way to do it? Thanks a lot.

Misc info: On the particular machine I am running the 64bit version of Ubuntu 8.10 Server edition. The motherboard is an Asus M3N78-EMH HDMI and the harddrive is a 640GB Samsung.

---

### Post by ghjf345 on 2008-11-04
I (sort of) solved this. All I had to do is shut down the PC and then start it again (a reboot didn't work).

However, even after I managed to spin down a drive, after about one minute it would spin up again. I found out that sensors-applet (together with hddtemp) was to blame for that. (Does a drive really have to spin up in order to read its temperature?) After having removed sensors-applet from the Gnome Panel, my drives have a pretty sound sleep.

---

### Post by kerneloftruth on 2009-03-16
ghjf345, this is still working for you ?

are you still using 8.10 ? or have you meanwhile upgraded to 9.04 ?

this problem of the disks permanently spinning up again after sending them to standby / sleep was an K.O. argument for using ubuntu since I already had disabled several services and apps but it would still spin up again

so sensors-applet and hddtemp were the only ones polling the drive(s) ?

and to answer your question:

yes:

for this unfortunately the drive needs to be spun up

this also applies to reading out the smart-status via smartctl 

thanks

---

### Post by ghjf345 on 2009-03-22
It used to work at the time, even though I'm still with 8.10.

Now I can't get my harddisks to spin down at all, not even when the respective partitions are unmounted.

I'm starting to think it may have something to do with the mainboard. The disks themselves seem to be ok, according to smartctl.

---

### Post by kerneloftruth on 2009-05-05
another reason for me why the harddisks kept spinning up was **nautilus**

fire up: ```
gconf-editor
```

then search for:

/apps/nautilus/preferences/media_automount 

or

/apps/nautilus/preferences/media_automount_open

disable at least the first one by clicking on the marked box: [x] 
so that it shows [ ] 

this solved it for me

alternatively you can also manually send the harddrives to sleep:

```
sdparm -C stop /dev/foo 
```
(this doesn't really work for me properly)

or 

```
hdparm -S 60 /dev/foo
```

---

### Post by ameno on 2009-05-09
the correct command for setting a drive to standby immediately is
```
hdparm -Y /dev/sdX
```

my backup script that runs every 24h uses this at the end to spin down my second (backup only) hdd.
that worked without problems in 8.10 intrepid but does no longer work in jaunty. for 8.10 i had to configure hddtemp and smartd to ignore sdb.

when i issue the command i can hear the drive shutting down for less than a second and then its accessed again.

---

### Post by ghjf345 on 2009-05-17
The solution (upgrading the kernel to mainline 2.6.29.2) is described here: [https://bugs.launchpad.net/bugs/374287](https://bugs.launchpad.net/bugs/374287)

---

