---
title: "USB ports have stopped working"
date: 2007-05-17
forum: Hardware &amp; Laptops
---

### Post by mroc on 2007-05-17
Hi.  I'm running Feisty (upgraded from Edgy) on an Inspiron 8200 laptop.  It has two usb 1.1 ports that used to work properly.  I don't remember exactly when they stopped working (sometime while using Edgy) but I finally got sick of not having them working, so I'm asking for help.

If I plug a usb flash drive in it does light up.  I have a PCMCIA usb 2 card that works fine (but I have to remove my wireless card - and only internet connection - to use it, which is very inconvenient).  Not sure if that is useful information or not.

I'm not sure what info to post.  Thanks for any help.

```
mroc@laptop:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
mroc@laptop:~$ dmesg | grep -i usb
[   12.055939] usbcore: registered new interface driver usbfs
[   12.055972] usbcore: registered new interface driver hub
[   12.056006] usbcore: registered new device driver usb
[   12.057380] USB Universal Host Controller Interface driver v3.0
[   12.058574] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   12.058760] usb usb1: configuration #1 chosen from 1 choice
[   12.058802] hub 1-0:1.0: USB hub found
[   12.162868] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 2
[   12.163027] usb usb2: configuration #1 chosen from 1 choice
[   12.163061] hub 2-0:1.0: USB hub found
[   12.401516] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   12.521400] usb 1-1: device descriptor read/64, error -71
[    5.204000] usb 1-1: device descriptor read/64, error -71
[    5.420000] usb 1-1: new full speed USB device using uhci_hcd and address 3
[    5.552000]  sda:<3>usb 1-1: device descriptor read/64, error -71
[    5.800000] usb 1-1: device descriptor read/64, error -71
[    6.016000] usb 1-1: new full speed USB device using uhci_hcd and address 4
[    6.424000] usb 1-1: device not accepting address 4, error -71
[    6.536000] usb 1-1: new full speed USB device using uhci_hcd and address 5
[    6.944000] usb 1-1: device not accepting address 5, error -71
[84622.132000] usb 1-1: new full speed USB device using uhci_hcd and address 6
[84622.252000] usb 1-1: device descriptor read/64, error -71
[84622.476000] usb 1-1: device descriptor read/64, error -71
[84622.692000] usb 1-1: new full speed USB device using uhci_hcd and address 7
[84622.812000] usb 1-1: device descriptor read/64, error -71
[84623.036000] usb 1-1: device descriptor read/64, error -71
[84623.252000] usb 1-1: new full speed USB device using uhci_hcd and address 8
[84623.660000] usb 1-1: device not accepting address 8, error -71
[84623.772000] usb 1-1: new full speed USB device using uhci_hcd and address 9
[84624.180000] usb 1-1: device not accepting address 9, error -71
[84925.792000] usb 1-1: new full speed USB device using uhci_hcd and address 10
[84925.912000] usb 1-1: device descriptor read/64, error -71
[84926.136000] usb 1-1: device descriptor read/64, error -71
[84926.352000] usb 1-1: new full speed USB device using uhci_hcd and address 11
[84926.472000] usb 1-1: device descriptor read/64, error -71
[84926.696000] usb 1-1: device descriptor read/64, error -71
[84926.912000] usb 1-1: new full speed USB device using uhci_hcd and address 12
[84927.328000] usb 1-1: device not accepting address 12, error -71
[84927.440000] usb 1-1: new full speed USB device using uhci_hcd and address 13
[84927.848000] usb 1-1: device not accepting address 13, error -71

```

---

### Post by Gnomester on 2007-05-19
I have, what may be, a similar problem with the two USB 2 ports on my Toshiba L30 laptop.
They work for a random amount of time before not recognising any devices plugged into them. I have tried two USB mice and a Kingston flash memory stick.
Reboot will restore the USB ports, but again they will work for anything up to an hour or sometimes 10 mins then ... no ports :confused:
Running Feisty 7.04 

thanks

---

### Post by teachop on 2007-05-19
I had problems that seems similar with my Acer Aspire 3100 + Feisty, and was able to "fix" it.  Warning I am a noob.

What was happening to me was all USB quitting.  I would notice the mouse first, but printer, hub, you name it, was dead.  Reboot would bring it back, yes.  I started poking around looking for log files updated at the critical moment and found "Network Manager nm_hal_device_removed ()" messages, lots of them, in a file called "daemon.log".

I cannot use Network Manager anyway (it kills my wireless), so I took the leap and uninstalled it.  I have been running now for days without any USB lock up situations.  I don't understand at all, but it seems to work now, and so I am confused but happy.

---

### Post by dhuff on 2007-05-19
Like teachop, my "USB devices not being detected" problem went away after I uninstalled Network Manager (since the system in question is a desktop with a static IP config, who needs it ? don't know why Feisty installed it in the first place)

Quite frankly, I feel quite circumspect about installing Network Manager even on my laptop, and this (apparent) new problem doesn't inspire any, add'l confidence in it...

---

### Post by ponx on 2007-05-20
Hmm, even after getting rid of Network Manager my problem still persists...!?

In fact, I never even had this problem to start with, even with NM running, it just started happening, I guess after an update or something...

Just to elaborate, my /etc/fstab file now has these stupid IDs to identify devices...  they weren't there when I first edited the file a couple of months ago..!?
Also, when I 'lsusb' the disk sometimes shows up, and sometimes doesnt..!?

---

### Post by teachop on 2007-05-20
Sorry that didn't work for you.  I am in the 6th day with no USB bugs, so I do believe it worked here.  Who knows why Network Manager would relate to USB crashing anyway (I sure don't).

I was very surprised to find those log messages in the first place, since I had disabled Network Manager in System->Preferences->Sessions a while ago.  I had to actually remove completely the Network Manager.

---

### Post by ponx on 2007-05-20
I have had NM/USB issues in the past but now with Feisty everything was fine - until a recent system update.

Anyway, I have now done the 'sudo aptitude purge network-manager' which looks to have gotten rid of NM, but my USB issue is still there...!?

Either I have not 'fully' got rid of NM, or my issue is something else...

---

### Post by mroc on 2007-05-21
Thanks for the replies everyone.  It sounds like my problem is a little different than what I've read in the replies.  My USB ports worked perfectly and then randomly stopped working completely.  I say "randomly," but it must have been related to an update.  Also, this began while running Edgy, well before the NetworkManager inclusion (I believe).  I upgraded to Feisty much later.  If I had to guess, I'd say they stopped working in late October.  I'd rather not mess around with NetworkManager since I do rely entirely on a wireless connection.

Anyone with a stronger technical understanding able to help?  I can post more info if someone can ask for specific output.

Thanks for any help.

---

### Post by teachop on 2007-05-22
I am sad to say that I had the USB lock up again after 6 days.  Getting rid of Network Manager may have "helped" or it may have been coincidence only that it stopped for days.  So... I too am back in the market for a solution to USB failure.

I am now printing over the network and using the touch pad in my laptop to eliminate USB devices, but I would really like to have a proper solution!

---

### Post by steven43126 on 2007-05-25
Similar problem here on Edgy Server ??

May 24 17:08:02 serverxp kernel: [42949847.140000] usb 1-1: new high speed USB device using ehci_hcd and address 6
May 24 17:08:03 serverxp kernel: [42949848.040000] hub 1-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
May 24 17:08:03 serverxp kernel: [42949848.170000] usb 1-1: new high speed USB device using ehci_hcd and address 7
May 24 17:08:04 serverxp kernel: [42949849.070000] hub 1-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
May 24 17:08:04 serverxp kernel: [42949849.200000] usb 1-1: new high speed USB device using ehci_hcd and address 8
May 24 17:08:04 serverxp kernel: [42949849.620000] usb 1-1: device not accepting address 8, error -71
May 24 17:08:05 serverxp kernel: [42949849.740000] usb 1-1: new high speed USB device using ehci_hcd and address 9
May 24 17:08:05 serverxp kernel: [42949850.160000] usb 1-1: device not accepting address 9, error -71

There is no cable it's a key drive plugged directly into the port.
Steve.

---

### Post by Gnomester on 2007-05-28
I apologize to you mroc if I have averted attention from your usb problem with Ubuntu.
I hope that your prob, and mine, can be sorted by somebody in the not too distant future.

---

### Post by dixon on 2007-06-16
So it happened also to me :( Since yesterday my usb ports just stopped working (i cannot use my mice, usb pen, nothing). I cannot remember that I've installed something new :\

dmesg
```

[  645.832000] usb 2-2: new low speed USB device using uhci_hcd and address 9
[  646.240000] usb 2-2: device not accepting address 9, error -71

```Please help :(

EDIT: I realized, that I installed some updates - but I cannot exactly remember what, but something like hal, libehal etc.... Hope this information will help and somebody will find a solution :(

---

