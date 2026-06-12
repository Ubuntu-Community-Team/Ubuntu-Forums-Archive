---
title: "ATI 9.1 Driver - No supported adapters detected"
date: 2009-02-06
forum: Hardware
---

### Post by CowzRule on 2009-02-06
I'm trying to install the new ATI 9.1 driver. I've followed the instructions at the [Ati Linux Wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Install_Method") using the Manual install method.
The packages install with no problem but when I do
"sudo aticonfig --initial -f"
I get
"aticonfig: No supported adapters detected"

I've tried installing these drives by just following the instructions to try and "upgrade" and by completely removing the 8.12 drivers and reverting to the original xorg.conf file.
Both methods have resulted in the same problem.
I've also tried rebooting without running "sudo aticonfig --initial -f" but that puts me into low graphics mode.

The card I have is an ATI HD2400 Pro AGP 8x
The previous 8.12 drivers work just fine, but I've read there is some improvement with the new drivers and I'd like to try them.

---

### Post by J117 on 2009-02-06
Perhaps that driver doesn't work with the AGP version?

---

### Post by Yashiro on 2009-02-06
I'm no stranger to messing around with drivers and one of my Ati systems also does this. Drivers upto 8.11 are fine. 8.12 and 9.1 hang X as soon as the GDM is launched. No errors, the system is running but with a black/random static on vt7.

This is using the manual method that works for all drivers upto that point. Odd, but there you go.

---

### Post by CowzRule on 2009-02-06
Well the 8.12 drivers are working fine for me, It's what I using now, but I do have some minor issues that I'd like to see if the new driver may improve or fix.
I'm just hoping that maybe it's a bug and I'll be able to try the next version.

---

### Post by Yashiro on 2009-02-06
Amd do type up pdf release notes of what bugs they fix. Have a look on their site perhaps. Or have good look on [http://www.phoronix.com/forums/](http://www.phoronix.com/forums/)

---

