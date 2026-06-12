---
title: "Keep getting server, want desktop"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by PFPunks on 2009-04-22
Hey Everyone,
I've downloaded Ubuntu 8.10 twice now, both times burned it to cd and ran it. Rebooted, selected ubuntu and both times it has come up as the server version. I get just a command line. I tried startx and xinit it said failed to find monitor. Am I retarded? I need this to setup a school project on so if anyone can give me any recommendations on older versions that would be completely idiot proof i.e. no server version. I would appreciate it. I'm running Vista AMD 64. 

Also, when I uninstalled Ubuntu each time it didn't remove the Ubuntu option from the boot list so now it shows Ubuntu twice, and because they are uninstalled neither of them work. Any advice on how to remove them? Thanks

Andrew

---

### Post by MN Noob on 2009-04-22
It sounds like you are trying to install without first booting live. Have you tried that yet, just booting without installing?
I believe once you get it installed you can modify grub to remove the other options if it doesn't do it for you.

---

### Post by PFPunks on 2009-04-22
Just downloaded 8.04.2, 64 bit version, and it seems to be setting up just fine. Yeah!! Thanks for your quick response though. 

Also, now there are three listings for ubuntu at the dual boot menu. Any idea how I can remove two of them?

---

### Post by MN Noob on 2009-04-22
Someone else should probably comment on editing grub file, but I would assume you could just comment/delete out what you don't want from /boot/grub/menu.lst. I have not made a change to it before.
Otherwise this should do the trick: [http://ubuntuforums.org/showthread.php?t=967797]("http://ubuntuforums.org/showthread.php?t=967797")

---

### Post by lisati on 2009-04-22
> **PFPunks said:**
> Just downloaded 8.04.2, 64 bit version, and it seems to be setting up just fine. Yeah!! Thanks for your quick response though. 

Also, now there are three listings for ubuntu at the dual boot menu. Any idea how I can remove two of them?

I'm not a guru on the contents of the grub menu, and I haven't actually seen what's on your system, so I'll try to keep my comments short:
The first entry is likely to be your successful install
The second entry is likely to be a "recovery" or "failsafe" mode that is roughly equivalent to Windows' "safe mode".
The third *could* be from previous install.

---

### Post by coffeecat on 2009-04-22
> **PFPunks said:**
> Also, now there are three listings for ubuntu at the dual boot menu. Any idea how I can remove two of them?

Not advisable. As the previous poster has said the second will be recovery mode. The third is almost certainly memtest - a memory tester, which you might need.

And every time you get a new kernel come in with an upgrade your Ubuntu menu.lst options will multiply like rabbits. It's not a good idea to remove the older entries because it's sometimes useful to boot into an earlier kernel for diagnostic reasons if you are experiencing odd driver problems that weren't there before.

---

