---
title: "glxgears gives a segmentation fault"
date: 2005-06-23
forum: Hardware &amp; Laptops
---

### Post by watje on 2005-06-23
When I run glxgears I get "Segmentation fault" when I look at dmesg I see:
```
glxgears[8023]: segfault at 0000002a956d8af0 rip 0000002a967ee4de rsp 0000007fbffff938 error 6
glxgears[8029]: segfault at 0000002a956d8af0 rip 0000002a967ee4de rsp 0000007fbffff938 error 6
glcpu[8030]: segfault at 0000002a95d2baf0 rip 0000002a974884de rsp 0000007fbffff948 error 6
glxgears[8833]: segfault at 0000002a956d8af0 rip 0000002a967ee4de rsp 0000007fbffff938 error 6
glxinfo[8870]: segfault at 0000002a9585aaf0 rip 0000002a96c5b4de rsp 0000007fbffff938 error 6
glxinfo[8871]: segfault at 0000002a9585aaf0 rip 0000002a96c5b4de rsp 0000007fbffff928 error 6
glxinfo[8872]: segfault at 0000002a9585aaf0 rip 0000002a96c5b4de rsp 0000007fbffff928 error 6
glxgears[9378]: segfault at 0000002a956d8af0 rip 0000002a967ee4de rsp 0000007fbffff828 error 6
glxgears[11448]: segfault at 0000002a956d8af0 rip 0000002a967ee4de rsp 0000007fbffff828 error 6
glxgears[11685]: segfault at 0000002a956d8af0 rip 0000002a967ee4de rsp 0000007fbffff828 error 6
```

My XF86conf:
```
Section "Module"
        Load    "GLcore"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "extmod"
        Load    "freetype"
        #Load   "glx"
        Load    "int10"
        Load    "record"
        Load    "speedo"
        Load    "type1"
        Load    "vbe"
        Load    "xtt"
        Load    "v4l"
EndSection
[..]
Section "Device"
        Identifier      "NVIDIA Corporation NVIDIA Default Card"
        Driver          "nvidia"
        BusID           "PCI:5:0:0"
        Option          "NoLogo"
EndSection

```
If I uncomment "glx" X won't start anymore.
Somebody knows whats wrong?
Thnx

---

### Post by Khannie on 2005-06-27
This problem seems to be all over the place, with no answers. I am currently at the point where I have overcome the problem you mention by installing the 7667 drivers from the nvidia website (I think that the headers were compiled for me for my 386 kernel, then when I upgraded to the K7 kernel they weren't recompiling), so you may want to try those newer drivers (They seem more or less identical to the 7664 ones)

After installing, I got about a 4% increase in glxgears over the default drivers, but after a reboot, glxgears segfaults again (though I can at least get into X with the glx module left in my xorg.conf).

If you don't need hardware accelleration, you can replace "glx" with "GLCore", though this will be very slow (read, no games).

---

### Post by daller on 2006-11-23
I just got a segmentation fault from glxgears after installing the newest drivers from tseliot.

Do you know what's wrong, and another way to test 3D acceleration?

Everything using 3D seems to fail:

daniel@dallap:~$ neverball
open /dev/sequencer: No such file or directory
Segmentation fault
daniel@dallap:~$

daniel@dallap:~$ neverputt
open /dev/sequencer: No such file or directory
Segmentation fault

---

