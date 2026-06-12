---
title: "Suspend with Ndiswrapper"
date: 2005-08-07
forum: Hardware &amp; Laptops
---

### Post by mjwood0 on 2005-08-07
I got Ubuntu installed on my Inspiron 8100.  Nvidia modules loaded and everything runs normally.  However, whenever I suspend, my network card's lights turn off and then nothing else happens.  ](*,) 

I checked dmesg and the following error appears over and over (about every 2 seconds)

```
usb usb1: USB disconnect, address 1
usb 1-2: USB disconnect, address 2
uhci_hcd 0000:00:1f.2: USB bus 1 deregistered
unregister_netdevice: waiting for wlan0 to become free. Usage count = 1
unregister_netdevice: waiting for wlan0 to become free. Usage count = 1
unregister_netdevice: waiting for wlan0 to become free. Usage count = 1
............
```

If I open a terminal and try to kill anything or shutdown, the terminal session hangs. 

Any advise?

Thanks in advance!

---

### Post by elsewhere on 2005-08-07
Well, FWIW, I'm using ndiswrapper on my inspiron 8100 and it works like a charm for suspending so at least there should be no hardware incompatibility for you unless it's to do with the specific win driver for your wireless card.

How are you suspending?  Closing the lid?  Triggering a suspend?

The acpi scripts or helper utilities often take additional actions prior to suspending that may be causing some issues as well.  I disabled most of the superfluous stuff in my scripts.

Just a thought, but maybe try manually triggering suspend with the command *sudo sh -c "echo mem > /sys/power/state"* and see if that works, might help narrow down the problem.

Cheers,
KV

---

### Post by mjwood0 on 2005-08-08
Thanks.  I'll give that a try tonight.

I've usually been attempting the suspend via the logout menu.

I'll let you know how it works.

---

### Post by mjwood0 on 2005-08-09
Okay.  I tried to suspend using the command supplied.  Slightly different behavior, but still the repeated network errors.  

Figured I'd remove the wireless card, reboot and try again.  Same problem.  What's weird is that ndiswrapper shouldn't be loaded if the card isn't in, right?

Thanks for the help so far!

---

### Post by mjwood0 on 2005-08-10
Anyone have any more suggestions?

I've looked in the HOWTOs and never seen anything quite like this before.

Thanks for any help!

---

### Post by jkka on 2005-08-20
I have the same problem. I have to unload the ndiswrapper module before suspending. Somehow the prepare.sh script is not able to do the unloading even that I have added ndiswrapper to the /etc/default/acpi-support.

As a workaround I simple added line

```
rmmod ndiswrapper >/dev/null&
``` 

in the beginning of the prepare.sh. Magically it works and because I left the ndiswrapper to the acpi-support file so it also becames reloaded when resuming.

Hope this helps.

Laptop is HP NC6120 with broadcom wireless (BCM4306). Im using self compiled ndiswrapper-1.2. The hoarys version didnt work at all.

---

### Post by elempoimen on 2005-08-20
Try installing "hibernate" through Synaptic (or apt-get, whatever your preference).  I suspect, like me, that your problem has less to do with your wireless and more to do with your setup.  Make sure you edit /etc/hibernate/hibernate.conf to use ACPI suspend instead of swsusp2, which I'm sure you don't have installed.

Before you use the hibernate script for the first time, you'll also want to make sure that your kernel boot line has "resume=/dev/hdaX", "X" being whatever your swap partition is, and be sure your swap partition is 2x your RAM + video RAM.

THEN, open a console and try "sudo hibernate."  If that works, there are tons of ways the script can be customized.  Go to [http://softwaresuspend.berlios.de](http://softwaresuspend.berlios.de) for more info.  (Yes, I know that's the site for swsusp2, but the hibernate script comes from there as well.)

I'm still working on making sure that this works with the hibernate command on the Log Out dialog (I've not tested it yet), but I have it working with my hibernate hotkey on the system.

---

### Post by elempoimen on 2005-08-20
OK, an update on hibernating from the Log Off dialog.  Here's what you need to do:

[list=1]
[*]Open a root Nautilus (gksudo nautilus) and navigate to /etc/acpi
[*]Rename "hibernate.sh" to "hibernate.old.sh" (or whatever you want...just keep it)
[*]Open a second root Nautilus (gksudo nautilus) and navigate to /usr/sbin
[*]Locate "hibernate" in /usr/sbin and EITHER right-click on it, select "Make link" and drag the new link over to /etc/acpi OR middle-drag "hibernate" over to /etc/acpi
[*]Rename the new link in /etc/acpi to "hibernate.sh"
[/list] 

And then, give it a whirl.  I think you'll be pleased!

---

### Post by toastedd on 2005-08-22
[QUOTE=elempoimen]Try installing "hibernate" through Synaptic (or apt-get, whatever your preference). ][/QUOTE]

They're talking about Suspend to RAM (aka Suspend)... not Suspend to Disk (aka Hibernate).

Hibernate is basically useless.

---

### Post by elempoimen on 2005-08-22
OK--didn't catch that.

But why do you say that hibernate is basically useless?  I have it 100% functional on my system--and I find it very useful.

---

