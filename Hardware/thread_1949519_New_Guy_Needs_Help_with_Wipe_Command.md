---
title: "New Guy Needs Help with Wipe Command"
date: 2012-03-30
forum: Hardware
---

### Post by Bill Z on 2012-03-30
New Guy Needs Help with Wipe

I’m new to Ubuntu and want to use ‘Wipe’ to clean off some HDs (wipe off everything).  It shouldn’t matter but the SATA HDs are connected via a USB adapter.

Wipe runs from the terminal and needs to know what drive to wipe.  
Being new, I don’t know how to know or tell Wipe what drive to wipe.

When I do a sfdisk –l  I get the following:

Device 		Start	End 	# Cyls	# Blocks 	ID	System
/dev/sbd1	0+ 	12-	13- 	102400		7 	hpfs/ntfs
/dev/sbd2	12+	9729-	9717-	78046208 	7 	hpfs/ntfs
/dev/sbd3 	0+	 -	0-	0- 	 0 	0 	Empty
/dev/sbd4 	0+	 -	0-	0- 	 0 	0 	Empty

So, I entered the following Wipe command:
wipe –frs /dev/sbd1
And got this error
/dev/sbd1: fatal: could not lstat:  No such file or directory

What am I doing wrong or what else should I try?

---

### Post by matt_symes on 2012-03-30
Hi

Are you sure it's not

```
/dev/s**db**1
```

With the deice plugged in

```
ls /dev/sd*
```

Kind regards

---

### Post by Bill Z on 2012-03-30
Thanks.  Yes, I noticed that after I submitted the post.  I did change it to SDB and wipe did not give me an error.  Did not respond in any way.

Now, when I do sfdisk -l the disk isn't there at all.  Just what did wipe do?  I want to reformat the disk and use it again.  If sfdisk can't find it, now what?

Let me ask:  What do I need to do to do a DOD clean of the DH so I can reuse it?

Maybe wipe isn't the answer.

---

### Post by Bill Z on 2012-03-30
Looks to me that when I run Wipe using a USB adaptor to a SATA HD the OS drops the USB conntection.  sfdisk doesn't find the drive.  However, if I move the USB connector to a different USB port, it finds it but nothing was done to wipe the HD.


What do I do to wipe the 3.5 HD using my laptop with Ubuntu?

---

### Post by matt_symes on 2012-03-30
Hi

Sorry for the late reply. Been out getting a memory stick.

Let's check to see what fdisk thinks first. With the device plugged in, open a terminal and type

```
sudo fdisk -l
```

(That's a small L after fdisk). Post back results.

If it's not finding it, unplug the device and type this into the terminal

```
tail -f /var/log/syslog
```

Plug the device in and wait 10 seconds. Post back the output.

As for wiping the device, i have read the DOD has used shred. I cannot verify this though.

```
man shred
```

Kind regards

---

### Post by Bill Z on 2012-03-30
I think the root of the problem is with me using a USB adapter to this SATA drive.

Before I run a wipe the USB connection is there according to sfdisk. After I run wipe, sfdisk can't see it.  All I have to do to get sfdisk to see it again is to change the USB port.

I started using shred as you suggested.  It seems to be doing what I started out wanting done with wipe.

As you requested, I ran tail -f /var/log/syslog   Know that I got this log as shred is running.

aspire@aspire-one:~$ tail -f /var/log/syslog
Mar 30 12:34:50 aspire-one ntfs-3g[5589]: Mounted /dev/sdb1 (Read-Write, label "", NTFS 3.1)
Mar 30 12:34:50 aspire-one ntfs-3g[5589]: Cmdline options: rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077
Mar 30 12:34:50 aspire-one ntfs-3g[5589]: Mount options: rw,nosuid,nodev,uhelper=udisks,silent,allow_other,nonempty,relatime,fsname=/dev/sdb1,blkdev,blksize=4096,default_permissions
Mar 30 12:34:50 aspire-one ntfs-3g[5589]: Global ownership and permissions enforced, configuration type 1
Mar 30 12:34:53 aspire-one avahi-daemon[670]: Invalid query packet.
Mar 30 12:35:54 aspire-one avahi-daemon[670]: last message repeated 44 times
Mar 30 12:36:57 aspire-one avahi-daemon[670]: last message repeated 34 times
Mar 30 12:37:58 aspire-one avahi-daemon[670]: last message repeated 66 times
Mar 30 12:39:01 aspire-one avahi-daemon[670]: last message repeated 68 times
Mar 30 12:40:06 aspire-one avahi-daemon[670]: last message repeated 36 times
Mar 30 12:41:06 aspire-one avahi-daemon[670]: last message repeated 39 times
Mar 30 12:41:27 aspire-one avahi-daemon[670]: last message repeated 34 times
Mar 30 12:41:27 aspire-one wpa_supplicant[714]: Trying to associate with 00:0b:86:c8:c4:60 (SSID='SpringNet' freq=2462 MHz)
Mar 30 12:41:27 aspire-one NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> associating
Mar 30 12:41:27 aspire-one kernel: [18434.860150] wlan0: deauthenticating from 00:0b:86:c8:82:00 by local choice (reason=3)
Mar 30 12:41:27 aspire-one kernel: [18434.928002] wlan0: direct probe to AP 00:0b:86:c8:82:00 (try 1)
Mar 30 12:41:27 aspire-one kernel: [18434.928128] wlan0: deauthenticating from 00:0b:86:c8:82:00 by local choice (reason=3)
Mar 30 12:41:27 aspire-one wpa_supplicant[714]: Association request to the driver failed
Mar 30 12:41:27 aspire-one wpa_supplicant[714]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Mar 30 12:41:27 aspire-one NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Mar 30 12:41:27 aspire-one kernel: [18434.953983] wlan0: direct probe to AP 00:0b:86:c8:c4:60 (try 1)
Mar 30 12:41:27 aspire-one kernel: [18435.153121] wlan0: direct probe to AP 00:0b:86:c8:c4:60 (try 2)
Mar 30 12:41:27 aspire-one kernel: [18435.155217] wlan0: direct probe responded
Mar 30 12:41:27 aspire-one kernel: [18435.155239] wlan0: authenticate with AP 00:0b:86:c8:c4:60 (try 1)
Mar 30 12:41:27 aspire-one kernel: [18435.157028] wlan0: authenticated
Mar 30 12:41:27 aspire-one kernel: [18435.157269] wlan0: associate with AP 00:0b:86:c8:c4:60 (try 1)
Mar 30 12:41:27 aspire-one kernel: [18435.164325] wlan0: RX AssocResp from 00:0b:86:c8:c4:60 (capab=0x421 status=0 aid=1)
Mar 30 12:41:27 aspire-one kernel: [18435.164346] wlan0: associated
Mar 30 12:41:27 aspire-one wpa_supplicant[714]: Associated with 00:0b:86:c8:c4:60
Mar 30 12:41:27 aspire-one wpa_supplicant[714]: CTRL-EVENT-CONNECTED - Connection to 00:0b:86:c8:c4:60 completed (reauth) [id=0 id_str=]
Mar 30 12:41:27 aspire-one NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> associated
Mar 30 12:41:27 aspire-one NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed
Mar 30 12:41:28 aspire-one NetworkManager: <debug> [1333129288.001175] periodic_update(): Roamed from BSSID 00:0B:86:C8:82:00 (SpringNet) to 00:0B:86:C8:C4:60 (SpringNet)
Mar 30 12:41:32 aspire-one avahi-daemon[670]: Invalid query packet.
Mar 30 12:42:36 aspire-one avahi-daemon[670]: last message repeated 17 times
Mar 30 12:43:27 aspire-one avahi-daemon[670]: last message repeated 32 times
Mar 30 12:43:27 aspire-one wpa_supplicant[714]: Trying to associate with 00:0b:86:c8:82:00 (SSID='SpringNet' freq=2412 MHz)
Mar 30 12:43:27 aspire-one NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> associating
Mar 30 12:43:27 aspire-one kernel: [18554.852131] wlan0: deauthenticating from 00:0b:86:c8:c4:60 by local choice (reason=3)
Mar 30 12:43:27 aspire-one kernel: [18554.914797] wlan0: direct probe to AP 00:0b:86:c8:c4:60 (try 1)
Mar 30 12:43:27 aspire-one kernel: [18554.914852] wlan0: deauthenticating from 00:0b:86:c8:c4:60 by local choice (reason=3)
Mar 30 12:43:27 aspire-one wpa_supplicant[714]: Association request to the driver failed
Mar 30 12:43:27 aspire-one wpa_supplicant[714]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Mar 30 12:43:27 aspire-one kernel: [18554.950779] wlan0: direct probe to AP 00:0b:86:c8:82:00 (try 1)
Mar 30 12:43:27 aspire-one NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Mar 30 12:43:27 aspire-one kernel: [18554.952820] wlan0: direct probe responded
Mar 30 12:43:27 aspire-one kernel: [18554.952831] wlan0: authenticate with AP 00:0b:86:c8:82:00 (try 1)
Mar 30 12:43:27 aspire-one kernel: [18554.957147] wlan0: authenticated
Mar 30 12:43:27 aspire-one kernel: [18554.957218] wlan0: associate with AP 00:0b:86:c8:82:00 (try 1)
Mar 30 12:43:27 aspire-one kernel: [18554.977904] wlan0: RX AssocResp from 00:0b:86:c8:82:00 (capab=0x421 status=0 aid=1)
Mar 30 12:43:27 aspire-one kernel: [18554.977915] wlan0: associated
Mar 30 12:43:27 aspire-one wpa_supplicant[714]: Associated with 00:0b:86:c8:82:00
Mar 30 12:43:27 aspire-one wpa_supplicant[714]: CTRL-EVENT-CONNECTED - Connection to 00:0b:86:c8:82:00 completed (reauth) [id=0 id_str=]
Mar 30 12:43:27 aspire-one NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> associated
Mar 30 12:43:27 aspire-one NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed
Mar 30 12:43:28 aspire-one NetworkManager: <debug> [1333129408.000994] periodic_update(): Roamed from BSSID 00:0B:86:C8:C4:60 (SpringNet) to 00:0B:86:C8:82:00 (SpringNet)
Mar 30 12:43:41 aspire-one avahi-daemon[670]: Invalid query packet.

---

### Post by matt_symes on 2012-03-30
Hi

Is it wiping the partition ? 

Have you tried fdisk instead of sfdisk ? Is the only problem that sfdisk does not see the partition after a successful wipe ?

I can see nothing wrong in that log snippet.

Kind regards

---

### Post by Bill Z on 2012-03-30
I can't tell you what it actually does, just what I notice.  I'll go over it the steps.

Remember that I'm running Ubuntu 11.0.  The /dev/sdb drive is connected to my laptop via a USB to SATA adapter.

sfdisk -l shows the drive along with my boot drive (shows both). Also, the disk utility under System Administration shows the drives also (both /dev/sda  and /dev/sdb).

Then, under sudo -s I run wipe /dev/sdb -frs.

In 1/2 second the Prompt is back indicating it is done (I guess).
Then when I do sfdisk -l again, the drive I was trying to wipe is gone (just /dev/sda is there).  Same with the disk utility under System Administration shows only 1 drive.

Now, here is the good part.  When I change the USB adapter from the USB plug it is in to another one, both sfdisk and the disk utility under System Administration shows both again.  Also, the target drive /dev/sdb still has the partitions and files.  Nothing was done.

I can recreate this all day long, but, since you suggested shred, I can get my original job done.

---

### Post by matt_symes on 2012-04-01
Hi

Wipe is not something i use.

I can only assume the problem is with

```
sudo wipe -frs /dev/sdb
```

I can only assume the above command need a path and not a block device.

The man page 

```
man wipe
```

suggests

> wipe -kq /dev/hda3
            Assuming /dev/hda3 is the block device corresponding to the third partition of the master drive on the primary IDE interface, it will be  wiped  in  quick
            mode (option -q) i.e. with four random passes.  The inode won't be renamed or unlinked (option -k). Before starting, it will ask you to type ``yes''.

You would need

```
sudo wipe -kq /dev/sda1
```

I would be surprised is the problem was with the USB circuitry or controller of the device.

Does shred work for you ? Is that destroying the data on the drive ?

Kind regards

---

### Post by Bill Z on 2012-04-02
Also, I was running Wipe from sudo.  I tried several switches with no love.  Plus, I can recreate the problem in minutes.  I know it intimately now.

However, as I said, above, the original problem was to remove or cover up all of the data on the hard drive.  I could care less what software I used.  Wipe was recommended but caused much grief.

I am now a Shred fan (when I have the time to execute it).

---

### Post by matt_symes on 2012-04-02
Hi

Cool. I'm glad it's fixed :)

shred is a good piece of software and i've read elsewhere again, only yesterday, that it's used by the DOD so it should be secure.

Kind regards

---

