---
title: "Video Issue installing 8.04.1"
date: 2008-09-15
forum: Hardware
---

### Post by iCeQuBe74 on 2008-09-15
When I try to install 8.04.1 on my Dell Inspiron 8000 laptop during installation and after the screen is weird.  It looks so strange like the screen is ssplit in the middle and when I move the mouse left off the screen it shows up on the right side of the screen and vise versa.  I didn't see a safe video mode install but i am very green when it comes to linux so I may have just missed it.  Any help would be appreciated.  Oh and windows works fine and so does Mandriva linux.  I also tried re-downloading and re-burning the install CD.  I can take a pic of the screen and post it if needed.

---

### Post by perspectoff on 2008-10-01
> **iCeQuBe74 said:**
> When I try to install 8.04.1 on my Dell Inspiron 8000 laptop during installation and after the screen is weird.  It looks so strange like the screen is ssplit in the middle and when I move the mouse left off the screen it shows up on the right side of the screen and vise versa.  I didn't see a safe video mode install but i am very green when it comes to linux so I may have just missed it.  Any help would be appreciated.  Oh and windows works fine and so does Mandriva linux.  I also tried re-downloading and re-burning the install CD.  I can take a pic of the screen and post it if needed.


I just installed Kubuntu 8.04 Hardy (I like Kubuntu instead of Ubuntu, but your mileage may vary) on an old Inspiron 8000 with ATI Mobility M4 AGP graphics.

It worked out of the box using the VESA video that usually installs at default, except I had the same problem as you with the screen.

The solution is simpler than you think, though. You have to change the monitor resolution:

System Settings --> Monitor & Display --> Administrator Mode --> Hardware --> Monitor #1 --> Configure --> Generic --> LCD Panel 1400 x 1050

Then either logout and "Restart X server" and re-login, or simply reboot the whole system.

I had no further display problems after doing this. I left the video as VESA, which worked for me.

I understand there are both open source and proprietary ATI graphics drivers that you can select instead of VESA as well, but I didn't play with them (since I don't generally use the 3D effects). I am extremely happy with Kubuntu Hardy on my Dell Inspiron 8000!

I had no sound issues and no Ethernet connectivity issues (using a USB Ethernet adapter, since the Inspiron 8000 doesn't have a built-in Ethernet port.

---

### Post by iCeQuBe74 on 2008-10-01
I am sure I am just missing it but where are the system settings?  i can't find anything that says that.  I hooked up an external monitor and that makes the screen look right for now, the problem though is with the monitor unplugged the screen goes scrambled again.  Thanks for the help.

---

