---
title: "how to enable automatic hardware disabling"
date: 2008-05-16
forum: Hardware
---

### Post by MaxIBoy on 2008-05-16
Ubuntu 8.04 runs like a dream on my laptop, very few complaints, even with all the compiz fusion effects on a crappy Intel chipset, but a major issue is that hardware isn't automatically disabled:
[LIST]
[*]headphones don't disable speakers, I have to do it in alsamixer
[*]closing the laptop doesn't disable plugged in mice or plugged in keyboards
[*]plugged in mouse doesn't disable touchpad
[*]typing doesn't disable touchpad (a feature I've seen on Ubuntu but never been able to find)
[/LIST]

Is there a way to enable that?

---

### Post by ryanhaigh on 2008-05-16
[http://www.ubuntugeek.com/disable-synaptics-touchpad-while-typing-in-ubuntu.html](http://www.ubuntugeek.com/disable-synaptics-touchpad-while-typing-in-ubuntu.html)

[http://linuxtidbits.wordpress.com/2007/10/27/switch-automatically-mouse-and-touchpad/](http://linuxtidbits.wordpress.com/2007/10/27/switch-automatically-mouse-and-touchpad/)

For sound Im pretty sure thats an alsa configuration issue. No idea about the lid closing, the usb is probably kept active because you may be using a usb disk or something, there may be a way to check whether a device is mouse/kb and disable that using the relevant acpi event script in /etc/acpi/events, see [here for more info]("http://www.thinkwiki.org/wiki/How_to_configure_acpid").

---

### Post by MaxIBoy on 2008-05-16
Actually, there's only been a flash drive in there once. I haven't needed it since I got the laptop.


As for the touchpad thingy, it worked, but it also put me in low graphics mode. Screen resolution is normal, but all my eye candy is gone. The compizconfig settings are still there, but they aren't being applied. I will try a full restart instead of a gui restart, see if that fixes it.

---

### Post by MaxIBoy on 2008-05-16
Okay, a friend of mine pointed out the problem. I copied and pasted the command from the website. As it turned out, curved quotes are a different character than straight quotes. Xorg.conf wanted straight quotes. I think you can guess the rest.

---

