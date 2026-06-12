---
title: "Lid closed - screen turns back on"
date: 2007-11-25
forum: Hardware &amp; Laptops
---

### Post by modu on 2007-11-25
Hi,
Todays problem I have is that when I close the lid on my laptop it becomes black, thats good, but after a while (everything from two seconds to a minute), it jumps back on, not so good. This happends both when its running on battery and when it isnt. This causes the battery to drain out of juice faster and worse, it makes the computer overheat if I leave it turned down but with the monitor on. 
I also noted that if I turn the monitor light up, which goes down to about 50% when running on battery, it jumps back after a few minutes, might this be related? Maybe that it keeps setting the monitor to right light level, which causes it to jump back on? I dont know, I'm just guessing.

Any idea on fix?

Specs:
Laptop, Dell D520. Latest ubuntu 7.10, standard installation pretty much, Gnome etc.
Full lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
02:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```
Standard kernel, 2.6.22-14-generic

---

### Post by gedden on 2008-04-23
I have the same problem on a compaq armada m300. It takes a bit longer for my screen to turn back on after I shut the lid. More like 10 to 20 min. 
Help! this is killin an already old laptop

7.1, everything else is standard.

---

### Post by gedden on 2008-04-24
Bump for any ideas on how to log the situation?

---

### Post by gedden on 2008-05-03
I had a revelation tonight. My fiancée noticed that the usb mouse that we have plugged into the laptop was causing the screen to turn back on. It was happening  with slight vibration.
So. I'm assuming the screen blanking thingy? isn't watching the screen closed variable. Is this a configuration problem or does a custom script need to be written?

---

### Post by jordoex on 2008-05-23
I've got the same problem here, with a Dell Inspiron 1520.  It happens with even without guidance-power-manager (KDE) running, so it's probably an ACPI bug.

Anyone know how to fix this?

---

### Post by gedden on 2008-05-23
I've just unplugged the usb mouse every time I shut the lid. It hasn't turned back on in two weeks. At least in my case this is what was turning my screen back on with the lid closed.

---

### Post by jordoex on 2008-05-23
I remember the other annoying problem that this makes: I use the multimedia keys for amarok when I have the lid closed and that also makes the screen go on, which isn't that big of a deal, but it's insanely annoying.

---

### Post by mindestens on 2008-05-26
EDIT: sorry, this is not a solution for your problem. i was thinking that your pc freeze after you close the lid! now i don't know how to delete this post :-/

post:
try to do this:
```
$ sudo su
# echo 7 > /proc/acpi/video/*/DOS 
```

if it works, you can automate this for every boot (otherwise the setting will be lost if you reboot):

edit /etc/rc.local by adding the following line before the line exit 0
```

for f in /proc/acpi/video/*/DOS; do echo 7 > $f; done
```

btw. its not my solution, got it from here: [http://bbs.archlinux.org/viewtopic.php?id=39840](http://bbs.archlinux.org/viewtopic.php?id=39840)


i have a HP 6510b with intel GM695 video and this works for me...


(if someone else has success with this woraround, could this person please spread the words to this topic: [http://ph.ubuntuforums.com/showthread.php?p=4692636](http://ph.ubuntuforums.com/showthread.php?p=4692636)
somehow i'm not able to register on this page :-(

---

### Post by jordoex on 2008-06-08
Yeah, something that I wanted to mention before is that I want the behavior to be as if you pressed the power button on your monitor, but it seems to behave as if you just waited long enough for the monitor to go onto power saving mode, in which case the screen should come back on.

In this case, it shouldn't.  Tis annoying and there's probably something in hal that should fix it.

---

