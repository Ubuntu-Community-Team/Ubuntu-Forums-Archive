---
title: "not booting gui after install"
date: 2009-10-01
forum: Installation &amp; Upgrades
---

### Post by Mmmtobacco on 2009-10-01
Hey there. As a complete linux newbie, I need some help as I think that I installed unbuntu incorrectly.

I have a hard drive that I wanted to have ubuntu 9.0.4 (i think that's the most recent, but dont quote me on that, and i cant check atm because I'm at work) on so I could dual boot, but not have to install it through windows so as to keep it fully functional. It's a 40GB IDE drive that I just formatted to have a fresh drive to install to.

Where I feel I went wrong was during the install process off of the CD, I selected the option "use entire drive" as that was the only option I saw I could choose to be able to install it on that particular drive.

The installation was successful so I removed the disk at the prompt and rebooted the PC.

When I chose Ubuntu as the boot option, it showed the loading splash screen, but instead of loading the GUI, it kicked me to the grub command prompt, and any of the options available when pushing esc did not take me anywhere besides back to the grub console. 

Where did I go wrong here? Any help would be greatly appreciated.

---

### Post by ptn107 on 2009-10-01
At that grub prompt try reinstalling the bootloader[1] (type the following):
```
grub-install /dev/hda
```

[1][_http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html_]("http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html")

---

### Post by Mmmtobacco on 2009-10-01
I'll try that when I get home. Would I need the CD, or does it install from the internet at that point?

---

### Post by rreese6 on 2009-10-01
Use the LiveCD.

---

