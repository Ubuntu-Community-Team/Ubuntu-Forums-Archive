---
title: "My own keyboard layout - Caps Lock"
date: 2023-07-31
forum: Hardware
---

### Post by borucki-andrzej on 2023-07-31
I am using Polish layout.
Is possible modify definitions of keys?
My Caps Lock often turn on  accidentally when I want press Tab or Shift but press Caps Lock.
I want turn Caps Lock only when I press Caps Lock and Alt (maybe Control or Shift)

---

### Post by him610 on 2023-07-31
I am unfamiliar with a Polish keyboard, but I have been frustrated by accidently pressing the Caps Lock when I originally intended to press the Shift or Tab key.
I found this in my notes where I swapped the Caps Lock key with the Esc key. Maybe you can use this to start.
> # Keyboard tips
Swap keys, Caps Lock with Escape
Edit /etc/default/keyboard
change the line 
XKBOPTIONS=""
to read 
XKBOPTIONS="caps:swapescape"
save the file
reboot
test the newly reassigned keys


---

### Post by borucki-andrzej on 2023-08-09
I search XKBOPTIONS
and found [https://wiki.archlinux.org/title/Xorg/Keyboard_configuration](https://wiki.archlinux.org/title/Xorg/Keyboard_configuration)

---

