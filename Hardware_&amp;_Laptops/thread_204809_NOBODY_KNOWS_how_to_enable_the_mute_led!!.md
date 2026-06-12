---
title: "NOBODY KNOWS how to enable the mute led!!"
date: 2006-06-27
forum: Hardware &amp; Laptops
---

### Post by yotamkr on 2006-06-27
Its not the first time that i or someone asks this question but somehow i still didnt find a good answer...
I have an HP ze2000 laptop and there is a Mute button which works, but the orange LED dosent light while the computer is muted (as in the Windows XP)....
any ideas??? is it simply impossible???

---

### Post by Hellkeepa on 2006-06-27
HELLo!

It is possible, and quite easy once you figure out what "file" to alter. Though you'll probably spent a lot of time searcing around to find it, unless someone knows the structure of the "modprobe" entry for your laptop.

To give you an idea on what must be done, you can read this post. It details the process to turn on the WiFi led on an IPW2200 chip.
[http://ubuntuforums.org/showpost.php?p=545771&postcount=26](http://ubuntuforums.org/showpost.php?p=545771&postcount=26)

Happy codin'!

---

### Post by yotamkr on 2006-06-27
thanks for the reply, but... well, i have done it with the Wireless Led and it works, but i still have no idea how to find the mute led file in my system... i have an HPze2000...

---

### Post by yotamkr on 2006-07-21
bulp

---

### Post by acojlo on 2006-07-22
> **yotamkr said:**
> Its not the first time that i or someone asks this question but somehow i still didnt find a good answer...
I have an HP ze2000 laptop and there is a Mute button which works, but the orange LED dosent light while the computer is muted (as in the Windows XP)....
any ideas??? is it simply impossible???

There should be some files at /sys/ directory structure which corellate to your's laptop leds. Those files are interfaces to hardware infrastructure saw by kernel. By issuing, for example, "echo ON > /sys/devices/system/mute_led" you should turn on led. This is just a direction to where you should look for a solution. I have different problems on my laptop :).

Sometimes because of this problems I think about linux in ubuntu as something in beta stage :)

---

### Post by yotamkr on 2006-08-24
someone???

---

### Post by muganor on 2007-12-20
Look at : [https://bugs.launchpad.net/ubuntu/+source/module-init-tools/+bug/124331](https://bugs.launchpad.net/ubuntu/+source/module-init-tools/+bug/124331)

It shows how to enable the mute led on two laptops, with different sound modules.

You may execute "lsmod | grep snd" to figure what is your sound module and patch the "options ... ac97_quirk=7" line with the appropriate module.

---

