---
title: "HP photosmart printer locks up"
date: 2009-11-14
forum: Hardware
---

### Post by miked2 on 2009-11-14
For some time now, I have had a problem with my HP photosmart 7450 under linux.  

After printing 1 or 2 pages, it locks up & doesn't respond anymore, reporting "Device communication error (5012), it's also unresponsive to front-panel button presses & impossible to switch off by the power switch button.  The only way to get it out of its locked-up state is to cycle the power, after which it's possible to print maybe 1 or 2 pages before locking up again.  

Something that gets it locked immediately is using the HP Device Manager (hp-toolkit) to align cartridges, clean cartridges, or print test page, although the other HP Device Manager functions appear to work without problem (those on the Status, Supplies, Print Settings and Printer Control tabs of the HP Device Manager GUI).  
I've tried using different USB ports & a different USB lead without success.

I have had this printer working on an earlier version of Ubuntu (07.10 I think) and before that on debian both with hplip.  Now I get the same problem when using this with debian Lenny and ubuntu Karmic.  It works without any problems on Windows so I know that the printer isn't damaged.  

I've found several other people having exactly the same problem, but none of the suggestions given so far have produced a significant improvement. 
[http://ubuntuforums.org/showthread.php?t=1089641&highlight=photosmart+7450]("http://ubuntuforums.org/showthread.php?t=1089641&highlight=photosmart+7450")
[http://ubuntuforums.org/showthread.php?t=809469&highlight=photosmart+7450]("http://ubuntuforums.org/showthread.php?t=809469&highlight=photosmart+7450")
[http://ubuntuforums.org/showthread.php?t=1083905&highlight=photosmart+7450]("http://ubuntuforums.org/showthread.php?t=1083905&highlight=photosmart+7450")
[http://ubuntuforums.org/showthread.php?t=904474&highlight=photosmart+7450]("http://ubuntuforums.org/showthread.php?t=904474&highlight=photosmart+7450")

I did raise a [bug report]("https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/241781") 1.5 years ago, a few other people seemed to be having the same problem there as well.  I thought it was working fine for a while after installing Ibex, as the problem didn't seem to show up immediately.  
Now I'm not so sure that this is a software bug, but possibly a configuration issue?  I'm hoping that there's someone that can take a look at my hp-check and my printingbuginfo outputs & immediately spot the problem.  

hp-check reports that cupsddk is missing, yet synaptic shows that I have cupsddk 1.4.1-5ubuntu2.1 installed.

Here's a typical sequence of events, starting with the printer locked up.  

I cycle printer power to get the printer responding, & message log reports:
```

Nov 14 16:21:10 badger kernel: [71518.217493] usb-storage: device scan complete
Nov 14 16:21:31 badger kernel: [71539.112032] usb 6-1: reset full speed USB device using uhci_hcd and address 59
Nov 14 16:21:46 badger kernel: [71554.224037] usb 6-1: device descriptor read/64, error -110
Nov 14 16:22:01 badger kernel: [71569.448031] usb 6-1: device descriptor read/64, error -110
Nov 14 16:22:17 badger kernel: [71584.776032] usb 6-1: device descriptor read/64, error -110
```

Attempt to print from an application, but printer has locked up

```
Nov 14 16:28:13 badger kernel: [71940.536039] usb 6-1: new full speed USB device using uhci_hcd and address 64
Nov 14 16:28:13 badger kernel: [71940.734216] usb 6-1: configuration #1 chosen from 1 choice
Nov 14 16:28:13 badger kernel: [71940.745224] usblp0: USB Bidirectional printer dev 64 if 0 alt 0 proto 2 vid 0x03F0 pid 0xB802
Nov 14 16:28:13 badger kernel: [71940.745452] scsi22 : SCSI emulation for USB Mass Storage devices
Nov 14 16:28:14 badger kernel: [71941.875519] usb 6-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
Nov 14 16:28:16 badger udev-configure-printer: Re-enabled printer ipp://localhost:631/printers/Photosmart-7400-series
Nov 14 16:28:16 badger udev-configure-printer: Re-enabled printer ipp://localhost:631/printers/Photosmart_7400
Nov 14 16:28:16 badger kernel: [71944.155568] usblp0: removed
Nov 14 16:28:18 badger kernel: [71945.765580] scsi 22:0:0:0: Direct-Access     HP       Photosmart 7400  1.00 PQ: 0 ANSI: 2
Nov 14 16:28:18 badger kernel: [71945.770079] sd 22:0:0:0: Attached scsi generic sg4 type 0
Nov 14 16:28:18 badger kernel: [71945.795562] sd 22:0:0:0: [sdc] Attached SCSI removable disk
```

Now attempt to print, succeeds
print again, succeeds, but now message log shows:

```
Nov 14 16:54:03 badger kernel: [73491.293051] usblp0: removed

```
print again, this time it fails, message log reports - 

```
Nov 14 16:59:13 badger kernel: [73801.112031] usb 6-1: reset full speed USB device using uhci_hcd and address 68
Nov 14 16:59:44 badger kernel: [73831.656035] usb 6-1: reset full speed USB device using uhci_hcd and address 68
Nov 14 17:00:14 badger kernel: [73862.200030] usb 6-1: reset full speed USB device using uhci_hcd and address 68
Nov 14 17:00:25 badger kernel: [73872.556036] usb 6-1: reset full speed USB device using uhci_hcd and address 68
Nov 14 17:00:35 badger kernel: [73882.800071] sd 26:0:0:0: Device offlined - not ready after error recovery
Nov 14 17:00:35 badger kernel: [73882.800340] usb 6-1: USB disconnect, address 68
Nov 14 17:00:35 badger kernel: [73882.925913] usb 6-1: new full speed USB device using uhci_hcd and address 69
Nov 14 17:00:35 badger udev-configure-printer: Disabled printer ipp://localhost:631/printers/Photosmart-7400-series as the corresponding device was unplugged or turned off
Nov 14 17:00:35 badger udev-configure-printer: Disabled printer ipp://localhost:631/printers/Photosmart_7400 as the corresponding device was unplugged or turned off
Nov 14 17:00:35 badger kernel: [73883.504033] usb 6-1: new full speed USB device using uhci_hcd and address 70


```
Printer is now locked up again!

---

### Post by miked2 on 2009-11-16
still no real progress on this but more information.  After installing hplip-doc, have been working through troubleshooting.html (I haven't seen this page elsewhere).  
I set the CUPS log level to debug & restarted the printer which gave me:

```
mike@badger:~$ sudo /etc/init.d/cups restart
[sudo] password for mike: 
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
mike@badger:~$ tail -f /var/log/messages
Nov 15 10:30:31 badger pulseaudio[1394]: ratelimit.c: 3 events suppressed
Nov 15 11:26:01 badger pulseaudio[1394]: ratelimit.c: 1 events suppressed
Nov 15 17:28:14 badger kernel: [81706.116059] usb 1-2: new high speed USB device using ehci_hcd and address 3
Nov 15 17:28:14 badger kernel: [81706.248500] usb 1-2: config 1 interface 0 altsetting 0 endpoint 0x83 has an invalid bInterval 0, changing to 9
Nov 15 17:28:14 badger kernel: [81706.249149] usb 1-2: configuration #1 chosen from 1 choice
Nov 15 17:30:43 badger kernel: [81854.788048] usb 1-2: reset high speed USB device using ehci_hcd and address 3
Nov 15 17:30:48 badger kernel: [81859.834645] usb 1-2: USB disconnect, address 3
Nov 15 20:53:29 badger python: hp-check[4264]: warning: NOT FOUND! This is an OPTIONAL/RUNTIME ONLY dependency. Some HPLIP functionality may not function properly.
Nov 15 20:53:30 badger kernel: [94021.679887] usblp0: removed
Nov 16 07:35:02 badger rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="573" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Nov 16 20:51:12 badger kernel: [180283.520058] usb 3-1: USB disconnect, address 14
Nov 16 20:51:12 badger udev-configure-printer: Disabled printer ipp://localhost:631/printers/Photosmart-7400-series as the corresponding device was unplugged or turned off
Nov 16 20:51:12 badger udev-configure-printer: Disabled printer ipp://localhost:631/printers/Photosmart_7400 as the corresponding device was unplugged or turned off
^[[A^[[B
Nov 16 20:51:23 badger kernel: [180294.544031] usb 3-1: new full speed USB device using uhci_hcd and address 15
Nov 16 20:51:23 badger kernel: [180294.743188] usb 3-1: configuration #1 chosen from 1 choice
Nov 16 20:51:23 badger kernel: [180294.751139] usblp0: USB Bidirectional printer dev 15 if 0 alt 0 proto 2 vid 0x03F0 pid 0xB802
Nov 16 20:51:23 badger kernel: [180294.753156] scsi3 : SCSI emulation for USB Mass Storage devices

Nov 16 20:51:24 badger kernel: [180296.077074] usb 3-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
Nov 16 20:51:26 badger udev-configure-printer: Re-enabled printer ipp://localhost:631/printers/Photosmart-7400-series
Nov 16 20:51:26 badger udev-configure-printer: Re-enabled printer ipp://localhost:631/printers/Photosmart_7400
Nov 16 20:51:28 badger kernel: [180299.762071] scsi 3:0:0:0: Direct-Access     HP       Photosmart 7400  1.00 PQ: 0 ANSI: 2
Nov 16 20:51:28 badger kernel: [180299.762678] sd 3:0:0:0: Attached scsi generic sg4 type 0
Nov 16 20:51:28 badger kernel: [180299.809060] sd 3:0:0:0: [sdc] Attached SCSI removable disk

```

I think that the output from lsusb is telling me that the printer is connected to a v2.0 usb port:

```
  bcdUSB               2.00
```

I would appreciate some confirmation on this though.  

I've attached the output of lsusb.  The printer is about 3/4 of the way down.

---

### Post by miked2 on 2009-11-17
Yet more information:
Caught the output from hp-align as it crashes.  It sends a 113 byte sequence 5 times & gets a returned error code on the 5th attempt.  Should the "dev" and "host" parameters be null?  Any ideas?

---

### Post by miked2 on 2009-11-17
I have a temporary workaround!
After reading [__this__]("https://answers.launchpad.net/ubuntu/+source/hplip/+question/73423"), I installed the 386 specific kernel.  I still have problems with hplip but they are now very different, but consistent.  hp-align gets a lot further without crashing (but it does crash).  
I've now completely uninstalled hplip & am using a gutenprint driver instead.  That's giving reasonable results, but I'm missing the services that hplip offers (ink levels, print head alignment etc).  
I'm thinking now that joelp could be correct when he says that the hp printer network support built into the kernel, conflicts with hplip usb comms.  
Perhaps my next step would be to compile a kernel without network printing support?  Is it possible to disable network printing support some other way?

---

### Post by dizzydon on 2010-11-12
Has there been any progress on solving this problem? I have had the same problem for over a year with Fedora and now Ubuntu.   I am currently running Ubuntu 10.04 with hplip 3.10.2-2ubuntu2.1 and  cups 1.4.3-1ubuntu1.3.

---

