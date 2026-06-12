---
title: "Tweak needed, HP laser printer installed twice"
date: 2010-06-05
forum: Hardware
---

### Post by Tom_ZeCat on 2010-06-05
My HP LaserJect P1005 was not printing.  I had HPLIP already installed, but when I went to print from OpenOffice Writer I would see the P1005 on the print menu and and choose print.  The software acted like it printed, but nothing came out of the printer.  Fortunately, a google revealed the info I needed to make it work at this link:  

[http://blog.ibeentoubuntu.com/2008/11/hp-laserjet-p1006-horror-wont-print.html]("http://blog.ibeentoubuntu.com/2008/11/hp-laserjet-p1006-horror-wont-print.html")

The following two commands in the terminal made it start working:  

> sudo aptitude install hplip-gui
sudo hp-setup

After the install, HP made me agree to an EULA and then the printer worked.  

Now when I go to print, the print menu comes up and I have a choice between these two supposed printers:
> HP_LaserJet_P1005
HP_LaserJet_P1005_2

Obviously, there's an extra instantiation of the printer.  If I choose to print from the HP_LaserJet_P1005, everything prints just fine, but I get a message complaining that the HP_LaserJet_P1005_2 may not be plugged in.  If I try to print from HP_LaserJet_P1005_2, it does not print.  

So it's great I can print, and it's no big deal to choose the first instantiation of the printer.  However, I'm going to be bugged about the supposedly unplugged P1005_2 each time I print.  Obviously, the thing to do is uninstall the extra one.  However, I've looked for an HPLIP gui and I can't seem to find it.  Is there a GUI?  And how do I get rid of the extra install?

---

