---
title: "USB keyboard not active after boot"
date: 2014-06-07
forum: Hardware
---

### Post by steaktartaar on 2014-06-07
Hello all,

I've just installed Xubuntu 14.04. I have a USB mouse and keyboard connected directly through the ports on the motherboard (no hub). In the live CD, during the install, in the BIOS menu and in GRUB these work fine.

When I start Xubuntu, the keyboard doesn't take input. The mouse, however, still works. I've confirmed the keyboard itself works by testing it with another computer running Raspbian (no issues).

When I plug in a second USB keyboard, this works fine while the first one stays inactive (that's how I'm typing this). 

lsusb shows the keyboard is at least correctly identified:

```
Bus 003 Device 005: ID 17f6:0802 Unicomp, Inc 
```

Any ideas?

---

### Post by ajgreeny on 2014-06-07
Have you tried switching usb sockets; perhaps one is faulty.

Also try enabling legacy-usb mode in your BIOS or UEFI, if it's available.

---

### Post by steaktartaar on 2014-06-08
I tried both suggestions; I get the same result with different USB ports and legacy usb mode was already enabled.

The problem has just gotten weirder:

- The keyboard works if I reboot the PC, either via the hardware reboot switch or through Xubuntu.
- I installed a copy of Windows on a second partition. It didn't have the problem; however, after reinstalling GRUB; Windows started showing exactly the same symptoms (keyboard doesn't work on boot, but works after a reboot)

Is there anything in GRUB that may be causing this? Something that happens only on cold boot?

---

### Post by ajgreeny on 2014-06-08
I don't think it can be the fault of grub as that runs before either of your two OSs has started, and it is the OS which actually runs the keyboard "driver" software.

---

### Post by steaktartaar on 2014-06-09
There's still got to be some sort of connection, even if it isn't a direct one - loading GRUB before the Windows boot loader causes the same symptoms. Are there any further diagnostic steps I can take?

---

### Post by ajgreeny on 2014-06-09
No idea.  Sorry.

Perhaps worth running a live system again on the same hardware to see if it is a keyboard hardware compatibility problem.

---

### Post by steaktartaar on 2014-06-15
Apologies for the resurrection, but I think I found the problem and maybe it can help some other poor sod who has the same issue:

Going through my motherboard's options, I noticed switches for EHCI and XHCI handoff; both set to enabled. Setting both of these to disabled allowed the PC to boot correctly with working USB keyboard input. I'm still trying to figure out *exactly* where the problem lies, but it's a start.

---

### Post by oldfred on 2014-06-15
On my old BIOS system, it was only grub that would not see keyboard, but ps/2 ports worked. But then I had to turn of legacy support in BIOS for it to work. Both Windows and Ubuntu seemed to have their own drivers and would work even without BIOS setting change.

Also some settings in BIOS may make a difference.

 Enabling USB Legacy Support - If keyboard does not work. 
[http://support.creative.com/kb/ShowArticle.aspx?sid=5754](http://support.creative.com/kb/ShowArticle.aspx?sid=5754)
IOMMU for USB3 ports Gigabyte board
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)
Linux kernel enable the IOMMU &#8211; input / output memory management unit support - AMD 
[http://www.cyberciti.biz/tips/howto-turn-on-linux-software-iommu-support.html](http://www.cyberciti.biz/tips/howto-turn-on-linux-software-iommu-support.html)
[http://ubuntuforums.org/showpost.php?p=9203674&postcount=5](http://ubuntuforums.org/showpost.php?p=9203674&postcount=5)

---

