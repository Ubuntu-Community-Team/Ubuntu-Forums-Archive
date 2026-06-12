---
title: "Touchpad can turn off but not back on"
date: 2010-02-28
forum: Hardware
---

### Post by 90sgamer on 2010-02-28
I have a Gateway NV53 laptop running Ubuntu 9.10, and there's a touch-sensitive "disable touchpad" button above my keyboard which defaults to "off" when I boot.  If I press the button once, the light underneath the button turns on, and the touchpad itself turns off like it should.  However, when I press the button again, the light underneath the button turns off to indicate that my touchpad is no longer disabled, but the touchpad remains disabled!  All the button does thereafter is toggle the status light.

For an alternate touchpad configuration tool, I installed gsynaptics, but when I run it, I get the message:  "Gsynaptics couldn't initialize.  You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics."  So, I followed the instructions at  [http://ubuntuforums.org/showthread.php?t=526459](http://ubuntuforums.org/showthread.php?t=526459) to no avail.  I get the same error message when I try to run GSynaptics.

This "disable touchpad" button works like it should in Windows 7.  What could I do to get it working here in Ubuntu?

Edit:  bump

---

### Post by 90sgamer on 2010-02-28
Looks like I can't bump this with an edit of the OP, so here's a reply.  Bump.

---

### Post by 90sgamer on 2010-03-01
bump

---

### Post by 90sgamer on 2010-03-05
Does anyone know how they would try to fix this problem?

---

### Post by dslachut on 2010-05-04
Same laptop, using Lucid, same issue.

*bump*

---

### Post by Elmer Fudd on 2010-05-11
My ACER 7736 has always had the problem (Lucid and Karmic) of not being able to turn the pad back on with the hardware switch. Now the pad doesn't work at all. The pad disable/enable button still works and sets the pad on/off toggle (you can watch it in gconf-editor).

---

### Post by jorgerivera on 2010-05-14
I had the exact same issue here, tested in both Lucid and Karmic. Mine is an Acer Aspire Timeline 4810T.

There is a document [here]("https://help.ubuntu.com/community/AspireTimeline/Fixes") about the Timeline family, and I found a fix that works!

Basically, you need to add the "i8042.nomux" option to the GRUB_CMDLINE_LINUX_DEFAULT line in /etc/default/grub, regenerate your grub entries (running update-grub) and reboot.

More details on the fix in [https://help.ubuntu.com/community/AspireTimeline/Fixes](https://help.ubuntu.com/community/AspireTimeline/Fixes) in the section "Touchpad On/Off button".  

It does work for me :)

---

