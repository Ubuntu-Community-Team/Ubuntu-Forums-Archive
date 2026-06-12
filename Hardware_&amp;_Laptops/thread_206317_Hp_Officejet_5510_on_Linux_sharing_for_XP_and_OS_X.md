---
title: "Hp Officejet 5510 on Linux sharing for XP and OS X"
date: 2006-06-29
forum: Hardware &amp; Laptops
---

### Post by jer2eydevil88 on 2006-06-29
Okay so here is my situation

Dell on the right of the room at my friends is running Ubuntu 6.06
Dell on the left of the room is running XP SP2 with all sorts of junk in the background (as usual).

They also have a Macbook Pro they take around the house and use wirelessly

They have an HP Officejet 5510 printer that I have working correctly locally and shared through samba.  Now how in the world do you get OS X to install it without having a driver seperate from the installer? and even better XP Pro wants the driver as well...?  I really would like help on this so any ideas at all just shoot them at me.

---

### Post by mpvano on 2006-06-30
Install the Macintosh printer drivers from HP's web site (buggy beta drivers), or from the HP the install disk (more stable, but incomplete) on the Macintosh as usual. Then set up printer sharing (preferably using a higher level protocol than CUPS!) using the normal Macintosh printer configuration dialogs.

Sometimes it can help to connect the printer locally and test it after installing the drivers to make sure they're working.

This is how you normally set up printers for printer sharing on any platform. The automated network driver installation protocol used by XP is not usually available for other platforms because it usually has binary driver issues and it's not part of CUPS. You don't need to use it if local drivers exist.

If you have CUPS properly set up, the Macintosh will have no trouble sharing the printer. (I've done it here for several OSX and Linux revisions). You can also usually directly share it via SMB protocols if the needed accounts, etc exist on all the machines. If you already use SMB networking, this is often the easiest way.

Sharing the scanner is another matter. If' it's possible at all, it's done through other tools.

The gotcha, however is that if you don't want to use SMB protocols, directories, naming conventions, etc on your network, then you'll need to share at the CUPS level and CUPS is a major nightmare. You'll probably need to configure low level "raw" network printers in CUPS, and that's pretty confusing to do. The more subtle configuration details can't be examined or set on ANY platform without reading a lot of bad documentation (mostly boilerplate with no content) and then modifying low level configuration files by hand. The security situation is dangerously confusing unless you understand Apache configuration files, and there are some "interesting" cross platform naming bugs with many CUPS implementations as well.

The biggest problem I've seen is that the HP OSX drivers are pretty flakey. The multifunction printers like our 5610 (especially if shared) come and go mysteriously from dialog lists for no apparent reason. Most of our problems disappeared, however once we started leaving the printers and the machines serving them turned on all the time....

hope this answers your question....

Mario

---

