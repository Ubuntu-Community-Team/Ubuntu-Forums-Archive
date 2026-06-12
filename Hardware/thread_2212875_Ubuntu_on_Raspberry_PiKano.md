---
title: "Ubuntu on Raspberry Pi/Kano?"
date: 2014-03-23
forum: Hardware
---

### Post by lorcastrand on 2014-03-23
I'm planning on getting a [Kano]("http://www.kano.me/") computer kit later this year, upon its release. I plan to hack it with a touchscreen to spawn a one-of-a-kind "KanoPad". Have any of you had any experience with Ubuntu on Rasbperry Pi/Kano? Will this work?

---

### Post by Kirboosy on 2014-03-24
Of course it will work but it just a matter of how much time you are willing to invest in it. I'm sure Kano OS is a Debian derivative so you might not get many benefits by putting Ubuntu on it. I would run with Kano OS first and see if you can modify it to fit your needs. That way you can stay as close to original product plus a few features. 

Hope that helps!
~Caboose

---

### Post by efflandt on 2014-03-24
The Raspberry Pi has an older ARM cpu that will not run Intel like operating systems, so it will not run Ubuntu out of the box. It typically runs a special Debian wheezy version called Raspbian booted from SD card using lxde desktop. Although, since Ubuntu is Debian based, you should be able to find your way around it easily and install packages if you know how to use apt-get (or get some practice with Lubuntu). Default browser Midori is not the best, but you can use iceweasel (a mozilla slimmer than firefox) or chromium browser.

There are some other operating systems too, like a couple of versions of Linux based XBMC (RaspBMC or OpenELEC), Pidora (maybe related to fidora), Arch Linux, or RISC OS. See[URL="http://www.raspberrypi.org/downloads"] [http://www.raspberrypi.org/downloads](http://www.raspberrypi.org/downloads)
[/URL]
You can try different systems on different SD cards. I set one up to autologin and run Quake III right from boot.

---

### Post by Iowan on 2014-03-24
My Raspberry Pi is sluggish enough with Raspbian. 
I also have a minimal system set up with Arch for playing with GPIO and Python.

---

### Post by lorcastrand on 2014-03-28
Thank you very much everybody for all the help! I might try ArchOS, I've seen a lot of Pis running that. Would it support a touchscreen?

---

### Post by Kirboosy on 2014-04-01
Arch would most likely support a touchscreen but I'm not sure how much effort and tweaking it would take for it to work properly.

---

### Post by lorcastrand on 2014-04-25
Thank you everyone for your help! I did a little research myself, and someone, somewhere, seems to be running every imaginable OS on their Pi. But I think I'll stay with ArchOS. Or, has anybody had any experience with KanoOS?

---

