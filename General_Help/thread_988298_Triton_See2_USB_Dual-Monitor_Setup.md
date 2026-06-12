---
title: "Triton See2 USB Dual-Monitor Setup"
date: 2008-11-20
forum: General Help
---

### Post by JammingEcono on 2008-11-20
Howdy all!  New to the forum and Ubuntu in general, but tremensdously excited to be (finally) getting onto the bandwagon.

Does anyone have any suggestions on how to set up my [Triton See2 USB 2.0 VGA Video Adapter]("http://www.trittontechnologies.com/products/TRIUV100.htm") to run on Ubuntu 8.10?  I know the Triton site (see [link]("http://www.trittontechnologies.com/products/TRIUV100.htm")) says that it only supports Windows 2000/XP/Vista, but I wonder if there's not a workaround to get it to work on Ubuntu?

The video card on the computer I'm using (Dell Optiplex 210L, Pentium 4 3GhZ, 1GB RAM) doesn't have additional DVI, etc. plugs, so I'm stuck with the Triton See2 adapter to run my precious dual-monitor setup, unfortunately.

Any advice would be much appreciated!

---

### Post by richb1 on 2009-04-20
Look Here:
[http://ubuntuforums.org/showthread.php?t=260863](http://ubuntuforums.org/showthread.php?t=260863)

Let me know if it works for you. I have one and have not been able to get it to work yet.

---

### Post by JammingEcono on 2009-11-25
I was never able to get this working despite the great advice in this and linked threads.  Does Ubuntu 9.10 address this issue?

---

### Post by JammingEcono on 2010-05-03
I was hoping that Ubuntu 10.04 might address this issue out of the box, but alas it did not once I upgraded.

I've been unable to make the work-around mentioned in the link earlier in this thread work but have been unable to do so.  If anyone in the community has a suggestion for an easy way to address this (particularly if there's a patch or something I can download that would do it automatically), I'd be forever in your debt.

---

### Post by ben@kietzman.org on 2010-05-05
I have the same problem.  My Tritton USB SVGA stopped working after upgrading from 9.10 to 10.04.  I know the device is still be recognized because it puts that red border around the edge of the screen.

According to lsusb the dongle is detectable:  "ID 0711:0900 Magic Control Technology Corp. SVGA Adapter".  According to linux-source-2.6.32/drivers/usb/misc/sisusbvga/sisusb.c the dongle is detectable:  "USB_DEVICE(0x0711, 0x0900)".  According to syslog the device is being found:  "USB2VGA dongle found".  According to lsmod the sisusbvga driver is being loaded.

However, according to /var/log/Xorg.0.log the dongle is not be loaded.  There isn't anything in the log showing up in the log regarding sisusb.  And I'm using the same xorg.conf that was working under 9.10.

Strange.

---

### Post by JammingEcono on 2010-05-05
Wow, you got farther than I did in getting it to run on 9.10.  I got the similar red border when I tried to configure it in 9.10, but never got it to work correctly.

Step-by-step instructions when/if someone is able to get it configured to work in 10.04 would be greatly appreciated.

---

### Post by ben@kietzman.org on 2010-06-04
After doing some research it looks like the xserver-xorg-video-intel driver is not equipped to handle Tritton USB SVGA equipment.  From what I've read, we need to use the xserver-xorg-video-i810 driver instead.  However, that driver has been retired from the repositories.  Does anyone know how to install the xserver-xorg-video-i810 driver in place of the xserver-xorg-video-intel on Ubuntu Lucid?  I think this is the missing key.

---

### Post by ben@kietzman.org on 2010-10-11
Great news!!!  Ubuntu 10.10 (Maverick Meerkat) has reinstated Tritton USB SVGA support via the xserver-xorg-video-sisusb driver.  The xorg.conf setup uses the same syntax as back when it worked under 9.10 via the xserver-xorg-video-i810 driver.

I wrote up this reply on my Tritton USB connection!

Here is a copy of my SISUSB specific settings:

```

Section "Monitor"
  Identifier   "MonitorUSB"
  VendorName   "Tritton"
  ModelName    "SVGA Adapter"
  VertRefresh  50-75
  HorizSync    30-90
  Option  "DPMS"
EndSection

Section "Device"
  Identifier "CardUSB"
  VendorName "SiS"
  BoardName  "SiS"
  Driver     "sisusb"
  BusID      "USB:0711:0900"
EndSection

Section "Screen"
  Identifier "ScreenUSB"
  Device     "CardUSB"
  Monitor    "MonitorUSB"
  SubSection "Display"
    Viewport   0 0
    Depth     1
  EndSubSection
  SubSection "Display"
    Viewport   0 0
    Depth     4
  EndSubSection
  SubSection "Display"
    Viewport   0 0
    Depth     8
  EndSubSection
  SubSection "Display"
    Viewport   0 0
    Depth     15
  EndSubSection
  SubSection "Display"
    Viewport   0 0
    Depth     16
  EndSubSection
  SubSection "Display"
    Viewport   0 0
    Depth     24
  EndSubSection
EndSection

```

---

### Post by bigswagg on 2010-12-10
> **ben@kietzman.org said:**
> Great news!!!  Ubuntu 10.10 (Maverick Meerkat) has reinstated Tritton USB SVGA support via the xserver-xorg-video-sisusb driver.  The xorg.conf setup uses the same syntax as back when it worked under 9.10 via the xserver-xorg-video-i810 driver.

I wrote up this reply on my Tritton USB connection!

Here is a copy of my SISUSB specific settings:

```

Section &quot;Monitor&quot;
  Identifier   &quot;MonitorUSB&quot;
  VendorName   &quot;Tritton&quot;
  ModelName    &quot;SVGA Adapter&quot;
  VertRefresh  50-75
  HorizSync    30-90
  Option  &quot;DPMS&quot;
EndSection

Section &quot;Device&quot;
  Identifier &quot;CardUSB&quot;
  VendorName &quot;SiS&quot;
  BoardName  &quot;SiS&quot;
  Driver     &quot;sisusb&quot;
  BusID      &quot;USB:0711:0900&quot;
EndSection

Section &quot;Screen&quot;
  Identifier &quot;ScreenUSB&quot;
  Device     &quot;CardUSB&quot;
  Monitor    &quot;MonitorUSB&quot;
  SubSection &quot;Display&quot;
    Viewport   0 0
    Depth     1
  EndSubSection
  SubSection &quot;Display&quot;
    Viewport   0 0
    Depth     4
  EndSubSection
  SubSection &quot;Display&quot;
    Viewport   0 0
    Depth     8
  EndSubSection
  SubSection &quot;Display&quot;
    Viewport   0 0
    Depth     15
  EndSubSection
  SubSection &quot;Display&quot;
    Viewport   0 0
    Depth     16
  EndSubSection
  SubSection &quot;Display&quot;
    Viewport   0 0
    Depth     24
  EndSubSection
EndSection

```

   will this work with see2 uv150 external vga video card?

---

### Post by ben@kietzman.org on 2010-12-11
I have no idea if the SEE2 UV150 external VGA video card works since I do not have one of those.  Sorry.

---

### Post by EXYZ1000 on 2012-03-18
Any one got this to work on See2 UV150 - Ubuntu 11.10?

Thanks

---

