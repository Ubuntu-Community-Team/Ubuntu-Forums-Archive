---
title: "Change touchscreen rotation on the fly?"
date: 2010-02-17
forum: Hardware
---

### Post by mooware on 2010-02-17
Hello forum people,

I have an Intel Classmate Convertible netbook which has a touchscreen. It has accelerometers to determine the position of the display, and I managed to set up automatic display rotation with them. But the touchscreen control does not rotate with it.
I can configure the rotation manually in my xorg.conf, in the following section:

```
Section "InputDevice"
        Identifier  "HID TOUCH"
        Driver      "xfhiddrv"
        Option      "Device" "/dev/usb/hiddev0"
        Option      "ScreenNo" "0"
        Option      "Rotation" "0"
        Option      "SwapY" "0"
        Option      "UpSound" "0"
        Option      "DownSound" "0"
EndSection
```Can I somehow change the "Rotation"-option dynamically, with a shell command for example?

**EDIT:**
Solved it myself. Intel had a patched version of xrandr for their Ubuntu 8.04-based setup ([http://intel-powered-classmate-pc.archive.canonical.com/ubuntu/dists/hardy-classmate/main/source/x11-xserver-utils_7.3+2netbook0natick1.tar.gz](http://intel-powered-classmate-pc.archive.canonical.com/ubuntu/dists/hardy-classmate/main/source/x11-xserver-utils_7.3+2netbook0natick1.tar.gz)), which didn't quite work for me, because the touchscreen input was always turned 180 degrees from what it should have been. I took the source and experimented a bit with it, eventually extracting the stuff that actually changes touchscreen rotation. From that I compiled a little tool that I now use in my screen-rotation script. If someone needs this program, just contact me, I am happy to help out.

---

### Post by daveguy on 2011-02-22
> **mooware said:**
> Hello forum people,

I have an Intel Classmate Convertible netbook which has a touchscreen. It has accelerometers to determine the position of the display, and I managed to set up automatic display rotation with them. But the touchscreen control does not rotate with it.
I can configure the rotation manually in my xorg.conf, in the following section:

```
Section "InputDevice"
        Identifier  "HID TOUCH"
        Driver      "xfhiddrv"
        Option      "Device" "/dev/usb/hiddev0"
        Option      "ScreenNo" "0"
        Option      "Rotation" "0"
        Option      "SwapY" "0"
        Option      "UpSound" "0"
        Option      "DownSound" "0"
EndSection
```Can I somehow change the "Rotation"-option dynamically, with a shell command for example?

**EDIT:**
Solved it myself. Intel had a patched version of xrandr for their Ubuntu 8.04-based setup ([http://intel-powered-classmate-pc.archive.canonical.com/ubuntu/dists/hardy-classmate/main/source/x11-xserver-utils_7.3+2netbook0natick1.tar.gz](http://intel-powered-classmate-pc.archive.canonical.com/ubuntu/dists/hardy-classmate/main/source/x11-xserver-utils_7.3+2netbook0natick1.tar.gz)), which didn't quite work for me, because the touchscreen input was always turned 180 degrees from what it should have been. I took the source and experimented a bit with it, eventually extracting the stuff that actually changes touchscreen rotation. From that I compiled a little tool that I now use in my screen-rotation script. If someone needs this program, just contact me, I am happy to help out.

I think I could use your help with this, it may not be a big deal to our users, but we are going to have over 300 of the machines out in our district, and it might be nice to have it working.

Oh, and one other thing, have you had any issues with the sound? Specifically, when headphones are plugged into one of the two headphone/external speaker ports, the headphones work, but the main speakers do not shut off?

Thank you for any help you could give me!

David Jorgenson
Computer Technician
Grand Forks Public Schools
[email]djorgenson@gfschools.org[/email]

---

