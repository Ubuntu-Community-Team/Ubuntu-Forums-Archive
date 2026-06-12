---
title: "MS Ergonomic keyboard 4000"
date: 2006-06-29
forum: Hardware &amp; Laptops
---

### Post by emil.s on 2006-06-29
All "normal" keys are working perfect. But as you see, it's some multimedia keys, and special keys.
And a "zoom wheel"
[http://www.activewin.com/reviews/hardware/keyboards/ms/nec4000/loresproduct1.jpg](http://www.activewin.com/reviews/hardware/keyboards/ms/nec4000/loresproduct1.jpg)

Some of the extra buttons are working. The "Web/home", "Search", "Mail" and the "Calculator" button working.
And the multimedia control.
But none of the 1-5 buttons, not the zoom wheel, and the "My favorites" button are working.

I get nothing in dmesg, and nothing in syslog. :roll: 
"xev" gives nothing.
The buttons are working in Windows, so they are alive.

I have no ideas about whath to do. :( 

Swedish users can take a look here:
[http://bbs.linux.se/viewtopic.php?t=29977](http://bbs.linux.se/viewtopic.php?t=29977)

---

### Post by degel3030 on 2006-06-30
i just bought this keyboard today, although i havent tested mine in winders, i have the same situation, would like the zoom to work, others i could care less

---

### Post by vigleik on 2006-06-30
I also have a keyboard with extra keys, and I use a little program called xbindkeys to customize the extra buttons. Install xbindkeys and xbindkeys-config (with apt-get) and run xbindkeys-config. As long as the linux kernel registers the keypresses, you can customize it to run any command when you press a key. Once you're done customizing, have xbindkeys start automatically when you log in, and everything should work seamlessly.

Here's a little sample of my .xbindkeysrc config file:

#Play/pause in xmms
"xmms -p &"
    m:0x0 + c:129 #This is the play/pause button
    NoSymbol

#Increase volume
"aumix -v +2"
    m:0x0 + c:176 #This is the volume key, turned clockwise
    NoSymbol

Of course you don't have to edit this file manually. The hardest part is actually figuring out the exact commands for doing the things you want your extra keys to do.

Vigleik

---

### Post by emil.s on 2006-07-01
I already use "xbindkeys" for the buttons who works. But read what i have wrote. 
"xev" gives nothing. So xbindkeys is not working. ;-)

---

### Post by vigleik on 2006-07-01
Sorry, I overlooked your little xev comment. And I agree, if xev isn't registering the keypresses then there is no easy fix. At least none that I can think of. It's very weird though.

Vigleik

---

### Post by emil.s on 2006-07-02
I have an idea!
A have read a little about the "evdev" driver. I use it for my MX1000 mouse.
But i have read, it's possible to use it for the keyboart to. :)

I tried to change to "evdev" as driver in xorg.conf, but X craches on start.

How shall i change in xorg.conf to get it work?

```
Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "se"
EndSection
```

---

### Post by emil.s on 2006-07-09
Please! [-o<

---

