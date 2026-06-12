---
title: "Inspiron 1545 built in MIC and MIC jack fixed ubuntu 9.10"
date: 2009-12-21
forum: Hardware
---

### Post by taylor.v.2008 on 2009-12-21
Hey all. I have a Dell Inspiron 1545 laptop. With the default install of Ubuntu 9.10, the front MIC jack and built in MIC do not work. This is how I fixed it.

First, open a terminal and run 
```
alsamixer
```

Next, use the right arrow key to select the tab that says "Digital". after it is selected, use the up and down arrow keys to select "Analog I". After that, press ALT+Q to quit, and close the terminal.

Now, we will check the graphical settings. right click on the sound icon in the system tray, and select "Sound Preferences".
Click the "Input" tab and make sure the mute box is not selected. This should solve your input problems!

---

### Post by Alderas24 on 2010-01-15
THANK YOU THANK YOU THANK YOU!

Now I don't have to use that **** they call pulseaudio. Seriously, the dev team needs to just scrap pulseaudio altogether because NOBODY likes it. Once again, thank you for your information. I'd kiss you if I could, that's just how much I hate pulseaudio. :D

---

### Post by zebraneo on 2010-02-10
> **taylor.v.2008 said:**
> Hey all. I have a Dell Inspiron 1545 laptop. With the default install of Ubuntu 9.10, the front MIC jack and built in MIC do not work. This is how I fixed it.

First, open a terminal and run 
```
alsamixer
```

Next, use the right arrow key to select the tab that says "Digital". after it is selected, use the up and down arrow keys to select "Analog I". After that, press ALT+Q to quit, and close the terminal.

Now, we will check the graphical settings. right click on the sound icon in the system tray, and select "Sound Preferences".
Click the "Input" tab and make sure the mute box is not selected. This should solve your input problems!
I was going crazy with this problem, I want to thank you so much for taking the time to put a solution to the problem, thank you from the bottom of my heart

---

### Post by davidY on 2010-02-15
This. Is. The. Win.

Thanks a lot for this

---

### Post by theronb on 2010-04-04
thank you, thank you, thank you!! I bought the 1545 primarily to do some home recording and was beginning to tear my hair out.

---

