---
title: "resolution wrong in gdm greeter only"
date: 2007-02-01
forum: Hardware &amp; Laptops
---

### Post by jbeiter on 2007-02-01
I'm running ubuntu 6.10 edgy on a Dell D820 laptop. The LCD is 1280x800 and the docking station LCD is 1280x1024.

If I boot undocked, gdm looks fine.. the resolution is good at 1280x800.

If I boot docked, gdm is messed up and stretched. After I log in though, the desktop comes up fine at 1280x1024. If I log out, the gdm greeter is messed up again.

So, my xorg.conf file is working okay for my docked and undocked resolutions.. but gdm isn't good docked.

Any clues?

---

### Post by allwin on 2007-02-01
Yeah!  I ran into the same problem with my keyboard monitor video switch!

There is an option you can put in Xorg.conf to tell it to ignore the EDID of the monitor, the little conversation between the monitor and XORG that tells it what resolutions are supported.  It's different depending upon whether nVidia or ATI.

For nVidia it's Option "UseEdidDpi" "FALSE" followed by Option "DPI" "96x96"

For the ATI driver (open source one) it's Option "IgnoreEdid" "true" if I remember correctly.

Check the doc on your particular video driver, whatever that is.  May have to hunt for it on the manuf. website.

Finding the right invocation cured the problem on two of my PC's I use to experiment here.  Sounds like it might work for yours.  My fonts were so large I could not physically log in.  Frustrating!

---

