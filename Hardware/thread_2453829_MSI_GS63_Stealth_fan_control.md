---
title: "MSI GS63 Stealth fan control"
date: 2020-11-17
forum: Hardware
---

### Post by itrytocode on 2020-11-17
Hello, 
I was wondering if someone knows a way of controlling my fan speed in Ubuntu maybe with a equivalent to Dragon Center in Windows.

---

### Post by CatKiller on 2020-11-18
The *best* way to control the fans is to have the hardware do it. If your computer came with Windows, and the manufacturer has some application to harvest that sweet, sweet, user data that they want to encourage you to use, then they may have turned off hardware control by default, but if they aren't *too* user-hostile there will be a way to turn it on in your UEFI setup.

In the absence of that, or if the hardware fan curves aren't to your liking, you can have software control of your fans with the appropriately-named **fancontrol**. This is a simple service that reads values from your temperature sensors, looks up your preferences from a text file, then sends a signal to your fans. You should immediately see that it needs to be able to read sensor values and send signals to fans; sensor chip makers are really secretive about how to address them, and hardware makers do their own shonky stuff, but if your particular sensor/fan configuration has been reverse-engineered enough that it works with **lm-sensors** then fancontrol will work well.

---

### Post by itrytocode on 2020-11-18
For what should I look in the BIOS in order to control the fans via hardware.

---

### Post by CatKiller on 2020-11-18
> **itrytocode said:**
> For what should I look in the BIOS in order to control the fans via hardware.

I've never seen your UEFI setup screen, so I don't know what they've called it. It's going to be something like "fan profile," though. Potentially buried in a sub-menu somewhere.

---

### Post by itrytocode on 2020-11-18
Yeah I dont think I have it 
[IMG]https://scontent.fsof3-1.fna.fbcdn.net/v/t1.15752-0/p480x480/126206157_391983525330742_3548514677678930324_n.jpg?_nc_cat=102&ccb=2&_nc_sid=ae9488&_nc_ohc=TID_B7D81CsAX-ZB8xF&_nc_ht=scontent.fsof3-1.fna&tp=6&oh=2820c86173ce46da53bd3071c1c9f7ff&oe=5FDC6539[/IMG]

---

### Post by Yellow Pasque on 2020-11-18
Since it's a laptop, the fan control is probably done through ACPI and you don't have control over it without a proprietary program like Dragon Center.

---

