---
title: "my mdadm issues with sata drives"
date: 2005-06-29
forum: Hardware &amp; Laptops
---

### Post by craveytrain on 2005-06-29
I have read through pages and pages of how-tos and other instructionals on my issues with this raid. This is a new system. However, they have not worked, but I haven't see anyone complain about one of the symtoms I am having. So maybe mine is something different.

I setup a new Ubuntu system. 40GB IDE drive, 2x250GB SATA drives. I am using the onboard Sil 3112A "raid" controller. The IDE is for the OS and the satas are for my media library (mythtv + samba server). I want to run Raid 1 (cause I don't want to lose this stuff).

 I go through the ubuntu install, put / and swap on the 40 gb ide. I make 1 partition on each of the sata drives (sda1 & sdb1), set them to ready for raid and go to the software raid setup. I make a raid 1 out of the 2 drives. I go and setup the raid volume as xfs and a mount point of /home. Everything seems to go smooth.

I reboot and while booting, I get the commonly reported "/dev/md0 does not exist". I figure there is something wrong with the raid it setup so I will make a new one. I clear out the mdadm.conf file and just put "DEVICE /dev/sda1 /dev/sdb1". I go to do a "mdadm --create /dev/md0 -l 1 -n 2 /dev/sda1 /dev/sdb1"

Then I get "mdadm: error opening /dev/md0: No such file or directory". Sure enough, there is no /dev/md0. Getting this error message when running mdadm from the command promt is the part i don't see any other how-to addressing. Is there a really stupid step that doesn't need to be called out in a how-to that I am missing or is there a legitimate error?

I have tried adjusting the pass number to "0" for md0 in /etc/fstab. I can even do a "mdadm -E /dev/sda1" and it sees the volume just fine. it tells me it's part of a raid with accurate information reflected in the ARRAY line of the mdadm.conf file. I tried just doing a "touch /dev/md0" to just create something there for it to see, and naturally it gives me an error saying it's "not an md device".

I would appreciate any tips or tricks y'all might have. I am sorta a noob, though I can follow instructions. Thank you for your time.

---

### Post by tonym on 2005-06-29
Not sure if this will help but worth a try.

Have you defined the underlying partitions as type "FD" - raid autodetect?  If so change with cfdisk.

I find things work best with no /etc/mdadm/mdadm.conf file at all.

when you call mdadm as the raid1 module loaded?  lsmod will show all loaded modules.   If not,  try modprobe raid1 before mdadm.

---

### Post by craveytrain on 2005-06-29
thanks for the advice.

Yes, the underlying partitions were set to FD, but i redid it, just in case. it still made no difference.

I did an lsmod and there wasn't a raid running. so I did a modprobe raid1 and it redid the lsmod and it showed up. but I still got "mdadm: error opening /dev/md0: No such file or directory" when trying to run msadm.

I removed the mdadm.conf and rebooted. low and behold /dev/md0 was there (along with 20 other mds). I ran mdadm create command again it it prompted me to overwrite the raid. I said yes and it went off like it is supposed to. raid finished building and I mounted /dev/md0 @ /home.

when rebooting immediately after, it disappears. /dev/md0 is just gone.

I can go recreate the raid by following the steps above, but as soon as I reboot /dev/md0 is missing again. I am sorta lost here. any suggestions?

---

### Post by alastair on 2005-06-29
It's hard to say ... I wish I could beam myself over there and help out!

I think it might be worth looking at your boot logs i.e.

/var/log/syslog

and looking to see :

a) the SATA sda/b devices are recognised OK
b) messages from any MD device / mdadm

If /dev/md0 is not found on boot (and this is something to do with udev), you can "force" udev to create the device by adding the following to the file :

/etc/udev/links.conf

Add something like :

M md0           b 9 0

This should force the device to get made on boot.

---

### Post by craveytrain on 2005-06-29
ok, I reinstalled the OS (I messed with too many things). used the ubuntu install disks to create the raid array, rebooted, md0 not found again.

I can access each of the disks that make up the raid individually and they are fine. I can even get raid information from them by doing a "mdadm -E /dev/sda1".

when I do your suggestion of forcing udev, it finds it, but then it gives a superblock error on boot up. I actually get 2 errors when I boot (after having made the addition in the link.conf). I get a complaint from adm saying"no devices found for /dev/md0" and I get an error from mount saying "/dev/md0: can't read superblock". It almost appears as if the link.conf is not creating the md0 fast enough for mdadm on boot up, but is getting it in time for the fstab to be processed. is that right? if so, what do I do about it?

once booted up, I can run "dpkg-reconfigure mdadm" and tell it to start up and it works great, until I reboot. for that matter, i don't even have to run reconfigure.

```
root@paco:/# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda3             37068816    279240  36789576   1% /
tmpfs                   453328         0    453328   0% /dev/shm
/dev/hda1                90297      6600     78880   8% /boot
/dev                  37068816    279240  36789576   1% /.dev
none                      5120      2816      2304  55% /dev
root@paco:/# mount -a
mount: /dev/md0: can't read superblock
root@paco:/# /etc/init.d/mdadm-raid stop
root@paco:/# /etc/init.d/mdadm-raid start
 * Starting RAID devices...
mdadm: /dev/md0 has been started with 2 drives.                          [ ok ]
root@paco:/# mount -a
root@paco:/# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda3             37068816    279048  36789768   1% /
tmpfs                   453328         0    453328   0% /dev/shm
/dev/hda1                90297      6600     78880   8% /boot
/dev                  37068816    279048  36789768   1% /.dev
none                      5120      2816      2304  55% /dev
/dev/md0             244076668       288 244076380   1% /home
```

btw, I keep getting a message on the terminal each time I run  the package reconfigure that says "md: md0: raid array is not clean -- starting background reconstruction".

then I can "cat /proc/mdstat" to see the progress. I can mount, all that jazz works great, but when I reboot, i can't access /dev/md0 again.

Update:
I have found if I make a link in rcS.d for "S99mdadm-raid" it actually works. However, it doesn't mount the volume from fstab, which is kinda important, since I am using it for /home. Could the fact that I am trying to mount it as /home be an issue?

---

### Post by craveytrain on 2005-06-30
ok... new clean install, setup the drives as a raid, /dev/md0 did not exist when I booted up. now, every time i reboot, I can restart the raid by simply typing
```
mdadm --assemble /dev/md0
```

I have no extra lines links.conf. putting the entry suggested didn't change anything after all. the only change I have made from the base install is the mdadm.conf:

```
DEVICE partitions
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=b403f7ab:6b887bb4:90b92c80:07ed555d auto=md
   devices=/dev/sdb1,/dev/sda1

```

so now i just gotta find a place to put "mdadm --assemble /dev/md0" in the start up procedures or find out why /etc/init.d/mdadm-raid doesn't work in it's place (@25) but works at 99.

---

### Post by steven_ellis on 2005-06-30
[QUOTE=craveytrain]
```
DEVICE partitions
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=b403f7ab:6b887bb4:90b92c80:07ed555d auto=md
   devices=/dev/sdb1,/dev/sda1

```

so now i just gotta find a place to put "mdadm --assemble /dev/md0" in the start up procedures or find out why /etc/init.d/mdadm-raid doesn't work in it's place (@25) but works at 99.[/QUOTE]

Try the following in /etc/mdadm.conf

```
DEVICE /dev/sd[ab]
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=b403f7ab:6b887bb4:90b92c80:07ed555d auto=md
   devices=/dev/sdb1,/dev/sda1

```

Steve

---

### Post by tonym on 2005-06-30
Try adding raid1 to /etc/modules

---

### Post by craveytrain on 2005-06-30
thank you for the tip, but neither of those suggestions changed a thing about how it booted up. still giving the same error.

actually, taking out the auto statement made my /dev/md0 disappear again. so that actually reverted it. but I tried all sorts of permutations of the suggestions y'all made. I'm afraid none of them help with the boot up procedure.

---

### Post by dawgg on 2005-07-15
i was having the same probs with my gentoo-install, but it finally works. (don't reinstall the os, that's the m$-aproach  ;-)   )

1. check that udev (re-)creates the device-nodes /dev/mdX on startup. (the nodes existing does not mean the array will be automatically started, but they have to be there before). udev is tricky, i added a line to a startup-script to get the device-nodes: (/etc/init.d/checkroot in gentoo)
```
for i in 0 1 2 3 4; do mknod /dev/md${i} b 9 ${i}; done
``` (i have 4 md-devs)
(probly not the best way but it works)

2. if the nodes are there and the raid-arrays can be started manually (mdadm -A ....)
check if the partition-type of the component-partitions ist really
**linux raid autodetect (fd)**
use cfdisk or fdisk for this.
this is what finally did it for me.

---

### Post by OzPhoenix on 2005-07-23
craveytrain,

Thank you for your extensive documentation on the issue you're having. I'm having the same problem and it was good to read your info.

My raid array works fine, but I have to manually start it due to errors during boot up that there is no /dev/md0. I have found that if you have no mdadm.conf you will have /dev/md0 and no errors. If you have mdadm.conf you will get errors and no /dev/md0 - unless your mdadm.conf has the auto=yes in it (or auto=md).

More specifically if you have no mdadm.conf, you will get about 20 /dev/md?? files. I believe the reason for this (after reading /etc/init.d/mdadm-raid) is that if there is no config file, rather than run mdadm -A -s at startup it just runs mdrun. I believe the side effect of this is to create multiple /dev/md??.

This is not too important, but does explain why you get no errors when there is no mdadm.conf.

I'm of the opinion that the boot order is incorrect. I believe that mdadm-raid and thereby also mountall are being run before it is possible to get the /dev/md?? files setup. I believe this to be true for two reasons:

1. If I have an mdadm.conf file, and I let it boot (and report errors - from both RAID and mounting) I can then do the following (manually) to bring my RAID online:
```
sudo mdadm -A -s
sudo mount -a
```
2. When your mdadm.conf has the auto=yes in it, it successfully creates the necessary /dev/md0 file, however it is not created until well after it is needed (hence the errors at boot for Starting RAID and for Mounting).

So if it is trying to start these at the wrong place, when is the earliest possible time that we could start it? What do we need to wait for to ensure that /dev/md?? will be present and functional? Can anyone tell us this?

For the time being I'm tempted to create a file called /etc/init.d/start-raid.sh with the contents:
```
mdadm -A -s
mount -a
```
and have it linked at S99. I get this idea from what you said earlier craveytrain.

Anyway, can anyone answer the question:
> So if it is trying to start these at the wrong place, when is the earliest possible time that we could start it? What do we need to wait for to ensure that /dev/md?? will be present and functional? Can anyone tell us this?


Cheers,
OP

---

### Post by OzPhoenix on 2005-07-23
Yup, so I've tried making my own file linked into the rcS.d at S99. I still obviously get the errors at the first attempt from the standard mdadm-raid and mountall. But when it gets down to me it works perfectly. Here is the file:
```
#!/bin/sh

. /lib/lsb/init-functions

log_begin_msg "2nd Attempt: Starting RAID..."
mdadm -A -s
mount -a
log_end_msg $?
```

The script is not perfect, as it will not print out [fail] if there was an error returned by mdadm. It is only going on the return status of mount -a (as $? will get overwritten). But I'm tired and don't care right now.

Anyway, now I've got that going, I can potentially move it up the boot order bit by bit until it fails again and then I might learn the correct place for it. See what happens. :?

Hope it helps all the others having issues with /dev/md0. ;)

---

### Post by TemplaraPheonix on 2005-07-25
Howdy, I have a very similar configuration here and after fiddling with enough settings I got mine working, well with one problem. I came across your posts while working to fix my issues and thought I might share...Also might help me.

I have a SiImage 3112 PCI with 2 200GB SATA drives in a Pentium III 866 with a 10GB ide boot drive.  The goal is to create an nfs server with mirroring.

No matter what I did with a vanilla 2.6 kernel, I could not get autodetect working. I'm not sure if this is a legit kernel issue or just my own inability to configure it correctly. 

Anyway...I switched to 2.4. It still had issues.

I would reboot and use mdadm --assemble /dev/md0 and get a no devices found error, but the assemble would work if I gave the devices, mdadm --assemble /dev/md0 /dev/hde1 /dev/hdg1. Similarly if I apt-get --purge mdadm and apt-get install I would get an error when it tried to load the array. To fix this I
added a 

DEVICE /dev/hde1 /dev/hdg1

before the autogenerated mdadm --detail --scan >> /etc/mdadm/mdadm.conf of said config file. I know I shouldn't even need the file, but it works.

I also added

md
raid1

to /etc/modules so that I was positive that my kernel had all the modules it needed. I know that module dependencies should be resolved automatically, but having just raid1 didn't work for me. I got a number of md: error messages saying things like bad superblock (on a newly created array with no data). If you add this and look at /var/log/syslog and get md: error messages you might be able to track down other issues. I know neither of my systems are udev, but here is where any udev messages would appear if it was a kernel-level problem.

Also, make sure that mdadm is set to autoload=true. This is found in /etc/default/mdadm otherwise unless you're booting from raid, the raid won't autload.

I hope that helps. My issue is that 2.4 raid is much slower than 2.6 raid. While my raid under 2.6 couldn't ever be recognized on reboot, it did start resyncing when I manually created it and said it would take around 50 minutes at speeds of 50MB/s. Under 2.4 the specs are closer to 90 minutes at 30 MB/s. I'd like my server to have good throughput. And thus use a more modern kernel.

I'm planning to roll my own kernel with raid support built-in (no module issues) and keep my working configs from 2.4, just changing the /dev entries. However, this may not work and introduces all kinds of other problems since its a custom kernel as well as the problems from a kernel chnage. If you guys can track down an easier way with the stock 2.6 kernel, I'd prefer just format, reinstall and implement that.

---

