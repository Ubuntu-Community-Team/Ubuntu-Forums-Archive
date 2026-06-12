---
title: "Alps Touch Pad typing issue"
date: 2009-04-28
forum: Hardware
---

### Post by Master_Taco on 2009-04-28
Hello, I installed Ubuntu on my laptop, and everything seems to work properly, except the touch pad's tap-click feature. I want to leave the tap type enabled, but, I also want to be able to type, and not worry about touching the touch pad and mistakenly clicking something. In Windows, it does just this, it disables the touch pad while typing. I was wondering if there was a way to do this in Ubuntu also?

I believe the touch pad is an Alps touch pad.

---

### Post by Master_Taco on 2009-04-29
Bump.

---

### Post by bhagwad on 2009-04-29
There's a utility called syndaemon that does this for you. Open a terminal and type "info syndaemon". It'll give you a list of options. Here's what I use:

```
 syndaemon -i 2 -d -t -k
```Meaning that the touchpad tap is disabled for 2 seconds after the last keypress, it starts in the background as a daemon, it ignores modifier keys like Ctrl, Alt etc, and the mouse can still move (though it can't tap).

Add this to your startup programs and you're set! Hope this helps.

---

### Post by Master_Taco on 2009-04-29
Thanks, I'll give that a try, and get back to you with results!

---

### Post by Master_Taco on 2009-04-29
It did work! However, I cannot get it to start up with the machine. I tried using Startup Applications (System>Preferences>Startup Applications) and it did not work. I may be doing something wrong? Here is a screen shot of my configuration...

[IMG]http://www.master-taco.com/images/Screenshot.png[/IMG]

---

### Post by bhagwad on 2009-04-29
Could you check system monitor and see if the syndaemon process is running after rebooting and adding to startup.

Note: I know you've probably done this, but no harm in checking - ensure that it's "ticked" in the startup dialog box.

---

### Post by Master_Taco on 2009-04-30
Actually, it was fine the way it was, except I forgot the "2" after the -i parameter... Thanks a ton for your help!

---

### Post by bhagwad on 2009-04-30
It takes 2 by default, so that shouldn't have caused problems. But if all is working now, then great!

---

### Post by Sojurner on 2010-10-14
i am using an alps touchpad, but can not get this to work because it says it is unable to find a synaptics device. Any ideas?

---

