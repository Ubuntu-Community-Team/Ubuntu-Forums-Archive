---
title: "ubuntu lucid won't mount android storage"
date: 2010-10-26
forum: Hardware
---

### Post by SaintDanBert on 2010-10-26
When I connect my Ubuntu Lucid laptop to my Android 2.1 phone (Samsung Galaxy-S "Captivate"), I see the following in the logs:
```

mumbles kernel: [29882.768051] usb 2-1: new high speed USB device using ehci_hcd and address 4
mumbles kernel: [29882.901148] usb 2-1: configuration #2 chosen from 1 choice
mumbles kernel: [29882.902119] scsi7 : SCSI emulation for USB Mass Storage devices
mumbles kernel: [29887.902914] scsi 7:0:0:0: Direct-Access     SAMSUNG  SGH-I897 Card    0000 PQ: 0 ANSI: 2
mumbles kernel: [29887.903379] scsi 7:0:0:1: Direct-Access     SAMSUNG  SGH-I897         0000 PQ: 0 ANSI: 2
mumbles kernel: [29887.905386] sd 7:0:0:0: Attached scsi generic sg1 type 0
mumbles kernel: [29887.907958] sd 7:0:0:1: Attached scsi generic sg2 type 0
mumbles kernel: [29887.920432] sd 7:0:0:0: [sdb] Attached SCSI removable disk
mumbles kernel: [29887.922160] sd 7:0:0:1: [sdc] Attached SCSI removable disk

```

In addition, the Nautilus file manager display gets two new file system icons named: **SAMSUNG  SGH-I897** and **SAMSUNG  SGH-I897 Card**.

In spite of all of this, I cannot open the Nautilus "file systems"
and **mount** does not show anything available. Also, I cannot use **sudo mount /dev/sdb /media/something** or **sudo mount /dev/sdc /media/something** even though the logs report that both are "attached SCSI removable disk".

<soap_box>
I am so very frustrated!!!  This is yet another situation where most of the postings say that this just works. Then when ** I ** try that same something, I have all sorts of grief.

I'm a 30+ year veteran bit-slinger and a 10+ year linux user.  If I have this sort of confabulation, pity the poor newbie all the more.
It is little wonder that linux gets such a bad rep in general.
</soap_box>

Can anyone help me?
~~~ 0;-Dan

---

### Post by leneflower on 2010-10-27
Are you sure you set the USB connection type to "Disk drive" on the phone? 

This is what I get when I set the connection type to "Charge only":
```
[599077.230047] usb 1-5: new high speed USB device using ehci_hcd and address 10
[599077.395658] scsi9 : usb-storage 1-5:1.0
[599078.393166] scsi 9:0:0:0: Direct-Access     HTC      Android Phone    0100 PQ: 0 ANSI: 2
[599078.394340] sd 9:0:0:0: Attached scsi generic sg1 type 0
[599078.401165] sd 9:0:0:0: [sdb] Attached SCSI removable disk

```sdb is not mountable.
And this when I set it to "Disk drive":
```
 usb 1-5: new high speed USB device using ehci_hcd and address 10
[599077.395658] scsi9 : usb-storage 1-5:1.0
[599078.393166] scsi 9:0:0:0: Direct-Access     HTC      Android Phone    0100 PQ: 0 ANSI: 2
[599078.394340] sd 9:0:0:0: Attached scsi generic sg1 type 0
[599078.401165] sd 9:0:0:0: [sdb] Attached SCSI removable disk
[599221.143522] sd 9:0:0:0: [sdb] 62333952 512-byte logical blocks: (31.9 GB/29.7 GiB)
[599221.145873] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[599221.151993] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[599221.152015]  sdb: sdb1

```Then I can mount sdb1...

---

### Post by SaintDanBert on 2010-10-27
How do I tell the phone to use this "disk drive" setting?
Is this a one-time config and use or is this needed every time?

Thanks,
~~~ 0;-Dan

---

### Post by matthanley on 2010-11-02
FWIW, I couldn't get mine to mount on a USB 1.1 port. (My computer has a few miles on it, and the ports in the front are 1.1)
I saw this message in the logs:
> usb 3-2: not running at top speed; connect to a high speed hub
so I plugged it into a USB 2.0 port (on the back, under the desk, banged my head) and selected "Mount as disk drive", it worked fine on its own after that.

---

### Post by SaintDanBert on 2010-11-04
I've seen the USB ports issue before as well, but it usually meant that I was trying to use an add-on hub that was not up to speed (sic). Similarly, my choice of cable has raised the same flag. However, I don't recall troubles -- even on grey-beard hardware -- when plugged directly to the computer with a quality cable.

Bonne chance,
~~~ 0;-Dan

---

### Post by Bufke on 2010-11-27
For anyone with this problem, try rebooting the phone too. I was getting this on dmesg 

[  389.740143] usb 1-2: new high speed USB device using ehci_hcd and address 9
[  389.926397] rndis_host 1-2:1.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-2, RNDIS device, be:ed:64:cb:cd:43
[  400.520077] usb0: no IPv6 routers present

Like it was seeing it as a USB NIC but not removable media. Phone reboot fixed it.

---

### Post by SaintDanBert on 2010-11-29
I have not recorded the choreography but there seems to be a dance.

1. Prepare the phone
2. connect the cable
3. tinker the phone
4. linux sees the phone's storage
(The Galaxy S has "internal" and "external" storage drives.)
5. udev and udrive do their thing and linux can access the phone.

I'll try to document the "prep" and "tinker" details and post what I learn. Sadly, neither seems required with win-doze.

{wish_list}
I'd love to access the phone storage as a SAMBA share or NFS or CIFS share.  

I'd also like to have the phone able to access intra-net files and folders and printers using SAMBA or NFS or CIFS shares.

Since android is a linux variant, it should be straight forward to get one (or more) of these clients (and servers) running on Android. Sadly, I do not have enough time for that project, but I'm available to help any who might be interested.
{/wish_list}

---

### Post by jbg144 on 2010-12-01
I just got a Samsung Transform (Sprint) phone and have had the same problems mounting the internal SD card as a USB drive.  
The problem seems to be related to the interaction between my phone's USB port and the ports on my Linux box.  Specifically:
1.  After turning the phone all the way off, then on again, and connecting to a Windows :-( computer, I get the proper USB notification on the phone and am able to mount the SD card as a USB storage device.
2.  When I attach the phone to my Ubuntu 10.04 box, I get the USB notification, but the SD card does NOT mount properly (can't see the drive).  If I disconnect and reconnect the phone from the Linux box, I no longer get the USB notification on the phone.  In addition, if I then attach the phone to the Windows box, I get an error message (unrecognized device).
3.  The solution is found here: 
[http://www.absolutelytech.com/2010/04/18/solved-unable-to-enumerate-usb-device-disabling-ehci_hcd/](http://www.absolutelytech.com/2010/04/18/solved-unable-to-enumerate-usb-device-disabling-ehci_hcd/)
4.  If I power cycle the phone, then run the following script, I receive the appropriate USB notification and can move files to/from the phone's SD card appropriately. I can successfully unmount / remount the phone from both the Linux and Windows boxes repeatedly. 
[PHP]cd /sys/bus/pci/drivers/ehci_hcd/
sudo sh -c 'find ./ -name "0000:00:*" -print| sed "s/\.\///">unbind'[/PHP]

5.This script disables the ehci_hcd driver, which slows the USB port to 1.1 speed. This shouldn't be a problem for printers, mice, keyboards, etc., but is likely to slow transfers to a USB HDD or CD/DVD to a crawl. As far as I can tell the only way to restore the USB ports to normal speed is by rebooting Linux.

I would be interested to hear if people with other Android devices find that this fix works for them as well.

---

### Post by SaintDanBert on 2010-12-01
Once again, win-dose sees the phone connection, does a dance, and presents the phone's storage as available as folders on the workstation.
Whereas linux requires some sort of low level tinkering on the workstation, the phone or both.

I understand that every developed product gets built and tested with win-dose as a target environment. Further, I understand that the linux community must accomplish the required integration and testing when the manufacturers do not. That said, why would anyone other than a chronic tinkerer volunteer for all of this extra integration work? More so, why would any business build a plan around so much tinker-til-done deployment.

A Chronic Tinkerer (or masochist),
~~~ 0;-Dan

---

### Post by stu44mag on 2010-12-02
I have a Droid X and limited experience with the Galaxy S phones, but I know that in order for me to access files on my phone I need to enable USB debugging.   I also have to connect in charge only mode to enable USB debugging, but I am then able to access the phone.  I am using Maverick.  If I do not enable USB debugging, my phone mounts, but I cannot access anything on the phone.
Good luck!

---

### Post by SaintDanBert on 2010-12-02
> **Bufke said:**
> 
...
Like it was seeing it as a USB NIC but not removable media.
...


(grinning)
So how do I get things to see the USB NIC ... ?

In a previous life:
[list]
[*]connect phone to laptop with "data cable"
[*]phone notices connection and displays a menu; linux waits
[*]menu has choices of "tether" "data sync" "usb store" etc
[*]select a choice; linux resumes
[*]crank turns to activate the phone option as selected
[/list]

With Android, I don't get any sort of menu on connect!
I just need to know which USB options to select BEFORE I plug in.

~~~ 0;-Dan

---

