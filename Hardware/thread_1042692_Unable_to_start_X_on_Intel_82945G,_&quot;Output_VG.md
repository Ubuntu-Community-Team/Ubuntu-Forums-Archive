---
title: "Unable to start X on Intel 82945G, &quot;Output VGA disconnected&quot;"
date: 2009-01-17
forum: Hardware
---

### Post by ziesemer on 2009-01-17
Using Ubuntu 8.10 / Intrepid Ibex.

All of the sudden, I find that my X refuses to start.  I've not changed anything other than installing the recommended security updates - and I don't recall anything in there related to the video drivers.

According to lspci, VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02).

Here is the end of my /var/log/Xorg.0.log:

```

(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 7872 kB
(II) intel(0): VESA VBE OEM: Intel(r) 82945G Chipset Family Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(r) 82945G Chipset Family Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): Output VGA disconnected
(WW) intel(0): No outputs definitely connected, trying again...
(II) intel(0): Output VGA disconnected

```

The output from "sudo startx" includes:

```

(EE) intel(0): No valid modes.
(EE) Screen(s) found, but none have a usable configuration.

```

Well, the VGA is certainly connected.  It's the only video output on the device, and I have the shell visible on the connected Samsung SyncMaster 753DF monitor, and it is working fine with my other computers.  The one possible issue I see is my Tripp-Lite 4-port KVM switch that is connected in the middle, but I've not had any issues with it before, including any issues passing the EDID data.

Also, I'm not sure if this is related, but why does "sudo dpkg-reconfigure xserver-xorg" not offer any options for configuring the video?  The only options I see that it gives me relate to the keyboard.

What is the best way to reconfigure the video and get it working on this system, even if I need to manually specify 1024x768 resolution @ 60 Hz, etc.?

Thanks!

---

### Post by sunkist on 2009-04-28
ziesemer - did you ever get this resolved?  I've got a similar issue.

Display is: DELL 2005FPW 
Graphics are: Intel Corporation 82945G/GZ Integrated Graphics Controller

Short story is: running fine on 8.04, upgraded to 8.10, lost display via Belkin omniview KVM (but works without), upgraded to 9.04 thinking it couldn't be worse, and I was right.  Still no good over KVM, but works fine without.

Display works when directly hooked to VGA cable + monitor, but not via KVM.  

If anyone has a solution, of course, it would be much appreciated.

---

### Post by sunkist on 2009-04-28
did some additional reading and found this:

"However, there are cases where the monitor fails to report EDID...There are several causes for EDID fail reads. One is if you're using a truly ancient monitor from the days before EDID. A second is if you're using a video extension cable, KVM, or other piece of equipment connected between the monitor and the video card that lacks the EDID wire."

my belkin 4-port (F1D104) is at least 5 yrs old (rel. date was 2/2002), so I am going lay blame on that because a 2-port iogear ([http://www.iogear.com/product/GCS62/](http://www.iogear.com/product/GCS62/)) worked without a hitch.

of course, YMMV.

here are links if you want to peruse.

[https://bugs.edge.launchpad.net/ubuntu/+source/xorg-server/+bug/194760](https://bugs.edge.launchpad.net/ubuntu/+source/xorg-server/+bug/194760)
&
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/313220](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/313220)
&
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/180601](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/180601)

---

### Post by TRON NZ on 2009-04-29
Exact same problem as above, really frustrating stuff! Any help appreciated on  this one as I am completely lost! Works with other LCD monitors just not my small 7" LCD monitor for the car :)

(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): Resizable framebuffer: not available (1 3)
(II) intel(0): Output VGA disconnected
(WW) intel(0): No outputs definitely connected, trying again...
(II) intel(0): Output VGA disconnected
(WW) intel(0): Unable to find initial modes
(EE) intel(0): No valid modes.
(II) UnloadModule: "intel"
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules//libvgahw.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support
         at [http://wiki.x.org](http://wiki.x.org)
 for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log


Thanks

Tron

---

### Post by ziesemer on 2009-05-31
Well, my KVM wasn't the issue with me loosing the EDID data - but a damaged monitor cable extension connecting the computer to the KVM was.  Replaced the cable, and now I have no more issues.

As sunkist mentioned, there are options to disable probing for the EDID and other data.  However, then the configurations must be manually given - which certainly appears to be no easy task.

---

