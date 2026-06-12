---
title: "Touchpad compaq (nx9105)"
date: 2005-02-09
forum: Hardware &amp; Laptops
---

### Post by realrasta on 2005-02-09
Hello,

Yesterday I installed hoary on my compaq but unfortunately the touchpad isn't working. I tried warty before but the same problem (and some others which seem to be solved now).

Any ideas how to get it working?

Best regards,

Rob

---

### Post by knappen on 2005-02-09
Do you know what type of touchpad you have?

---

### Post by realrasta on 2005-02-09
Somewhere on the net I read it is an ALPS touchpad

Regards,

Rob

---

### Post by realrasta on 2005-02-13
I tried the synaptics driver for xorg but it does not detect my touchpad. 

Anybody with ideas  how to solve this?

Regards

Rob

---

### Post by julian on 2005-02-14
I have an ALPS touchpad on my Dell Inspiron 500m.   Using Warty it was not detected as a touchpad, just as a PS/2 mouse with much too sensitive tap behaviour.

I solved this by recompiling the kernel (actually only needed to compile the psmouse driver I think) with an ALPS patch.  With this patch in the kernel driver the X synaptics driver works and you can control your touchpad settings.

The ALPS patch is available in this package:

[http://web.telia.com/~u89404340/touchpad/files/synaptics-0.14.0.tar.bz2](http://web.telia.com/~u89404340/touchpad/files/synaptics-0.14.0.tar.bz2)

You only need the ALPS patch as the rest of this driver seems to be already installed in X.

After applying the patch you need to add the following line to psmouse.h to make it compile:

#define PSMOUSE_CMD_DISABLE	0x00f5

Julian

---

### Post by shuflie on 2005-02-14
Have you tried following the setup [here](http://www.ubuntulinux.org/wiki/SynapticsTouchpadHowto)? One other thing you should do is make sure you pass the "AlwaysCore" option when calling the touchpad driver in the server layout section. e.g.


Section "ServerLayout"
	.
        .
        .
        .
	InputDevice	"Synaptics Touchpad" "AlwaysCore" 
	.
	.
	.
EndSection

---

### Post by mathiasv on 2005-02-18
Hi. I have got the synaptics touchpad on my Medion working. But for some strange reason I had to configure /boot/grub/menu.lst to work with the touchpad (?$¤%*!). I have added "i8042.nomux" so this part of the file now looks like this:

```
title           Ubuntu, kernel (custom-FEB2005)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.8.1 root=/dev/hda1 ro quiet splash i8042.nomux
initrd          /boot/initrd.img-2.6.8.1
savedefault
boot
```

Hope this helps someone. Mv.

---

