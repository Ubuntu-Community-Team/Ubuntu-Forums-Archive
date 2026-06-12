---
title: "Help installing ATI x1650 pro pci-e"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by Gizmo89 on 2007-10-21
hi, i recently reinstalled 7.10 after mucking up my video card settings, so i'm trying it all again
So far i have installed the "ati-driver-installer-8.40.4-x86.x86_64.run" and got as far as the ati config thingy. This is where it went wrong:

# aticonfig --initial --input=/etc/X11/xorg.conf
Warning: Could not find configuration file
Please copy configuration file template to /etc/X11
root(myname)# aticonfig --dtop=horizontal --overlay-on=1
Warning: Could not find configuration file
Please copy configuration file template to /etc/X11
root(myname)# aticonfig --resolution=0,1600x1200,1280x1024,1024x768
Warning: Could not find configuration file
Please copy configuration file template to /etc/X11
root(myname)# aticonfig --force-monitor=crt1,notv
Warning: Could not find configuration file
Please copy configuration file template to /etc/X11

can anyone help?

i have also done a diagnosis thingy:

# cat /var/log/Xorg.0.log | grep "EE"
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) Unable to locate/open config file
(II) Loading extension MIT-SCREEN-SAVER
(EE) Failed to load module "type1" (module does not exist, 0)
(EE) open /dev/fb0: No such file or directory
(EE) AIGLX: Screen 0 is not DRI capable

---

### Post by phenix777 on 2007-10-23
I'm having the same problem with the same hardware (x1650 pro).  Feisty was working great with dual monitors (bigDesktop), and now on Gutsy I'm having trouble even getting a single monitor to work at the proper resolution (it runs with a VESA driver at very low res).
On another note, when I run:
[HTML]sudo dpkg-reconfigure xserver-xorg[/HTML]
The wizard exits without succesfully modifying my xorg.conf file, outputting:

md5sum: /etc/X11/xorg.conf: No such file or directory

Very strange.  Any thoughts?

---

### Post by phenix777 on 2007-10-31
As a followup:
  I spent about 20 hours and followed countless pieces advice on trying to get my ATI X1650 card to work with Gutsy (dual monitors to top it off) and in the end had to give up.
  I bought and installed an nVidia 7600 GT (AGP), reinstalled Gutsy and now have a fantastically stable, beautiful looking OS.  I guess it'll be nVidia from now on for me.

Cheers.

---

### Post by TheInevitableTruth on 2007-11-07
I too got stuck with the ATI driver, A solution is thus.

Backup your xorg.conf first

cat /etc/X11/xorg.conf | aticonfig --initial -f 

This overwrites your xorg with a new file made from scratch. 

If you like me want a dual head config then use the command

cat ./xorg.conf.samsbackup | aticonfig --initial=dual-head -f

Once a new xorg.conf has been written restart the computer and see the full glory of ATI proper drivers.

Note, both need to be run sudo root

---

