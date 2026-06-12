---
title: "Ubuntu does not boot with screen plugged in..."
date: 2017-08-02
forum: Hardware
---

### Post by andrewhiggs on 2017-08-02
Hi there

I have a very weird issue. I have a PC which will boot fine when an HP monitor is plugged in but not with many others (I have tested AOC, Proline and Acer screens).

The boot process appears to never start. It displays the boot logo and then goes off. The PC boots fine if you unplug the monitor. The monitor then displays as expected when plugging in after a minute or so and the boot process has completed.

How can I resolve this? What can I look at to try to determine where the problem lies?

Any assistance would be greatly appreciated.

Regards

---

### Post by Autodave on 2017-08-02
How is the monitor connected to the PC: VGA, DVI, or HDMI? Have you tried another cable?

---

### Post by andrewhiggs on 2017-08-03
Hi Autodave,

It is strange. The same cable works on the HP monitor but not the others during boot. As stated, if I boot with the VGA cable unplugged and wait a minute or two and then plug the VGA cable in all screens works as expected.

Thanks for the response.

Regards

---

### Post by vocx on 2017-08-03
> **andrewhiggs said:**
> Hi Autodave,

It is strange. The same cable works on the HP monitor but not the others during boot. As stated, if I boot with the VGA cable unplugged and wait a minute or two and then plug the VGA cable in all screens works as expected.

Thanks for the response.

Regards
VGA is an analogue signal which is subject to electric interference. It is theoretically possible to damage the circuit boards of the monitor or the computer if the configuration of either is not correct.

First of all, use HDMI if possible. HDMI is a digital signal, so it is less affected by interference. If your monitors are old, they probably don't have HDMI, so you are stuck with VGA or DVI. In that case, make sure the cables are in good shape, and the connector plugs are properly connected to the computer and monitor. Also make sure the computer and the monitor are properly grounded. They should have a three-pronged power plug connected to a properly grounded wall socket.

Old and new monitors usually have a menu or physical buttons to manually adjust some things like refresh rate and resolution. When the monitor is on, reset the options to the default values, even if the screen ends up looking a bit weird. Next see if you can boot normally, with the VGA cable connected to the monitor. If it works, gently adjust your monitor options as you want, reboot and try again. There may be an option that is preventing you from booting correctly, so you should find out which it is, to stop using that.

---

### Post by mastablasta on 2017-08-04
you can also check dmesg old log to see if there is any problem logged.

---

