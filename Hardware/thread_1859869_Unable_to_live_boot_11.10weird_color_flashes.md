---
title: "Unable to live boot 11.10/weird color flashes"
date: 2011-10-14
forum: Hardware
---

### Post by CHAORAIN on 2011-10-14
I am unable to live boot 11.10 on my Dell XPS M1730. I downloaded and burned the disk on Win 7, I was planning on reformatting my Ubuntu partition (I messed up some drivers).

When I try to load the live boot I get to the purple screen with "keyboard = person in circle" Then the screen starts flash red, green, blue and white slowly, about 1 second per color. If I wait long enough I hear the log on screen sound effect.

Any ideas on how to get 11.10 to live boot?

P.S.
11.04 was working fine until I messed it up.

---

### Post by Sunsp0t on 2011-10-15
I usually don't post, but saw yours and thought to hop in and respond that you aren't alone. I also have an M1730 and the identical thing is happening to me. I'm sure its an Nvidia driver issue as it craps out right where Plymouth should be. I"m currently downloading the Alternate CD to install without a graphical installer.

---

### Post by Sunsp0t on 2011-10-15
Okay, here's the issue. The default drivers are somehow incompatible with the M1730's screen. I was able to install 11.10 by hooking up an external monitor and using the Alternate CD. Since the Alternate CD uses a text-based installer, the installation works perfectly fine on the laptop's screen. Upon reboot after installation, you'll see the Ubuntu login screen on your external monitor while the laptop screen will flash those colors. Simply log-in to Ubuntu and install the proprietary Nvidia drivers by click on the gear/wrench Icon in the Unity taskbar and then clicking on "Additional Drivers". Choose Nvidia's current drivers (the ones that say "Recommended") and install. Reboot and you'll be greeted with the Login Screen on the M1730's screen.

Hope this helps.

---

### Post by CHAORAIN on 2011-10-17
Thanks for the help. I found that just hooking up another monitor and using the normal install disc worked.

The monitor on my laptop still flashed those colors, forgot to mention it also flashed black. But my secondary monitor worked perfectly.

Is there someplace I should report this bug?

---

### Post by Tuinhark on 2011-10-22
Just wanted to let the world (or anyone who can fix* this) that I have the same problem when using the Ubuntu 11.10 Live CD.

I assume the above work-around will work for me too (I too use a Dell XPS M1730), but unfortunately I cannot test that work-around yet.

* As far as I'm concerned the Live CD needs "fixing", seeing that it doesn't work for my system by default, whereas the previous version (11.04) did.

---

### Post by RezoApio on 2011-11-17
Thanks guys !!!! Cannot test right now as I am at work but I have no doubt either the external monitor or the alternate cd will work !!

BIG THUMBS UP !!!

---

