---
title: "USB Mouse Keeps Freezing"
date: 2005-05-31
forum: Hardware &amp; Laptops
---

### Post by reuben on 2005-05-31
Hello, I updated via synaptic late last week, and am using the system for the first time since a reboot this morning. My USB mouse keeps locking up - specifically the cursor will freeze on the screen, and will not move. I can "fix" this by plugging it into a different USB port, but it is very annoying, to say the least. Approximately every 10-15 minutes this happens.

What package controls the USB mouse? I will downgrade, and verify that this caused the problem.

Thanks
Reuben

---

### Post by thrift on 2005-05-31
It seems most likely that this would be the kernel or one of the kernel modules.  It's hard to tell without knowing exactly what is going on.  If you open a terminal and

dmesg > dmesg.txt

and then attach the dmesg.txt file from your home directory it can be much easier to diagnose.  In the mean time you could try rolling back your kernel and see if that resolves the problem.  

This could of course also be a problem with your USB controller on the machine or the mouse, so if you have a liveCD, you could check the hardware like that.

---

### Post by peluchio on 2005-05-31
Check this post:
[http://ubuntuforums.org/showthread.php?p=193134#post193134](http://ubuntuforums.org/showthread.php?p=193134#post193134)

I solved it disabling acpi.

Cheers!

---

### Post by reuben on 2005-05-31
What are the implications of turning acpi off?

sudo modprobe -r usbhid ; sudo modprobe usbhid ... works. What provides usbhid?

dmesg.txt attached -- at the end, you can see all of my unplugging & replugging in the mous, and the above modprobe goodness.

Thanks

---

### Post by thrift on 2005-05-31
acpi is a form of power managment among other things.  It's been none to cause issues from time to time.  I currently have it enabled, but have had to run with it disabled to even boot before.  It depends a lot on your motherboard.

usbhid is a kernel module and therefore part of the kernel.

It depends on the ehci_hcd module for usb 2.0 and the uhci_hcd module for usb 1.0 on your machine.  there are two type of usb 1.0 modules uhci_hcd and ohci_hcd.  Depending on your usb controller the module you use may vary.  I currently am using the ohci_hcd.  You could try removing the uhci_hcd and modprobing the ohci_hcd then modprobing the usbhid.

If this doesn't work though, it probably won't cause any negative effects to turn acpi off and see if that helps.

---

### Post by reuben on 2005-06-13
Interestingly, this problem went away by itself the next time I rebooted the computer; no config changes necessary. Perhaps the direction of the wind caused the problem. :-?  :-?  :-?

---

### Post by zerolives on 2005-07-29
[QUOTE=reuben]Interestingly, this problem went away by itself the next time I rebooted the computer; no config changes necessary. Perhaps the direction of the wind caused the problem. :-?  :-?  :-?[/QUOTE]
 I'm having this problem myself with 5.04 Hoary. I've rebooted a dozen times or more, and it keeps happening. I'll boot the machine, log into Ubuntu, and then a minute later it's completely frozen. USB mouse and keyboard both.

How might I try disabling acpi?

---

