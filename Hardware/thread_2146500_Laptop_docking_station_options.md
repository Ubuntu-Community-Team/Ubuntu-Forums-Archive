---
title: "Laptop docking station options?"
date: 2013-05-18
forum: Hardware
---

### Post by hambone79 on 2013-05-18
I currently have a desktop machine running Ubuntu 12.04 and another desktop running Windows 7. Both machines are showing their age so I would like to consolidate/replace them with a laptop. My only issue is that I would like to keep my current dual monitor setup with the laptop but I'm not familiar with how to do this. Here are my options from what I understand looking online:

1. Get a laptop that supports dual displays out of the box. Unfortunately, I haven't found any that can support dual displays.
2. Get a laptop that supports dual displays via a docking station. This is a good option, but it seems that the laptops that support a docking station are somewhat limited.
3. Get a newer laptop and setup dual displays via a USB docking station. I have never used this type of hardware before so I really don't know anything about performance, max resolution, etc.

BTW, I intend to do some light CAD work with Pro/E and some gaming (mostly HL and HL2 based games) so I need the external displays to have decent performance.

Can anyone out there enlighten me on a good configuration that would work for both OSes and perform well enough to do what I want to do?

---

### Post by linrunner on 2013-05-18
Hi,

3) Just forget USB docking stations. The contained Display Link chips won't make you happy on Linux. In fact there are drivers but no support for the desktop.

---

### Post by hambone79 on 2013-05-18
> **linrunner said:**
> Hi,

3) Just forget USB docking stations. The contained Display Link chips won't make you happy on Linux. In fact there are drivers but no support for the desktop.

After digging a little more it looks like everyone is using USB 3.0 for the docking station these days so I think #2 is out of the question as well. It looks like my only option at this point is to use something like the Matrox DualHead2Go. It isn't as clean as using a docking station, but it beats being stuck on one monitor.

---

### Post by linrunner on 2013-05-19
Not everyone. Serious business laptops (Lenovo ThinkPad T/X/W series, HP Elitebook, Dell Latitude) still have classic docking stations.

---

### Post by Askel on 2013-05-19
I've got a Dell Precision M4600 with nvidia and 12.04 lts and a dockingstation. It works out of the box with external monitor connected to the displayport of the port-replicator. I havn't tried it with dual monitors, but from what I've read it works fine with up to three monitors. I have to disconnect the displaycable when grub loads to get it to work though

---

### Post by Phateless on 2013-11-03
My work laptop is a Dell Latitude E6430, and at the office I have the docking station plus dual monitors. I haven't booted Linux while it's on the dock, just a live usb while undocked. - [http://www.dell.com/us/business/p/latitude-e6430/pd](http://www.dell.com/us/business/p/latitude-e6430/pd)

At home my machine is a Dell Latitude D620 with a docking station, 2nd monitor, and Lubuntu 13.10 live usb when I'm not in the mood for windows. Dual monitors work just fine on the live usb with ARandR from the Software Center. The only kink is that disconnecting from the dock while the laptop is on causes weirdness leftover from the dual displays, and reconnecting while on seems to lock the system - so you'd have to reboot every time you disconnect and reconnect. If you're only using it on the dock during the day and taking it home at night, this is no issue. If you're a manager constantly running in and out of meetings, this is a show stopper.

linrunner is right that serious business laptops still have proper docking stations, and my E6430 seemed to do just fine on my live usb. Start googling for business laptops with docking stations and see where you end up.

Good luck!

---

