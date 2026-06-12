---
title: "help with install drivers dell c840"
date: 2006-06-05
forum: Hardware &amp; Laptops
---

### Post by lugher on 2006-06-05
please someone, :confused: who want to helpme :confused:, well i recently install ubuntu 5.1 on my laptop dell c840, everyting goes fine, until when i saw the LCD display it's 800 x 600 ](*,) and i don't know where i can find the driver, and the modem driver 'cause i need it for a terminal service, is the first time that i install these software, 'cause i really want to leave all software of microsoft:-k , so if any one can helpme i apreciate it verymuch.

thanks....

---

### Post by .t. on 2006-06-05
Don't install 5.10 anymore. Try with Dapper 6.06 - who knows, your problems may be fixed.

---

### Post by lugher on 2006-06-05
hi, thanks i'll try it, but you refer to the new distribution of ubuntu 6.1 cause i'll want to install it, or upgrade, i have the cd, how can upgrade my ubuntu 5.1 without format it fron cero?.... i just want to make the upgrade... help me

---

### Post by geekspeed on 2006-07-04
In your /etc/xorg.conf add this line to the "Default Monitor" section

```

Modeline "1400x1050"  129  1400 1464 1656 1960 1050 1051 1054 1100 +Hsync +Vsync

```

Then add this
```

"1400x1050"

```

to the Modes line in the 24bit depth display subsection.


Then just do a ctrl+[backspace] and you should be back in 1400x1050.

::gS::

---

