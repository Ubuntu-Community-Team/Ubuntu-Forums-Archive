---
title: "USB Devices Generating Excessive Interrupts on MBP 5,5"
date: 2010-09-02
forum: Hardware
---

### Post by worldgnat on 2010-09-02
I'm not sure if this is a "problem" or not, but when I run Powertop, I see this:

 31.5% (113.0)   [kernel scheduler] Load balancing tick
  11.9% ( 42.7)   USB device  3-6 : Apple Internal Keyboard / Trackpad (Apple In
   8.0% ( 28.6)   [eth1, nouveau] <interrupt>
   7.5% ( 27.0)   USB device  2-5 : Card Reader (Apple)
   6.6% ( 23.5)   [ehci_hcd:usb2] <interrupt>
   6.3% ( 22.6)   [extra timer interrupt]

or similar. What concerns me is that ehci_hcd:usb2 and other usb devices are generating some sort of interrupts for no apparent reason. USB autosuspend is enabled, so why are usb devices that have nothing plugged into them (not, apparently, even Apple internal hardware that is using USB,) generating 20 or more interrupts in the time that powertop checks them? If possible, I'd like to simply deactivate the devices (especially iSight, IR Receiver, etc) that I'm not using, but I'm not sure how to do that, and Googling hasn't shed any light on the matter. 

I'm using Brian Rogers' 2.6.35 kernel that has been compiled with patches to correct excessive load balancing ticks, on Lucid. 

Thanks in advance.

---

