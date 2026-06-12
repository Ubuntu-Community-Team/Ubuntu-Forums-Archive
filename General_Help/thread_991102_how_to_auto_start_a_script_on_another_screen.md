---
title: "how to auto start a script on another screen"
date: 2008-11-23
forum: General Help
---

### Post by lime4x4 on 2008-11-23
I need to start this conky file automatically on screen 1

conky -c /usr/share/conkyforecast/example/conkyrc &

My main screen is screen 0 my second screen is screen 1

So when i reboot the computer i want that script to run on the second panel

using intrepid running 2 monitors as seperate x screens

---

### Post by Dr Small on 2008-11-23
> **lime4x4 said:**
> I need to start this conky file automatically on screen 1

conky -c /usr/share/conkyforecast/example/conkyrc &

My main screen is screen 0 my second screen is screen 1

So when i reboot the computer i want that script to run on the second panel

using intrepid running 2 monitors as seperate x screens
Try:
```
export DISPLAY=:1 && conky -c /usr/share/conkyforecast/example/conkyrc &
```

---

### Post by sisco311 on 2008-11-23
try:
```
**DISPLAY=:0.1** conky -c /usr/share/conkyforecast/example/conkyrc &
```

---

### Post by Dr Small on 2008-11-23
> **sisco311 said:**
> try:
```
**DISPLAY=:0.1** conky -c /usr/share/conkyforecast/example/conkyrc &
```
Why is the display 0.1? I thought it would have been :1

---

### Post by lime4x4 on 2008-11-23
thanks if i run that command in a terminal it works.
but if i add that command to my start session it doesn't run

---

### Post by sisco311 on 2008-11-23
> **Dr Small said:**
> Why is the display 0.1? I thought it would have been :1

i don't know why, but the DISPLAY variable is set to :0.1 on my second screen.
```
echo $DISPLAY
:0.1
```

---

