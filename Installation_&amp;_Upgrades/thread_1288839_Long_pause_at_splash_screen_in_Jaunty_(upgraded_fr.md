---
title: "Long pause at splash screen in Jaunty (upgraded from Hardy)"
date: 2009-10-11
forum: Installation &amp; Upgrades
---

### Post by wlangston on 2009-10-11
I recently upgraded my desktop (see basic specs below) from Hardy to Jaunty (both amd64).  Everything works fine except every time I boot there is a long pause on the splash screen (when the progress bar is about an eighth of the way through).  I'm attaching bootchart output and dmesg output.  I think the problem is related to udevd but I haven't been able to track down the exact problem.

Once I'm into my desktop there are 4 udevd processes that run at 100% CPU for about 5 minutes.  Then everything is normal until I plug in a USB drive and I get the udevd processes back for another 5 minutes or so.

Any and all suggestions are greatly appreciated.

Hardware config:
AMD Opteron 180 Dual-core
ASUS A8N5X motherboard
4 GB RAM (4 x 1GB)
NVidia 8600GTS
LG GSA-H55N DVD burner

---

### Post by rreese6 on 2009-10-12
I am not sure what your problem is, but you might want to try to edit the kernel line in the grub menu to see what is hanging up.
in the grub menu Press "e". highlight the Kernel line and Press "e"
go to the end of the line and remove "quiet splash --". Hit enter then 
Press "b" to boot. that will do a text boot and hopefully show you what seems to be taking so long to load.

the edit to the kernel line is temporary. it will return to normal after a reboot.

---

### Post by wlangston on 2009-10-12
Thanks for your reply.  I hand edited the boot command as you suggested.  The long pause (> 3 min.) occurs at this location:

...
[   15.636027] intel8x0: clocking to 46959
[   15.662296] usbcore: registered new interface driver snd-usb-audio
[  195.936656] it87: Found IT8712F chip at 0x290, revision 7


I copied these lines from dmesg output but I did do a text boot to verify.

Any suggestions???

---

### Post by rreese6 on 2009-10-12
for kernel 2.6.31 there is a bug with the it87: (IT8712F chip at 0x290, revision 7). Seems like this related the  the ACPI controls. I saw some ppl talking about making bios control the fans
something called "q-Fan". try checking your BIOS settings under power management. and disable any software control. let bios handle it, if possible. 
One last point, this problem did not exist in earlier kernels such as 8.04LTS...may be easier to revert back for a while until the bug is fixed.

---

### Post by wlangston on 2009-10-13
Thanks for the information.  I'll try to disable the fan control and see what happens.

---

### Post by wlangston on 2009-10-16
UPDATE:  I tried disabling all of the software fan control and that didn't solve the problem.  I also tried disabling Q-Fan in my bios (it was previously enabled) but no luck with that either.  Since Hardy was working just fine before I'm just going to revert back to that for now.  

Thanks for the suggestions.

---

