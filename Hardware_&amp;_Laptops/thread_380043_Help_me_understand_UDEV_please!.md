---
title: "Help me understand UDEV please!"
date: 2007-03-09
forum: Hardware &amp; Laptops
---

### Post by jay019 on 2007-03-09
Hi All,

I have tried writnig a udev rule for my usb mouse so that once it's plugged in it will run a script in my .scripts directory. Here is what I have in /etc/udev/rules.d/09-usbmouse.rules ...

```

BUS=="usb", SYSFS{idVendor}=="04d9", RUN+="/home/jay019/.scripts/usbmouse.sh"

```

I restarted udev (sudo /etc/init.d/udev restart) but my rule doesn't appear to work. All the script does at the moment is display a dialog using zenity, but the purpose is to disable the touchpad once the usb mouse is plugged in.

So, is something missing? Does it need a KERNEL=="" in the rule?


Also, is there a way to check if the usb mouse is plugged in at boot time and run my rule (once it works)

Thanks.

Jay

---

### Post by jay019 on 2007-03-11
Anyone? I'm sure its something simple that just wont click for me. Udev is new to me and I have to admit I have no idea.

---

