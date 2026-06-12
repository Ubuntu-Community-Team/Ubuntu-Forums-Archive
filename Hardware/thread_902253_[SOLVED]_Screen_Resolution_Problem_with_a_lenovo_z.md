---
title: "[SOLVED] Screen Resolution Problem with a lenovo z61m"
date: 2008-08-27
forum: Hardware
---

### Post by ierpe on 2008-08-27
I know this problem has been treated many times, and I have been reading many threads but still can't solve my problem.

I have a laptop Thinkpad z61m 9450-4BG, and the second monitor (wide 22") I am using is a bit awkward. Under windows I have to use a 1600x1200 resolution, and it fits well in width, but in height the desktop is scrolled up&down when I move the mouse up or down, which is actually ok, since it is the best result I could get.

I have seen many xorg.conf, but none is giving a conf for a 1600x1200 resolution, I think ideally this screen would need a 1600x1050 resolution.
Could someone give me the code for such conf?
I tried different confs with different resolutions, but it's whether unstable ,it doesnt fit, or the second screen doesnt start when I apply the changes, and instead of keeping the resolution i selected, the monitor is selected "off"

Could you help me please?

---

### Post by overdrank on 2008-08-27
> **ierpe said:**
> I know this problem has been treated many times, and I have been reading many threads but still can't solve my problem.

I have a laptop Thinkpad z61m 9450-4BG, and the second monitor (wide 22") I am using is a bit awkward. Under windows I have to use a 1600x1200 resolution, and it fits well in width, but in height the desktop is scrolled up&down when I move the mouse up or down, which is actually ok, since it is the best result I could get.

I have seen many xorg.conf, but none is giving a conf for a 1600x1200 resolution, I think ideally this screen would need a 1600x1050 resolution.
Could someone give me the code for such conf?
I tried different confs with different resolutions, but it's whether unstable ,it doesnt fit, or the second screen doesnt start when I apply the changes, and instead of keeping the resolution i selected, the monitor is selected "off"

Could you help me please?

Hi and have you tried the command ```
gksu displayconfig-gtk
``` and adjust there.

---

### Post by ierpe on 2008-08-28
Thx I didnt know this...

So I added the driver for my second screen, but when i test it, both screens (my laptop and my 22" widescreen) go gray/snow, nothing is displayed properly anymore...

I actually faced that problem before with another laptop and never could get it working properly... :/
The ubuntu team needs to do something about it! :p

But so it didnt solve my problem... :/

---

### Post by overdrank on 2008-08-28
> **ierpe said:**
> Thx I didnt know this...

So I added the driver for my second screen, but when i test it, both screens (my laptop and my 22" widescreen) go gray/snow, nothing is displayed properly anymore...

I actually faced that problem before with another laptop and never could get it working properly... :/
The ubuntu team needs to do something about it! :p

But so it didnt solve my problem... :/

Ok I believe the laptop is a ATI graphics correct? Also when I use the test function it shows the snow background but does work in some cases after reboot. I am not saying it will work but you can try and if it fails then you can use the xfix option by booting into recovery mode. If you wan to try :)
Edit there is also the ATI control center but I do not use ATI so I can not help there.

---

### Post by dburnett77 on 2008-08-28
> **ierpe said:**
> I know this problem has been treated many times, and I have been reading many threads but still can't solve my problem.

I have a laptop Thinkpad z61m 9450-4BG, and the second monitor (wide 22") I am using is a bit awkward. Under windows I have to use a 1600x1200 resolution, and it fits well in width, but in height the desktop is scrolled up&down when I move the mouse up or down, which is actually ok, since it is the best result I could get.

I have seen many xorg.conf, but none is giving a conf for a 1600x1200 resolution, I think ideally this screen would need a 1600x1050 resolution.
Could someone give me the code for such conf?
I tried different confs with different resolutions, but it's whether unstable ,it doesnt fit, or the second screen doesnt start when I apply the changes, and instead of keeping the resolution i selected, the monitor is selected "off"

Could you help me please?


Here's a good post with instructions:

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

The modeline reference link should help you with setting the proper resolution in xorg.conf and the instructions on how to edit it are also in this post.

---

### Post by ierpe on 2008-08-28
Ok i got it working! You were right, the test wasnt working properly, but after a restart everything's fine! :)

Thx very much!

---

