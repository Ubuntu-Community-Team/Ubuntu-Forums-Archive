---
title: "iRiver T30 MP3 player - Fedora but not Ubuntu?"
date: 2006-08-06
forum: Hardware &amp; Laptops
---

### Post by Boolean263 on 2006-08-06
Heya folks!  Nice place you've got here.  These forums have already helped me with lots of Ubuntu problems, for which I'm grateful.  I've finally got an account to ask you something I haven't yet found a solution to here.

Background: I've been using Linux for about five years now.  I started with Red Hat 7.2 and progressed up to Fedora Core 2, and as I became dissatisfied with it, a friend hooked me up with Ubuntu.  I've been using it for about a year, but I'm still kind of "pale green" when it comes to Ubuntu-specific stuff.

I got an iRiver T30MX MP3 player recently.  As purchased it uses the MTP format to put music on it, but I got [the UMS firmware update]("http://www.iriver.com/html/support/faq/sufq_view.asp?idx=387") so I could use it in Linux.  I had to apply the update at work, since I don't have access to a WinXP machine at home.  So I applied the firmware, and then tried it on my workstation at work (a Fedora Core 4 machine), and it appeared as a USB mass storage device.  Sweet.  (Tangent: the thing even plays OGG files!)

But I had no such luck when I got it home to my Dapper Drake computer!  Instead of creating a mountable /dev/sdn1 partition, it creates /dev/sg1, which is a character device and I can't use it.  Can someone help me figure out what's different between these two Linux computers, so I can make use of my new music player?

Here's the uname -a of my FC4 machine (the one that works):
```
Linux version 2.6.17-1.2141_FC4 (bhcompile@hs20-bc1-4.build.redhat.com) (gcc version 4.0.2 20051125 (Red Hat 4.0.2-8)) #1 Fri Jun 30 14:53:04 EDT 2006
```

And here's what appears in /var/log/messages when I attach the iRiver to the FC4 machine:
```
Jul 26 08:35:11 davidp1 kernel: usb 1-5: new high speed USB device using ehci_hcd and address 9
Jul 26 08:35:11 davidp1 kernel: usb 1-5: configuration #1 chosen from 1 choice
Jul 26 08:35:11 davidp1 kernel: scsi7 : SCSI emulation for USB Mass Storage devices
Jul 26 08:35:16 davidp1 kernel:   Vendor: iriver    Model: T30 Pure      Rev: 1.00
Jul 26 08:35:16 davidp1 kernel:   Type:   Direct-Access      ANSI SCSI revision: 02
Jul 26 08:35:16 davidp1 kernel: SCSI device sdb: 1017856 512-byte hdwr sectors (521 MB)
Jul 26 08:35:16 davidp1 kernel: sdb: Write Protect is off
Jul 26 08:35:16 davidp1 kernel: sdb: assuming drive cache: write through
Jul 26 08:35:16 davidp1 kernel: SCSI device sdb: 1017856 512-byte hdwr sectors (521 MB)
Jul 26 08:35:16 davidp1 kernel: sdb: Write Protect is off
Jul 26 08:35:16 davidp1 kernel: sdb: assuming drive cache: write through
Jul 26 08:35:16 davidp1 kernel:  sdb: unknown partition table
Jul 26 08:35:16 davidp1 kernel: sd 7:0:0:0: Attached scsi removable disk sdb
Jul 26 08:35:16 davidp1 scsi.agent[14843]: disk at /devices/pci0000:00/0000:00:10.3/usb1/1-5/1-5:1.0/host7/target7:0:0/7:0:0:0 
```

Just as one would hope.

Here's the uname -a output on my Ubuntu machine (the one I want it to work on, but it doesn't):
```
Linux master 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686 GNU/Linux
```

And here's the /var/log/messages output when I attach the iRiver to my Ubuntu machine:
```
Aug  6 13:06:11 localhost kernel: [17228756.740000] usb 3-4: new high speed USB device using ehci_hcd and address 8
Aug  6 13:06:11 localhost kernel: [17228756.872000] scsi2 : SCSI emulation for USB Mass Storage devices
Aug  6 13:06:16 localhost kernel: [17228761.872000]   Vendor: iriver    Model: T30 Pure          Rev: 1.00
Aug  6 13:06:16 localhost kernel: [17228761.872000]   Type:   Direct-Access                      ANSI SCSI revision: 02
Aug  6 13:06:16 localhost kernel: [17228761.872000] SCSI device sdb: 1017856 512-byte hdwr sectors (521 MB)
Aug  6 13:06:16 localhost kernel: [17228761.876000] sdb: Write Protect is off
Aug  6 13:06:16 localhost kernel: [17228761.880000] SCSI device sdb: 1017856 512-byte hdwr sectors (521 MB)
Aug  6 13:06:16 localhost kernel: [17228761.880000] sdb: Write Protect is off
Aug  6 13:06:16 localhost kernel: [17228761.880000]  sdb: unknown partition table
Aug  6 13:06:16 localhost kernel: [17228761.888000] sd 2:0:0:0: Attached scsi removable disk sdb
Aug  6 13:06:16 localhost kernel: [17228761.888000] sd 2:0:0:0: Attached scsi generic sg1 type 0

```

Not cool.

I wondered if FC4's more recent kernel was what allowed my iRiver to work there, so I [built a newer kernel package]("http://www.ubuntuforums.org/showthread.php?t=217657"), but nothing was different when I ran from that package.  I even tried comparing the .config files between the two machines, and trying to select similar options on my Ubuntu machine as are on by default in FC4, but with no luck.

The Ubuntu error message says something about an unknown partition table.  But like I said, the iRiver works just fine on another flavour of Linux, so I'm pretty certain that the problem lies somewhere in my Ubuntu setup.  I'd rather not have to do anything drastic to my MP3 player (such as fdisk'ing/fsck'ing/formatting it) if it's not strictly needed.

If anyone can help me figure out what lets it work on FC4, and how to transfer that to my Ubuntu setup, I'd be very grateful.  If you need logfiles, output from other commands, etc., just say the word.

Thanks in advance!

---

### Post by Boolean263 on 2006-08-08
Ever heard of partitionless drives before?  Me neither.  But apparently it's all the rage these days with the Microsoft gang.  Ubuntu has no problem with it; I just needed to do a
```
mount /dev/sdb /mnt/iriver
```
and it worked like a charm.

Apparently, Fedora has some hotplug workaround thingy in place.  In a way, I'm glad they do, because otherwise I'd never have known my player really does work with Linux.  But it's also kind of confusing.

Anyway, thanks for your time and consideration.  Hopefully my post can keep a few other people from falling into the same trap.

---

