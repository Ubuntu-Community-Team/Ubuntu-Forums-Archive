---
title: "Freeze on bootup."
date: 2009-07-20
forum: Installation &amp; Upgrades
---

### Post by dlw on 2009-07-20
Installing 9.04 on two Acer Aspire Ones dual boot with XP.
The first went fine and works great.
The second boots as far as the Ubuntu Netbook splash screen and freezes.
It gets past entering the username, password and the opening theme tune.
I tried booting up in recovery mode trying the 'repair broken packages', file system check' and 'resume normal boot'. Nothing works.
I'm ready to try the 'root shell with networking' but have no idea what to do when I get there.

Update:
After dropping into a console as root, 'startx' gets things going again but once it reaches the home screen it freezes again. No keys work. Mouse does not work. Have to hold down 'on/off' switch for two seconds to get out in order to start over.

Any help appreciated since reinstalling and updating takes quite some time.

dlw

---

### Post by komputes on 2009-07-20
Check that you have the most recent BIOS firmware version. Also you may want to try boot options like hpet=disable or acpi_osi=Liunx as seen in this bug:
[https://bugs.edge.launchpad.net/netbook-remix/+bug/309960](https://bugs.edge.launchpad.net/netbook-remix/+bug/309960)

If you are trying to run UNR and it is not working, try installing the simple 386 version to see if it makes a difference.

---

