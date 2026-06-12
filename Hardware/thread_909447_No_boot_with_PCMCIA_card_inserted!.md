---
title: "No boot with PCMCIA card inserted?!"
date: 2008-09-03
forum: Hardware
---

### Post by gvigorus on 2008-09-03
Hi folks. Does anyone know why xubuntu does not boot (stalls) when PCMCIA USB2 card is inserted? Everything works great when I insert PCMCIA card after boot. But the progress bar just hangs on boot with this card in the slot.
My PCMCIA card is OrangeUSB2 by OrangeMicro
My Laptop is Dell Inspiron 4000 Xubuntu 8.04

Thanks to all!
S

---

### Post by bobalice on 2009-03-02
I am also having this issue, except my system freezes when I insert the card, and it will not booth with the card in...

[http://ubuntuforums.org/showthread.php?t=1084941](http://ubuntuforums.org/showthread.php?t=1084941)

---

### Post by sudogeek on 2009-03-07
Kernel panics on boot has been a recurring problem for me on various laptops since 6.04. Although I am not using your partucilar card, let me share the fix in a smiliar setting. Currently I am using the Linksys WPC11 wireless pcmcia card on a Dell Latitude C840 with Ubuntu 8.10.

The boot is halted by a kernel panic if the pcmcia card is inserted prior to boot, but works fine if inserted after.

In this case, the problem can be traced to hostap. If you blacklist hostap and hostap_cs in /etc/modprobe.d/blacklist, the orinoco drivers are loaded instead and boot proceeds without a problem. [In that case, since hostap and NetworkManager are no longer handling the card, you must explicitly define the interface in /etc/network/interfaces and also the dns servers in /etc/resolv.conf.]

If you want to use NetworkManager (and hostap), you must remove the card, boot, then reinsert the card. This works well _if_ you disable the loading of the hernes and orinoco drivers which can interfere with hostap. One way to do this is to create the file "/etc/modprobe.d/00local" with the lines "install orinoco /bin/true" and so on for orinoco, orinoco_cs, hermes, and any other module you wish to prevent loading after hotplug.

YMMV with other cards. Often the problem can be traced to a particular module being loaded at that time in the boot sequence. Check lsmod after a clean boot and after inserting the card to see what is being loaded, then try blacklisting the modules to see if that is the problem. You can delay the loading of the module until later in the boot (by creating a local script) and that sometimes works. Sometimes, though, you just need to keep the damn card out and insert it later. At least it works then - some cards crash the system even if inserted later.

---

