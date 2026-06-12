---
title: "Dell C1765nf Laser Printer Configuration"
date: 2013-11-04
forum: Hardware
---

### Post by rtv_73 on 2013-11-04
Hi all,

Have anyone had any luck installing Dell C1765nf Laser Printer? I am having problems finding a compatible CUPS drivers for it.

Thank-you!

---

### Post by hugh2 on 2013-11-21
> **rtv_73 said:**
> Hi all,

Have anyone had any luck installing Dell C1765nf Laser Printer? I am having problems finding a compatible CUPS drivers for it.

Thank-you!

I am struggling also... had I known it didnt support PCL, I would not have ordered it.. now I am stuck (not willing to pay the shipping and restocking fees)

---

### Post by jp734 on 2013-11-22
I have a Dell 1700n and I used Lexmark driver. As far as I know, Dell are made by Lexmark. Good luck

---

### Post by rtv_73 on 2013-12-27
No luck with the Lexmark drivers. I am also trying to modify the MacOS PPD files, but not look so far :(

---

### Post by rtv_73 on 2014-04-09
Solved

You need the foo2hbpl driver for this HBPL printer protocol. You can get the driver at the following site:

[http://foo2hbpl.rkkda.com/](http://foo2hbpl.rkkda.com/)



> 
UBUNTU NOTES
------------
    Install build-essential, tix, foomatic-filters, groff, dc FIRST:
    $ sudo apt-get install build-essential tix foomatic-filters groff dc

    $ wget -O foo2zjs.tar.gz [http://foo2zjs.rkkda.com/foo2zjs.tar.gz](http://foo2zjs.rkkda.com/foo2zjs.tar.gz)
    $ tar zxf foo2zjs.tar.gz
    $ cd foo2zjs
    $ sudo make uninstall
    $ make
    $ ./getweb 1020
        OR other printer
    $ sudo make install install-hotplug cups

    For 7.10 and later users:
        $ sudo system-config-printer

    For 5.10/6.06/6.10/7.04 users:
        $ sudo gnome-cups-manager
        [configure ColorMode = Color if a color printer]
        $ sudo make cups

        Ubuntu has a bug in gnome-cups-manager with Color, so you must
        restart cups.  No other distro has this bug.

    If that doesn't work, then fire up:
    $ firefox [http://localhost:631](http://localhost:631)

    And click on:
        Printers -> Set Printer Options -> Color Mode -> Color
    Then click on:
        Set Printer Options

---

### Post by polzin on 2014-11-29
So how is your color printing quality?
Mine is rather bad. Pictures have a bad resolution, a lot of shading artefacts and the colors are much to intense.
Regards, TP

---

### Post by polzin on 2014-12-02
The color printing is an issue of a bug/incompatibility with Ghostscript 9+. The foo2h* INSTALL file contains a description to install GS 8.71. With some modification (see  [http://foo2zjs.rkkda.com/forum/read.php?86,3911](http://foo2zjs.rkkda.com/forum/read.php?86,3911)) this worked and fixed the color printing.

---

