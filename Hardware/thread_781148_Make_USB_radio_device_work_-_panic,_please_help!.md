---
title: "Make USB radio device work - panic, please help!"
date: 2008-05-04
forum: Hardware
---

### Post by mrtibs on 2008-05-04
Hi,

I have a USB radio device that didn't come with Linux drivers. When I plug it in, under the Device Manager, I can see the USB device: audio interface (for sound) and HID interface (for tuning). I can also see a new file: /dev/dsp1.

I opened /dev/dsp1 with VLC. It worked the first time, but now VLC plays only static! I tried it on another Linux machine and same thing happened: VLC played it, I closed VNC, unplugged the device, restarted VLC, plugged in the device and VLC couldn't play it any more (/dev/dsp1 was opened successfully, but you can hear only static).

I thought this is a VLC issue, but I don't think it is. When you plug it in for the first time, some files must be written somewhere on the hard drive. I poked around /sys/devices/pciXXX, but I don't know enough about Linux device drivers to understand what's in there.

I have to get this solved for a school project and I'm panicking. I couldn't get an answer for this on the VLC forums or the Ubuntu Multimedia forums, so I'm trying here.

Thanks,
Tiberiu

---

