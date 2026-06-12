---
title: "pcmcia_usb2.0_adapter_support"
date: 2011-05-24
forum: Hardware
---

### Post by maxclaus on 2011-05-24
Hi all,

using a Sitecom pcmcia=>usb2.0 adapter under Ubuntu 9.04 on my Fujitsu Lifebook E7110 to have two additional speeded up USB ports available, everything runs perfect since 2009. Trying Ubuntu 10.04 from a live-cd i recognized, that USB devices plugged into the adapterports (several different USB sticks, external harddrive) cannot be mounted any more (neither automatic via hotplug nor by mount command in the terminal). The native USB 1.1 ports function as normal usual. 

Tracing this behaviour backwards shows that 9.10 (live-cd) functions normal (as 9.04 does).

Looking to the kern.log by accident under 9.04 showed the following:

Excerpt Kern.log:
..........
Jan 20 12:13:44 xxx-laptop kernel: [10438.794307] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
Jan 20 12:13:44 xxx-laptop kernel: [10438.794314] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
Jan 20 12:13:44 xxx-laptop kernel: [10438.794318] pcmcia: see [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) for details.
...........

Looking to the mentioned adress under kernel.org didn't lead to something substantial for me to solve the problem.

Trying other distries/tools (e.g. PartedMagic in several versions) seems to show, that all kernels above 2.6.31.xx don't support at least the used Sitecom adapter.

My questions are:
- does Ubuntu from kernel 2.6.31.xx upwards no longer support pcmcia to USB adapters generally? 
or
- could it be that this is depending on the adapters hardware and other adapters may function (sorry, the Sitecom is my only adapter, and as this kind of hardware is a bit old fashioned its not really easy to buy different ones)?
or
- is there any additional software which has to be downloaded after installation of 10.04?

Does anyone have experience / a helping hint or e.g. another adapter in use which is functioning under 10.4?

Greetings and many thanks in advance / maxclaus

---

