---
title: "Can't scroll in virtual consoles (tty) on an ASUS N580GD"
date: 2018-11-26
forum: Hardware
---

### Post by El Potro on 2018-11-26
Hello dear Ubuntu community,

This computer isn't easy to set up, I can tell you...
I'm doing some tests with Ubuntu 18.10

I can't get it to scroll up/down on virtual consoles (tty1-6) with the laptop's keyboard (it works fine with an external keyboard).

I tried to figure out why the usual combination doesn't work, i.e.: Shift+PgUp, and there may be some "fun" into it. 

I tried reconfiguring keyboard-configuration package
# dpkg-reconfigure keyboard-configuration

It doesn't make any difference what keyboard I choose, I tried:
Asus Laptop
Apple Laptop
Generic 101-key PC
Generic 105-key PC

With numlock off, PgDn shows a tilde, and PgUp enters nothing (not even a space), but the cursor blinks.
Adding Shift doesn't make any difference.

It does scroll in programs like "man"

Maybe I should create my own XkbModel or XkbLayout?

With the X environment I also get some uncomfortable behavior since I can't scroll in xterm. If I press Shift+PgUp(NumLk off) I get a 9. If I press Shift+9(NumLk on) I get "~2".
I can scroll in Konsole, but only with Shift+9(NumLk on).

For what is worth, these are some keycodes I got using showkey:

Laptop keyboard
pgup   = 73
pgdown = 81
lshift = 42
rshift = 54

External KB:
pgup   = 104
pgdown = 109
lshift = 42
rshift = 54

Any help will be greatly appreciated

---

