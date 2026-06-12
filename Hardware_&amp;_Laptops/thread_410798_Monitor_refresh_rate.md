---
title: "Monitor refresh rate"
date: 2007-04-16
forum: Hardware &amp; Laptops
---

### Post by william_nbg on 2007-04-16
Can't seem to raise my refresh rate on my monitor.

Even stuck in a custom modeline

would like 75 but it's stuck at 60

from xorg.conf

Section "Monitor"
    Identifier     "Eizo F77"
    HorizSync       30.0 - 95.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
    # V-freq: 75.00 Hz  // h-freq: 80.42 KHz
    Modeline "1280x1024" 151.83  1280 1360 1544 1888  1024 1024 1027 1072 	
EndSection

Any ideas

---

### Post by william_nbg on 2007-04-16
Bump!!!!

One more question.

Would I have to block the:

HorizSync 30.0 - 95.0
VertRefresh 50.0 - 160.0

for the modeline to function???

---

### Post by earobinson on 2007-04-16
I dont think so, are you sure that resoultion is supported by your monitor?

---

### Post by william_nbg on 2007-04-16
Well, according to a quick google search it is.

I have an Eizo F77

---

### Post by Erlander on 2007-04-17
If it is an NVidia display card try running:

```
nvidia-settings
```

It solved my refresh rate problems.

Rob

---

### Post by Wim Sturkenboom on 2007-04-17
Check if it is solved if you add the line below to the device section in you x configuration
```

Option       "UseEdidFreqs" "False"

```
My nvidia card refused to go over 75Hz and the above solved the issue.

---

### Post by william_nbg on 2007-04-17
Yeap! That was it.

Adding "Option       UseEdidFreqs" "False"
to device section. And changing the res' in screen section :

from - "1280x1024"

to - "1280x1024_75"

Also, I took the modeline out

---

