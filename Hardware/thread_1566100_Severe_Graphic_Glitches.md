---
title: "Severe Graphic Glitches"
date: 2010-09-01
forum: Hardware
---

### Post by gnrathon on 2010-09-01
I was changing my screensaver in Ubuntu 10.04 when the computer freezes. I was unable to restore function so I powered the computer off. 

Once i restarted and logged in, my desktop was unusable unless I disable compiz.

Help?
I will post a picture so you can see


Oh, By the way, Hardware Specs:
Intel Celeron  3.06 Ghz
Ati Radeon Xpress 200
Open Source ATI Drivers (Xorg Edgers)

---

### Post by gnrathon on 2010-09-02
Please, anyone have any insight on how i can at least reinstall the drivers with out having to reinstall ubuntu

---

### Post by JHCKX on 2010-09-02
Use ppa-purge to remove the xorg-edgers programs. When you restart, the standard Xorg drivers will be re-installed. After that, you could re-install the xorg-ppa.

Command:
sudo ppa-purge xorg-edgers

(If ppa-purge is not installed yet, use

sudo apt-get install ppa-purge

---

### Post by robert shearer on 2010-09-02
> =gnrathon]I was changing my screensaver in Ubuntu 10.04 when the computer freezes. I was unable to restore function so I powered the computer off. 


Avoid powering off like that. It is not usually necessary and can lead to file-system corruption.
There is a simple alternative that works in most cases.

[http://www.arsgeek.com/2006/12/12/how-to-gracefully-reboot-your-ubuntudebian-system-if-all-else-fails/](http://www.arsgeek.com/2006/12/12/how-to-gracefully-reboot-your-ubuntudebian-system-if-all-else-fails/)

For **RSEIUB** the key is to do each combo slowly allowing a pause between.
Occasionally you have to repeat the sequence with it rebooting the second time through.
Has not failed me yet.

---

### Post by gnrathon on 2010-09-02
Thanks guys! PPA purge did the trick. 
just some FYI the screensaver that froze my computer was
CubeStorm and it still freezes my computer.

---

