---
title: "HP LaserJet 1018 in Karmic"
date: 2010-01-10
forum: Hardware
---

### Post by dualspace on 2010-01-10
Hello...

My printer ( HP LJ 1018 ) won't work in Karmic. It used to work in Jaunty, although not always (I had to turn it off and on again, reset the computer etc.)
Now, I found some similar topics on these forums, and maybe some other places, and followed the instructions I got there... But they didn't help me. The problem is, I don't know what exactly I installed or uninstalled or (de)activated... I just did a bunch of stuff, and it didn't make my printer work.

I know that you probably need some additional information, but I don't know which information that is... You can tell me and I'll post everything you need to know in order to help me solve my problem. However, I have to warn you I'm not really an Ubuntu expert, so please tell me how to obtain the information that you need.

Thank you.

---

### Post by LinuxDeal on 2010-01-13
[openprinting.org]("http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_1018") says:

> The firmware of the printer must be uploaded after turning it on. You can use a hotplug/udev script which comes with foo2zjs, or do it manually: "cat /usr/share/foo2zjs/firmware/sihp1018.dl >  /dev/usb/lp0".

This command simply needs to be entered into a terminal after the printer is connected and turned on.

Hope this helps.

---

