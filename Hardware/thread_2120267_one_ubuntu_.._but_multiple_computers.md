---
title: "one ubuntu .. but multiple computers"
date: 2013-02-26
forum: Hardware
---

### Post by Cuore gang on 2013-02-26
so i have ubuntu installed in my Usb drive! 
-----------------------------------------------------
[B] it's not a live usb ..:) it's installed in th usb drive like if it was installed in my hard drive :) -
so my usb contain 3 partition / /home and swap :)[/B]
-----------------------------------------
i want to use it in my Laptop, but also be able to use it on my Desktop and other computers ! Is it a problem to run one copy of Ubuntu on multiple hardware? to be specific i want to make compiz extra effect work .. so i need the appropriate graphic card driver of each hardware installed in this usb drive ! how can i solve this ?

---

### Post by varunendra on 2013-02-26
> **Cuore gang said:**
> i want to make compiz extra effect work .. so i need the **appropriate graphic card driver of each hardware** installed in this usb drive ! how can i solve this ?
This maybe a problem ^^, otherwise it's fine.

With native kernel drivers you should be able to boot a large variety of hardware. But once a proprietary graphics driver is installed, it will almost certainly cause resolution and hardware acceleration issues on all other different graphic cards.

Although you should always be able to boot in safe graphics mode (failsafeX in recovery menu) if the proprietary driver causes booting problems with some hardware.

Also, this behaviour is same for both a full installation and a live persistent one.

---

### Post by sudodus on 2013-02-26
You have found ***the*** problem: If you install proprietary drivers, typically for graphics and wifi, it will not be portable to computers with other kinds of hardware.

You get a long way with the built-in drivers with the current Ubuntu versions 12.04 LTS and 12.10.

I would recommend a flavour with a lighter desktop environment (than standard Ubuntu's Unity)

- Xubuntu with the light-weight XFCE or
- Lubuntu  with the ultra light-weight LXDE

for portable systems partly because of the limits set by the built-in drivers with some graphics chips, and partly because of the limits set by the USB 2 interface. USB 3 or eSATA are much faster.

---

### Post by oldfred on 2013-02-26
Best not to install proprietary graphics. I boot my flash drive without issue on two different systems.

I did save these links, but never tried any of these methods. Now also getting older so I do not know if they still work. 

       [http://ubuntuforums.org/showthread.php?t=1714456](http://ubuntuforums.org/showthread.php?t=1714456)
Boot using recovery mode & 'Reconfigure graphics' or
Create Portable Ubuntu for 2 different Video Cards - script
[http://ubuntuforums.org/showthread.php?p=8107778](http://ubuntuforums.org/showthread.php?p=8107778)
There is a application named switchconf that lets you choose between xorg.conf files at boot.
[http://meandubuntu.wordpress.com/2008/05/07/changing-system-configuration-switchconf/](http://meandubuntu.wordpress.com/2008/05/07/changing-system-configuration-switchconf/)

---

### Post by C.S.Cameron on 2013-02-26
> **oldfred said:**
> Best not to install proprietary graphics. I boot my flash drive without issue on two different systems.

I did save these links, but never tried any of these methods. Now also getting older so I do not know if they still work. 

       [http://ubuntuforums.org/showthread.php?t=1714456](http://ubuntuforums.org/showthread.php?t=1714456)
Boot using recovery mode & 'Reconfigure graphics' or
Create Portable Ubuntu for 2 different Video Cards - script
[http://ubuntuforums.org/showthread.php?p=8107778](http://ubuntuforums.org/showthread.php?p=8107778)
There is a application named switchconf that lets you choose between xorg.conf files at boot.
[http://meandubuntu.wordpress.com/2008/05/07/changing-system-configuration-switchconf/](http://meandubuntu.wordpress.com/2008/05/07/changing-system-configuration-switchconf/)

Since about 10.04 or so, video drivers are loaded prior to running xorg.conf.

Thus switchconf no longer works for video drivers.

Switchconf was ok for choosing between generic and Nvidia or between generic and ATI.

Switchconf would not let you choose between Nvidia and ATI as Nvidia and ATI drivers can not be installed at the same time.

I'm not sure if proprietary drivers are still required to make Compiz work.

---

### Post by sudodus on 2013-02-26
> **C.S.Cameron said:**
> ...
I'm not sure if proprietary drivers are still required to make Compiz work.
Compiz works without any proprietary drivers in Knoppix 7. It even runs well in my IBM Thinkpad T42 with an old Pentium M.

---

### Post by varunendra on 2013-02-27
Compiz effects will work as long as a driver can provide 3d hardware accelaration. It does not necessarily have to be a proprietary driver.

---

