---
title: "Asus G53 Screen Brightness"
date: 2011-02-28
forum: Hardware
---

### Post by fragviper1 on 2011-02-28
Hi, I've never used Linux or Ubuntu before, but have recently installed the OS on my computer to tinker around on.

I've done some google searching for this solution but can't seem to figure out how to fix my problem.

I have an ASUS G53JW laptop, which has a Nvidia GTX 460m. Fn+F5 or Fn+F6 doesn't actually change my screen brightness. Also Fn+F3 and Fn+F4 doesn't change the keyboard brightness.

If anyone could give a noob some detailed instructions that would be awesome! I really want to use Linux as my main OS, but these problems don't make it very practical for me to use my computer away from a wall plug or any time at night.

Thanks,

---

### Post by adrian_n9 on 2011-03-15
I'm having the exact same problem. I've tried xbacklight and tinkering with the /etc/acpi/asus-brn-down.sh and up.sh but to no avail.

So far I've reverted to using the nVidia XServer Settings to adjust the brightness levels just to keep my eyes from burning up.

---

### Post by Brokensoul on 2011-04-20
just add 
"
        Option "RegistryDwords" "EnableBrightnessControl=1"
"
in your /etc/X11/xorg.conf device section, and that should work (edit with "sudo nano /etc/X11/xorg.conf" for example)
I have a G53 myself, that's ok now. Still looking for the backlit keyboard though..

---

### Post by adrian_n9 on 2011-08-12
Keyboard backlight script is here:
[https://launchpad.net/asus-keyboard-backlight](https://launchpad.net/asus-keyboard-backlight)

---

### Post by gillza on 2011-10-05
> **adrian_n9 said:**
> Keyboard backlight script is here:
[https://launchpad.net/asus-keyboard-backlight](https://launchpad.net/asus-keyboard-backlight)

Thank you for the link. This solved my keyboard backlight issue on G53SX-A1!

---

### Post by aws910 on 2012-01-07
> **Brokensoul said:**
> just add 
"
        Option "RegistryDwords" "EnableBrightnessControl=1"
"
in your /etc/X11/xorg.conf device section, and that should work (edit with "sudo nano /etc/X11/xorg.conf" for example)
I have a G53 myself, that's ok now. Still looking for the backlit keyboard though..

I had been looking for a solution to this for weeks!  Thank you!

---

### Post by sklein35 on 2012-01-18
> **Brokensoul said:**
> just add 
"
        Option "RegistryDwords" "EnableBrightnessControl=1"
"
in your /etc/X11/xorg.conf device section, and that should work (edit with "sudo nano /etc/X11/xorg.conf" for example)
I have a G53 myself, that's ok now. Still looking for the backlit keyboard though..
I'm also very new at this and while appreciate your explanation I was wondering if you could explain further for me? I also have an Asus G53SX and would like to know how to get the fn keys to work with the brightness, also with the backlit keyboard if possible. I'd greatly appreciate any further details, thanks!

---

### Post by gillza on 2012-01-18
> I'm also very new at this and while appreciate your explanation I was wondering if you could explain further for me? I also have an Asus G53SX and would like to know how to get the fn keys to work with the brightness, also with the backlit keyboard if possible. I'd greatly appreciate any further details, thanks!

For the future [www.googlubuntu.com](www.googlubuntu.com) is your best friend and for now to answer your questions look at my signature.

P.S. Did it help?

---

### Post by a12jun on 2012-01-22
I have an Asus G53 SW and was searching around for a long time for solutions to keyboard brightness on Ubuntu 11.04.  This was the closest I found: [http://www.blog.project13.pl/index.php/fun/1163/g73-keayboard-backlight-scripts/](http://www.blog.project13.pl/index.php/fun/1163/g73-keayboard-backlight-scripts/)

I never did get it working on Ubuntu but I recently switched to ArchBang linux (an augmented version of Arch linux) and those scripts in the link above worked a treat.  I'm still playing with getting the maximum brightness to it's full level as it only currently goes up one notch, but it's still a darn sight better than not at all.  Ktoso, the guy who runs the site, is a very helpful guy, he happily answered all of my questions.

---

