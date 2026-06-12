---
title: "Slow USB mouse after upgrade to Natty."
date: 2011-04-29
forum: Hardware
---

### Post by sjuranic on 2011-04-29
I have a Dell Latitude E6410 that I just yesterday upgraded to Natty.  Everything seemed to go fairly well, save for one issue.  The USB mouse that I have plugged into it shows *A LOT* of lag between what I'm doing with it and what shows up on the screen.  When using the integrated trackpad or thumbstick, everything seems okay.  I've played around with the sensitivity and acceleration in the settings menu, which helped a little, but the mouse is still pretty "muddy".

This issue occurs with both Unity and GNOME.

I hate using the thumbstick because I'm always accidentally bumping it while I type, and the thumbstick and track pad are on the same bus, so you can't have one without the other.  I'd love to figure out what's going on with this mouse so that I can disable the thumbstick once again.

Thanks in advance to any and all.

Cheers!

---

### Post by sikander3786 on 2011-04-29
Hopefully it is not what I am thinking but wouldn't it be better to test your mouse with some other PC/OS. It might just be a co-incidence that mouse somehow went bad at the same time when you did the upgrade.

Or try some other mouse with Natty if possible.

---

### Post by sjuranic on 2011-04-29
Well, now that you mention it, I did kind of notice that the mouse on my docking station seemed a bit "slow" as well after the upgrade.  I won't be back in the office until Monday, so I'll have to pay attention when I get back.  It will be more critical that this is working correctly then because the machine will be in clamshell operation and I won't have access to the track pad.

---

### Post by sjuranic on 2011-04-29
Okay, so I've tried a couple of things: Modifying the pointer feedbacks (both via xset and xinput) and modifying the mouse polling rate by using the "mousepoll=" option when loading the usbhid kernel module.  I've been able to make small improvements, but the performance is still noticeably worse than with the integrated track-pad / thumb-stick.

Still eager for any suggestions or other ideas.

Thanks.

---

### Post by sjuranic on 2011-04-29
Well, gee.  I rebooted into the older version of the kernel (2.6.35) and unplugged the secondary monitor from the laptop.  Then the mouse was working properly.  So I was ready to blame it on the kernel version.  However, I've now rebooted into the "stock" natty kernel (2.6.38) and things are still fine.  I'm starting to think that it actually has something more to do with the extra monitor being attached.  I'll play around with it a little more and see if I can narrow it down.

All I can say for now is, after several reboots, everything seems to be fine.

Hmmmm.

---

### Post by sjuranic on 2011-04-29
All right.  Now I rebooted with the second monitor attached and everything is **still** okay.  So I'm officially stumped.

I'm glad that the problem is fixed, but I sure wish I knew what fixed it.

---

### Post by sikander3786 on 2011-04-30
Glad to know it is fixed and hope it will not return as we don't yet know the causes :-)

---

### Post by arnemunk on 2011-05-09
I have this slow mouse-problem too after the narwhal-upgrade, the mouse starts off ok, but for some reason it gets tired after a while and gets very slow and elastic.

I have just the one monitor

cheers

---

### Post by Marco Mariani on 2011-05-20
I have the same issue with a Latitude E6410, since the Natty upgrade. I've never seen it before that.

Once in a while (maybe a little below 10% of the times) the mouse is laggy and slow and jumpy on all of the 4 USB ports.

Touchpad works ok, a USB thumb drive works ok (after manually mounting, didn't pop up a window)
Rebooting usually fixes the mouse.

Is there some log message I could look for? I didn't see anything crying for alert but didn't look very hard.

kernel is 2.6.38-8-generic-pae #42


thanks

---

### Post by uwf_doc on 2011-06-10
I'm having the same problem on a Dell Latitude E6510.  Once out of every 5 bootups or so, the mouse will really lag.  If I unplug it and try different USB ports it does the same thing in all 4 ports.  If I reboot, usually the problem goes away, but sometimes not.

---

### Post by thodpol on 2011-06-13
I can confirm the same behavior. The problem started from ubuntu 10.10 but after some updates it was fixed. Now that I upgraded again my system to 11.04 I am having the same problem. I have a latitude E6510 with a usb logitech m510 mouse.  

Is there any way of restarting the daemons responsible for mouse and usb instead of rebooting again and again?

---

### Post by walidzohair on 2011-06-27
Natty sucks and it is very slow .. I wish i stayed with maverick .. and now all my files and bookmarks and tiny whiny lil details is on this flash and i do not want to reinstall :(

---

### Post by uwf_doc on 2011-07-05
I've been hoping for a solution to this problem for weeks now.  I too am using a Dell E6510, but I'm using Linux Mint, so I've been hesitant to post a bug report myself.  After about every 5th boot, the mouse will be choppy, slow, and laggy.  Unplugging and replugging doesn't help, nor does moving to a different USB port.  Sometimes it can take up to 3 reboots before the problem goes away.

There has to be a daemon or something that can be restarted to fix this, right?

---

### Post by TheFluffyOne on 2011-07-27
I see this issue as well. It happens intermittently at boot, and a reboot will usually sort it out.

Machine: Dell Latitude E6510
OS: Ubuntu Natty (11.04)
Mouse: Microsoft Bluetooth Notebook Mouse 5000

The jerkiness only affects the external mouse; the internal touchpad and stick work smoothly.

Have had a dig through Launchpad and found a few similar-sounding bugs; [the closest of these]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/294822") seems to be related to the Logitech MX900. I'm not sure it's quite the same issue.

Anyone know if there's a bug raised for the specific issue described in this thread? If not, I'll raise one.

---

### Post by ArTaX on 2011-08-21
I have the same problem on Dell Latitude E6510 with Ubuntu 11.04.
I've found [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/658538"), may it be related?

---

### Post by moebius10 on 2011-09-01
I'm seeing the exact same issue. I just installed (dual boot) Natty and the mouse is so sluggish it's painful to use. The mouse is a wireless Logitech M310.
The touchpad on the Inspiron works fine.

---

### Post by machs on 2011-12-18
I was having a similar problem, 

Slow USB transfers and the usb mouse became slow / floaty when ever i plugged in a flash drive. 

Plugged the mouse into an external hub then into the PC and things are much better now.

Apparently the USB speed is set to the slowest device on the hub.

---

### Post by emacs on 2011-12-28
I too have the same problem on Dell E6410.

It is a "slow usb" problem in general at least for me.
Whether you plug in a mouse or a disk, everything is really slow as if the USB 2.0 ports are operating in USB 1.0 mode.  For example disk I/O is less than 2 mega bytes per second when my machine is in that state.

The only solution seems to be to reboot possibly multiple times.
Sometimes usb ports seem to come up and operate at USB 2.0 speed.
At other times they come up at USB 1.0 speed.
Sometimes it takes multiple boots to come up at 2.0 speed.
Plugging in a usb mouse and moving it is a really good way to test.  If it is sluggish, then the machine came up in 1.0 mode.
If the mouse movement is crisp, then the machine came up in 2.0 mode.

I even updated the main BIOS software, but not much different.
Sigh.

---

### Post by darence on 2012-02-17
Same here. Moreover, the problem is not exclusive to Ubuntu. I've tried Fedora and OpenSUSE as well, the problem appeared sooner or later on both (I have a Dell E6510). So the problem is in some of the core system components, maybe even in the kernel itself... and it exists since almost a year as far as I could notice.

---

### Post by stefano_to on 2012-05-14
Same problem here with Ubuntu 11.10 and a Dell Latitude E4310. I've tried with several "mouse", wireless and wired, and the problem persists (even if, once in a while, the mouse works)... :(

---

### Post by dunecoon on 2012-07-15
Same problem here, got an old toshiba whatsitsmodel. Touchpad works fine, but the mouse feels like it's retarded

---

### Post by TheodoreWard on 2012-11-15
> **uwf_doc said:**
> I've been hoping for a solution to this problem for weeks now.  I too am using a Dell E6510, but I'm using Linux Mint, so I've been hesitant to post a bug report myself.  After about every 5th boot, the mouse will be choppy, slow, and laggy.  Unplugging and replugging doesn't help, nor does moving to a different USB port.  Sometimes it can take up to 3 reboots before the problem goes away.

There has to be a daemon or something that can be restarted to fix this, right?

I have had this problem intermittently as well for some time. And its kind of a hard bug to search for due to the generic terms.
I usually reboot, but for me Ubuntu is a slow booter and it sucks when I have to do it twice in a row.

I haven't tried it for this issue, but something along [these lines]("http://abunchofbaloney.blogspot.com/2012/11/reset-usb-ports-in-ubuntu-1210.html") just might kick it in the nuts enough to get it going.

Basically unbind and rebind USB:
  tward $ lspci | grep USB 
  00:1a.0 USB controller: ...
  00:1d.0 USB controller: ...

Then do the following:

  tward $ echo -n "00:1a.0" | \
          sudo tee /sys/bus/pci/drivers/ehci_hcd/unbind
  tward $ echo -n "00:1a.0" | \
          sudo tee /sys/bus/pci/drivers/ehci_hcd/bind

---

### Post by fiskekroken on 2013-04-13
Double post delete

---

### Post by fiskekroken on 2013-04-13
I have the exact same problem, Dell E6410 laggy mouse from time to time.. currenly running Linux Mint 14, but its the same in Ubuntu 12.10 :(

TheodoreWard solution worked fine, created a script for it:

```
#!/bin/sh
# Buttkicker script

sudo echo -n "0000:00:1a.0" | tee /sys/bus/pci/drivers/ehci_hcd/unbind
sudo echo -n "0000:00:1d.0" | tee /sys/bus/pci/drivers/ehci_hcd/unbind
sudo echo -n "0000:00:1a.0" | tee /sys/bus/pci/drivers/ehci_hcd/bind
sudo echo -n "0000:00:1d.0" | tee /sys/bus/pci/drivers/ehci_hcd/bind
```

Thanks

---

### Post by lukasz-iwaszkiewicz on 2014-01-22
Hi same issue here. I have Dell Lattitude E6510 running Ubuntu 12.10 

uname -a
Linux unitra 3.5.0-44-generic #67-Ubuntu SMP Tue Nov 12 19:36:14 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

I also noticed that If I connect the mouse to the docking station everything works fine, and no lag issue ever happens. Also I have custom USB device (STM32F4 USB OTG, ST's USB stack) which performs interrupt transfers extensively (just like mouse, but single transfer is 64B wide), and when connected to notebook's USB ports it sometimes hangs, but when connected to the docking station it works seamlessly (but of course my device may be buggy as well). Can it be that latitudes have buggy USB hardware, and kernel works fine?

---

