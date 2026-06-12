---
title: "Dual Monitor in Intrepid Ibex"
date: 2009-01-23
forum: Hardware
---

### Post by AchimRS on 2009-01-23
Yes, I know there are dozends of threads like this, but I have the gut feeling that the most of them are not valid anymore for the new design in Intrepid Ibex 8.10.

I like to setup a second monitor beside my laptops monitor with BigDesktop or MergedFB setup like described [here]("http://ubuntuforums.org/showthread.php?t=221174")
But they massivly edit the xorg.conf file and as far as I understood, this is not good for Intrepid.

So I partly succeeded with "xrandr --output VGA-0 --auto --right-of LVDS" but I guess this result in a Xinerama setup, at least it behaves like that because 3D is not possible anymore.

So I would like to configure in MergedFB or the ATI specific BigDesktop mode, but how can I do this with xrandr/gradr without editing the xorg.conf?
Why do I not want to edit the xorg.conf? Because any changes inside will be overwritten by some package updates as I already experienced with the "Virtual" setting by doing an "sudo dpkg-reconfigure -phigh xserver-xorg" it will simply disapear.

My setup is KUbuntu 8.10 running KDE4 on an IBM T40p laptop with an ATI Radeon 9000 card with ati-driver (currently no fglrx, but if this helps...). So I cannot use all this fancy hints for NVIDIA cards driver or Gnome-tools.

---

