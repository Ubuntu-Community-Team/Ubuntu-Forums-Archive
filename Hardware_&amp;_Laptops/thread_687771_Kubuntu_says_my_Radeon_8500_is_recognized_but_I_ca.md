---
title: "Kubuntu says my Radeon 8500 is recognized but I can't change res or refresh rate"
date: 2008-02-04
forum: Hardware &amp; Laptops
---

### Post by finny388 on 2008-02-04
I am new to linux and using kubuntu (am I better off posting at Kubuntu.org?)

When I go to Devices I see my card recognized as a Radeon 8500 LE. Fine.

But when I go to change res/refresh rate it won't budge from 1024x768 @60Hz.
There is no ATI console - it looks about as generic as can be.

I have downloaded the .rpm and .run from ATI that are supposed to support the card (8.28? (I am not at home right now to look it up))

I have seen similar posts and gone through the wikis with no luck.

All installations seem to have to go through Adept. How do I install the ATI drivers now that they are sitting in my Home folder?

Frustratingly, it claims to be supported for 2D and 3D:
[HardwareSupportComponentsVideoCardsAti]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti")

Also, is there an ATI console (how will I know I have it correctly installed))?

THANKS

---

### Post by finny388 on 2008-02-04
Tried this:

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_drivers_in_Ubuntu_Dapper_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_drivers_in_Ubuntu_Dapper_Manually")

used the following codes:

> sudo apt-get update
sudo apt-get install module-assistant build-essential
sudo apt-get install fakeroot dh-make debconf libstdc++5 linux-headers-$(uname -r)

    Create .deb packages: 
sh ati-driver-installer-8.28.8.run --buildpkg Ubuntu/gutsy

    Install .deb packages: 
sudo dpkg -i xorg-driver-fglrx_8.28.8-1*.deb
sudo dpkg -i fglrx-kernel-source_8.28.8-1*.deb
sudo dpkg -i fglrx-control_8.28.8-1*.deb

    Remove any old fglrx debs from /usr/src/: 
sudo rm /usr/src/fglrx-kernel*.deb

    Compile the kernel module: 
sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a


at Create .deb packages this error happened:

> k-desktop:~$ sh ati-driver-installer-8.28.8.run --buildpkg Ubuntu/gutsy
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager
-e ==================================================
./ati-installer.sh: 165: Syntax error: Bad substitution
Removing temporary directory: fglrx-install

any ideas?

---

### Post by finny388 on 2008-02-05
^

---

### Post by finny388 on 2008-02-06
Does anyone out there use k/ubuntu with a Radeon 8500?

It seems to me the proprietory driver doesn't work with Gutsy and the restricted driver blows.

Stuck at 1024x768 @60Hz ?? I am too sensitive to low refresh rates - kubuntu is unusable.

I was so hoping that this wouldn't be jumping through hopes just to have the display working.

Do I have to upgrade my system just to use Gutsy properly? (sounds like the camp I am trying to leave)

P4 1.6 Northwood
Asus P4S533
1.5 GB DDR
Radeon 8500

---

### Post by tweedledee on 2008-03-02
> **finny388 said:**
> I am new to linux and using kubuntu (am I better off posting at Kubuntu.org?)

When I go to Devices I see my card recognized as a Radeon 8500 LE. Fine.

But when I go to change res/refresh rate it won't budge from 1024x768 @60Hz.
There is no ATI console - it looks about as generic as can be.

I have downloaded the .rpm and .run from ATI that are supposed to support the card (8.28? (I am not at home right now to look it up))

I have seen similar posts and gone through the wikis with no luck.

All installations seem to have to go through Adept. How do I install the ATI drivers now that they are sitting in my Home folder?

Frustratingly, it claims to be supported for 2D and 3D:
[HardwareSupportComponentsVideoCardsAti]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti")

Also, is there an ATI console (how will I know I have it correctly installed))?

THANKS

You may have already determined this and/or given up, but the issue is that the 8.28.8 driver does not work with X.org later than 7.1 (Edgy).  I have the same card, and essentially the restricted driver will not work (without downgrading X.org, which leads to all kinds of other complications), and the open source does not provide 3D worth squat.  In short, you (and I) are going to have to upgrade the video card to get reasonable 3D, even though there really isn't good reason to, in the sense that the card works fine and is quite capable.  I've been using the open source driver for over a year, but finally hit a couple of things I needed real 3D for, only to realize I'm now unable to do so.

---

