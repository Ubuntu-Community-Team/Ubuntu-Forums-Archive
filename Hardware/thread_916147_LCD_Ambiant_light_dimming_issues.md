---
title: "LCD Ambiant light dimming issues"
date: 2008-09-10
forum: Hardware
---

### Post by Bigboltrules on 2008-09-10
SO, I am running Hardy and I have a Asus M50SV.  It has a webcam, which in vista dims the screen for different lighting.  In Vista, you can disable this.  In ubuntu, since I am new, and I have been searching the forums for 2 hours, there is no clear way to disable this.  I have tried xbacklight, no dice.  I have tried turning off dimming in the bios, which is only for when you are unplugged.  No dice there either.  

If anyone has any suggestions, and please keep in mind I new to ubuntu, I would greatful if you could post them.

Thanks.

---

### Post by Bigboltrules on 2008-09-12
bump

---

### Post by damis648 on 2008-09-12
Try setting it in the BIOS. There must be a BIOS option to disable it.

---

### Post by Bigboltrules on 2008-09-15
> **damis648 said:**
> Try setting it in the BIOS. There must be a BIOS option to disable it.

Well, like I said in the original post, I tried that.  The only setting in the bios is for Dimming when not plugged in.  I tried that enabled and disabled and neither worked.

Any other ideas?

---

### Post by Bigboltrules on 2008-09-15
> **Bigboltrules said:**
> SO, I am running Hardy and I have a Asus M50SV.  It has a webcam, which in vista dims the screen for different lighting.  In Vista, you can disable this.  In ubuntu, since I am new, and I have been searching the forums for 2 hours, there is no clear way to disable this.  I have tried xbacklight, no dice.  I have tried turning off dimming in the bios, which is only for when you are unplugged.  No dice there either.  

If anyone has any suggestions, and please keep in mind I new to ubuntu, I would greatful if you could post them.

Thanks.


I did figure this out myself by searching the crud out of forums.  

I had to edit the rc.local file and place the following into it:

echo 0 > '/sys/devices/platform/asus-laptop/ls_switch'


Once I did this, it fixed it.  You can try it first by opening the terminala and doing:

sudo -s

echo 0 > '/sys/devices/platform/asus-laptop/ls_switch'

Worked great for me!

---

