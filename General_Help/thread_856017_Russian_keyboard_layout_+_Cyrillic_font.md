---
title: "Russian keyboard layout + Cyrillic font?"
date: 2008-07-11
forum: General Help
---

### Post by HarvesterOfBeer on 2008-07-11
I've got 8.04 x86 Desktop installed...replacing XP on my wife's machine. Woo! In general, it's fine, but one thing she needs for school is to be able to work in Russian. 

On XP, once I turned on the Russian layout, she could just hit the hotkey (Alt+Shift?), and flip between US and RU layouts + fonts. Hit the hotkey and she'd be typing using the Russian keyboard layout and the characters on the screen would be in the correct Cyrillic font. 

Would somebody please point me to how to accomplish the same thing in Ubuntu? I've got the Russian language packages installed, and the Russian layout enabled, but switching the layout doesn't switch the font.

Urk! I don't want to go back to Windows!

Thanks.

-HoB

---

### Post by mybeat on 2008-07-11
If you are using gnome, I think you can add a keyboard notificator to panel and configure it from there. Havent used gnome in a while so i cant remember.

There's another way to do this.
Open xorg.conf and add 2 lines under Section "InputDevice"
```

 Option    "XkbLayout" "us,ru"
 Option    "XkbOptions" "grp:alt_shift_toggle" 
```
Then restart xserver by pressing ctrl+alt+backspace and it should work, by pressing alt+shift.

---

### Post by soul_ache on 2009-02-16
> **mybeat said:**
> If you are using gnome, I think you can add a keyboard notificator to panel and configure it from there. Havent used gnome in a while so i cant remember.

There's another way to do this.
Open xorg.conf and add 2 lines under Section "InputDevice"
```

 Option    "XkbLayout" "us,ru"
 Option    "XkbOptions" "grp:alt_shift_toggle" 
```
Then restart xserver by pressing ctrl+alt+backspace and it should work, by pressing alt+shift.


Thank you for that!
Simple and works!

---

### Post by pvsavola on 2009-02-28
There is also GUI for that: System-Preferences-Keyboard -- Layouts-LayoutOptions and there "Key(s) to change layout", select alt+shift (or other more suitable).

For whatever reason the default 2xAlt didn't work for me.

---

### Post by kwv43 on 2009-04-25
**I have a Toshiba netbook purchased in Moscow.  sing alt + shift  toggles Russian/English.**

---

### Post by zivrozz on 2009-12-07
Check this tool: Russian Virtual keyboard [http://keyboard.erozz.com/ru](http://keyboard.erozz.com/ru)

I hope this would help..

---

