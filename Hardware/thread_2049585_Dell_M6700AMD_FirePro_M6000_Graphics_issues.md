---
title: "Dell M6700/AMD FirePro M6000 Graphics issues"
date: 2012-08-28
forum: Hardware
---

### Post by pvandoren on 2012-08-28
Hi All:

I have Ubuntu 12.04 running on a Dell M6700.  Everything install pretty smooth, except the open video drivers don't work with multiple displays with the AMD FirePro M6000 graphics card.

The Proprietary drivers work:  However only with 2 displays.  I'm really hoping to have a Tri-Head display system that I know is possible with the M8900 video using the open video drivers on the Dell M6600.

Does anyone know what I need to hack to get the open driver to work on the M6000?  Currently it only displays on the laptop display, and doesn't recognize that my Samsung displays are attached.  It's also stuck in Unity 2d mode -vs- 3d mode.

The proprietary drivers work, but I can only get it to work with two displays instead of all 3.

I had to hack the proprietary drivers to get rid of the "Unsupported Hardware" overlay, but that was it. (basically I followed the recommendation from: [http://superuser.com/questions/54157/amd-unsupported-hardware-watermark-in-linux-mint](http://superuser.com/questions/54157/amd-unsupported-hardware-watermark-in-linux-mint) for extracting the /etc/ati/control file from the latest version of the driver from AMD.



Thanks:

Pete

---

### Post by burakvarhan on 2012-09-02
Hello Pete,
I have ordered a Dell Precision m6700 with AMD FirePro m6000. I was looking for the proprietary driver. AMD's driver download web site says that I have to go to Dell's driver support web site to get drivers. However, Dell only provides Windows drivers for AMD FirePro m6000.

I 'd appreciate if you could let me know where/how you got proprietary AMD FirePro m6000 drivers.

Thanks

---

### Post by pvandoren on 2012-09-12
> **burakvarhan said:**
> Hello Pete,
I have ordered a Dell Precision m6700 with AMD FirePro m6000. I was looking for the proprietary driver. AMD's driver download web site says that I have to go to Dell's driver support web site to get drivers. However, Dell only provides Windows drivers for AMD FirePro m6000.

I 'd appreciate if you could let me know where/how you got proprietary AMD FirePro m6000 drivers.

Thanks

Ubuntu 12.04 comes with a version of the Proprietary AMD drivers, but it doesn't support the M6000 out of the box. (It works but displays "unsupported hardware" in the bottom corner.

What I did was using dash search for "Additional Drivers"
Install the ATI/AMD proprietary Drivers and reboot the computer.

This should come up with the "unsupported Hardware" issue, but works.   When I tried the ATI/AMD proprietary (post-release updates)  It didn't install properly with 12.04 but 12.04.1 was just released so they may have fixed that. (haven't tried)

To remove the unsupported hardware I downloaded the latest driver from AMD: 

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)

but instead of doing a full install of that driver I used the trick 

./ati-driver-installer-10-1-x86.x86_64.run --extract to extract the files (instead of installing them)

I then copied the new control file.

sudo cp /etc/ati/control /etc/ati/control-old
sudo cp common/etc/ati/control /etc/ati/control


Generally I don't like this, but it did work.  I had issues just installing the 12.8 drivers directly.

In trying various things the video driver was messed up at various points, so I had to completely remove the video drivers at some point.

I just googled for it and found this site:
[http://askubuntu.com/questions/78675/how-do-i-remove-the-fglrx-drivers-after-ive-installed-them-by-hand](http://askubuntu.com/questions/78675/how-do-i-remove-the-fglrx-drivers-after-ive-installed-them-by-hand)

The answer worked for me.


Hope this helps

Pete

---

### Post by pvandoren on 2013-06-20
Just and update on this:

With the latest version of Ubuntu 12.04.2 I can now get 3 displays to work with the open source radeon driver.  However with the Proprietary driver up to version 13.4 only 2 displays will work (The hack I initially had to do is no longer required)

With the proprietary driver everything seems like it should work.  But when ever I try to add the third display I get a CRTC error.

Using xrandr I verified  this with the following command line:

xrandr --verbose --fb 6016x1152 --output LVDS --auto --output DFP5 --auto --right-of LVDS --output DFP9 --auto --right-of DFP5
screen 0: 6016x1152 1592x305 mm  95.94dpi
crtc 0:    2048x1152   59.9 +1920+0 "DFP5"
crtc 1:    2048x1152   59.9 +3968+0 "DFP9"
crtc 2:    1920x1080   60.0 +0+0 "LVDS"
xrandr: Configure crtc 2 failed
crtc 0: disable
crtc 1: disable
crtc 2: disable
crtc 3: disable
crtc 4: disable
crtc 5: disable
screen 0: revert
crtc 0: revert
crtc 1: revert
crtc 2: revert
crtc 3: revert
crtc 4: revert
crtc 5: revert


Although this video card should support 6 displays, so far no joy with the proprietary drivers. Ugh.  With the Radeon drivers I don't get 3d support for unity which is a must..

I've tried adding the third display in various fashions. (LVDS panel, Dock VGA connector, Dock Display port connector, and laptop Displayport connector, and no joy in all cases.)


Anyone out there having better luck?

Pete

---

