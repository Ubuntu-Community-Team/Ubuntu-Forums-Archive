---
title: "s-video card acting up"
date: 2009-10-08
forum: Hardware
---

### Post by hydrotemplar on 2009-10-08
with Jaunty Xubuntu on a Dell Dimension 2100 with an ATI Radeon 7000

Using the s-video output on the video card, I am able to see everything fine with the manufacturer's screen, the bios, grub, and the splash screen, but after that, the screen goes blank.  from a live cd, it's the same thing, I get through the language selection, select "try xubuntu...", then the splash screen, then when it should get to the login screen, nothing.

I tried inputing my login and password, and I could hear the computer working, so everything's loading fine, it's just not outputting to the TV.

I also tried adding
Option "TVDACLoadDetect" "TRUE"
to my xorg.conf under "device" over ssh and rebooted, but that didn't help anything.

thanks,
david

---

### Post by hydrotemplar on 2009-10-09
I have a friend who suggested changing the init state in inittab from 5 to 3 so it would boot to CLI rather than GUI, and see if that works.

Well, I did some research, and Ubuntu doesn't have the same init states as is linux standard.  All of the init states for Ubuntu boot into GUI.

Is there another way I could force an immediate dump into terminal?

---

