---
title: "psmouse.proto????"
date: 2004-11-29
forum: Hardware &amp; Laptops
---

### Post by captfats on 2004-11-29
So I have a issue with erratic mouse when connect via KVM switch. 
So the solution worked fine using Fedora (Don't worry I'm a full Ubuntu convert now!) when I passed the 'psmouse.proto=imps'. However in with Warty release I get error saying the option is unknown. Any ideas??

---

### Post by ecz on 2004-12-10
The psmouse is a module in Ubuntu. Therefore the kernel does not understand the option.  Add this line to a file in /etc/modprobe.d/ (I use /etc/modprobe.d/options, modprobe will read all files in the dir.):

options psmouse proto=imps

[QUOTE=captfats]So I have a issue with erratic mouse when connect via KVM switch. 
So the solution worked fine using Fedora (Don't worry I'm a full Ubuntu convert now!) when I passed the 'psmouse.proto=imps'. However in with Warty release I get error saying the option is unknown. Any ideas??[/QUOTE]

---

### Post by meep on 2005-11-12
This worked for me!  I can't freaking believe it. 

Two systems on a KVM setup, with a usb mouse using a ps2 converter.  On one system, I have an outdated Gentoo installation, and the mouse worked fine. 
On the other system, I have Hoary. 

Switch to Gentoo, things are fine. 
Switch to Hoary, things are evil and jumpy and well, you just don't use the mouse until you reboot.

The log said psmouse.c lost synchronization.

I added an options file to modules.d like you said, copied your note exactly, and it works in both systems now. I'm changing my Gentoo box to Breezy now. :)

---

### Post by jmacmich on 2006-08-11
Just wanted to note that this fix works in Dapper as well.  Now my Dapper install recognizes the mouse faster than XP after switching.  Schweet

---

### Post by xyphur on 2006-10-13
Running Dapper here as well, but the fix doesn't work for me. I used the options file method as it was already there for some gstreamer options among other things.

I'm assuming (silly me, I know) that this should work regardless of whether the mouse in question is USB, connected to PS/2 via an adaptor, or just a standard PS/2 mouse. Am I wrong?

At any rate, I fired an e-mail off to Belkin support to see if they can figure out why I can't flash the firmware on my OmniView SOHO 4-port KVM, because they've apparently fixed this issue in hardware. It'd be nice not to have to fiddle with software settings (or unplug/replug the mouse) every time I hook up a non-windows machine... I can dream, can't I?

---

### Post by Neko- on 2006-10-22
I'm a complete newbie at Linux, and am currently trying out Ubuntu 6.06 LTS as my first actual expirience in Linux and working with it.

It's installed on a machine and is working (appearantly) as it should. The problem comes when I hook it up to the KVM switch (Belkin Omniview 4 prt) responsible for maintaining my three machines (Two Windows machines and the Ubuntu machine).

As Ubuntu starts through the KVM switch it works fine. As I then return to Windows (which is still my primary PC) and then return to Ubuntu, my mouse is showing erratic behaviour. 

The pointer is all over the screen, and appearantly random 'clicks' even if no buttons are actually depressed. This kind of makes Ubuntu unworkable. I've had this problem before running Windows systems, after installing IntelliMouse to use the scroll-function. As I deinstalled IntelliMouse and opted for BrowserMouse as the scroll function provider, my problems ceased to be.

Found a few solutions on the web, all referring to either adding a psmouse.proto=bare to the kernel-line in the menu.lst (which I tried. It was ignored as an illegal switch), followed by the editing of /etc/modules, and adding the proto=bare (aswell as later on the proto=imps) to the psmouse line. Also noted adding a line in the /etc/modprobe.d/ folder to a random file with the content of 'options psmouse proto=imps' would solve things. No such luck.

None of these solutions worked. So I have to use a separate mouse (which kind of defeats part of the usage of the KVM switch which it was bought for) to actually be able to use Ubuntu without loosing access to my normal machines. Any further thoughts on this are appreciated.

---

