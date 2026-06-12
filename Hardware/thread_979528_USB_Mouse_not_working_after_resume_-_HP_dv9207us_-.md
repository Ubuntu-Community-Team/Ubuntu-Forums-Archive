---
title: "USB Mouse not working after resume - HP dv9207us - Intrepid Ibex 8.10 i386"
date: 2008-11-12
forum: Hardware
---

### Post by nelliott71 on 2008-11-12
As stated in the subject line, I have an HP dv9207us laptop.  I played around with 8.04 a while back, but had problems with suspend.  That was a deal-breaker for me so I left my Ubuntu partition idle after fiddling with it for a while.

I upgraded to 8.10 when it came out, and so far suspend seems to be working properly... with the exception of my USB wireless mouse.

After resume, I get the following error in dmesg:

[ 2564.780129] usb 2-1: reset low speed USB device using uhci_hcd and address 5

This error repeats constantly about once per second.  If I unplug the wireless receiver from the USB port and plug it back in everything starts working again and the messages cease.

I have been searching the forums and google for a solution to this problem, and have seen some similar issues with suggestions such as blacklisting USB modules either via /etc/modprobe.d/blacklist or /etc/pm/config.d/config.  These solutions have not worked so far.

Any ideas?

Thanks!

---

### Post by nelliott71 on 2008-11-13
After more searching, I *think* I have it fixed.  It's worked several times in a row now:

Copy /usr/lib/pm-utils/defaults to /etc/pm/config.d/config and change the line that says:

# SUSPEND_MODULES=""

to

SUSPEND_MODULES="uhci_hcd ohci_hcd ehci_hcd"

I'll try to report back in a day or two on how stable the results are.

---

### Post by maestrobwh1 on 2008-11-14
I have not tried this but I have also had luck with 

sudo /etc/init.d/hal restart
sudo /etc/init.d/udev stop
sudo /etc/init.d/udev start 

I tried sudo /etc/init.d/udev **restart** but for some reason, it hangs longer at reloading the drivers.

It does take a while for udev to start and will seem to hang... maybe a minute or two.

---

### Post by nelliott71 on 2009-01-29
UPDATE - I did a re-install of 8.10 and had to sort this problem out again.

I discovered I only need to unload one driver, so

/etc/pm/config.d/config file has this line:

SUSPEND_MODULES="uhci_hcd"

(Be sure to remove the leading # sign from the existing line!)

---

