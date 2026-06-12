---
title: "Problems with Toshiba laptop..."
date: 2006-02-18
forum: Hardware &amp; Laptops
---

### Post by SolPhoenix on 2006-02-18
I'm not quite sure where this should go... So if this is in the wrong place, could someone please tell me where I should ask these questions?

Okay... To start off, I'm using the Dapper "Flight Test" because Breezy had some weird conflict between ACPI and Networking that wouldn't let me go online AT ALL (i.e. absolutely no networking) without disabling ACPI.

I now want to be able to use my Fn keys that are on the Toshiba laptop's keyboard, so I tried installing the FnFx package which gave the error "Fatal error: Could open /proc/acpi/toshiba/keys" and I've even tried using "modprobe toshiba_acpi" (which was mentioned in README.toshiba in the documentation folder) and it results in "FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.15-15-386/kernel/drivers/a cpi/toshiba_acpi.ko): No such device" My question is: Does anyone know how to get my Fn keys to work? I'm using a Toshiba Satellite (from the M45 series.)

Also... I've been having some problems with my wireless recently and I've noticed when restarting/shutting down that I'd see many errors resulting from ipw2200 (the intel wireless driver) and someone told me to do a "dmesg | tail" which showed "[4304423.809000] ipw2200: Firmware error detected. Restarting.
[4304423.809000] ipw2200: Sysfs 'error' log already exists." several times just like what happened when I was restarting/rebooting. It didn't happen when I first tried out the Dapper "flight test", so I must assume that some "update" has actually caused this error. Anyone know what's going on here and how fix this to keep my wireless connection without having the driver randomly fail?

Again, I'm sorry if I'm posting this in the wrong place...

---

### Post by WiredPig on 2006-09-06
I have a Toshiba M45-S265. Dapper installed fine, but, panicked after I entered my user ID and password. I tried everything I could think of to fix the issue. I finally stumbled across adding pci=noapic (not pci=noacpi and not acpi=off) to the boot command. 

All works well so far. Sound, CPU scalling, etc. Just a minor issue of looing connectivity when I attach my BT dongle and connect to my GPS... but an easy reboot and its back up.

For more help, take a look at [Small FAQ for Ubutnu on Toshiba laptops]("http://ubuntuforums.org/showthread.php?t=230565&highlight=toshiba+faq").

I have not tried the fn keys yet.

If you boot from the live CD, add pci=noapic when grub starts as described in the link above. Also, if all works well with the live cd boot and device detection, configure your wifi connection before you install and the settings will be carried over. I assume (bad word, I know) that configuring your wired connection will work the same way. 

Hope some of this helps. Keep me posted.

WP

---

### Post by WiredPig on 2006-09-07
I goofed... the pci=noapic is the boot command under SuSE 10.1. I apologize... the correct boot command to add is pci=noacpi.

---

