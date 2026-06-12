---
title: "DisplayLink Issue - Low Graphics Mode"
date: 2018-02-14
forum: Hardware
---

### Post by hectospark on 2018-02-14
Hello Guys,

I have recently installed the drivers for displaylink onto my Ubuntu 16.04 LTS (the only version i could get drivers to work with). I have now encountered an issue. On startup if I have the displaylink plugged in it comes up with low graphics mode with the displaylink not displaying anything. My work around is to unplug it and plug it back in. Then I have to reset how I have my displays setup everytime. 

Does anyone know either:
A - How to fix the low graphics mode on startup
B - How to create a script to click to reset how displays are setup.

Thanks a million,
Alex

---

### Post by cruzer001 on 2018-02-14
Boot with the displaylink plugged in and run this command:

```
xrandr
```

Please post the output.

---

