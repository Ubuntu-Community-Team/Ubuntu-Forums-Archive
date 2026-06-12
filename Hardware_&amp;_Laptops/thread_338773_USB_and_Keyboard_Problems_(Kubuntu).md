---
title: "USB and Keyboard Problems (Kubuntu)"
date: 2007-01-14
forum: Hardware &amp; Laptops
---

### Post by bky1701 on 2007-01-14
Hi. I asked this on the Kubuntu forums but didn't get much of a reply, I thought maybe it would be read more here.

I have Kubuntu 6.10 and am having a lot of odd issues with hardware I never seen before. The main problem is my USB mouse, but I don't think it's the mouse itself that's the problem.

Sometimes when I start the computer my mouse works, most of the time it doesn't. As far as I can tell it's totally random when it works and when it doesn't. I can't see any errors in the dmseg other than:

> [17181116.756000] APIC error on CPU0: 40(40)
[17181941.236000] APIC error on CPU0: 40(40)

and

> [17179576.892000] irq 209: nobody cared (try booting with the "irqpoll" option)
[17179576.892000]  <c01499a4> __report_bad_irq+0x24/0x80  <c0149a9d> note_interrupt+0x9d/0x270
[17179576.892000]  <f88fe854> usb_hcd_irq+0x24/0x60 [usbcore]  <c0149323> handle_IRQ_event+0x33/0x60
[17179576.892000]  <c0149448> __do_IRQ+0xf8/0x110  <c0105c89> do_IRQ+0x19/0x30
[17179576.892000]  <c010408a> common_interrupt+0x1a/0x20  <c0102080> default_idle+0x0/0x60
[17179576.892000]  <c01020aa> default_idle+0x2a/0x60  <c0102122> cpu_idle+0x42/0xb0
[17179576.892000]  <c03f07a1> start_kernel+0x321/0x3a0  <c03f0210> unknown_bootoption+0x0/0x270
[17179576.892000] handlers:
[17179576.892000] [<f88fe830>] (usb_hcd_irq+0x0/0x60 [usbcore])
[17179576.892000] Disabling IRQ #209


I tried irqpoll but it still had the error, unless I input it wrong, but I don't think I did.

What's really odd is, the mouse powers on even when it doesn't work, but if I unplug it and plug it back in, it doesn't power back on. When it works, it does power back on. I have tried other ports but it doesn't help, and one of my other USB devices, my wacom tablet, also doesn't power on.

The mouse doesn't even get listed in /dev/input, so it's not an X error.

My second problem is my keyboard. It maybe related to the USB/mouse error, but my keyboard is PS2. Sometimes I am typing and the keyboard just stops working, and the only way to fix it is to reboot.

Also, the keyboard doesn't work on the command line (when I press ctrl+alt+backspace), but I CAN use ctrl+alt+F* to change terminals and ctrl+alt+shift to turn the system off...

My last problem is the most odd but least major, my video card makes an odd high-pitch buzz sometimes while using the proprietary drivers, but not using the open drivers. The buzz normally happens when minimizing/moving windows or mousing over the close/minimize buttons (just going over them). I also noticed odd crock's ray-like things on some patterned images, like the background of the firefox scrollbar. I haven't checked to see if those are on the open drivers.

My monitor is LCD, my video card is a GeFroce 6600, my USB mouse is a razer copperhead, my keyboard is the one that came with the comp and my CPU is an AMD Athlon 64 x2 (I am running 32 bit Kubuntu for software compatibility reasons) and it all works fine on other OSes (suse@64, WindowsXP@32 and Fedora@64), though I did have some X server issues on Fedora 32 bit that I have yet to figure out, but I think they are unrelated.

---

### Post by bky1701 on 2007-01-16
Something else happened, my sound cut out last light and was only fixed by me rebooting - and bump. 8)

---

### Post by bky1701 on 2007-01-17
Anything??? The system is near unusable and seems to have new errors every day, I am pretty close to just going back to fedora and dealing with the issues I had there, at least they made sense. :confused:

---

