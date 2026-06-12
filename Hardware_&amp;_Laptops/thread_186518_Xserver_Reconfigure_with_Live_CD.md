---
title: "Xserver Reconfigure with Live CD?"
date: 2006-06-02
forum: Hardware &amp; Laptops
---

### Post by MonkeyBoy on 2006-06-02
I'm trying to install xubuntu on my Armada 3500 but have an irritating problem.  The hardware detection on the xubuntu disk sets my screen colour resolution to 32.  With breezy I was able to install then reconfigure xserver before rebooting which was just fine but if I reboot the live cd it starts with its default settings of course.  With 32bit colour when I load xubuntu live and go to the installer the window doesn't fit on my screen and I can't see the lower buttons.

Do any of you know how I can either start the live disc using 16bit colour or, failing that, restart xserver after I have reconfigured it?

Any help would be really appreciated.  Thanks in advance.

---

### Post by jonny on 2006-06-02
```
sudo dpkg-reconfigure xserver-xorg
```
Then <ctrl>+<alt>+<backspace>

---

### Post by MonkeyBoy on 2006-06-02
Perfect.  That did it.  

Thanks very much.:)

---

