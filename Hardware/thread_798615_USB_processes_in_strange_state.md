---
title: "USB processes in strange state"
date: 2008-05-18
forum: Hardware
---

### Post by Homer Wolfe on 2008-05-18
I'm having USB troubles, but I don't know what processes control USB detection in 8.04.

I'm using Kubuntu 8.04 on a Toshiba Satelite, and I have a USB mouse, and two USB hdds connected to the standard USB ports.  During tansfer of files from one drive to the other, sometimes the mouse spontaneously stops working completely (laser off), and the transfer speed between the drives drops dramatically. Unplugging and replugging the mouse does not help.  I have seen this occur with many permutations of which port the devices are connected, and I never saw it happen with 7.10.  I don't know how to restart the USB services, so I reboot, but it hangs somewhere (probably trying to sync or unmount the drives), and I'm forced to hard powerdown.  The touchpad on the laptop continues to work.

My questions are: 

What processes control USB detection etc, and how do I restart them?  There's no /etc/init.d/hotplug on my system, so I assume its performed by something else.  

What should I look for in the error logs when this happens so I can better characterize this?  Nothing stands out in dmesg.

Thanks,
Homer

---

### Post by smsmith050 on 2008-06-06
I have an HP6715b which will stop responding to hot plugged usb devices. This usually happens on a suspend resume. The only way I have found to fix it is re-boot. 
This same laptop will stop recognizing usb devices when docked and undocked several times while running vista business 32.

---

