---
title: "Edgy breaks Axim USB support"
date: 2006-10-30
forum: Hardware &amp; Laptops
---

### Post by Psiren on 2006-10-30
Hi guys,

I've recently installed Edgy on my machine at home and I can't get it to recognise my Dell Axim X51v properly. I'm using VMWare Server and Windows XP to actually sync and develop with it, I just need the USB subsystem to support it properly. The driver shows up as (none) in /proc/bus/usb/devices, and as a consequence I can't connect it in VMWare. My Dapper installation at work recognises it properly using the driver usbfs, and it works just fine under VMWare. Any ideas why Edgy would stop recognising it? I'm using 
kernel 2.6.17-10-generic under Edgy, and 2.6.15-26-686 under Dapper. Any help appreciated.

---

### Post by Psiren on 2006-11-12
Anyone? I still haven't had any luck with this. Is there somewhere else I should be asking for advice?

---

### Post by ginge on 2006-11-20
Try this:-

sudo mount -t usbfs usbfs /proc/bus/usb

You can do this while VMWare is running, and then attach the device using the menu.

Baz

---

### Post by Psiren on 2006-11-21
Hi,

/proc/bus/usb is mounted, as I mentioned in my first post. It's just that there is no driver assigned to the device in /proc/bus/usb/devices.

Thanks for responding though :)

---

### Post by ginge on 2006-11-22
Odd, I had the exact same problem, and as bug resolution 35004 solved it for me.

| [https://launchpad.net/distros/ubuntu/+source/sysvinit/+bug/35004](https://launchpad.net/distros/ubuntu/+source/sysvinit/+bug/35004)

If you already have the procbususb line in mount, I am lost.

| procbususb on /proc/bus/usb type usbfs (rw)

The only thing I had to do to get it working fully (edgy amd64) is mount the above, and apply the vmware-any-any-105 update from 

[http://ftp.cvut.cz/vmware/](http://ftp.cvut.cz/vmware/)

Sorry I couldn't help :(

---

### Post by ginge on 2006-11-22
I made a small mistake on that post...

none on /proc/bus/usb type usbfs (rw)

should appear in the mount list as well as procbususb.

Despite the fact that procbususb is mounted, try to remount it anyway.

I also (just) has this problem with another machine and my XDA. this mount also solved it for this device.

B

---

### Post by Psiren on 2006-11-22
Nope, no luck. What concerns me is that it's showing up in the devices file, just with a driver of (none). So, it's definitely finding the device on the bus, just not doing anything useful with it :/

Thanks for trying to help though :)

---

