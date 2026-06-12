---
title: "Trouble getting graphics tablet to work after Debian-&gt;Ubuntu switch"
date: 2005-02-22
forum: Hardware &amp; Laptops
---

### Post by quinn on 2005-02-22
I've got a KB Gear Tablet (kbtab), and in Debian, using the linux kbtab.ko driver, combined with the 0.6.x XFree86 Wacom tablet driver, I was able to make the tablet work. Unfortunately, I'm having no luck doing this in Ubuntu (Warty for the moment)-- I'm going to detail some of the stuff I've tried and futzed with, and if anyone can help point me in the right direction, I'd be very grateful.


Anyhow, in Debian, I was using vanilla 2.6.x kernels from kernel.org, 2.6.9 at the time I switched. There was one minor hack I made to the kbtab driver, because it had a habit of needing to be reloaded every time X restarted. When I switched over to Ubuntu, I noticed that this particular hack didn't work. (basically, it would briefly report the "PEN' tool not in use every time the device was successfully opened-- this seemed to not effect Ubuntu's patched 2.6.8.1  kernel.)-- without the hack, the tablet should have worked, the first time X loaded up. But 'xinput test tablet' reports absolutely nothing from the tablet.

The 'wacdump' diagnostic tool that comes packaged with the X11 Wacom driver's source reports the tablet working just fine. All three axes, and the button signals come through. However, the X driver doesn't seem to be able to read it successfully. When the Debug level of the X driver is cranked up, when it was working, it would spam my X logs with lines like this:


xf86WcmDevReadPacket: device=/dev/input/event1 fd=7 pos=0 remaining=256
xf86WcmReadPacket buffer has 64 bytes
xf86WcmEvent: c=0 i=0 t=0 s=0x0 x=5324 y=2727 b=0x1 p=71 rz=0 tx=0 ty=0 aw=0 rw=0 t=0 df=0 px=0 st=40252
commonDispatchEvents

...however,  now that it's not working,  it's just repeating those first two lines, and occasionally saying that usbParse exceeded the event queue. This is identical with both the stock Ubuntu XFRee86 wacom driver (which appears to be patched to 0.6.4), and 0.6.6, downloaded directly from the driver's homepage.

My kernel is completely Ubuntu-stock, apart from the minor kbtab hack. (though I get identical behavior whether the hack is present or not). I haven't yet tried a Vanilla kernel, and I'd like to avoid it if I can. I have a hunch there's some sort of patch in either X or the Kernel that somehow subtly changes the communication between the kernel and the X driver, and manages to completely break things.

Does anyone have any bright ideas? Thankn in advance for saving my sanity.

{EDIT: minor changes to clarify, addition of X config)

I've attached my X config, if that helps at all. The strange /dev/input devices are symlinks done by my udev config-- Tablet still misbehaves when I use the /dev/input/eventX directly.

---

