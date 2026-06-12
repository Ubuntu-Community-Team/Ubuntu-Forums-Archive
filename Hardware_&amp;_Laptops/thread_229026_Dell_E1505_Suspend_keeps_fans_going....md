---
title: "Dell E1505 Suspend keeps fans going..."
date: 2006-08-03
forum: Hardware &amp; Laptops
---

### Post by DoubleDangerClub on 2006-08-03
I have managed to get everything working on my Dell E1505, except for the sleep, which from what I understand is the same thing as Suspend.

It will go to sleep/suspend, but it keeps the fans going, which kills the battery and heats up the laptop.
I have ACPI_Sleep = True in my /etc/default/acpi-support.

My hibernate works well enough, though with both I still get a screen that says Resume Error 5 or something to that effect when it comes back to life.  But the programs are still up, etc, so it's not that big a deal.

Any help that someone can throw my way to make my lappy happy when sleeping?
Any help is much appreciated.  Thanks!

DDC

---

### Post by UltraMathMan on 2006-08-05
**EDIT:** This worked the first time but hasn't since - I will continue working on it and let you know. In the meantime, anyone else have a fix?

Error given on resume```
17196512.168000] hci_usb 5-2:1.0: resume error -5
```
--------
Hi, same problem. I think the resume errors are the reason why the fans keep going (services have not been shut down). I think I fixed this problem on my E1505 by doing the following: 
1) note the resume error when it comes up. In my case it began with hci_usb (I assume yours is something similar) 
2.) run the command ```
lsmod |grep usb
``` to see what usb modules are loaded. In my case the result is ```
usbhid                 42752  0
hci_usb                18004  2
bluetooth              54084  7 rfcomm,l2cap,hci_usb
usbcore               139076  5 usbhid,hci_usb,uhci_hcd,ehci_hcd
``` This shows 2 usb modules, usbhid and hci_usb as well as the usbcore and the modules dependent on it. 
3.) I then edited the MODULES="" line of /etc/default/acpi-support with ```
sudo gedt /etc/default/acpi-support
``` to ```
MODULES="hci_usb,usbhid"
``` and saved. So far (past 20-30mins) the fans haven't come on during suspend and I no longer receive resume errors. Thanks to quini for his info [ in this thread]("http://ubuntuforums.org/showthread.php?p=1342562#post1342562")! 
Hope this helps :)

---

### Post by ahallubuntu on 2006-08-05
Hmm.  I can hibernate just fine on my E1505 but I can't resume with the correct state!  At first it would try to resume, seeming to load the saved memory image, but then it would just revert back to login.  I thought my swap space was too small but when I tried upping that, I could no longer resume at all, because the partition number of the swap partition changed due to where my free space was.  I couldn't change it back.  Instead of trying to figure it out, I think I will just re-install yet again with a larger swap partition...

In the meantime, question:  for 1GB that you say your E1505 has, what's your swap partition size?  I know the general rule is at least 1.5X of your RAM.  I have 2GB of RAM and initially had only a 2GB swap partition, but due to the 1024 bytes per K, I may have made it slightly too small.    I hate to use more than I need to - I have a 100GB hard drive with dual-boot Windows XP and Windows needs 2GB too!  I hate to keep reserving so much hard disk just for swap!

---

### Post by UltraMathMan on 2006-08-05
ahallubuntu, you might want to check out [this thread]("http://ubuntuforums.org/showthread.php?t=229550&highlight=swap+size")

I think I got fanless suspend working now (it worked the past 4 suspends, length ~30min-1hr). I changed the MODULES="" line in /etc/default/acpi-support to include all the dependents of usbcore (see my previous post) so that the line now is ```
MODULES="hci_usb usbhid uhci_hcd ehci_hcd"
``` I realized the commas were unnecessary :oops: .I'm going to keep checking and I'll let you know if the fans keep coming on during suspend. 

Hope this helps :)

EDIT: 1 month 17 days, no problems :D

---

