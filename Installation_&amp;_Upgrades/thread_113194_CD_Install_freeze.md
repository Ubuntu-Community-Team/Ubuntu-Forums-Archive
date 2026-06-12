---
title: "CD Install freeze"
date: 2006-01-05
forum: Installation &amp; Upgrades
---

### Post by trajik78 on 2006-01-05
hi all, 1st post here and im excited to get going on some new Linux Os fun as Windoze is slowly killing me. just ahving some probs w/ install to an ATA HD.

I've downloaded the 5.10 .iso burned the cd which boots fine. The CD seems to boot properly into the install menus and I get to the part where it seaches my hardware after i pick my keyboard layout then it just goes to a blue screen and seems to have no more going on. The CD isn't spinning and the HD doesn't seem to be ticking. any seggestions? Tx!

----
Specs:
3.4e P4
P4C800-E
2x512 Corsair PC4400
eVGA 6800GT
SB Audigy 2 ZS
60GB Hitachi Deskstar (IDE)

---

### Post by byen on 2006-01-06
Ok. this might work since it might be an acpi issue or a legacy support issue.
Try this:
try to install again with the acpi-off option
also you might want to go to your boot menu and disable the "legacy usb support system" in your computer. A lot of distros seem to have problems with these two. Let us know if this worked out. If now we can start digging into other areas.
And Hey.since this is your first post. Welcome to Ubuntu.

---

### Post by trajik78 on 2006-01-06
i let the blue screen i get after it says it's lookign at my hardware go fo about 3 minutes at which oint  i get a dialouge that says "unable to mount CD, most likely due to cd being ejected.." or something to that effect.

Legact USB s off in my BIOS. i will try the acpi-off option. where do i enter that  command? i assume at the point when i get the "boot" prompt and have the ability to add special commands such as server installation?

i looked at the quick start guide (wiki?), but it seems to skip installation and goes straight to the next step.

---

### Post by tseliot on 2006-01-06
[QUOTE=trajik78]i let the blue screen i get after it says it's lookign at my hardware go fo about 3 minutes at which oint  i get a dialouge that says "unable to mount CD, most likely due to cd being ejected.." or something to that effect.

Legact USB s off in my BIOS. i will try the acpi-off option. where do i enter that  command? i assume at the point when i get the "boot" prompt and have the ability to add special commands such as server installation?

i looked at the quick start guide (wiki?), but it seems to skip installation and goes straight to the next step.[/QUOTE]
You can try either acpi=off or noapic nolapic.

Boot the Ubuntu install CD.
You will see the brown Ubuntu logo and some lines below it. The last line is "boot:"

you have to be fast because this thing is displayed only for some seconds (maybe I'm wrong though)

type the following options (which will appear after the "boot:" word)

```
linux acpi=off
```

Press ENTER and see if the installation goes on

OR if that didn't work reboot and try this:

```
linux noapic nolapic
```

I hope it helps

---

### Post by trajik78 on 2006-01-06
awsome  i will try those when i get home tonight and post my results. what's APIC anywho?

---

### Post by tseliot on 2006-01-06
[QUOTE=trajik78]awsome  i will try those when i get home tonight and post my results. what's APIC anywho?[/QUOTE]
[http://en.wikipedia.org/wiki/Apic]("http://en.wikipedia.org/wiki/Apic")

---

### Post by kook44 on 2006-01-06
Do you have a SATA or PATA drive?  The debian installer is known to have issues with SATA drives.  I had problems installing debian sarge on an SATA drive.  Look here:
[http://www.debian.org/releases/stable/debian-installer/](http://www.debian.org/releases/stable/debian-installer/)
scroll down to the Errata section and read about it there.  somehting about "SATA driver can block access to CD drive in installations from CD"

I searched the web quite a bit and couldn't find much else on it.  maybe you will ahve better luck.  Fortunately for me, the updated version of the installer that comes with ubuntu 5.10 worked.

good luck

---

### Post by trajik78 on 2006-01-06
i have a SATA HD hooked up that has WinXP Pro on it, but the HD i will be installing to will be a PATA HD. is it a problem if the SATA HD is simply hooked up?

---

### Post by kook44 on 2006-01-06
[QUOTE=trajik78]i have a SATA HD hooked up that has WinXP Pro on it, but the HD i will be installing to will be a PATA HD. is it a problem if the SATA HD is simply hooked up?[/QUOTE]

It was for me.  I was trying to do the exact same thing.   I think just the presence of the SATA was blocking the PATA CD-ROM.

Like I said, this was trying to install debian sarge.  ubuntu breezy has a newer installer, which worked for me.  Not sure if you are having the exact same problem, but maybe this will get you on the right track.

---

### Post by trajik78 on 2006-01-06
i think im using the latest installer (5.10) i just DL'd it. well, hopefully the APIC fix works. What Intel chipset started to include this chip in favor of the older 8259 chip? 

It be a bit rediculous that a little thing like a SATA HD being plugged in would cause this problem. I guess in a perfect Linux world the installer would know what to do automatically...baby steps i guess.

---

### Post by trajik78 on 2006-01-06
well, im at a loss. i tried the 1st seggestion: i used the 1st cod "linux acpi=off" and the same thing happened. i then used the 2nd code "linux noacpi nolacpi" and that made the install hang when it started loading the ide drivers.

then i tried simply disconnecting the sata drive and that didn't work. then i tried the codes again, and same result. wtf!??

::EDIT::
i DL'd Debian and the installion went fine. but now im stumpped as to get to a desktop. i've logged in and im sitting at this prompt:

pat@debian:~$

---

### Post by tseliot on 2006-01-07
[QUOTE=trajik78]well, im at a loss. i tried the 1st seggestion: i used the 1st cod "linux acpi=off" and the same thing happened. i then used the 2nd code "linux noacpi nolacpi" and that made the install hang when it started loading the ide drivers.

then i tried simply disconnecting the sata drive and that didn't work. then i tried the codes again, and same result. wtf!??

::EDIT::
i DL'd Debian and the installion went fine. but now im stumpped as to get to a desktop. i've logged in and im sitting at this prompt:

pat@debian:~$[/QUOTE]
Ehm, the 2nd code was  "linux noapic nolapic" (not "linux noacpi nolacpi").

If Debian's installation went fine it means that its kernel (2.4.x) has the support for your chipset (of the ide controller or sth else).

I think Debian can be a bit difficult for a newbie.

Why don't you try Mepis (which is based on Debian)?
You can try the latest (testing) version (3.4.2 RC1) which seems stable or 3.3.1 (which is stable but as old as Debian). You can install it from the livecd(which is the same as the install cd) and you can choose between kernel 2.6.12 and 2.4.x.

You can download it from Mepis website: [http://www.mepis.org/]("http://www.mepis.org/")

---

### Post by trajik78 on 2006-01-07
i DL'd the DVD installer for Fedora (before is read this) and now it likes to hang when it's loading the 1394 driver and keeps trying to disable IRQ #11.

---

### Post by tseliot on 2006-01-07
[QUOTE=trajik78]i DL'd the DVD installer for Fedora (before is read this) and now it likes to hang when it's loading the 1394 driver and keeps trying to disable IRQ #11.[/QUOTE]
That happened also to a computer of mine... (I had a SATA controller)

You can try both Mepis and PCLinuxOS.

In Mepis try both the newer and the older kernel. See which boots.

It's just a matter of kernel (version and modules).

---

### Post by jesrah on 2006-01-07
hey can you help me i'm using ubuntu live cd stuck on enter presession... 10% configuring snapshot

---

### Post by tseliot on 2006-01-07
[QUOTE=jesrah]hey can you help me i'm using ubuntu live cd stuck on enter presession... 10% configuring snapshot[/QUOTE]
What do you mean by enter presession?

---

