---
title: "unable to enumerate USB device on port"
date: 2012-04-08
forum: Hardware
---

### Post by jim_deadlock on 2012-04-08
I have a Maxtor 3200 external USB HDD. I've tested it on 3 different dual-boot computers (2 desktops, 1 laptop) and I have the same symptoms on all 3 machines.

In Win7 the drive is recognised and works no problem. In Ubuntu 11.10 (64) I get the following:

```
Apr  8 18:38:09 jim-home kernel: [  847.876567] hub 1-1:1.0: unable to enumerate USB device on port 3
Apr  8 18:38:09 jim-home kernel: [  848.132240] hub 1-1:1.0: unable to enumerate USB device on port 3
Apr  8 18:38:10 jim-home kernel: [  848.387952] hub 1-1:1.0: unable to enumerate USB device on port 3
Apr  8 18:38:10 jim-home kernel: [  848.643644] hub 1-1:1.0: unable to enumerate USB device on port 3
Apr  8 18:38:10 jim-home kernel: [  848.899333] hub 1-1:1.0: unable to enumerate USB device on port 3
Apr  8 18:38:10 jim-home kernel: [  849.155025] hub 1-1:1.0: unable to enumerate USB device on port 3
Apr  8 18:38:11 jim-home kernel: [  849.410714] hub 1-1:1.0: unable to enumerate USB device on port 3
Apr  8 18:38:11 jim-home kernel: [  849.666405] hub 1-1:1.0: unable to enumerate USB device on port 3

```The drive is currently formatted as NTFS but I have previously tried ext2 and ext4. I've also tried a fresh Ubuntu install but nothing works. It's supposed to be a plug-and-play device so I'm assuming it's not a driver problem. Any ideas?

Update #1  I've tried a fresh install of 11.10 32bit, still getting the same error.

Update #2  10.10 32bit (kernel 2.6.35) still the same thing.

---

### Post by UrFriendlyVirus on 2012-07-09
Hey jim_deadlock,

Sorry I am just giving you a link to a forum, but I found this helpful.

**[Unable to detect HDD]("https://bbs.archlinux.org/viewtopic.php?pid=1040087")**

I also had this issue with "unable to enumerate on port 1". I just temporary disabled ehci_hcd. I **[COLOR="Red"]DO NOT[/COLOR]** recommend *blacklisting* or *deleting* **ehci_hcd** or you [COLOR="red"]**WON'T**[/COLOR] be able to use your usb ports.

Here is another forum I found helpful for this general usb enumeration issue:

**[USB not working properly]("https://bbs.archlinux.org/viewtopic.php?id=114077")**

Let me know if this helped at all.

All the best,
UrFriendlyVirus

---

### Post by jim_deadlock on 2012-07-09
In the end I cracked open the plastic box and took out the HDD which works fine as a normal drive. It was the USB parts which must have been worn out or whatever.

---

### Post by UrFriendlyVirus on 2012-07-09
Ok. Glad to hear it was fixed in the end.

-UrFriendlyVirus

---

### Post by romanr2 on 2013-04-24
2.6.32-46-generic #108-Ubuntu SMP Thu Apr 11 15:55:01 UTC 2013 i686 GNU/Linux
Having the same problem with HP printer.
Solved by unloading usb-storage module.
Seems somehow usb-storage is trying to handle the printer.

---

