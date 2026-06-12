---
title: "Logitech Cordless Desktop Wave - All keys work with HIDPoint"
date: 2009-03-04
forum: Hardware
---

### Post by vprasaj on 2009-03-04
Hi all.

I was looking to make all extra keys working on my wave keyboard. I saw that no solution was posted yet.

You can enable and configure all keys with [_HIDPoint_]("http://www.hidpoint.com/"). (Page is slow. Be patient.) It supports many Logitech keyboards and mices.

What you need to do is just download bin file, make it executable with

```
chmod +x hidpoint1-0.bin
```

and then you simply run it

```
sudo ./hidpoint1-0.bin
```

You get nice GUI installer. Follow the steps. After installation reboot the system. (Logout or ctrl+alt+backspace (x restart) didn't work for me. Reboot did.)

After reboot you get one icon in panel. From there you can simply configure your extra keys with a nice GUI.

[[img]http://www.shrani.si/t/u/mg/4yuJdFEp/hidpoint-configuration.jpg[/img]](http://www.shrani.si/?u/mg/4yuJdFEp/hidpoint-configuration.png)

[[img]http://www.shrani.si/t/3N/MW/106VXZZv/hidpoint-configuration1.jpg[/img]](http://www.shrani.si/?3N/MW/106VXZZv/hidpoint-configuration1.png)

[[img]http://www.shrani.si/t/3J/A5/4fzP7RIk/hidpoint-configuration2.jpg[/img]](http://www.shrani.si/?3J/A5/4fzP7RIk/hidpoint-configuration2.png)

BTW: Mice middle click is called wheel button.

Cheers. ;)

---

### Post by etnlIcarus on 2009-03-13
I've got the exact same keyboard and mouse combo as you: Wave cordless w/ bundled LX8 Laser mouse.

Mouse dropdown didn't list the LX8 **Laser**, only the optical model but I figure it shouldn't make a difference.

[img]http://img13.imageshack.us/img13/1173/screenshot2b.png[/img]

What am I doing wrong?

Also, were you getting this with your mouse?

[img]http://img13.imageshack.us/img13/8374/screenshot1mit.png[/img]

---

### Post by etnlIcarus on 2009-03-14
Well got the HIDPoint drivers working but wasn't very impressed. Mouse latency seemed worse - regardless of where i set acceleration, horizontal scrolling was still sucky and I could no longer assign the side mouse buttons to expo/shift switcher in Compiz. Have uninstalled them. Will be doing a fresh install just as soon as 9.04 goes beta and I get another HDD so hopefully HAL's autodetection has improved by then.

---

### Post by NavyJoe on 2009-03-15
NEVER MIND!

also cant get it to recognize my keyboard/mouse ex110 combo.  It's been fixed now. Thanks anyway.

---

