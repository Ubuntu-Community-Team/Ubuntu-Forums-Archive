---
title: "Logitech MX 5000 Bluetooth Keyboard/Mouse not working"
date: 2007-01-09
forum: Hardware &amp; Laptops
---

### Post by durnurd on 2007-01-09
I am stuck with the dreaded wired keyboard/mouse combo for now.  As soon as I turn on my computer, my wireless USB keyboard and mouse combo (Logitech MX 5000) works just fine.  I can get into the BIOS, and I can start Ubuntu, but as soon as Ubuntu starts booting, my wireless keyboard and mouse stop working altogether.  I currently have another set of keyboard and mouse hooked up simultaneously so that I can work inside the OS.  Both keyboards and both mice work fine just as the mouse shows up in the OS, but about three seconds later, one of them just stops.  Any suggestions?

---

### Post by ecurb on 2007-01-10
i have the same problem but i found a temp around.

when i get to the login screen i don't have the keyboard or mouse working but i found that if i pull out the bluetooth and put it back in, a few seconds later they both work!!!

its a pain because you have to do it every time you reboot or reset but when you dont have another keyboard or mouse i can wait till someone has a fix..

---

### Post by matt221984 on 2007-01-19
I have the above issue as well, and the unplug/plug fix works for me, but I have been doing it since Edgy came out and it is starting to get on my nerves.

I remember seeing a post or a page about putting something in the startup to reconnect the device, but I cant seem to find it now.

---

### Post by Roger Mudd on 2007-01-19
I have the same hardware, have the same problem and I'm using the same solution - unplugging the dongle and plugging it back in as soon as the login screen appears. I remember their being a trouble ticket for this issue on launchpad. A search for "bluetooth" and "mouse" returns [118 results]("https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=bluetooth+mouse&orderby=status&search=Search&field.status%3Alist=Unconfirmed&field.status%3Alist=Confirmed&field.status%3Alist=In+Progress&field.status%3Alist=Needs+Info&field.status%3Alist=Fix+Committed&field.assignee=&field.owner=&field.omit_dupes=on&field.has_patch=&field.has_no_package=").
I don't think the issue has been resolved.

---

### Post by matt221984 on 2007-01-20
I found what I was looking for...

here is the bug report [https://launchpad.net/ubuntu/+source/bluez-utils/+bug/32415](https://launchpad.net/ubuntu/+source/bluez-utils/+bug/32415)

it looks like removing all bluez packages might work for some people. It worked for me.

```
sudo apt-get remove bluez-cups bluez-pcmcia-support bluez-pin bluez-utils
```

However, if you do this, you won't be able to connect any other bluetooth devices like headsets, phones, etc.

If you read at the bottom of that bug report someone says that this bluez bug has been fixed in kernel 2.6.19rc3. So when Ubuntu goes to 2.6.19 it shouldnt be an issue anymore.

However it also says something about this fix only affecting the powerpc.

> 
The kernel patch applies to all platforms (it changes arch-independent sources).

But the bug doesn't occur on the other platforms:
- x86 is 32bit userspace on a 32bit kernel
- amd64 is 64bit userspace on a 64bit kernel.

The bug only appears when a 32bit userspace is used on a 64bit kernel - this is the powerpc64 platform.

So the kernel patch applies to all platforms, but it only fixes breakage specific for powerpc64.


Anyway, if you don't care about other bluetooth devices not working, just run that command above.

---

### Post by Innova on 2007-05-21
I am considering the MX5000 or the Microsoft 7000 bluetooth keyboard/mouse...

I am just wondering on what the status of bluetooth keyboard/mice is with Fiesty.

Can anyone post an update?

---

### Post by gi2k15 on 2007-05-24
The same problem still happens with 7.04.

---

### Post by Jabone on 2008-04-04
> **gi2k15 said:**
> The same problem still happens with 7.04.

Same problem in hardy too.

---

### Post by durnurd on 2008-05-03
I was able to get the mouse working with at least some of the buttons.  Left,right,middle, scroll wheel, and forward and back on the side.  You have to install the Bluetooth Obex server in add/remove applications.

I have not used the keyboard for awhile now, since it doesn't have auto-recharging like the mouse.

---

