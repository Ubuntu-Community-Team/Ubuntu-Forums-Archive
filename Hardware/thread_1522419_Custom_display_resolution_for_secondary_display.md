---
title: "Custom display resolution for secondary display?"
date: 2010-07-02
forum: Hardware
---

### Post by e_torano on 2010-07-02
Today, I decided to hook up my old LCD TV as a secondary screen for my laptop via HDMI. However, the TV has an odd resolution of 1440x900 (which, obviously, wasn't a resolution option int he display manager).

Therefore, I tried running

```

xrandr --addmode HDMI1 1440x900
xrandr --output HDMI1 --mode 1440x900

```

via the terminal. But, I just received the following error:

```
xrandr: cannot find mode "1440x900"
```


I've also tried looking for me ~/.xprofile but to no avail.

I'm currently running Ubuntu 10.04. There are plenty of tutorials backdated to 2007 etc, but I can't find any working information for the current version - any help would be much appreciated! ;)

---

### Post by clrg on 2010-07-02
1440x900 is not that odd, my 14" ThinkPad has that resolution. 

Does xrandr (without arguments) show 1440x900 as a possible resolution for your external display?

---

### Post by e_torano on 2010-07-02
No, it does not unfortunately D:

---

### Post by clrg on 2010-07-02
In this case, either your display or your graphics driver don't support the desired resolution. Do you have the latest drivers for your graphics card, and are you sure the display supports 1440x900?

---

### Post by e_torano on 2010-07-02
Yeah, I use the Ubuntu drivers rather than the propietary nvidia drivers though, so that might be the problem. The resolution is definitely right - I just checked the manual and it states it as the maximum. 

Could the problem be due to the fact I'm using HDMI?

---

### Post by clrg on 2010-07-02
I don't think so, HDMI supports very high resolutions. I'm sorry, I can't help you further.

---

### Post by e_torano on 2010-07-03
Ah right, no problem. I just tried using 1280x720 and though it works, it isn't quite right due to black borders >.>

---

