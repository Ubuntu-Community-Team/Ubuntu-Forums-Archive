---
title: "Cannot mount external USB hard drive"
date: 2005-06-01
forum: Hardware &amp; Laptops
---

### Post by Xitron on 2005-06-01
[FONT=Courier New]First, I've just gotta tell ya that Ubuntu is blowing me away!  I've been using SuSE for years, and Ubuntu is miles ahead in many ways.  And I say this as someone who has been a Unix SysAdmin for many many years.

Here is my current dilemma.  I have an external USB hard drive that I'm attempting to mount.  When I had SuSE 9.1 Professional on this laptop (Dell Latitude D800) it worked fine.  Too fine, in fact.  I got frustrated that SuSE would mount the drive before I ever got a chance to do anything.  Had to unmount it and remount it in my own way for it to show up in the 'df' output.

Here is the ouput of 'lsmod | grep -i usb'
  usb_storage            64064  0
  usbhid                 29376  0
  usbcore               107384  5 usb_storage,usbhid,ehci_hcd,uhci_hcd
  scsi_mod              119936  4 usb_storage,sd_mod,sr_mod,sbp2
  ide_core              118988  5 usb_storage,ide_cd,ide_generic,ide_disk,piix

So it looks like the modules are all in place.

When I hook up, this is what /var/log/messages has to say:
   Jun  1 14:16:25 powder3 kernel: usb 4-4: new high speed USB device using ehci_hcd and address 19
  Jun  1 14:16:26 powder3 kernel: usb 4-4: khubd timed out on ep0in
  Jun  1 14:16:31 powder3 kernel: usb 4-4: khubd timed out on ep0in
  Jun  1 14:16:31 powder3 kernel: usb 4-4: new high speed USB device using ehci_hcd and address 20
  Jun  1 14:16:32 powder3 kernel: usb 4-4: khubd timed out on ep0in
  Jun  1 14:16:37 powder3 kernel: usb 4-4: khubd timed out on ep0in


A google search for the 'ep0in' error turns up lots of questions, but no answers.  To add clues, I then inserted my usb 128MB stick drive (with reiserfs onboard), and get the following from /var/log/messages

  Jun  1 14:19:31 powder3 kernel: usb 2-2: new full speed USB device using uhci_hcd and address 3
  Jun  1 14:19:31 powder3 kernel: scsi1 : SCSI emulation for USB Mass Storage devices
  Jun  1 14:19:32 powder3 usb.agent[10865]:      usb-storage: already loaded
  Jun  1 14:19:36 powder3 kernel:   Vendor: LEXAR     Model: JUMPDRIVE         Rev: 1.03
  Jun  1 14:19:36 powder3 kernel:   Type:   Direct-Access                      ANSI SCSI revision: 01 CCS
  Jun  1 14:19:36 powder3 kernel: SCSI device sda: 251904 512-byte hdwr sectors (129 MB)
  Jun  1 14:19:37 powder3 kernel: sda: Write Protect is off
  Jun  1 14:19:37 powder3 kernel: SCSI device sda: 251904 512-byte hdwr sectors (129 MB)
  Jun  1 14:19:37 powder3 kernel: sda: Write Protect is off
  Jun  1 14:19:37 powder3 kernel:  /dev/scsi/host1/bus0/target0/lun0: p1
  Jun  1 14:19:37 powder3 kernel: Attached scsi removable disk sda at scsi1, channel 0, id 0, lun 0
  Jun  1 14:19:37 powder3 scsi.agent[10915]:      sd_mod: loaded sucessfully
  Jun  1 14:19:37 powder3 kernel: ReiserFS: sda1: found reiserfs format "3.6" with standard journal
  Jun  1 14:19:37 powder3 kernel: ReiserFS: sda1: using ordered data mode
  Jun  1 14:19:37 powder3 kernel: ReiserFS: sda1: journal params: device sda1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
  Jun  1 14:19:37 powder3 kernel: ReiserFS: sda1: checking transaction log (sda1)
  Jun  1 14:19:37 powder3 kernel: ReiserFS: sda1: replayed 1 transactions in 0 seconds
  Jun  1 14:19:37 powder3 kernel: ReiserFS: sda1: Using r5 hash to sort names


And the new drive pops up on the screen with no prompting from me, exactly the same way that my hard drive *doesn't*.

I'm very hopeful that someone on the forum has encountered something similar, and has an answer to this dilemma.  I really need to be able to access this drive.

Thanks!

Unca Xitron[/FONT]

---

### Post by enquiry on 2005-06-01
I suggest you file a bug report.

---

### Post by coaxx on 2005-06-10
maybe I have the same Problem here trying to connect a Harddrive to USB 2.0. (hoary)

Here are my outputs:

lsmod | grep usb

```

usb_storage            64064  0
usbhid                 29376  0
usbcore               107384  7 usb_storage,ehci_hcd,ohci_hcd,uhci_hcd,cpad,usbh           id
scsi_mod              119936  3 usb_storage,sr_mod,sbp2
ide_core              118988  5 usb_storage,ide_cd,ide_generic,piix,ide_disk
 
``` 

/var/log/messages
```

Jun 10 21:43:52 localhost kernel: usb 4-3: new high speed USB device using ehci_
hcd and address 10
Jun 10 21:43:53 localhost kernel: usb 4-3: khubd timed out on ep0in
Jun 10 21:43:59 localhost kernel: usb 4-3: khubd timed out on ep0out
Jun 10 21:44:04 localhost kernel: usb 4-3: khubd timed out on ep0out
Jun 10 21:44:04 localhost kernel: usb 4-3: new high speed USB device using ehci_
hcd and address 11
Jun 10 21:44:05 localhost kernel: usb 4-3: khubd timed out on ep0in
Jun 10 21:44:10 localhost kernel: usb 4-3: khubd timed out on ep0out
Jun 10 21:44:15 localhost kernel: usb 4-3: khubd timed out on ep0out

``` 

Wouldt be great if there is somebody out there who can help us with this issue. Thank U!

//edit

a "sudo modprobe --remove ehci_hcd " helped here. Dont know if all other usb things are still working, but mouse and Storage does now.

---

### Post by xero1 on 2007-03-30
need help .. ubuntu does not let me copy or write any thing in a usb  devices an it saids that i dont have permision ..? how can y give me  permission? please help i am new in ubuntu   i need the removable  devises for classes  thanks

---

