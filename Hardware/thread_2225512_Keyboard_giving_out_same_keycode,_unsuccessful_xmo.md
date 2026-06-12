---
title: "Keyboard giving out same keycode, unsuccessful xmodmap"
date: 2014-05-21
forum: Hardware
---

### Post by fio2 on 2014-05-21
Hi,

I am new to the forums. I would like to thank everyone that participates in advance.

I have been using Ubuntu for some years, but it is the first time I do so with a USB backlit keyboard. I ignore if using a PS/2 adaptor could damage my computer or keyboard given the energy required for the backlighting, so I have not tried that yet (awaiting vendor support on that issue). My current Ubuntu version is Ubuntu 12.04 Precise 64-bit.The keyboard model is BG N8HAWK, 105 keys, Spanish International distribution and it works on Window$. When I try to use it in Ubuntu, the Caps Lock key works but won't light up its corresponding led, and most importantly, the CTRL key is recognized as a shift key. I also do not have the ALT GR key working. 

**I did a thorough search and found similar posts, but neither of the solutions posted in any of them worked out for me**. I am also new at using xmodmap and other keyboard utilities so I know it is likely that I am just doing something wrong. So far I have tried xev, xmodmap, 
sudo dpkg-reconfigure keyboard-configuration

Any suggestions?

Any pointers will be much appreciated.

---

### Post by salure2 on 2014-09-02
Hi ;)

I have the very same problem, Did you already solve it?

---

### Post by Roger Abella on 2014-10-15
Same keyboard, same problem...

---

### Post by jeremy31 on 2014-10-16
Getting the same keycode from what?  Have you tried CTRL+ALT+F1 to enter tty1 and use ```
showkey
``` to see the keycode.  CTRL+ALT+F7 or F8 will usually get you back to Unity or whatever DE you might have

---

### Post by Roger Abella on 2015-02-02
> **jeremy31 said:**
> Getting the same keycode from what?  Have you tried CTRL+ALT+F1 to enter tty1 and use ```
showkey
``` to see the keycode.  CTRL+ALT+F7 or F8 will usually get you back to Unity or whatever DE you might have

Yes ,I did it, and : left shift, left Ctrl, windows key, Alt key, ALtGr key, right Ctrl and right Shift give the same code: 42.

the most incredible is that in windows works fine.

.....

---

