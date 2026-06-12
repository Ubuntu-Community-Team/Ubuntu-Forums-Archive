---
title: "Monitor error during installation"
date: 2005-09-04
forum: Hardware &amp; Laptops
---

### Post by ciproxr on 2005-09-04
Ubuntu launches fine till the the instalation is about to start, i get a blank screen and with an error on my monitor "out of range" and " vga in 720 x 400" I have a 17" neso pixo flat panel .......How can i overcome this ? i looked around the the forum but i found no solution , everyone keeps talking about editing a config file but how am i going to edit that if ubuntu isnt installed yet ? i do have an old crt monitor that i thought of using but , once the installation is done will ubuntu work when gnome boots ?

---

### Post by CheshireCat on 2005-09-05
I'm getting this error as well, is there anything that can be done?

---

### Post by ciproxr on 2005-09-15
bump - can someone please help

---

### Post by blair on 2005-09-15
My experience is that most Linux distros inherently do not like LCD monitors out of the box. One of the reasons you hear so much grumbling about getting Linux installed on laptops is that laptops use LCDs. 

My experience is that simply forcing the vertical refresh rate/refresh frequency to the default monitor value will often cause the other video settings to fall into place nicely. Get out your monitor user manual or pull the specs off the net. Find the "optimum resolution". e.g. 1280x1024 @72Hz. In this example you would force Ubuntu to boot at 72Hz. 

When you boot, auto-hardware detect is used in case you specify otherwise. In your case, autodetect doesn't work. I'm not sure about Ubuntu, but several Knoppix-based distros test the monitor for max resolution, max color bit depth and max refresh rate and then use those. In your case it is out of range. You want to specify video settings, rather than leaving it to Ubuntu to auto detect. 

When you first boot from the install CD, you see the boot prompt. Hit F1 within 10 seconds to see boot options or auto install will begin. F1 brings you to a series of F menus you can explore. 

If you enter "expert" at the boot prompt, it will walk you through your install config options for all hardware including video. This is one option. Another option is to boot into default mode by entering "linux" at the boot prompt, however adding the specific video parameter for the refresh rate, which is vsync, For example boot: linux vsync=72

Ubuntu is Debian-based, so cruise over to the Debian site to learn about boot options:

[http://www.us.debian.org/releases/stable/i386/ch05s01.html.en#id2529073](http://www.us.debian.org/releases/stable/i386/ch05s01.html.en#id2529073)

good luck

---

