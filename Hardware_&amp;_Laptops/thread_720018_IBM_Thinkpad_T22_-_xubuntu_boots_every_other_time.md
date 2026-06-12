---
title: "IBM Thinkpad T22 - xubuntu boots every other time"
date: 2008-03-09
forum: Hardware &amp; Laptops
---

### Post by metro2003 on 2008-03-09
Hi,

I successfully installed Xubuntu (latest version) on my laptop.  Everything is working fine, however, I have a small issue. My laptop boots into Xubuntu every other time. Without fail !!  I start up the laptop  and it hangs. I force a shutdown by holding the power button and boot again.  It then works.  has anyone any idea what could be wrong?  When in log in, everything works just fine. it's not an issue but more of an annoyance.

system:
IBM Thinkpad T22 - P3 800Mhz, 256MB ram
dual boot. I have windows XP as well
wireless network, Netgeat WG511t card
S3 Savage video card - a whooping 8MB of RAM

thanks.

-m

---

### Post by tgalati4 on 2008-03-09
You're not playing games on that bad boy.  Hit Alt-F1 during boot up to see messages.  Is it at least booting to the GRUB menu?

Go into the BIOS and check the boot order.  Remove the CD and Floppy from the boot order.

---

### Post by metro2003 on 2008-03-10
hi,

thanks for response tgalati4.

ok, the laptop does boot into grub and I see all the selections.  I use the standard boot which is the first selection into xubuntu.  XP is last.  I went into the bios and disabled the other boot options.

I then hit ALT+F1 and looked at the messages. nothing stood out. it all went [OK] and all the drivers are loaded, and right before the main loging screen supposed to come on, that's where it hangs.  

strange !!

---

### Post by ted209 on 2008-05-11
Hi, I had the same problem a while ago. This is how I fixed it:


I followed instructions here:

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T20#Ubuntu_8.04_Hardy_Heron](http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T20#Ubuntu_8.04_Hardy_Heron)

This was to fix 3d graphics acceleration which was not working. I believe I didn't have to change any of my configuration, but I did have to do this:

Make sure the package libgl1-mesa-dri is installed

Now 3d acceleration works and my laptop ALWAYS boots!

Ed

---

### Post by mr_brefast on 2008-05-11
> **ted209 said:**
> Hi, I had the same problem a while ago. This is how I fixed it:


I followed instructions here:

[http://www.thinkwiki.org/wiki/Instal...a_ThinkPad_T20](http://www.thinkwiki.org/wiki/Instal...a_ThinkPad_T20)

This was to fix 3d graphics acceleration which was not working. I believe I didn't have to change any of my configuration, but I did have to do this:

Make sure the package libgl1-mesa-dri is installed

Now 3d acceleration works and my laptop ALWAYS boots!

Ed


I sent you a PM, don't know if I was clear in it, so I figured I would do my first post here.  I definitely haven't had too many problems getting the same machine mentioned by the OP running Xubuntu 8.04 - works like a charm.

And, although it won't be the best experience, I am trying to get Warcraft III to run on this machine.  I currently get a whopping 6 frames per second, a la no 3D accelerator working.  I hope that you can repost that link you put up - it didn't work for me Ed.

Thanks, and I will advise here if I get it working.

-Mike

**EDIT**

I found the link, and got this monster of a machine working - Warcraft III does interesting things, and is unplayable, but thats ok - I quitupled my framerate in general   :)

Link for those who need it:
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T20#Ubuntu_8.04_Hardy_Heron](http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T20#Ubuntu_8.04_Hardy_Heron)

---

