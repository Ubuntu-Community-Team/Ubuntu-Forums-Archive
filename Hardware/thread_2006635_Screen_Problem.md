---
title: "Screen Problem"
date: 2012-06-19
forum: Hardware
---

### Post by adamgm10 on 2012-06-19
I have a Acer Aspire AO532h thats screen is half broken so when I'm not using my desktop I use the monitor for my netbook. But the problem is whenever I switch displays its fine but I can't type anything because if I do then it switches the display back to the netbook. Can anyone help?

---

### Post by cortman on 2012-06-19
> **adamgm10 said:**
> I have a Acer Aspire AO532h thats screen is half broken so when I'm not using my desktop I use the monitor for my netbook. But the problem is whenever I switch displays its fine but I can't type anything because if I do then it switches the display back to the netbook. Can anyone help?

How are you switching the display? What port are you using (VGA, HDMI, etc.) ?
There's a script available to automatically switch display at startup, if it's plugged in- see [here]("http://cortman.wordpress.com/2012/04/07/cortmans-display-switching-script/").

---

### Post by adamgm10 on 2012-06-19
> **cortman said:**
> How are you switching the display? What port are you using (VGA, HDMI, etc.) ?
There's a script available to automatically switch display at startup, if it's plugged in- see [here]("http://cortman.wordpress.com/2012/04/07/cortmans-display-switching-script/").

It's VGA and thank you I'll try the script later.

---

### Post by cortman on 2012-06-19
If you use the script be sure to substitute VGA1 for HDMI1 wherever it uses the latter.
You can test it quickly by running

```
xrandr --output VGA1 --primary
```

---

