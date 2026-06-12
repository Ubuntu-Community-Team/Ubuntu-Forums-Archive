---
title: "Ubuntu Does Not Auto-Mount USB Thumb Drive"
date: 2009-04-23
forum: Hardware
---

### Post by coldReactive on 2009-04-23
When Ubuntu logs in, it does not auto-mount my USB Flash/Thumb Drive (Like Windows, and previous Ubuntu releases.) How can I get it to auto-mount it?

This only happened when I started using Jaunty. The drive itself is **FAT32**.

---

### Post by ddrichardson on 2009-04-23
Plug it in and check the output of```
dmesg
```To see if there's an issue.

---

### Post by coldReactive on 2009-04-23
No issues it seems.

```
[  933.769898] usb 2-5: USB disconnect, address 4
[  937.788032] usb 2-5: new high speed USB device using ehci_hcd and address 5
[  937.922193] usb 2-5: configuration #1 chosen from 1 choice
[  937.958321] Initializing USB Mass Storage driver...
[  937.958531] scsi6 : SCSI emulation for USB Mass Storage devices
[  937.958664] usb-storage: device found at 3
[  937.958670] usb-storage: waiting for device to settle before scanning
[  937.958783] scsi7 : SCSI emulation for USB Mass Storage devices
[  937.958891] usb-storage: device found at 5
[  937.958894] usb-storage: waiting for device to settle before scanning
[  937.958910] usbcore: registered new interface driver usb-storage
[  937.958916] USB Mass Storage support registered.
[  942.956202] usb-storage: device scan complete
[  942.956248] usb-storage: device scan complete
[  942.956771] scsi 7:0:0:0: Direct-Access     SanDisk  Cruzer           8.01 PQ: 0 ANSI: 0 CCS
[  942.961137] scsi 6:0:0:0: Direct-Access     IOI      CF/MicroDrive    1.07 PQ: 0 ANSI: 0 CCS
[  942.966010] scsi 6:0:0:1: Direct-Access     IOI      SM/xD-Picture    1.07 PQ: 0 ANSI: 0 CCS
[  942.970876] scsi 6:0:0:2: Direct-Access     IOI      SD/MMC           1.07 PQ: 0 ANSI: 0 CCS
[  942.975746] scsi 6:0:0:3: Direct-Access     IOI      MS/MsPro         1.07 PQ: 0 ANSI: 0 CCS
[  942.978715] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[  942.978888] sd 6:0:0:0: Attached scsi generic sg2 type 0
[  942.980376] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[  942.980474] sd 6:0:0:1: Attached scsi generic sg3 type 0
[  942.988030] sd 6:0:0:2: [sdd] Attached SCSI removable disk
[  942.988125] sd 6:0:0:2: Attached scsi generic sg4 type 0
[  942.994386] sd 6:0:0:3: [sde] Attached SCSI removable disk
[  942.994499] sd 6:0:0:3: Attached scsi generic sg5 type 0
[  943.009862] sd 7:0:0:0: [sdf] 15682559 512-byte hardware sectors: (8.02 GB/7.47 GiB)
[  943.010329] sd 7:0:0:0: [sdf] Write Protect is off
[  943.010334] sd 7:0:0:0: [sdf] Mode Sense: 45 00 00 08
[  943.010339] sd 7:0:0:0: [sdf] Assuming drive cache: write through
[  943.049854] sd 7:0:0:0: [sdf] 15682559 512-byte hardware sectors: (8.02 GB/7.47 GiB)
[  943.051520] sd 7:0:0:0: [sdf] Write Protect is off
[  943.051525] sd 7:0:0:0: [sdf] Mode Sense: 45 00 00 08
[  943.051529] sd 7:0:0:0: [sdf] Assuming drive cache: write through
[  943.051541]  sdf: sdf1
[  943.057570] sd 7:0:0:0: [sdf] Attached SCSI removable disk
[  943.057701] sd 7:0:0:0: Attached scsi generic sg6 type 0

```

It didn't show up in mnt or on the desktop when I logged into Ubuntu though.

---

### Post by ddrichardson on 2009-04-23
It should automount in /media - is there a specific entry in /etc/fstab?

---

### Post by coldReactive on 2009-04-23
> **ddrichardson said:**
> It should automount in /media - is there a specific entry in /etc/fstab?

It isn't in media when the machine restarts and logs into ubuntu with the drive plugged in all the while. The only special entries in fstab are the SDA and SCD entries (cdrom0 for the latter.)

---

### Post by coldReactive on 2009-04-23
pysdm doesn't detect the USB Drive either when it's left plugged in before the machine boots and goes into booting.

Looks like I'll have to go to windows if I want this feature *sighs*

---

### Post by sgosnell on 2009-04-23
Search the forums for automount.  There are a few threads discussing this.

---

### Post by coldReactive on 2009-04-24
> **sgosnell said:**
> Search the forums for automount.  There are a few threads discussing this.

That's the problem, I already searched google right before I posted that issue with pysdm.

---

### Post by coldReactive on 2009-04-24
I edited the first post, I forgot to mention I'm using Jaunty, it doesn't happen in other versions of Ubuntu.

Currently though, I'm back on Windows. I can fresh install Ubuntu over again if you want me to and see if it still happens.

---

### Post by coldReactive on 2009-04-24
Yeah, when I leave the USB drive in, restart with the liveCD with it still plugged in, the Jaunty LiveCD doesn't even detect it, not in the media folder.

---

### Post by ddrichardson on 2009-04-24
I've seen three posts now remarking on this issue, I think the best thing to do is to report the bug in Launchpad.

---

### Post by coldReactive on 2009-04-24
Well, here's the bug then:

[https://bugs.launchpad.net/ubuntu/+bug/366296](https://bugs.launchpad.net/ubuntu/+bug/366296)

---

### Post by ddrichardson on 2009-04-24
Someone from the bug squad should pick it up and triage it - I'm not sure which project needs so I haven't set the package. They are likely to want you to post various outputs too.

I hope you hear something soon.

---

### Post by maharaja2 on 2009-04-24
same problem on Kubuntu 9.4 too. It can't find any USB stick

---

### Post by ddrichardson on 2009-04-24
Add your voice to the [bug report]("https://bugs.launchpad.net/ubuntu/+bug/366296"). Remember that's where devs are notified!

---

### Post by coldReactive on 2009-04-24
> **ddrichardson said:**
> Add your voice to the [bug report]("https://bugs.launchpad.net/ubuntu/+bug/366296"). Remember that's where devs are notified!

The bug report package was changed to gnome-mount, which I don't believe comes with Kubuntu by default. This also isn't about when you plug in (manually) the USB Drive either, as that's fine.

---

### Post by coldReactive on 2009-04-25
I found the problem. Seems that the module **usb_storage** was not added to /etc/modules.

add **usb_storage** on its own line in /etc/modules. it SHOULD fix the problem.

---

### Post by ddrichardson on 2009-04-25
Glad it's sorted.

---

### Post by StormRoBoT2 on 2009-04-26
help new here, how did you add usb_storage to /etc/modules?

---

### Post by ddrichardson on 2009-04-26
```
sudo echo usb_storage >> /etc/modules
```

---

### Post by StormRoBoT2 on 2009-04-26
bash: /etc/modules: Permission denied

how do i log in as root?

user name root?

---

### Post by silentknyght on 2009-04-26
> **StormRoBoT2 said:**
> bash: /etc/modules: Permission denied

how do i log in as root?

user name root?

When you use "sudo", it should ask you to input your password.

---

### Post by StormRoBoT2 on 2009-04-26
> **silentknyght said:**
> When you use "sudo", it should ask you to input your password.
```
ajwad@ajwad-laptop:~$ sudo echo usb_storage >> /etc/modules
bash: /etc/modules: Permission denied
ajwad@ajwad-laptop:~$ 
```


no its not asking :(

---

### Post by StormRoBoT2 on 2009-04-26
thanks problem solve :)

---

### Post by TheFounder on 2009-07-18
> **StormRoBoT2 said:**
> ```
ajwad@ajwad-laptop:~$ sudo echo usb_storage >> /etc/modules
bash: /etc/modules: Permission denied
ajwad@ajwad-laptop:~$ 
```


no its not asking :(


I'm seeing the same problems...


```

[    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 5f800000:9f600000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 387935
[    0.000000] Kernel command line: root=UUID=dbc07159-9276-44f6-8710-f4913c8bb243 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3466.823 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 7821760 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds

```

---

### Post by rsmereka on 2009-08-24
I just finished loading 9.04 on a Dell Vostro 420 desktop and I have no automount of usb devices. Output of dmesg follows:
```
[  120.748514] usb 2-2: new high speed USB device using ehci_hcd and address 2
[  120.891676] usb 2-2: configuration #1 chosen from 1 choice
[  120.912066] scsi10 : SCSI emulation for USB Mass Storage devices
[  120.925020] usb-storage: device found at 2
[  120.925022] usb-storage: waiting for device to settle before scanning
[  125.928010] usb-storage: device scan complete
[  125.929015] scsi 10:0:0:0: Direct-Access              Patriot Memory   PMAP PQ: 0 ANSI: 0 CCS
[  127.184877] sd 10:0:0:0: [sdb] 62554112 512-byte hardware sectors: (32.0 GB/29.8 GiB)
[  127.185374] sd 10:0:0:0: [sdb] Write Protect is off
[  127.185376] sd 10:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  127.185378] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[  127.186874] sd 10:0:0:0: [sdb] 62554112 512-byte hardware sectors: (32.0 GB/29.8 GiB)
[  127.187373] sd 10:0:0:0: [sdb] Write Protect is off
[  127.187375] sd 10:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  127.187376] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[  127.187378]  sdb: sdb1
[  127.187938] sd 10:0:0:0: [sdb] Attached SCSI removable disk
[  127.187985] sd 10:0:0:0: Attached scsi generic sg2 type 0
```This looks normal from what I can tell. This was after I inserted the usb stick after booting. The drive with the volume label appears in 'places' but I cannot launch a file browser. I suspect it's because the volume is not mounted.

As per this thread, I added
```
usb_storage
```to /etc/modules which made absolutely no difference whatsoever.

I have also read the bug 366296. The threads stop on July 23rd. What's up with that? There is a post that seems to indicate that if I downgrade "hal, libhal1, and libhal-storage1", auto-mounting will work once again. Can anyone verify this? Also, how do you do a force downgrade?

In the meantime, I have to learn how to manually mount fat32 devices. I got the device to mount but not r/w from a non-root user. I am still trying to figure out how to mount giving read/write permissions to non-root users.

Rick

---

### Post by _Ian_ on 2009-09-23
Same problem with 9.04 Ubuntu, similar dmesg - anyone found a solution that works?

```

[   70.612016] usb 1-2: new high speed USB device using ehci_hcd and address 2
[   70.745039] usb 1-2: configuration #1 chosen from 1 choice
[   70.745249] scsi2 : SCSI emulation for USB Mass Storage devices
[   70.745376] usb-storage: device found at 2
[   70.745378] usb-storage: waiting for device to settle before scanning
[   75.744213] usb-storage: device scan complete
[   75.744855] scsi 2:0:0:0: Direct-Access     ACTIONS  HS USB FlashDisk 2.00 PQ: 0 ANSI: 0 CCS
[   75.745802] sd 2:0:0:0: [sdb] 16077745 512-byte hardware sectors: (8.23 GB/7.66 GiB)
[   75.751850] sd 2:0:0:0: [sdb] Write Protect is off
[   75.751854] sd 2:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[   75.751856] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   75.757174] sd 2:0:0:0: [sdb] 16077745 512-byte hardware sectors: (8.23 GB/7.66 GiB)
[   75.757669] sd 2:0:0:0: [sdb] Write Protect is off
[   75.757671] sd 2:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[   75.757673] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   75.757677]  sdb:
[   75.830556] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   75.830637] sd 2:0:0:0: Attached scsi generic sg2 type 0

```Adding usb_storage to /etc/modules didn't improve things - at least not for me.

---

### Post by rsmereka on 2009-09-23
> **_Ian_ said:**
> Same problem with 9.04 Ubuntu, similar dmesg - anyone found a solution that works?

```

[   70.612016] usb 1-2: new high speed USB device using ehci_hcd and address 2
[   70.745039] usb 1-2: configuration #1 chosen from 1 choice
[   70.745249] scsi2 : SCSI emulation for USB Mass Storage devices
[   70.745376] usb-storage: device found at 2
[   70.745378] usb-storage: waiting for device to settle before scanning
[   75.744213] usb-storage: device scan complete
[   75.744855] scsi 2:0:0:0: Direct-Access     ACTIONS  HS USB FlashDisk 2.00 PQ: 0 ANSI: 0 CCS
[   75.745802] sd 2:0:0:0: [sdb] 16077745 512-byte hardware sectors: (8.23 GB/7.66 GiB)
[   75.751850] sd 2:0:0:0: [sdb] Write Protect is off
[   75.751854] sd 2:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[   75.751856] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   75.757174] sd 2:0:0:0: [sdb] 16077745 512-byte hardware sectors: (8.23 GB/7.66 GiB)
[   75.757669] sd 2:0:0:0: [sdb] Write Protect is off
[   75.757671] sd 2:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[   75.757673] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   75.757677]  sdb:
[   75.830556] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   75.830637] sd 2:0:0:0: Attached scsi generic sg2 type 0

```Adding usb_storage to /etc/modules didn't improve things - at least not for me.
It did not improve things for me either but it might have. You see I had disabled GDM. As soon as I re-enabled GDM and had put usb_storage into /etc/modules, auto-mounting started working. I know this might not be any help to you but...do you have GDM disabled?

Rick

---

### Post by Ferralll on 2009-09-24
I am still having this same problem.

Also some funny things happen.  
I am trying to mount a standard thumbdrive. Some times it works, some times it does not.

Often, if the mount works, it does not stay mounted, and the system constantly mounts and unmounts. 

When I use dmesg i get:
```
 [###.####] usb 4-4: new high speed USB device using ehci_hcd and address ##
``` 
(sorry I am not on my linux box right now. 
But it gives me that message with differant numbers many times.  ANd then when I run dmesg again, it will give me a new number.  

Is this the same problem?

---

### Post by _Ian_ on 2009-09-24
Just adding some more info in the hope that it may be related to my earlier problem of not being able to mount USB devices. 

I've just noticed I appear to have lost at least some of my admin privileges too.

I'm the only user of a single user system (id shows me being in the adm and admin groups).

In the System->Administration menu the commands that require a password to access them still prompt me and I can enter my password and change settings. 

But for those commands that have an unlock button, the unlock button remains greyed out and I can't change any privileged settings.

I've been playing with vnc via an ssh tunnel recently (possibly at the same time as I was already logged in to the machine locally), both running gnome sessions. Is it possible somethings been messed up by running the 2 sessions simultaneously (if I did). Or is it possible just running vnc messed things up.

Thanks in advance.

---

### Post by saucier on 2009-10-03
Same Problem here. Dmesg tells me the drive is recognised but it does not show up in nautilus and is not mounted. 
Adding usb_storage to /etc/modules did not help, Permissions are set correctly and Nautilus is also correctly configured.

---

### Post by coldReactive on 2009-10-03
I better just say it now:

You will probably have to wait until Ubuntu 9.10 comes out, and see if it works.

---

### Post by Ferralll on 2009-10-05
> **coldReactive said:**
> I better just say it now:

You will probably have to wait until Ubuntu 9.10 comes out, and see if it works.
I kinda figured that is what I would end up doing.  

Any word on when that is? 


Also, are there any good threads or post that give a good easy way to switch from one Ubuntu to another with out loosing all of my saved info, and/or personal settings? 
Not that I have a very personalized settings, but I am not too keen on re-structuring all of my files and stuff.

---

### Post by timjohn7 on 2009-10-05
Although in danger of veering off topic, I upgraded from Intrepid to jaunty using the "Upgrade" button in the Update Manager and it went flawlessly, retaining all settings, personal info and applications.

---

### Post by Ivo_Wever on 2009-10-13
Adding usb_storage to /etc/modules only has an effect after rebooting. If you want an immediate effect, you need to issue

sudo modprobe usb_storage

to load the usb_storage kernel module. Doing that immediately resulted in my usb device being detected.

My situation was rather the reverse from some others I found in the fora: if my usb drive was connected while booting, it was automounted (and would continue to be automounted when removed/replaced). If the drive wasn't present while booting, it wouldn't be detected when connecting it afterwards.

---

### Post by aminga on 2009-10-18
I just ran into this problem that USB thumb drives and cameras did not auto mount anymore.  It happened after **"Legacy USB Support"** was turned off in **BIOS**.  I enabled it in BIOS again and auto mount problem disappeared.

I also tried **pySDM** and it was not listing the USB devices when legacy USB support was still off.  This may not help everyone, but might help a few of those out there.

---

### Post by asaturn on 2009-10-30
also getting this problem after upgrading to 9.10

I can manually mount devices just fine, but they refuse to auto-mount


USB mice, keyboards, etc work just fine -- only USB storage fails to mount

arrrgh!

and what's weird -- my other computer (identical setup) with 9.10 works fine!?!?

edit: just realized I had server edition installed at one point, will this mess the settings up? right now its 9.10 64bit

---

### Post by plb on 2009-10-30
Same problem, USB storage does not automount Ubuntu 9.10 64bit

---

### Post by kija on 2009-10-30
Same Problem here too... my usb drives are not auto mounting in 9.10..:(
Can someone please help..

Thank you..

---

### Post by oshunluvr on 2009-10-31
I'm still using 9.04 and downgrading hal to 0.5.12~rc1+git20090403-0ubuntu1 (jaunty) did nothing. No cd's or usb devices automount at all. They did a week ago so something recently broke.

this is buggin the crap outa me

---

### Post by waif on 2009-10-31
I have the same problem. Ubuntu 9.10 x64. Installed on the clean computer.
Usb mouse and other devices doesn't auto-mount.

---

### Post by dekiruhito on 2009-11-01
I just wanted to add I am also running ubuntu 9.10. My SD Card through a SanDisk Mobile reader DOES work for some reason. Just not my FAT formatted drives. This is on ubuntu 8.10. I'm assuming my camera's memory card is also FAT but older since it was formatted with a Canon Digital Camera.

---

### Post by Ferralll on 2009-11-02
I am still having this problem.

It was working fine for a while... but just now it is doing it again.

What it seems to be doing is constantly trying to mount, and then unmounts. (This happens with my thumbdrive, Ipod, and SonyWalkman)

I do a dmesg, and get this:
```
[115535.687502] usb 4-4: new high speed USB device using ehci_hcd and address 67
[115538.435017] usb 4-4: new high speed USB device using ehci_hcd and address 81
[115540.614670] usb 4-4: new high speed USB device using ehci_hcd and address 92
[115541.666445] usb 4-4: new high speed USB device using ehci_hcd and address 97
[115545.161834] usb 4-4: new high speed USB device using ehci_hcd and address 115
[115548.093316] usb 4-4: new high speed USB device using ehci_hcd and address 4
[115555.548079] usb 4-4: new high speed USB device using ehci_hcd and address 43
[115557.915568] usb 4-4: new high speed USB device using ehci_hcd and address 55
[115560.847056] usb 4-4: new high speed USB device using ehci_hcd and address 70
[115563.606563] usb 4-4: new high speed USB device using ehci_hcd and address 84
[115566.162120] usb 4-4: new high speed USB device using ehci_hcd and address 97
[115569.445617] usb 4-4: new high speed USB device using ehci_hcd and address 109
[115570.497430] usb 4-4: new high speed USB device using ehci_hcd and address 114
[115573.252982] usb 4-4: new high speed USB device using ehci_hcd and address 2
[115575.576017] usb 4-4: new high speed USB device using ehci_hcd and address 9
[115580.537156] usb 4-4: new high speed USB device using ehci_hcd and address 30
[115581.025073] usb 4-4: new high speed USB device using ehci_hcd and address 32
[115581.325023] usb 4-4: new high speed USB device using ehci_hcd and address 33
[115583.467064] usb 4-4: new high speed USB device using ehci_hcd and address 39
[115585.086780] usb 4-4: new high speed USB device using ehci_hcd and address 47
[40781.834647] usb 4-4: new high speed USB device using ehci_hcd and address 67
[40782.134071] usb 4-4: new high speed USB device using ehci_hcd and address 68
[40783.185410] usb 4-4: new high speed USB device using ehci_hcd and address 73
[115606.638891] usb 4-4: new high speed USB device using ehci_hcd and address 91
[40787.459734] usb 4-4: new high speed USB device using ehci_hcd and address 98
[115613.328455] usb 4-4: new high speed USB device using ehci_hcd and address 109
[40789.649344] usb 4-4: new high speed USB device using ehci_hcd and address 113
[40789.949176] usb 4-4: new high speed USB device using ehci_hcd and address 114
[115619.397464] usb 4-4: new high speed USB device using ehci_hcd and address 120
[40791.164738] usb 4-4: new high speed USB device using ehci_hcd and address 121
[40792.591896] usb 4-4: new high speed USB device using ehci_hcd and address 2
[40796.363414] usb 4-4: new high speed USB device using ehci_hcd and address 29
[40798.335989] usb 4-4: new high speed USB device using ehci_hcd and address 52
[115641.476372] usb 4-4: new high speed USB device using ehci_hcd and address 55
[115642.152250] usb 4-4: new high speed USB device using ehci_hcd and address 58
[115643.204074] usb 4-4: new high speed USB device using ehci_hcd and address 63
[40799.985206] usb 4-4: new high speed USB device using ehci_hcd and address 67
[40801.412420] usb 4-4: new high speed USB device using ehci_hcd and address 74
[115655.201684] usb 4-4: new high speed USB device using ehci_hcd and address 91

```

---

### Post by nickwebha on 2009-11-02
Figured I would throw in my info:
[LIST]
[*]9.10 (x86_64)
[*]Running an MSI GT627-216US
[*]Three clean installs where the disk was wiped and one on a different machine
[*]Added *usb_storage* and booted but still no go
[/LIST]
What follows are the logs from two different USB flash drives:
```
[  401.520165] usb 2-2: new high speed USB device using ehci_hcd and address 6
[  401.683825] usb 2-2: configuration #1 chosen from 1 choice
[  401.705578] scsi8 : SCSI emulation for USB Mass Storage devices
[  406.745309] scsi 8:0:0:0: Direct-Access              Patriot Memory   PMAP PQ: 0 ANSI: 0 CCS
[  406.746953] sd 8:0:0:0: Attached scsi generic sg2 type 0
[  407.111829] sd 8:0:0:0: [sdb] 125304832 512-byte logical blocks: (64.1 GB/59.7 GiB)
[  407.112432] sd 8:0:0:0: [sdb] Write Protect is off
[  407.115548]  sdb: sdb1
[  407.159426] sd 8:0:0:0: [sdb] Attached SCSI removable disk
```
```
[  616.490231] usb 2-2: new high speed USB device using ehci_hcd and address 7
[  616.981376] usb 2-2: configuration #1 chosen from 1 choice
[  617.002598] scsi9 : SCSI emulation for USB Mass Storage devices
[  622.002341] scsi 9:0:0:0: Direct-Access     Corsair  UFD              0.00 PQ: 0 ANSI: 2
[  622.003594] sd 9:0:0:0: Attached scsi generic sg2 type 0
[  622.004941] sd 9:0:0:0: [sdb] 63176704 512-byte logical blocks: (32.3 GB/30.1 GiB)
[  622.005559] sd 9:0:0:0: [sdb] Write Protect is off
[  622.009317]  sdb: sdb1
[  622.291589] sd 9:0:0:0: [sdb] Attached SCSI removable disk
```
That is all I get. Granted, I do not know as much as I would like yet, however I do not see any messages about attempting to mount anything.

Edit:
I am not sure what happened but the drive now auto-mounts reliably. How odd.

---

### Post by Fsmv on 2009-11-02
> **StormRoBoT2 said:**
> bash: /etc/modules: Permission denied

how do i log in as root?

user name root?

```
sudo su
echo usb_storage >> /etc/modules

```

---

### Post by nickwebha on 2009-11-03
> **Fsmv said:**
> ```
sudo su
echo usb_storage >> /etc/modules

```

If you are still having a problem-- or just like to do things a bit differently-- you can also do "sudo gedit /etc/modules" and add "usb_storage" to the end of the file manually. "sudo" giving you root access after entering your password, "gedit" being your text editor (which can be replaced by your favorite if you have one), and "/etc/modules" being the path to the file you want to edit. You still need to reboot after this change.

---

### Post by Naegling23 on 2009-11-04
Im having the same issues, my fat formatted drives are not automounting.  I noticed that when I install ubuntu-volume-manager, they are showing up, in the disk-utility as unknown or unused.

any help please, this is a VERY high priority bug for me.

---

### Post by calif99x on 2009-11-21
This is very disappointing; I am also having the problem on 9.04 of the being unable to mount USB flash drives, even after the adding usb_storage to /etc/modules.

Overall both 9.04 and 9.10 do not seem to be at the same quality level as 8.04 & 8.10 given that my sound also stopped working with 9.04.

---

### Post by turvyc on 2009-12-18
Same problems ... Jaunty 64-bit. It's strange, usb drives were working fine, next day, nothing. I can still manually mount them, but automounting is a thing of the past. Then recently, my cd/dvd drive stopped automounting too! Again, I can manually mount it, but it is a serious PITA. 

Tried all the suggestions in this thread, as well as those in similar threads, *sans* dice.

The mystery continues ...

---

