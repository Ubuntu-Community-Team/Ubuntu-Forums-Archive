---
title: "Epson TM88IV Printer not working on Ubuntu 11.10"
date: 2011-11-15
forum: Hardware
---

### Post by markoshust on 2011-11-15
Hi all,

I had this printer working on Ubuntu 10.04, but just did a clean install and now it seems as though I cannot get it working.

Before, I set the Device URI for the printer to usb:/dev/usb/lp0 or something similar. However, after the upgrade I am not seeing any /dev/usb folder that exists. When I do an lsusb I am seeing the printer connected. 

Any help? Anyone know of a Device URI I could use? I am on the most recent version of cups (1.3.2).

Thanks,
Mark

---

### Post by 73ckn797 on 2011-11-15
Maybe this can help?
I am running 11.10 in a dual boot with 10.04. My HP printer was recognized but would not print in 11.10. I found my solution to be: Go to Printing. Click on the printer listed then right click and select properties. Under policies I found the "accepting print jobs" was not checked. I checked it and now the printer is working. Also make sure it is enabled.

---

### Post by markoshust on 2011-11-15
Unfortunately that box is already checked.

I noticed it is showing in lsusb:
~$ lsusb | grep -i 'epson'
Bus 002 Device 002: ID 04b8:0202 Seiko Epson Corp. Receipt Printer M129C

but not in dmesg:
~$ dmesg | grep -i 'epson'
~$

---

### Post by markoshust on 2011-11-15
So, apparently this means the driver didn't install correctly.

I then noticed that I installed tmt-cups, but not with sudo (ARG OOPS). Remember the sudo peeps. I feel stupid.

Thanks for the help.

---

