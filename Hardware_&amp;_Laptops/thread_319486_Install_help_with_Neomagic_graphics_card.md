---
title: "Install help with Neomagic graphics card"
date: 2006-12-15
forum: Hardware &amp; Laptops
---

### Post by ProjectWhat on 2006-12-15
I need help install this.[http://packages.ubuntulinux.org/dapper/x11/xserver-xorg-driver-neomagic]("http://packages.ubuntulinux.org/dapper/x11/xserver-xorg-driver-neomagic") Yes I am still new to this. Where is the download file?

---

### Post by hikaricore on 2006-12-15
> **ProjectWhat said:**
> I need help install this.[http://packages.ubuntulinux.org/dapper/x11/xserver-xorg-driver-neomagic]("http://packages.ubuntulinux.org/dapper/x11/xserver-xorg-driver-neomagic") Yes I am still new to this. Where is the download file?

You should be able to simply open a terminal.

Applications Menu, Accessories, Terminal

and type:

```
sudo apt-get install xserver-xorg-driver-neomagic
```

If that does not work, on that same page you linked on, click on your hardware type.

amd64,   i386,  or   powerpc

which for example I will use i386 and it will take you to a page of mirrors such as this one:

[http://ubuntu.cs.utah.edu/ubuntu/pool/main/x/xserver-xorg-driver-neomagic/xserver-xorg-driver-neomagic_1.0.0.5-0ubuntu1_i386.deb](http://ubuntu.cs.utah.edu/ubuntu/pool/main/x/xserver-xorg-driver-neomagic/xserver-xorg-driver-neomagic_1.0.0.5-0ubuntu1_i386.deb)

After downloading it (assuming you download it to your desktop) just double click (or single click if using kde) on it and click install when the package installer pops up.

You will need to reconfigure X after you're done using:

```
sudo dpkg-reconfigure xserver-xorg
```

And select the correct driver.

Reconfiguring your X server incorrectly can leave you without a GUI to use, so make sure you select the correct options or look for more info on the forums here about that command if you are not comfortable doing so.

Good luck,

--Aaron

---

### Post by talkingwires on 2006-12-15
I have a laptop with a NeoMagic video chip. I'm not a Linux guru, just a user, but if hikaricore's post didn't help, perhaps I can. If you're just trying to install the driver, downloading it using apt should work fine. (I believe that it is installed by default, though.) To enable it, edit your /etc/X11/xorg.conf file and look for the "Device" section. Change the driver to "neomagic".

---

### Post by hikaricore on 2006-12-15
> **talkingwires said:**
> I have a laptop with a NeoMagic video chip. I'm not a Linux guru, just a user, but if hikaricore's post didn't help, perhaps I can. If you're just trying to install the driver, downloading it using apt should work fine. (I believe that it is installed by default, though.) To enable it, edit your /etc/X11/xorg.conf file and look for the "Device" section. Change the driver to "neomagic".

sudo dpkg-reconfigure xserver-xorg

Also allows you to do this, if it's not showing neomagic as an option after you have properly installed the driver then something is very wrong.

---

