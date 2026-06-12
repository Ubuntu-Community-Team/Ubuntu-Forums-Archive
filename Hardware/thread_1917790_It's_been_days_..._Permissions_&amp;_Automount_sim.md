---
title: "It's been days ... Permissions &amp; Automount simply VANISHED overnight."
date: 2012-01-30
forum: Hardware
---

### Post by WinRiddance on 2012-01-30
**Alright, I'm at wits end with this ...** :(
To my knowledge, nothing has changed on my system - except for standard updates.

I have two external USB drives that I like to **automount via mnt** with the appropriate fstab settings. I've been using these settings for the past few years and even wrote a howto tutorial on the subject right here in the forum. Never had a problem, until now. By default I always use the options for having full privileges for externally mounted USB drives since most of my personal data is contained on those drives anyway.

Well, a few days ago my two external USB drives _simply stopped allowing access_ to the data on those drives. I can't even gain read only access to view the data. The only way for me to access the external USB disks is by starting nautilus in administrative mode. Then I can click on the auto-mounted drives from there, to see the data on them. However, I can only view the data and nothing more since all files & folders are now locked. Both USB drives have the ntfs file system. When I do a sudo blkid in the terminal, all drives show up just fine ... including the two that won't grant me complete access anymore.
This has been driving me batty for almost a week.
Anyone know anything about _FORCING_ access permissions to external drives? :confused:

I've tried chmodding the files, I've tried sudo chown -R, i've tried umount even though the drives should already be automounting in the first place, and I've read at least 50+ forum posts from the Internet. Please see the screenshot too. Any help would be sincerely appreciated. Thanks in advance ...

.

---

### Post by WinRiddance on 2012-01-31
BUMMMMP ..... anyone ... ??? :(

Okay, I've completely removed the original **/mnt** mount points to include editing the fstab with nano, followed by creating new mount points with different names directly in the home/user folder. Then I rebooted. Well, that didn't work.

I also tried manually re-assigning permissions to the two external USB drives via a root terminal, which didn't work either.

Finally I downloaded and installed the Storage Device Manager via synaptic, set everything how I wanted things to be, **and even that didn't work.** This is just completely nuts !!! The additional screenshots show root access to Nautilus as well as the settings in the Storage Device Manager. _Unbelievably the settings reverted to read-only access_ after rebooting, even though the SDM is supposed to mark and enable exactly what the user set up in the preferences. It's as though my external drives have been permanently set to read-only access, no matter what I do or how I try to gain access to my own files. **The last screenshot** displays the SDM _after_ rebooting. Before rebooting the box for read-only was unchecked, then, after rebooting, the box for read-only was checked even though I had previously unchecked it and saved/applied those changes within the SDM. Geeez, not even the root terminal would permit me to by-pass, least not with my limited knowledge.[B]

Really[/B], nobody has a clue at all, nobody can help me ... ??? :(

.

---

### Post by Toz on 2012-01-31
Are the drives healthy? Can you run a chkdsk on them from a Windows system?

When you plug them in, what messages get logged to /var/log/syslog?

---

### Post by WinRiddance on 2012-01-31
Hi. Thanks for the response. I'm not really sure what I'm looking at in that log file, so here's what I did. Based on info. from another thread I went ahead and removed the fstab automount entries entirely. I also removed the /mnt directories completely and finally I removed the Disk Management program to make sure none of those settings would take over after a restart.

My system now boots up clean, my external drives check out with the disk utility, and both external USB drives mount without a problem. So the mounting issue for those two ntfs drives has been resolved in a way that I can live with. However, the read-only persists. I'm still not able to do anything but view my own content on those two external ntfs USB drives.

Directly after the restart and checking to see if the drives were mounting, I took a look at that syslog file. Since I don't really understand what I'm looking at, I copied everything from the moment of the restart. This is what that file shows me from the restart until now:

> 
Jan 31 23:20:45 winriddance-Dell anacron[1854]: Normal exit (0 jobs run)
Jan 31 23:20:48 winriddance-Dell kernel: [   41.926766] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
Jan 31 23:20:48 winriddance-Dell NetworkManager[1123]: <info> (eth0): IP6 addrconf timed out or failed.
Jan 31 23:20:48 winriddance-Dell NetworkManager[1123]: <info> Activation (eth0) Stage 4 of 5 (IP6 Configure Timeout) scheduled...
Jan 31 23:20:48 winriddance-Dell NetworkManager[1123]: <info> Activation (eth0) Stage 4 of 5 (IP6 Configure Timeout) started...
Jan 31 23:20:48 winriddance-Dell NetworkManager[1123]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Jan 31 23:20:48 winriddance-Dell NetworkManager[1123]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Jan 31 23:20:48 winriddance-Dell NetworkManager[1123]: <info> Activation (eth0) Stage 4 of 5 (IP6 Configure Timeout) complete.
Jan 31 23:20:49 winriddance-Dell dbus[1078]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Jan 31 23:20:49 winriddance-Dell dbus[1078]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
[COLOR=Navy]Feb  1 04:20:49 winriddance-Dell rtkit-daemon[1917]: Successfully called chroot.
Feb  1 04:20:49 winriddance-Dell rtkit-daemon[1917]: Successfully dropped privileges.
Feb  1 04:20:49 winriddance-Dell rtkit-daemon[1917]: Successfully limited resources.
Feb  1 04:20:49 winriddance-Dell rtkit-daemon[1917]: Running.
Feb  1 04:20:49 winriddance-Dell rtkit-daemon[1917]: Canary thread running.
Feb  1 04:20:49 winriddance-Dell rtkit-daemon[1917]: Watchdog thread running.
Feb  1 04:20:49 winriddance-Dell rtkit-daemon[1917]: Successfully made thread 1915 of process 1915 (n/a) owned by '1000' high priority at nice level -11.
Feb  1 04:20:49 winriddance-Dell rtkit-daemon[1917]: Supervising 1 threads of 1 processes of 1 users.
Feb  1 04:20:51 winriddance-Dell rtkit-daemon[1917]: Successfully made thread 1942 of process 1915 (n/a) owned by '1000' RT at priority 5.
Feb  1 04:20:51 winriddance-Dell rtkit-daemon[1917]: Supervising 2 threads of 1 processes of 1 users.
Feb  1 04:20:51 winriddance-Dell rtkit-daemon[1917]: Successfully made thread 1943 of process 1915 (n/a) owned by '1000' RT at priority 5.
Feb  1 04:20:51 winriddance-Dell rtkit-daemon[1917]: Supervising 3 threads of 1 processes of 1 users.[/COLOR]
Jan 31 23:20:56 winriddance-Dell dbus[1078]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Jan 31 23:20:56 winriddance-Dell dbus[1078]: [system] Successfully activated service 'org.freedesktop.UDisks'
Jan 31 23:20:58 winriddance-Dell kernel: [   52.005944] NTFS driver 2.1.30 [Flags: R/O MODULE].
Jan 31 23:20:58 winriddance-Dell kernel: [   52.077434] NTFS volume version 3.1.
Jan 31 23:20:59 winriddance-Dell kernel: [   52.869953] NTFS volume version 3.1.
Jan 31 23:21:00 winriddance-Dell kernel: [   54.067209] NTFS volume version 3.1.
Jan 31 23:21:03 winriddance-Dell dbus[1078]: [system] Activating service name='org.blueman.Mechanism' (using servicehelper)
Jan 31 23:21:04 winriddance-Dell blueman-mechanism: Starting blueman-mechanism 
Jan 31 23:21:04 winriddance-Dell dbus[1078]: [system] Successfully activated service 'org.blueman.Mechanism'
Jan 31 23:21:05 winriddance-Dell blueman-mechanism: loading Config 
Jan 31 23:21:05 winriddance-Dell blueman-mechanism: loading RfKill 
Jan 31 23:21:05 winriddance-Dell blueman-mechanism: loading Ppp
One thing that I noticed which struck me as very peculiar is the fact that the restart took place at 23:20 hrs. Viewing the mounts, the log file, and the content copying took place apx. 10 minutes later, at around 23:30 hrs. Yet for some weird reason there are entries which are dated February 1st, about 5 hours into the future ... ??? Hmmmm, wonder what that's all about? Well, at least the mounting is back, now I just need help figuring out how to get my full access privileges back again ...

.

---

### Post by Toz on 2012-02-01
Since these are external drives, unplug them from the computer. Open a terminal window and type in:
```
tail -f /var/log/syslog
```
...and leave this window open and visible.

Now plug in the drive and post back the messages that appear in the terminal window.

Were you able to check the drives for errors on a Windows system? I believe that it drives are not unmounted properly or contain inconsistencies, the Linux kernel will mount them as read-only (should be some sort of error message in your logs indicating this if it is the reason).

---

### Post by WinRiddance on 2012-02-01
Thanks again. Before I paste the info., I'd like to reiterate the fact that this permissions issue began overnight on three disks total, all of which are strictly external USB disks with NTFS file systems. Two of the drives are less than 6 months old and none of them receive more than an average of 4 hours usage per day. Given that three drives were affected at the same time I do not believe that there's anything physically wrong with the drives themselves. That kind of coincidence would be astronomical. But anyway, here's what I got from the terminal after plugging two of them back in:

> 
Feb  1 01:26:00 winriddance-Dell kernel: [  551.325148] usb 2-1.3: new high speed USB device number 6 using ehci_hcd
Feb  1 01:26:00 winriddance-Dell kernel: [  551.419906] scsi10 : usb-storage 2-1.3:1.0
Feb  1 01:26:00 winriddance-Dell mtp-probe: checking bus 2, device 6: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3"
Feb  1 01:26:01 winriddance-Dell mtp-probe: bus: 2, device: 6 was not an MTP device
Feb  1 01:26:01 winriddance-Dell kernel: [  552.417220] scsi 10:0:0:0: Direct-Access     WD       Elements 1023    2005 PQ: 0 ANSI: 4
Feb  1 01:26:02 winriddance-Dell kernel: [  552.527689] sd 10:0:0:0: Attached scsi generic sg2 type 0
Feb  1 01:26:02 winriddance-Dell kernel: [  552.528376] sd 10:0:0:0: [sdb] 976769024 512-byte logical blocks: (500 GB/465 GiB)
Feb  1 01:26:02 winriddance-Dell kernel: [  552.529617] sd 10:0:0:0: [sdb] Test WP failed, assume Write Enabled
Feb  1 01:26:02 winriddance-Dell kernel: [  552.530689] sd 10:0:0:0: [sdb] Asking for cache data failed
Feb  1 01:26:02 winriddance-Dell kernel: [  552.530699] sd 10:0:0:0: [sdb] Assuming drive cache: write through
Feb  1 01:26:02 winriddance-Dell kernel: [  552.534286] sd 10:0:0:0: [sdb] Test WP failed, assume Write Enabled
Feb  1 01:26:02 winriddance-Dell kernel: [  552.535357] sd 10:0:0:0: [sdb] Asking for cache data failed
Feb  1 01:26:02 winriddance-Dell kernel: [  552.535365] sd 10:0:0:0: [sdb] Assuming drive cache: write through
Feb  1 01:26:02 winriddance-Dell kernel: [  552.569558]  sdb: sdb1
Feb  1 01:26:02 winriddance-Dell kernel: [  552.572344] sd 10:0:0:0: [sdb] Test WP failed, assume Write Enabled
Feb  1 01:26:02 winriddance-Dell kernel: [  552.574225] sd 10:0:0:0: [sdb] Asking for cache data failed
Feb  1 01:26:02 winriddance-Dell kernel: [  552.574234] sd 10:0:0:0: [sdb] Assuming drive cache: write through
Feb  1 01:26:02 winriddance-Dell kernel: [  552.574241] sd 10:0:0:0: [sdb] Attached SCSI disk
Feb  1 01:26:02 winriddance-Dell kernel: [  553.311862] xhci_hcd 0000:02:00.0: WARN: transfer error on endpoint
Feb  1 01:26:02 winriddance-Dell kernel: [  553.317918] hub 3-1.3:1.0: port 4 disabled by hub (EMI?), re-enabling...
Feb  1 01:26:02 winriddance-Dell kernel: [  553.318415] usb 3-1.3.4: USB disconnect, device number 9
Feb  1 01:26:03 winriddance-Dell kernel: [  553.586144] usb 3-1.3.4: new low speed USB device number 10 using xhci_hcd
Feb  1 01:26:03 winriddance-Dell kernel: [  553.607216] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Feb  1 01:26:03 winriddance-Dell kernel: [  553.608460] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Feb  1 01:26:03 winriddance-Dell kernel: [  553.608958] usb 3-1.3.4: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
Feb  1 01:26:03 winriddance-Dell mtp-probe: checking bus 3, device 10: "/sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/usb3/3-1/3-1.3/3-1.3.4"
Feb  1 01:26:03 winriddance-Dell mtp-probe: bus: 3, device: 10 was not an MTP device
Feb  1 01:26:03 winriddance-Dell kernel: [  553.614334] input: USB Mouse as /devices/pci0000:00/0000:00:1c.2/0000:02:00.0/usb3/3-1/3-1.3/3-1.3.4/3-1.3.4:1.0/input/input15
Feb  1 01:26:03 winriddance-Dell kernel: [  553.614673] generic-usb 0003:15D9:0A41.0004: input,hidraw0: USB HID v1.10 Mouse [USB Mouse] on usb-0000:02:00.0-1.3.4/input0
Feb  1 01:26:15 winriddance-Dell kernel: [  565.807448] usb 3-2: new high speed USB device number 11 using xhci_hcd
Feb  1 01:26:15 winriddance-Dell kernel: [  565.825753] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Feb  1 01:26:15 winriddance-Dell kernel: [  565.826751] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Feb  1 01:26:15 winriddance-Dell kernel: [  565.827873] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Feb  1 01:26:15 winriddance-Dell kernel: [  565.828999] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Feb  1 01:26:15 winriddance-Dell kernel: [  565.830876] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Feb  1 01:26:15 winriddance-Dell mtp-probe: checking bus 3, device 11: "/sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/usb3/3-2"
Feb  1 01:26:15 winriddance-Dell kernel: [  565.831793] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
Feb  1 01:26:15 winriddance-Dell kernel: [  565.832182] scsi11 : usb-storage 3-2:1.0
Feb  1 01:26:15 winriddance-Dell mtp-probe: bus: 3, device: 11 was not an MTP device
Feb  1 01:26:16 winriddance-Dell kernel: [  566.836606] scsi 11:0:0:0: Direct-Access     WL1500GS A3272C                PQ: 0 ANSI: 2
Feb  1 01:26:16 winriddance-Dell kernel: [  566.866393] sd 11:0:0:0: Attached scsi generic sg3 type 0
Feb  1 01:26:16 winriddance-Dell kernel: [  566.867801] sd 11:0:0:0: [sdf] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
Feb  1 01:26:16 winriddance-Dell kernel: [  566.870493] xhci_hcd 0000:02:00.0: WARN: Stalled endpoint
Feb  1 01:26:16 winriddance-Dell kernel: [  566.871049] sd 11:0:0:0: [sdf] Write Protect is off
Feb  1 01:26:16 winriddance-Dell kernel: [  566.871060] sd 11:0:0:0: [sdf] Mode Sense: 38 00 00 00
Feb  1 01:26:16 winriddance-Dell kernel: [  566.872836] xhci_hcd 0000:02:00.0: WARN: Stalled endpoint
Feb  1 01:26:16 winriddance-Dell kernel: [  566.873396] sd 11:0:0:0: [sdf] No Caching mode page present
Feb  1 01:26:16 winriddance-Dell kernel: [  566.873406] sd 11:0:0:0: [sdf] Assuming drive cache: write through
Feb  1 01:26:16 winriddance-Dell kernel: [  566.876580] xhci_hcd 0000:02:00.0: WARN: Stalled endpoint
Feb  1 01:26:16 winriddance-Dell kernel: [  566.878866] xhci_hcd 0000:02:00.0: WARN: Stalled endpoint
Feb  1 01:26:16 winriddance-Dell kernel: [  566.879360] sd 11:0:0:0: [sdf] No Caching mode page present
Feb  1 01:26:16 winriddance-Dell kernel: [  566.879367] sd 11:0:0:0: [sdf] Assuming drive cache: write through
Feb  1 01:26:16 winriddance-Dell kernel: [  566.888213]  sdf: sdf1
Feb  1 01:26:16 winriddance-Dell kernel: [  566.892150] xhci_hcd 0000:02:00.0: WARN: Stalled endpoint
Feb  1 01:26:16 winriddance-Dell kernel: [  566.900977] xhci_hcd 0000:02:00.0: WARN: Stalled endpoint
Feb  1 01:26:16 winriddance-Dell kernel: [  566.901458] sd 11:0:0:0: [sdf] No Caching mode page present
Feb  1 01:26:16 winriddance-Dell kernel: [  566.901468] sd 11:0:0:0: [sdf] Assuming drive cache: write through
Feb  1 01:26:16 winriddance-Dell kernel: [  566.901475] sd 11:0:0:0: [sdf] Attached SCSI disk
Feb  1 01:26:16 winriddance-Dell ata_id[2374]: HDIO_GET_IDENTITY failed for '/dev/sdf': Invalid argument
Feb  1 01:26:16 winriddance-Dell kernel: [  567.273253] NTFS volume version 3.1.
Feb  1 01:26:17 winriddance-Dell kernel: [  567.601520] EXT3-fs error (device sdc1): ext3_find_entry: reading directory #2 offset 0
Feb  1 01:26:17 winriddance-Dell kernel: [  567.601571] quiet_error: 18 callbacks suppressed
Feb  1 01:26:17 winriddance-Dell kernel: [  567.601573] Buffer I/O error on device sdc1, logical block 0
Feb  1 01:26:17 winriddance-Dell kernel: [  567.601575] lost page write due to I/O error on sdc1
Feb  1 01:26:17 winriddance-Dell kernel: [  567.601576] EXT3-fs (sdc1): I/O error while writing superblock
Feb  1 01:26:17 winriddance-Dell kernel: [  567.601595] EXT3-fs error (device sdc1): ext3_find_entry: reading directory #2 offset 0
Feb  1 01:26:17 winriddance-Dell kernel: [  567.601632] Buffer I/O error on device sdc1, logical block 0
Feb  1 01:26:17 winriddance-Dell kernel: [  567.601633] lost page write due to I/O error on sdc1
Feb  1 01:26:17 winriddance-Dell kernel: [  567.601635] EXT3-fs (sdc1): I/O error while writing superblock
Feb  1 01:26:17 winriddance-Dell kernel: [  567.601640] EXT3-fs error (device sdc1): ext3_find_entry: reading directory #2 offset 0
Feb  1 01:26:17 winriddance-Dell kernel: [  567.601677] Buffer I/O error on device sdc1, logical block 0
Feb  1 01:26:17 winriddance-Dell kernel: [  567.601679] lost page write due to I/O error on sdc1
Feb  1 01:26:17 winriddance-Dell kernel: [  567.601680] EXT3-fs (sdc1): I/O error while writing superblock
Feb  1 01:26:17 winriddance-Dell kernel: [  567.601685] EXT3-fs error (device sdc1): ext3_find_entry: reading directory #2 offset 0
Feb  1 01:26:17 winriddance-Dell kernel: [  567.601722] Buffer I/O error on device sdc1, logical block 0
Feb  1 01:26:17 winriddance-Dell kernel: [  567.601723] lost page write due to I/O error on sdc1
Feb  1 01:26:17 winriddance-Dell kernel: [  567.601724] EXT3-fs (sdc1): I/O error while writing superblock
.

**Also** ... Since all entries have been removed from the fstab and since the corresponding mnt directories have been removed as well, these drives now show up in the mtab file instead. For example, the Primary_Media disk with NTFS file system shows up like this in the /etc/mtab file:

> /dev/sdf1 /media/PRIMARY_MEDIA ntfs ro,nosuid,nodev,uid=1000,gid=1000,dmask=0077,fmask=0177,uhelper=udisks$

I've tried changing dmask and fmask to 0000 and 1111 to make everything executable but that didn't give me access either because as soon as I rebooted the ro permissions were back in place. Tried removing them from the mtab followed by rebootingt but that didn't have any effect at all. I'm wondering if this whole problem could have something to do with the fact that I had 2 USB cameras connected for a week 24 X 7, with a couple of reboots involved as well. When I noticed that, i removed the cameras from the USB ports. Thinking back now, maybe that's when this whole mess with the permissions began ... Totally baffled at this point ...

---

### Post by Toz on 2012-02-01
There are some interesting log entries:
> Feb 1 01:26:02 winriddance-Dell kernel: [ 552.569558] sdb: sdb1
Feb 1 01:26:02 winriddance-Dell kernel: [ 552.572344] sd 10:0:0:0: [sdb] Test WP failed, assume Write Enabled
Feb 1 01:26:02 winriddance-Dell kernel: [ 552.574225] sd 10:0:0:0: [sdb] Asking for cache data failed
**Are these drives connected directly to the computer or are you going through some sort of USB hub? **

> Feb 1 01:26:02 winriddance-Dell kernel: [ 553.311862] xhci_hcd 0000:02:00.0: WARN: transfer error on endpoint
USB3 issues? See: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/647973]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/647973")
**Can you try plugging them into a USB2 port?**

> Feb 1 01:26:02 winriddance-Dell kernel: [ 553.311862] xhci_hcd 0000:02:00.0: WARN: transfer error on endpoint
Related? [https://answers.launchpad.net/ubuntu/+source/util-linux/+question/170351]("https://answers.launchpad.net/ubuntu/+source/util-linux/+question/170351")

> Feb 1 01:26:16 winriddance-Dell ata_id[2374]: HDIO_GET_IDENTITY failed for '/dev/sdf': Invalid argument

> Feb 1 01:26:17 winriddance-Dell kernel: [ 567.601520] EXT3-fs error (device sdc1): ext3_find_entry: reading directory #2 offset 0
Feb 1 01:26:17 winriddance-Dell kernel: [ 567.601571] quiet_error: 18 callbacks suppressed
Feb 1 01:26:17 winriddance-Dell kernel: [ 567.601573] Buffer I/O error on device sdc1, logical block 0
Feb 1 01:26:17 winriddance-Dell kernel: [ 567.601575] lost page write due to I/O error on sdc1
Feb 1 01:26:17 winriddance-Dell kernel: [ 567.601576] EXT3-fs (sdc1): I/O error while writing superblock

**What updates did your system receive in the last day or so that may have precipitated this problem? Did you get a new kernel update? If so, maybe you can try booting the previous kernel for trouble-shooting purposes.**

---

### Post by WinRiddance on 2012-02-01
Good morning. I'm attaching some screenshots from where I've gotten between last night and this morning. I did check your posted links but none of them applied since the USB 3.0 issues should have been resolved with the release of *buntu 11.04 (I'm running 11.10 like you) and since my USB 3.0 worked perfectly for a couple of months without any issues whatsoever.

One of those threads also mentioned Ext3/Ext4 partitions and oddly enough I have no problem at all with one of the "problem drives" once I converted it to Ext3. The Ext3 converted drive mounts just like the other two, exception being that I have ownership and that I can do with that drive whatever I want. My system was completely shut off for 15 minutes after I cleaned everything up, and after I unmounted everything. Then I powered up again ....

... **All drives mount as they should**, being visible in /media/drivelabel. No errors during bthe boot process either. The converted Ext3 disk behaves as it should, belonging to me with permissions. The other two (NTFS) disks still show up as read only. Even gksu nautilus won't let me change anything although I'm clearly recognized as the owner of those disks (see screenshots). Some inner tick has simply locked those drives into read-only mode. Nuts, nuts, nuts ... ](*,)

The two problem drives are (and have been) mounted directly into the USB 3.0 ports because I don't think there's such a thing as USB 3.0 hubs (yet). Those drives are actually USB 3.0 disks. Got them because of the (noticeably) faster transfer speed. I can't check my USB 2.0 port compatibility until Saturday because I had to start getting caught up on other tasks which are going to prevent me from removing/adding any disks until I'm done. **YES** ... there was a kernel update, I think around the same time that these issues started, but I won't be able to check another kernel until Saturday either. :(

In the meantime, I'd appreciate any other info. that someone can offer. Thank you so much.

.

---

### Post by Toz on 2012-02-01
> YES ... there was a kernel update, I think around the same time that these issues started, but I won't be able to check another kernel until Saturday either.It would be interesting to see if using the previous kernel brings back the functionality you had. Perhaps a bug in the new kernel? Let me know how it goes on Saturday.

---

### Post by WinRiddance on 2012-02-03
Alright, here again since I got everything that I was backed up on finished. I'm going to mark this thread as solved because I implemented a solution that can work for others, as long as they're not "die hard ntfs" users. It definitely works for me.

**The USB 2.0 versus USB 3.0 didn't make a difference**. The last two drives that I was trying to correct the permissions on were each using one of these. Swapping them and rebooting made no difference either. I did revert back to the previous kernel, but that too made no difference whatsoever. Searched the Internet high and low for identical problems, only to find out that Linux is supposed to have some type of built-in safety mechanism which can activate itself, based on certain hard disk related conditions in order to protect the data from being misused. I can't elaborate on that though, since I don't know enough about Linux to fully comprehend what I was reading. _This behavior does not appear to be a bug though,_ just some kind of internal safety which then forces the read-only situation to take effect. I'm sure someone who really knows their way around the "guts" within Linux would probably know how to correct this easily & quickly in a matter of minutes ... but those are more than likely not the kind of Linux Gurus that you'd ever find on an Ubuntu forum ... ;)

Anyway, if this ever happens to you, the loss of your NTFS permissions in an Ubuntu based system, you really only have one of two choices. Either split a partition where one part is dedicated strictly to Windoze for nothing but Windoze related stuff, and the other part for nothing but your Ubuntu related stuff. If you need to transfer files back and forth from one to the other, get in the habit of using a USB stick, just to be safe. Of course you can transfer from *buntu directly to the Windoze partition too, I'm just talking about a situation like this, where full access to your NTFS is no longer possible for some reason.

**The Ultimate solution though** (unless you're a hard core Windoze gamer who's so addicted that you can't do without Windows) is to just save all of your data ... buy or borrow another disk if you need to ... followed by dumping everything you have on freshly formatted Ext3 or Ext4 partitions/drives _to which you claim ownership when you initiate the formatting_ process (with Disk Utility). There's a box for that, just put a checkmark there, then start the formatting. You'll end up with full privileges and since you've claimed ownership the drive(s) will even mount automatically during restarts. No need to edit fstab ...

I used Windoze for almost 20 years. There's nothing, I mean there's no Windoze program out there (aside from games) that can't be replaced with a similar or even better *buntu alternative. Yeah, after 12 years with Photo Shop and Paint Shop Pro the Gimp was a pain for me to get used to, but now I wouldn't dream of ever using anything else. Browsing, Editing, Publishing, you name it ... top notch professional software is available and it's even free. Just because the manufacturer of your system dumped Windoze on your machine ... doesn't mean that you have to use it. The last 4 computers that I bought all had Windoze. It never hurt my feelings to ignore that .... anf if you're worried about your warranty simply create a new partition on the disk and run your *buntu from a dual-boot setup. Keep the Windoze partition just as big as needed, perhaps 20 - 25 GB in size.
**Linux rocks and Linux *buntus rule!**

:lolflag:

---

### Post by mac67 on 2012-02-05
> **WinRiddance said:**
> Alright, here again since I got everything that I was backed up on finished. I'm going to mark this thread as solved because I implemented a solution that can work for others, as long as they're not "die hard ntfs" users. It definitely works for me.

**The USB 2.0 versus USB 3.0 didn't make a difference**. The last two drives that I was trying to correct the permissions on were each using one of these. Swapping them and rebooting made no difference either. I did revert back to the previous kernel, but that too made no difference whatsoever. Searched the Internet high and low for identical problems, only to find out that Linux is supposed to have some type of built-in safety mechanism which can activate itself, based on certain hard disk related conditions in order to protect the data from being misused. I can't elaborate on that though, since I don't know enough about Linux to fully comprehend what I was reading. _This behavior does not appear to be a bug though,_ just some kind of internal safety which then forces the read-only situation to take effect. I'm sure someone who really knows their way around the "guts" within Linux would probably know how to correct this easily & quickly in a matter of minutes ... but those are more than likely not the kind of Linux Gurus that you'd ever find on an Ubuntu forum ... ;)

...


Hi, I am struggling with a very similar problem, I cannot copy on external hard drive (but can copy on 4GB USB pen drive) from Ubuntu 11.10 64 bit. I cannot even copy into the Windows 7 partition. I can copy on the same external drives when I am in Ubuntu on an older PC though, running Kubuntu 11.04.

So, I wonder why the "data protection" procedure has taken place in the new Ubuntu version while not active with the old one. Just kernel?

I do not like [COLOR=Red]at all[/COLOR] the idea to separate the partition in a "Windows stuff" and a "Linux stuff" container. One thing I like in Ubuntu is that it reads Windows partition. Unfortunately "the rest of the world" uses Windows and I have somehow to interact with them. I am sure many Linux users also have to. If Linux becomes an isolated system, unable to talk to Windows partition, I see bad days for it.

---

### Post by WinRiddance on 2012-02-06
Hi Mac67.
I don't mean to be rude, but part of what you say has to do with your lack of knowledge about computers. Most people switch to Linux/Ubuntu for more than one reason and usually those reasons have to do with these facts ... Linux is more stable, Linux is more secure, with Linux you won't have viruses, Linux has no registration or licensing requirements (use it on as many computers as you like), and finally, Linux is free as opposed to costing hundreds of dollars for the Operating System. You can possibly save even thousands of dollars more by not having to _purchase expensive third party software._ Last time that I purchased Microshaft Office and Adobe Photoshop several years ago, both programs cost me $1100 dollars. If I could switch to Linux 100% after 20 years with Windows, I dare say that ANYONE can make the switch. Think about that.

Just imagine what would happen if Linux actually advertised on TV like other companies. Microshaft would lose tens of millions of dollars in revenue. The tide is already (finally) turning though as there are now literally hundreds of millions of people Worldwide who use Linux in one form or another ... Word of mouth has started spreading around like wildfire in the past 2 - 3 years and it's only getting better. Some computer manufacturers are even selling computers with Linux now. That was pretty much unheard of just 5 years ago.

**As far as the problems that you mention are concerned** ... think about this. Also, please read this entire thread one more time, slowly and carefully, because all of your answers can be found if you're willing to read. I'm curious though, what makes you think that you need Windows at all? As I said in an earlier thread ... just use Gparted to make your Windows partition as small as possible and then use your Ubuntu for everything else. _Your personal data files don't care_ if the partition you're using is FAT32, NTFS, EXT3, EXT4, whatever. That's because they're raw data files which are just being stored on the machine. It's only the System files for the Operating System itself, as well as proprietary third party software installations that require specific file systems and procedures. That's why I converted all of my drives to Ext3 ... since I can use all of my personal Windows/Office files, photos, graphics, movies, music, browser bookmarks (favorites), email, and just about everything else directly from my *Ubuntu setup. I only know three people whom I interact with who have Windows on their machines. If I ever need to do anything Windows related with them for whatever reason, a USB stick will be all that I'll need for that. So again, consider what I said before and also in this reply ... YOU REALLY DON'T NEED WINDOWS AT ALL ANYMORE ... and without Windows, your hard disk & access issues are over instantly!
Only addicted hard core gamers with their precious Windows games *MUST* have Windows ... :D

.

---

### Post by mac67 on 2012-02-06
> **WinRiddance said:**
> Hi Mac67.
I don't mean to be rude, but part of what you say has to do with your lack of knowledge about computers. Most people switch to Linux/Ubuntu for more than one reason and usually those reasons have to do with these facts ... Linux is more stable, Linux is more secure, with Linux you won't have viruses, Linux has no registration or licensing requirements (use it on as many computers as you like), and finally, Linux is free as opposed to costing hundreds of dollars for the Operating System.

... 

**As far as the problems that you mention are concerned** ... think about this. Also, please read this entire thread one more time, slowly and carefully, because all of your answers can be found if you're willing to read. I'm curious though, what makes you think that you need Windows at all? As I said in an earlier thread ... just use Gparted to make your Windows partition as small as possible and then use your Ubuntu for everything else. _Your personal data files don't care_ if the partition you're using is FAT32, NTFS, EXT3, EXT4, whatever. That's because they're raw data files which are just being stored on the machine. It's only the System files for the Operating System itself, as well as proprietary third party software installations that require specific file systems and procedures. That's why I converted all of my drives to Ext3 ... since I can use all of my personal Windows/Office files, photos, graphics, movies, music, browser bookmarks (favorites), email, and just about everything else directly from my *Ubuntu setup. I only know three people whom I interact with who have Windows on their machines. If I ever need to do anything Windows related with them for whatever reason, a USB stick will be all that I'll need for that. So again, consider what I said before and also in this reply ... YOU REALLY DON'T NEED WINDOWS AT ALL ANYMORE ... and without Windows, your hard disk & access issues are over instantly!
Only addicted hard core gamers with their precious Windows games *MUST* have Windows ... :D

.

Hi, I must correct you: [COLOR=Red]much[/COLOR] of what I say is due to my lack of knowledge of computers. Therefore, I have to read very carefully all posts to see if I understand what is the solution to my problem. However...

I have not seen one .doc file, so far, that is not messed up when opened with Open Office, and viceversa: fonts, position of figures, whatever is not as in the original file. I do not complain with Ubuntu or Open Office, but, since I have to interact with many people who use Windows (and even MAC), I need full compatibility.And, unfortunately, this is not yet the case.

I had no problem (and still have none) with Ubuntu 11.04 on the older laptop: it reads the external drive, no matter if EXT3, EXT4 or NTFS. But the same external drive is not read by Ubuntu 11.10 64 bit on the new laptop. In my opinion Ubuntu makes a step back if people, who are not Linux geeks, have to learn about kernel, setting permissions, etc. "Linux for human beings", if I remember correctly.

---

### Post by WinRiddance on 2012-02-07
> **mac67 said:**
> I have not seen one .doc file, so far, that is not messed up when opened with Open Office, and viceversa: fonts, position of figures, whatever is not as in the original file. I do not complain with Ubuntu or Open Office, but, since I have to interact with many people who use Windows (and even MAC), I need full compatibility.And, unfortunately, this is not yet the case.

You would have full compatibility if you installed the Microshaft core fonts package. I'm surprised that you haven't checked for fonts in the Software Center yet, because if you did you'd find the core fonts with Arial and so on in order to make your docs look the same with both Office programs. Lack of knowledge by the user should never be blamed on the Operating System. All of my docs look almost identical no matter which computer or OS is being used ... but part of that has to do with the fact that I only use fonts which are recognized across the board. Where you do find a large difference is between old outdated versions of MS Office such as Office95 or Office97 and the current OpenOffice or LibreOffice. That too would be blamed on the user though, for not updating software that's over 10 years old.

Data security on a hard disk is never a step back. That is quite a foolish remark to make ... the kind of remark that someone would make who can't be bothered to learn a few new things and a few extra tricks. If you bothered to spend more time to learn, you'd find out that you can do everything identical and better with *buntu while remaining completely compatible. Believe me, as a 20 year long Windoze user on a professional level, having used every single version of Windoze since version 3.0, I know what I'm talking about. Click on the next line, that post should be able to solve your hard disk permissions issues:
**[http://ubuntuforums.org/showthread.php?t=1916069](http://ubuntuforums.org/showthread.php?t=1916069)**

You could always open your file manager as root after restarting. That should give you full access but it's not really recommended to do that. After every restart just open your terminal and enter **gksu nautilus** which will open the file manager in administrative/rot mode. The gksu nautilus command will prompt you for your regular password that you created when you installed Ubuntu. If you're using [COLOR=Navy]**X**[/COLOR]ubuntu or [COLOR=Navy]**K**[/COLOR]ubuntu that command won't work since they have different default file managers.

Last but not least .... I don't even know any professionals any more (and I know quite a few of them) who still use that old .doc format which anyone can alter, change, resave as their own, and so on. Most professional documents these days are saved as PDF files because they're not only _universally cross-compatible,_ but also because they're much harder to change, resave, etc. PDF is a much safer way to have business files, especially if you're emailing such files. Luckily both OpenOffice and LibreOffice (same thing) enable the author to export a doc file directly as a PDF document. To my knowledge the same applies to xls documents. Besides, if you convert docs to universally viewable PDF files ... your clients, friends, or family would never even know which Office program was used to create that file in the first place.

**Full compatibility is definitely there.** You just have to be willing to take a little time to learn, and maybe do a little bit of your own research too. Again, I used windows professionally for 20 years and know exactly what I'm talking about. Isn't it worth a little effort if it'll provide you with a more stable, more secure, and a completely free system?

.

---

### Post by mac67 on 2012-02-07
> **WinRiddance said:**
> You would have full compatibility if you installed the Microshaft core fonts package. I'm surprised that you haven't checked for fonts in the Software Center yet, because if you did you'd find the core fonts with Arial and so on in order to make your docs look the same with both Office programs. Lack of knowledge by the user should never be blamed on the Operating System. All of my docs look [COLOR=Red]almost[/COLOR] identical no matter which computer or OS is being used ... but part of that has to do with the fact that [COLOR=Red]I only use fonts[/COLOR] which are recognized across the board. Where you do find a large difference is between old outdated versions of MS Office such as Office95 or Office97 and the current OpenOffice or LibreOffice. That too would be blamed on the user though, for not updating software that's over 10 years old.



As you say, almost. That's what I mean. And if you work with other people, no matter what you do, [COLOR=Red]they[/COLOR] will send you files with other fonts. So what? Will you teach them all to use Ubuntu? I love Ubuntu, but it seems to go back in terms of ease of use.

> **WinRiddance said:**
> 

Data security on a hard disk is never a step back. That is quite a foolish remark to make ... the kind of remark that someone would make who can't be bothered to learn a few new things and a few extra tricks. If you bothered to spend more time to learn, you'd find out that you can do everything identical and better with *buntu while remaining completely compatible.



Data security introduced in new versions without prompting solutions is a step back if you want to bring "Linux to human beings". The problem I have does not appear with Ubuntu 11.04. Is Ubuntu 11.04 not secure? Was the problem so big? Then prompt a message that helps people to solve their problem.

> **WinRiddance said:**
> 
Last but not least .... I don't even know any professionals any more (and I know quite a few of them) who still use that old .doc format which anyone can alter, change, resave as their own, and so on. Most professional documents these days are saved as PDF files because they're not only _universally cross-compatible,_ but also because they're much harder to change, resave, etc. PDF is a much safer way to have business files, especially if you're emailing such files. Luckily both OpenOffice and LibreOffice (same thing) enable the author to export a doc file directly as a PDF document. To my knowledge the same applies to xls documents. Besides, if you convert docs to universally viewable PDF files ... your clients, friends, or family would never even know which Office program was used to create that file in the first place.


If you write files and send them to other people who may need to modify them, I suppose you do not send them as PDF. That's what I mean when I say I have to interact with people. I guessed that should be clear to anyone working with computers on a day-to-day basis.

---

### Post by mac67 on 2012-02-07
> **WinRiddance said:**
> 

**[http://ubuntuforums.org/showthread.php?t=1916069](http://ubuntuforums.org/showthread.php?t=1916069)**


.
Thanks for this link, I'll let you know if it works.

---

### Post by WinRiddance on 2012-02-07
> **mac67 said:**
> If you write files and send them to other people who may need to modify them, I suppose you do not send them as PDF. That's what I mean when I say I have to interact with people. I guessed that should be clear to anyone working with computers on a day-to-day basis.

**Well, it wasn't clear to me** because as a professional with massive (not kidding) desktop publishing & internet experience, I've almost never in the past 20 years had to send anyone editable files. Regardless if business cards, brochures, flyers, form pages, spreadsheets, catalog merchandise pages, business letters, php, html, xhtml, css, javascript, and so on ... people receive either a finished product from me, or a draft. If's a draft with some issues, I'd receive an email or a phone call back from them letting me know that this paragraph or that line needs to be corrected/changed.

I've also done tons and tons of image work, probably with around 50.000 or more images during the past 20 years, usually for commercial purposes which was so specialized that no one but me could do any additional editing on those images to begin with. More edmails or phone calls if thiongs weren't perfect. So I'm sorry to say that I don't have a clue as to what kind of a file (aside from email) anyone would possibly have to send someone else for editing purposes. And that on a regular/frequent basis no less. Even our Son who's in an Online High School for languages never sends files back and forth between himself and the instructors, which require cross-editing between the involved parties. I would be very interested in knowing specifically what kind of doc or xls files could possibly require editing by more than one party? You also ignored my comments about PDF files altogether ...

Yeah, I know this probably sounds a bit snotty, but it rubbed me wrong when you said that your needs should be oh so clear to anyone working with computers on a day to day basis. **Say what** ???  I've been working with them since 1991 and as someone who thinks that I'm not a complete moron, your comments about identical doc requirements weren't clear to me at all. Furthermore, when I stated almost identical, I meant that the files were so close that the difference was virtually nill i.e. hardly noticeable. _Where I have found differences_ in the past, even amongst Windows based doc and xls files, was when someone had a different page default size set up from mine. Then I would find huge changes in the entire layout at times, either because my file was attempting to conform to another person's default page layout, or vice versa. The last time that I had to deal with something like that was over 10 years ago though. Well guess what? **That's actually one of the main reasons** why PDF documents were ever introduced ... to ensure complete conformity regardless what kind of OS or business software was being used. PDF is PDF, the same on all machines with PDF viewing/printing capabilities.

Well, whatever, this thread's obviously been beaten to death, now completely off-topic as well. This'll be it for me. Good luck with your file permissions issues and everything else.

---

### Post by mac67 on 2012-02-07
> **WinRiddance said:**
> **Well, it wasn't clear to me** because as a professional with massive (not kidding) desktop publishing & internet experience, I've almost never in the past 20 years had to send anyone editable files.


Good for you that you do not need to send editable files. But people who work in offices, schools, places where many hands contribute to documents, produce files that fly around from pc to pc many times. That seems obvious to me, but if it is not, well, I am wrong.

You don't have to convince me that Microshaft, as you like to call it, has some defects, so to say. For instance, I sent a 2007 Word file to a user with Mac Office 2008 and equations were converted into images. You may ask "why write equations with Word when you have LaTeX?", but again, I have to fit with the rest of the world, since the rest of the world doesn't fit to me.

> **WinRiddance said:**
> 
Well, whatever, this thread's obviously been beaten to death, now completely off-topic as well. This'll be it for me. Good luck with your file permissions issues and everything else.

Back to my problem: if Ubuntu is "Linux for human beings" I cannot  understand why a filesystem that is OK with Ubuntu 11.04 becomes  "read-only" in Ubuntu 11.10 and one has to be a Linux geek to modify  this situation. What has this with data security to do?

---

### Post by mac67 on 2012-02-07
> **WinRiddance said:**
> You also ignored my comments about PDF files altogether ...



I know little about root operations and system administration, but I am not so stupid not to see that Word and Open(Libre)office offer the possibility to export the document as a PDF file. I just skipped that since I considered it irrelevant for our discussion. I have been working for about 20 years in physics research, using Windows, Linux (Suse and Red Hat) and Mac. I mention this just to make clear that I know how to use computers. But I am not a system administrator. And frankly, I do not want to be, that's why I choose Ubuntu instead of, say, Suse.

---

### Post by mac67 on 2012-02-08
> **WinRiddance said:**
> Click on the next line, that post should be able to solve your hard disk permissions issues:
**[http://ubuntuforums.org/showthread.php?t=1916069](http://ubuntuforums.org/showthread.php?t=1916069)**

.

I read the posts in the link, but I do not find a solution in there. I checked the fstab file in the old and new laptops: they are basically identical.

Both have the Ubuntu partition and the swap area. The ftsab file in the old laptop also has the cdrom drive. None has instructions for removable drives. :confused:

---

### Post by mac67 on 2012-02-09
I solved my problem, Windows 7 had changed permissions when I first plugged the external drives in. I changed privileges and now I can copy files fromn Ubuntu into those NTFS partitions.

It happens that people who know little about system administration find solutions, too.

---

### Post by Hudy on 2012-02-24
As a good netizen, I make it a personal policy, and a basic tenet of my philosophy, to not intrude on others' flame wars.  One very good sign of such is the signet phrase "I don't mean to be rude..........".  But for this one, I must make an exception.

Mac67, I hope you see this.  You have nothing to be in ashamed about, not in the slightest degree.  I have never seen a genuine Ubuntu fanboi before now; not in the modern definition of the term (dyed-in-the-wool, true-blue hyperbolic presence on the 'net) --- extremism exceeded only by the degree to which OpenOffice itself is exalted as the One True Path(TM).

Mac67, your statements re interop of document formats is entirely correct.  I won't cite the many (many!) examples of this being a problem through web history. It's one of the most painful aspects of my job as a Senior IT Architect for the largest hardware+software+services providers in the world.  It's so easy to debunk this type of argument that I won't go there.

I also won't cite my own "decades-long career consulting with Fortune 100 companies" while running Linux myself for most of that time (full-time, every day, as is, was, and ever shall be, amen) and having run UNIX on a Northgate '386 computer with 4MB of RAM at home in 1989. Street Cred? I don't much care.

Because those things have nothing to do with your problem, or your situation.  As does the non sequitur regarding ODF formats.

A few basic facts:

/etc/mtab is not an editable file.  It's the real-time representation of what the OS thinks is mounted.  Use the command (no quotes) "cat /proc/mounts" (in a "terminal") to see the same info.  Editing this file is pointless.

When an NTFS filesystem is mounted read-only, there are only a few reasons possible for that occurrence:

a)  the NTFS file system was 'hibernated' (implying dual-boot? we don't know, OP was remiss in not giving any specific technical information at all)

b)  the NTFS journal(s) is/are 'unclean' (e.g., power loss to the machine)

c)  /etc/fstab contains options for each specific partition that include 'ro' (I think we can rule this out)

d) Late-breaking news.  It may be a kernel regression - it's present not only in Oneiric, but in Precise (12.04).  See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/925760](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/925760)

Running the 'mount' command from a terminal will show you whether a filesystem has been mounted 'rw' or 'ro' (latter being, obviously, read-only).

I'm done.  As I said I don't like to intrude, and I won't be answering any responses to this post.  There's far more important work to be done.  But this was like the horse that threw Christopher Reeve - the horse was (likely) not nearly as intelligent, but nonetheless the damage was done. 

Mac67, live long and prosper.

As Blaise Pascal said....if I had more time, this would not have been so long. 

/B

---

