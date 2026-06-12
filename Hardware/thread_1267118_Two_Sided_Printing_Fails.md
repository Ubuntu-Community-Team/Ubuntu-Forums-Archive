---
title: "Two Sided Printing Fails"
date: 2009-09-15
forum: Hardware
---

### Post by celem on 2009-09-15
I have an HP Deskjet 6940 that supports a manual 2 sided printing mode that works well in Windows XP but fails in Ubuntu 9.04.

Documents print normally when one sided printing (the default) is selected. However, when I select 2-sided printing, the first page prints about 2/3 of the way and a print failed pop-up appears and the printer freezes with its power light blinking. 

When I press the trobuleshoot button in the pop-up it reveals that /usr/lib/cups/filter/foomatic-rip failed.

When I clicked the button to activate additional debugging in CUPS, the print job froze, as before, but this time no pop-up, namely no message at all!

A power cycle of the printer is required to get it working again.

Anybody have two-sided printing working?

---

### Post by celem on 2009-09-15
Just happened again but this time it was a plain, one-sided print. Locked up the system so totally that I couldn't even SSh into it from another machine. I restarted via Alt/SysReq+REISUB and then checked the log messages. Looks like a nasty segfault from libc-2.9.so surrounded by a bunch of hp related messages. See below:

```

Sep 15 11:15:43 ubu-squirrel kernel: [64130.324363] hpijs[11086]: segfault at 0 ip 00007f3ac163811b sp 00007fffcb8d8e58 error 6 in libc-2.9.so[7f3ac15b4000+168000]
Sep 15 11:16:37 ubu-squirrel python: hp-info[11125]: warning: No display found.
Sep 15 11:16:37 ubu-squirrel python: hp-systray[11126]: warning: No display found.
Sep 15 11:16:41 ubu-squirrel python: hp-info[11125]: warning: Unable to connect to dbus. Is hp-systray running?
Sep 15 11:17:43 ubu-squirrel kernel: [64249.733455] usb 1-7: USB disconnect, address 5
Sep 15 11:17:56 ubu-squirrel kernel: [64263.032039] usb 1-7: new high speed USB device using ehci_hcd and address 6
Sep 15 11:17:56 ubu-squirrel kernel: [64263.166136] usb 1-7: configuration #1 chosen from 1 choice
Sep 15 11:17:56 ubu-squirrel kernel: [64263.167375] usblp0: USB Bidirectional printer dev 6 if 0 alt 0 proto 2 vid 0x03F0 pid 0x8904
Sep 15 11:19:18 ubu-squirrel kernel: [64345.645084] usblp0: removed

```

---

### Post by steveneddy on 2009-09-15
Have you tried HPLIP from HP to help you with the HP printer woes?

Make sure you uninstall anything you did printer wise before you start the installation.

I use double sided printing with my HP all in one and it works perfectly using HPLIP.

---

### Post by celem on 2009-09-15
HPLIP is loaded - apparently automatically when the printer was originally added. My problem isn't that two-sided printing isn't supported - it is. Rather the problem was freezing randomly the system while the printing took place. It happened one on a single sided print so the duplexing isn't the issue. The segfault was in hpijs so it is related to the printer driver software. Nonetheless, thank you for the suggestion.

---

### Post by steveneddy on 2009-09-15
> **celem said:**
> HPLIP is loaded - apparently automatically when the printer was originally added. My problem isn't that two-sided printing isn't supported - it is. Rather the problem was freezing randomly the system while the printing took place. It happened one on a single sided print so the duplexing isn't the issue. The segfault was in hpijs so it is related to the printer driver software. Nonetheless, thank you for the suggestion.

Don't use the HPLIP from the repos.

Uninstall it and use the version that you download - in the link provided.

The version of HPLP in the repos is missing something.

---

### Post by celem on 2009-09-15
OK - loaded the newest version of HPLIP from HP, as steveneddy suggested. Having the latest version, at a minimum, changes the libraries that I was using, so after a random number of printing jobs I guess I'll find out if it had any effect. Thanks steveneddy!

---

### Post by steveneddy on 2009-09-15
> **celem said:**
> OK - loaded the newest version of HPLIP from HP, as steveneddy suggested. Having the latest version, at a minimum, changes the libraries that I was using, so after a random number of printing jobs I guess I'll find out if it had any effect. Thanks steveneddy!

You're welcome.

That is what it took to get my system running.

I haven't used the HPLIP version from the repos in a few years.

I hope that it helps.

If not, please post back. We'll help you get it figured out.

---

### Post by steveneddy on 2009-09-17
I wonder if this finally fixed the OP's issue?

---

### Post by celem on 2009-09-17
No failures since loading HPLIP directly from HP. I'm going to test a couple of more days before I mark as Solved.

---

### Post by steveneddy on 2009-09-17
> **celem said:**
> No failures since loading HPLIP directly from HP. I'm going to test a couple of more days before I mark as Solved.

Sweet!

---

### Post by celem on 2009-09-20
I marked the thread as solved. With the HPLIP direct from HP I have no problems. It appears that there must be something wrong with the HPLIP in the 9.04 repository.

---

### Post by steveneddy on 2009-10-04
> **celem said:**
> I marked the thread as solved. With the HPLIP direct from HP I have no problems. It appears that there must be something wrong with the HPLIP in the 9.04 repository.

I have found that issue years ago and always DL it from HP and have no issues myself.

---

### Post by celem on 2009-10-07
While my printer no longer randomly locks up the OS, a valuable feature present in the Windows driver seems to be missing in HP's Linux driver. In Windows, I can set the print job to manual two sided printing. The front side of all pages prints and a dialog box pops up. Then you flip the page stack over and click Continue in the dialog box. Then the back side prints. This is a valuable feature missing in Linux. Am I missing something? Does anyone know how to do this with HPLIP?

---

### Post by dadie11 on 2010-10-03
> **celem said:**
> While my printer no longer randomly locks up the OS, a valuable feature present in the Windows driver seems to be missing in HP's Linux driver. In Windows, I can set the print job to manual two sided printing. The front side of all pages prints and a dialog box pops up. Then you flip the page stack over and click Continue in the dialog box. Then the back side prints. This is a valuable feature missing in Linux. Am I missing something? Does anyone know how to do this with HPLIP?
....g'day...mine is a similar problem ~ everything prints, but alternate pages are turned 180 degrees. Anyone any ideas please...? Many Thanks. DC.

---

