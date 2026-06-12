---
title: "[SOLVED] another HP 1020 question"
date: 2008-01-25
forum: Hardware &amp; Laptops
---

### Post by opscure on 2008-01-25
Hello everyone,

I know there has been a ton of threads on the hp 1020 printer, but my situation is a bit different.  I have the foo2zjs driver along with hotplug, firmware, etc. installed and working.  The problem I am having is that when the printer is turned off along with the pc when it reboots, I have to manually power cycle the printer (ie close communication to i/o port and reload firmware) for the /dev/usb/lp0 port to free up and printing to resume.   I have searched quite a bit on this issue and it seems that if I remove the printer from gnome-cups-manager and attempt to install it again without the printer power cycle it does not detect that a printer is connected to the usb port (lpstat -t).  I am wondering if there is something that I have overlooked?  I followed all directions on foo2zjs page....   when I try  ```
cat /usr/share/foo2zjs/firmware/sihp1020.dl >/dev/usb/lp0 
``` I get device or resource busy.  If I power cycle the printer this works alright.  I am seeing this issue in both my feisty box and my gusty laptop.  I did notice, however, if I continually keep power to the printer while the pc is rebooted the device is detected fine on boot.  

I am wondering what is happening when I am turning off the printer power with the reboot of the pc?  Could it have something to do with the way udev or hotplug is handling the boot process?  I attempted to modify the hplj1020 file in hotplug to comment out DEV="" which did not help my cause.  I tried to restart udev which didn't help either.  I tried to remove usblp and reinsert using:```
sudo modprobe -r usblp; modprobe usblp
``` which successfully completed, but didn't help with the issue I am having.  

I attempted to use fuser to see what processes were being used by the /dev/usb/lp0 port when it is in the non-responsive state none of which seem to be holding this port open.  I even tried removing the whole device and recreating it with ```
MAKEDEV usb
``` and loading the firmware from there.  This worked, sort of, I still needed to go into the gnome-cups-manager and recreate the printer (unable to incorporate this into a script).  

So, I suppose my main question (after all my ramble) is how do I get the firmware loaded into the printer when power goes from off on both devices to on and allow the /dev/usb/lp0 port to accept my print jobs with out having to power cycle the printer?

Any help/links/scripts/etc would be greatly appreciated,  thanks in advance.

---

### Post by 11hjpphty76lkjj on 2008-01-25
Although I can't answer your question specifically, I wanted to tell you that the LaserJet 1020 is fully supported by the latest hplip and does work great.  Hope this helps!  A

---

### Post by opscure on 2008-01-25
Thanks for the response.  I believe I was using the hplip from the repositories.  I will download the most recent build and try again.

---

### Post by 11hjpphty76lkjj on 2008-01-25
Well just keep in mind the fix isn't released yet. :)  It will be on the next release of hplip.  A

---

### Post by opscure on 2008-01-28
I found this reply to Bug #162016, it helps explain why this is happening... 

> 

Sorry, HPLIP uses libusb/usbfs instead of usblp. Libusb uses the "/dev/bus/usb/xxx/xxx" device node instead of the "/dev/usblp0" device node.

Since usblp and libusb cannot claim the the same usb device, any HPLIP device I/O usage (ie: scanning, printing or faxing) will remove usblp from the "/dev/usblp0" device node.

If you are using CUPS this means in general you should always use the HPLIP's "hp" backend (ie: "hp:/usb/...") instead of the standard CUPS "usb" backend (ie: "usb://...").

The "hp" backend will always use the libusb device node. If you try to use the "usb" backend the "/dev/usblp0" device node may not be available.

Currently hal_lpadmin calls hp-info and hp-probe which are io intensive and will interfere with hp-firmware download for the LJ1018 and LJ1020. Because of this interference HAL will not see these printers at plug-in-play time and disable the print queue.

The hp-info and hp-probe calls in hal_lpadmin should be replaced with the hp-makeuri call. The udev sysfile information will provide the usb "bus" and "device" information necessary for the "hp-makeuri bbb:ddd" command. Hp-makeuri will return a valid HPLIP uri if the usb device is supported by HPLIP.

Hp-makeuri is a light weight call that has very little io overhead. The hp-makeuri command will not interfere with the hp-firmware download.

-dave


---

### Post by rickrich on 2008-03-27
Driver: 
[http://foo2zjs.rkkda.com]("http://foo2zjs.rkkda.com")
Follow ALL instructions

---

### Post by 11hjpphty76lkjj on 2008-03-27
[FONT=Futura Bk][SIZE=3]Hewlett-Packard supports Open Source  ideals and principals through the development and support of the HP  Linux Imaging & Printing (HPLIP) software which supports nearly  all IPG printing devices.  Hewlett-Packard recognizes that there  are alternatives to HPLIP in the market today and some of these software  solutions provide satisfactory results for Hewlett-Packard customers.[/SIZE][/FONT] 


 [FONT=Futura Bk][SIZE=3]Since HPLIP software is designed  by engineers with an in-depth understanding of Hewlett-Packard’s imaging  and printing technology, the result is software that provides outstanding  print quality, with fast, efficient printing, scanning and faxing solutions.   Furthermore, HPLIP customers can be assured that great care has been  taken to ensure all licensing issues have undergone the strictest legal  scrutiny, delivering a robust Open Source solution for their needs.

Aaron
[/SIZE][/FONT]

---

### Post by opscure on 2008-04-04
The newest version of foo2zjs seemed to fix this issue.  I'm not sure what change occurred, but it's working and that's good enough for me.  Thanks for all the replies.

---

