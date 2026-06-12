---
title: "Installing 8.10"
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by FoXoF on 2009-03-02
Hey,


I'm an experienced windows XP user who refuses to upgrade to Vista. I dont like where windows is going so I tried out the 8.10 boot cd. I was pleasantly surprised at how much ubuntu can actually do compared to the mainstream leader, windows. So I decided to wipe my spare 80gb hard drive and install ubuntu 8.10.


I have two 80GB hard-drives in my computer. One of them is empty, the other has windows XP on it.

When I use the installer I successfully get up to the "Checking Battery State" part. At which point the screen flashes a few times for about 20 seconds and then displays an error message about something todo with display failing 6 times in last 90 seconds.

I have tried various solutions to this problem, running in safe graphics mode, running in OEM install mode.

I have also used the following command line options using F6 on the installer:

```
acpi_osi="Linux"
"acpi=force pci=noacpi"
"acpi=off"
```

Should the '--' that is at the end of the command line be left there? When I used to command line options I left it there. I ask this as I am aware that in some programming languages it is used to denote a comment. Thus my command line options may have been ignored.
None of them helped.

I have these main components in my pc:

```
nVidia GeForce 9800gtx+
Creative X-Fi Sound Blaster Fatal1ty Xtreme Gamer Edition
Athlon(tm) 64 Processor 3000+ (2.01 GHz)
1GB DDR ram
```

Help would be seriously appreciated as I'd love to use ubuntu as an alternative to windows but I just can't install it successfully.

---

### Post by avtolle on 2009-03-02
I believe you are running into a problem with your graphics card during the installation. Have you tried the alternate cd iso (uses a text based installer, and avoids many problems with graphics cards) to get installed. I recall seeing more than one thread involving your card, perhaps a Google search with the card name and Ubuntu will get you to a helpful post or site which can get you going (often works better than the search function on the forum).

EDIT: While you are not upgrading to 8.10 from an earlier release, I wonder whether desktop effects being on by default is causing the problem, as documented in the release notes for upgrades. I don't know how to "turn them off" to allow installation from the Live CD. Hopefully, someone else will be able to get you going in the right direction.

---

### Post by FoXoF on 2009-03-02
Thanks for the quick response. I'll try the other install cd. I'll let you know if that fixes the problem.

---

### Post by avtolle on 2009-03-02
> **FoXoF said:**
> Thanks for the quick response. I'll try the other install cd. I'll let you know if that fixes the problem.
I've had another thought; the alternate CD may be able to get the system installed, but at that point you may have a problem getting booted up. However, try it and see if you get the system installed, and then hopefully someone with more knowledge than I can help you get around any further problems which might arise.

---

