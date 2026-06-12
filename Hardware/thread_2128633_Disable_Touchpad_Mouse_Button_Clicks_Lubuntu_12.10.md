---
title: "Disable Touchpad Mouse Button Clicks Lubuntu 12.10 Thinkpad T42"
date: 2013-03-23
forum: Hardware
---

### Post by megrimm on 2013-03-23
Hello,

I have an old t42 thinkpad and the buttons right below the touchpad are broken. I would like the disable just the hardward built in buttons while keeping the touchpad functionality (tap2click, etc).

Optionally, I would like the "enable" the 3 hardware buttons right above the touchpad to take over for the functionality im loosing by disabling the buttons right below the touch pad. These three buttons above the touchpad so not seem to be functioning at the moment.

If there is a way to do this via text file rather than some gui that would be much better...

thanks!
m

---

### Post by ajgreeny on 2013-03-23
Have a look at synclient command which may help you out.
synclient -l will show you the current settings and may give you a clue what to change with command such as ```
synclient TapButton1=0
```

---

