---
title: "Latitude CPi-A hotplug probs"
date: 2005-11-03
forum: Hardware &amp; Laptops
---

### Post by hagis on 2005-11-03
Hello dear reader

I have a very old laptop with 5.04 installed. It is a nice OS but I have problems with the hotplug sub system. At launch it hangs every other time, so I start the computer wait for the hotplug hang and then force a restart and then it works.

I have tried installing 5.10 with more problems with hotplug. I had no problems runing Debian stable, Fedora Core 4 and other linux based distros. But I really like Ubuntu.

I have included a dmesg for my data (computer) please help me if you can.

---

### Post by jorgen_s on 2005-11-03
Do you have a NeoMagic sound card?

If so: I think you have the same problem as me and Tsume in this thread:
[http://www.ubuntuforums.org/showthread.php?t=80527](http://www.ubuntuforums.org/showthread.php?t=80527)

I think it's a bug in the ALSA module nm256 and I am thinking about compiling but that's something new for me...
Check out the ALSA link in my post in the thread above.

---

### Post by hagis on 2005-11-03
Yes there is a neomagic card installed in the fantastic datamaskin that i use. I read the thread you refered to. Sounds nice but scary, what will happen when a update comes out for 5.04, will the recompiled driver/module get replaced or? Do you know?

---

### Post by iainm2 on 2005-11-04
Hmmm, yes I had the same problem after upgrading. I have reinstalled Ubuntu Hoary on the Latitude CPi-A and so far the only time it has hung was on the first reboot after installing. So far it has booted up each time ok. I did the install a couple of days ago. My skills are of the noob variety so compiling kernel thingies are a bit out of my depth but I hope that this either helps or encourages anyone reading this. 
BTW - wireless is a snip as I take the latitude from work network connection (wired) to home network (wireless) and it connects. I also have Ubuntu on an Inspiron 3000 which found Gnome too hard to handle but XFCE4 as per the how-to was painless and easy and makes Ubuntu work on a much slower laptop. Just do it!

---

