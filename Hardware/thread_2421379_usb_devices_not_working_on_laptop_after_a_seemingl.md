---
title: "usb devices not working on laptop after a seemingly random amount of time"
date: 2019-06-20
forum: Hardware
---

### Post by naso4265 on 2019-06-20
I Installed Ubuntu Mate on an old Toshiba Satellite A105-S2071 a couple of days ago. It worked okay, but every so often, the usb ports just stop working. It becomes almost impossible to use, because the track pad is busted. After that, it eventually freezes, and requires unplugging. I don't have this issue on Windows 7, or when using the same devices on a different computer running Ubuntu Mate.

---

### Post by Autodave on 2019-06-20
Does this happen on battery power or when plugged in?

---

### Post by naso4265 on 2019-06-20
plugged in, because the battery literally lasts one second.

---

### Post by naso4265 on 2019-06-21
I think I will try running xubuntu when I have the time. Switching distros isn't a big deal for me.

---

### Post by Autodave on 2019-06-21
Switching distros isn't likely to correct that problem.

Do you have any USB devices connected?  Try disconnecting them.  You *may* be having a problem with too low voltage on the USB.

---

### Post by CatKiller on 2019-06-21
I suspect that the USB ports are being put to sleep when idle - which is a standard power-saving measure - and then they can't wake up again because the computer's on its last legs. Since the laptop's plugged in all the time anyway, you may be able to turn off the sleeping behaviour. I don't know where the setting is off the top of my head, but powertop may list it.

---

### Post by naso4265 on 2019-06-21
Well, I had a problem when installing Ubuntu mate, where it would just freeze on the live DVD. I think that possibly the mouse was just freezing, and when using the live DVD of Xubuntu, i have no problems. I thought that possibly the problem was with the power to the USB ports, because the power supply I use with this laptop has a lower amperage, but I don't have this problem on Windows 7, and this problem happens even when I only have my trackball plugged in. I managed to find the proper power supply, but that didn't help.

---

### Post by naso4265 on 2019-06-21
> **Autodave said:**
>  You *may* be having a problem with too low voltage on the USB.
Actually, you may be onto something. I just barely discovered that when the USB ports aren't working, if i plug in a laser mouse, the laser just flashes, or doen't even turn on. My Wi-Fi transceiver still has power, but the power light flashes when I plug it in again.

---

### Post by naso4265 on 2019-06-21
Well, I don't know how, but installing Xubuntu fixed the problem.

---

