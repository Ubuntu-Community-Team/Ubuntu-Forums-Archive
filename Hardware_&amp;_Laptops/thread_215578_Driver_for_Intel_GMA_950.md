---
title: "Driver for Intel GMA 950"
date: 2006-07-14
forum: Hardware &amp; Laptops
---

### Post by rajeshrs on 2006-07-14
[http://www.linlap.com/tiki-index.php?page=Lenovo+3000+N100](http://www.linlap.com/tiki-index.php?page=Lenovo+3000+N100)

In that review (^^^link), the guy has used an i810 chipset driver for linux and got the GMA 950 card working. 

Does this disable any features of the GMA950 or will the card work to its full potential? Is there no out of the box support for the GMA 950 with Ubuntu?

Regards
Rajesh

---

### Post by twoseids on 2006-07-14
I've got the same problem over here. I think the i810 driver is what my buddy used to get my GMA 950 working (I'm on a Dell Latitude D520). But movies and video clips look awful. My screen looks fine when not watching movies, so I'm not freaking out. But switching over to Windows to watch videos, when I used to do it fine with Breezy, sucks.

---

### Post by Daniel15 on 2006-07-14
Even though the driver is called 'i810', I believe it's a generic Intel driver. If you get bad performance, try installing [this driver](http://beerorkid.com/compiz/pool/main/x/xserver-xorg-driver-i810/xserver-xorg-driver-i810_1.5.0.1-0ubuntu2_i386.deb). It's basically a newer version of the i810 driver that comes with Ubuntu.

Then, reconfigure X by typing ```
sudo dpkg-reconfigure xserver-xorg
``` in a Terminal window. Follow all the directions, but pay special attention to the 'Memory Available' step. If the GMA 950 is anything like the 810E in my computer, it has no internal memory whatsoever. This means that you need to type in an amount of system memory to use. Try something like 8 MB (8192KB) to begin with.

After doing all that, restart X. Opening a terminal window and typing 'glxinfo' should show something like 'Direct rendering: Enabled' at the top of the page. This means that Direct Rendering is enabled, which should improve performance.

Honestly though, the Intel graphics cards are horrible, you shouldn't expect much from them...

---

### Post by twoseids on 2006-07-15
> **Daniel15 said:**
> Even though the driver is called 'i810', I believe it's a generic Intel driver. If you get bad performance, try installing [this driver](http://beerorkid.com/compiz/pool/main/x/xserver-xorg-driver-i810/xserver-xorg-driver-i810_1.5.0.1-0ubuntu2_i386.deb). It's basically a newer version of the i810 driver that comes with Ubuntu.

Then, reconfigure X by typing ```
sudo dpkg-reconfigure xserver-xorg
``` in a Terminal window. Follow all the directions, but pay special attention to the 'Memory Available' step. If the GMA 950 is anything like the 810E in my computer, it has no internal memory whatsoever. This means that you need to type in an amount of system memory to use. Try something like 8 MB (8192KB) to begin with.

After doing all that, restart X. Opening a terminal window and typing 'glxinfo' should show something like 'Direct rendering: Enabled' at the top of the page. This means that Direct Rendering is enabled, which should improve performance.

Honestly though, the Intel graphics cards are horrible, you shouldn't expect much from them...
Thanks for the tips. I tried all that just now, but when I typed in "glxinfo" it said, "Direct rendering: No".

Hmm.

---

