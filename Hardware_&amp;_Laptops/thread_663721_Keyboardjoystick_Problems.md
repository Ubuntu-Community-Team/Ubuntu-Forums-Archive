---
title: "Keyboard/joystick Problems"
date: 2008-01-10
forum: Hardware &amp; Laptops
---

### Post by chrini on 2008-01-10
Ok, I have a Dell Latitude D610 and I've had problems with the small joystick-thing on the keyboard messing with my mouse pointer. I even had problems in windows, but I was able to disable it so I didn't have any problems with it. 

Basically what it does, is pulls my pointer to the top-right or lower-left corner of the screen and I can't move it out of there without having to push the joystick as hard/far to the opposite direction (to counter the pull).

Well, I never use the thing so I'd like to disable it. I've tried the preferences under "mouse" and there is nothing there. Does anyone have any ideas as to how I can disable it. I am still a little weak at using shell commands so as much details as possible is appreciated. Thanks.

-Nick

---

### Post by ashmew2 on 2008-02-14
Open a terminal , type 
```

xev 
```

After the window opens , press your "joystick thingy" on the keyboard. It should give you the keycode for that key (Look in the terminal).

Let that keycode be XX (represented by XX)
Then to disable it , in the terminal you do

xmodmap -e "keycode XX = 0x0000"

I hope that answers you.

---

