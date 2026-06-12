---
title: "Can't find /dev device for usb mass storage"
date: 2006-10-27
forum: Hardware &amp; Laptops
---

### Post by rdfx100 on 2006-10-27
Hi,

I've bought a new usb external harddrive (Western Digital MyBook), and when I plug it in, I get a single message in /var/log/messages:

usb 2-2: new full speed USB device using uhci_hcd and address 4

How do I get which device this is using?  I have one other external harddrive that works fine and shows up as /dev/sda1, but there doesn't seem to be anything else there.  I think I'm going to have to format the new drive, but don't I need to know the right entry in /dev/?   I've been looking at /proc/bus/usb/devices, but hasn't helped...

---

### Post by lgmdaniel on 2006-10-28
I have same problem with a Mini SD card plugged in to a reader... just gives me the following messages.

> Oct 28 14:45:46 localhost kernel: [17180328.188000] usb 3-1: new full speed USB device using uhci_hcd and address 6
Oct 28 14:45:47 localhost kernel: [17180328.748000] usb 3-1: new full speed USB device using uhci_hcd and address 7
Oct 28 14:45:48 localhost kernel: [17180329.316000] usb 3-1: new full speed USB device using uhci_hcd and address 8
Oct 28 14:45:48 localhost kernel: [17180329.844000] usb 3-1: new full speed USB device using uhci_hcd and address 9
Oct 28 14:53:26 localhost kernel: [17180787.588000] usb 3-2: new full speed USB device using uhci_hcd and address 10
Oct 28 14:53:26 localhost kernel: [17180788.148000] usb 3-2: new full speed USB device using uhci_hcd and address 11
Oct 28 14:53:27 localhost kernel: [17180788.716000] usb 3-2: new full speed USB device using uhci_hcd and address 12
Oct 28 14:53:28 localhost kernel: [17180789.244000] usb 3-2: new full speed USB device using uhci_hcd and address 13


---

### Post by rdfx100 on 2006-10-28
hmm... still not working.  Similar thing in [this thread]("http://www.ubuntuforums.org/showthread.php?t=271600"), so moved question there...

---

