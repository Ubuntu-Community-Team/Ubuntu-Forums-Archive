---
title: "USB 3.0 not working with external HD (Drobo)"
date: 2018-06-16
forum: Hardware
---

### Post by pragm on 2018-06-16
I have a Drobo 5D3 that I'm trying to get to work with my machine. Connecting via USB 2.0 works fine: I managed to format the drive as ext3 and can copy to it. Unfortunately, USB 3.0 is not working so well. While I can mount the drive and look at its contents, I can't do much else. When I tried to format the drive via USB 3.0 it always died at the step: "Writing superblocks and filesystem accounting information". After successfully formatting the drive via USB 2.0, if I try to copy to it via USB 3.0 it hangs indefinitely. Any suggestions?

Edit:

Here is what the logs say. Looks like a reset is being triggered.

> 
Jun 16 14:04:55 -desktop kernel: [   50.257377] usb 6-2: new SuperSpeed USB device number 2 using xhci_hcd
Jun 16 14:04:55 -desktop kernel: [   50.278311] usb 6-2: New USB device found, idVendor=19b9, idProduct=3533
Jun 16 14:04:55 -desktop kernel: [   50.278315] usb 6-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Jun 16 14:04:55 -desktop kernel: [   50.278318] usb 6-2: Product: Drobo5D3
Jun 16 14:04:55 -desktop kernel: [   50.278321] usb 6-2: Manufacturer: Drobo
Jun 16 14:04:55 -desktop kernel: [   50.278323] usb 6-2: SerialNumber: D0C181302600623
Jun 16 14:04:55 -desktop kernel: [   50.340678] usb-storage 6-2:1.0: USB Mass Storage device detected
Jun 16 14:04:55 -desktop kernel: [   50.340895] scsi host10: usb-storage 6-2:1.0
Jun 16 14:06:06 -desktop kernel: [  121.721979] usb 6-2: reset SuperSpeed USB device number 2 using xhci_hcd


---

### Post by TheFu on 2018-06-16
Check the system logs for issues. Any complaints?

Try a different USB3 cable.
Try a different USB3 port - on the other side of the machine, connected to a different controller.
Get a new USB3 controller (I use a front-panel connected to SATA ports).

And if there is any USB hub involved, remove  that.

---

### Post by tyoungls on 2018-11-26
We had a similar thing happen.
We had done an upgrade on our system and the Drobo stopped working around then.  We recently had time to debug it and found that rolling back to the old kernel let the drobo work again.  Not sure what the root cause is.  At the moment, it is working and we will probably leave it there for the time being.
What we found was:
kernel 4.15.0-39 did not work
kernel 4.4.0-135 did work

---

### Post by shaunc on 2019-02-22
Thank you for this post!

I can confirm that the Drobo 5d3 works well over USB 3.0 on Ubuntu 16.04 LTS using the 4.4.0 kernel. Any combination of Ubuntu 16.04, 18.04, 18.10 with the 4.15 kernel are confirmed to not work. This has been tested with 2 different chipsets, the intel X99 usb3 ports, the asmedia usb3 ports, and the usb 3 ports on the hp z840 which I think are texas intruments. What happens is the device is detected, it shows up as USB 3.0 in the lsusb -D info, but if you try to do any operations with it, it will lock up the process, with the xHCI device reset message showing up in the dmesg log. The activity LED will not be functioning when the device is hooked up to a non-compatible kernel. When connected over USB2 or with a kernel 4.4.0 over USB3, the green activity LED is fully functional. 

My question is how can we diagnose the specific way the Drobo 5d3 is working that is incompatible with newer kernels. If any one has any thoughts on where to start there, would be much appreciated (have quite a few of these devices that I would like to hook up without downgrading the kernel.

---

