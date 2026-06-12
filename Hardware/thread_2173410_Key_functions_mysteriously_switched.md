---
title: "Key functions mysteriously switched"
date: 2013-09-09
forum: Hardware
---

### Post by Pramita on 2013-09-09
The " and @ keys on my Dell laptop have mysteriously switched functions. They continue to work as before for the number 2 and single quotation mark, but the double quotation mark and @ functions have been switched. Also, the hash key, though still a functioning number 3, gives me a £ sign instead of a hash sign. I suspect it's a hardware problem, but I can't be sure of this. Any help would be much appreciated. Thanks in advance.

---

### Post by sudodus on 2013-09-09
Welcome to the Ubuntu Forums :-)

I suspect you have another keyboard setting (for example another language). What is the output of the following command in a terminal window?

```
setxkbmap -print
```

---

### Post by coffeecat on 2013-09-09
What you describe sounds like the UK layout. In UK keyboards, " is shift-2, @ is shift-', £ is shift-3, and # is just to the left of the return key.

Which desktop are you using? If Unity, see what your default is in System settings -> Keyboard layout.

---

### Post by Pramita on 2013-09-09
The output is

xkb_keymap {
    xkb_keycodes  { include "evdev+aliases(qwerty)"    };
    xkb_types     { include "complete"    };
    xkb_compat    { include "complete"    };
    xkb_symbols   { include "pc+gb+inet(evdev)"    };
    xkb_geometry  { include "pc(pc105)"    };
};

I'm a newbie, so I have absolutely no idea what this means.

---

### Post by Pramita on 2013-09-09
> **coffeecat said:**
> What you describe sounds like the UK layout. In UK keyboards, " is shift-2, @ is shift-', £ is shift-3, and # is just to the left of the return key.

Which desktop are you using? If Unity, see what your default is in System settings -> Keyboard layout.

I checked -- my default is indeed English (UK). However, I have no idea how this switch happened (I am assuming I had the US layout earlier). Strange!

---

### Post by sudodus on 2013-09-09
You can change back to US English keyboard with
```
setxkbmap us
```
in a terminal window.

---

### Post by coffeecat on 2013-09-09
Or if you prefer the GUI, simply System Settings -> Keyboard Layout and change the default to whichever layout you wish. :)

---

### Post by Pramita on 2013-09-09
> **sudodus said:**
> You can change back to US English keyboard with
```
setxkbmap us
```
in a terminal window.

Worked. Thanks a lot! :D

---

### Post by Pramita on 2013-09-09
> **coffeecat said:**
> Or if you prefer the GUI, simply System Settings -> Keyboard Layout and change the default to whichever layout you wish. :)

Thank you! :) Phew, I was a bit worried initially, but a simple enough solution!

---

