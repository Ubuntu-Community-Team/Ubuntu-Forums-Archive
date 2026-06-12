---
title: "Joystick Detected As Mouse"
date: 2009-04-10
forum: Hardware
---

### Post by prahs rozar on 2009-04-10
I have an Xbox 360 Controller I use on my computer. Up until I upgraded to 8.10 it worked on Ubuntu. Now it is detected as a mouse. I've read into this topic a bit, and it seems this is a fairly common problem.

I tried this fix [https://help.ubuntu.com/community/Joystick_lshal_outputs_done](https://help.ubuntu.com/community/Joystick_lshal_outputs_done) and a few others, but I can't remember which. 

Here is my lshal output: [http://rafb.net/p/o58mxM43.html](http://rafb.net/p/o58mxM43.html)

---

### Post by prahs rozar on 2009-04-10
Bump.

---

### Post by prahs rozar on 2009-04-10
Bump.

---

### Post by prahs rozar on 2009-04-11
Bump.

---

### Post by prahs rozar on 2009-04-11
Bump.

---

### Post by prahs rozar on 2009-04-11
Bump.

---

### Post by prahs rozar on 2009-04-12
Bump.

---

### Post by prahs rozar on 2009-04-12
Bump.

---

### Post by prahs rozar on 2009-04-12
Bump.

---

### Post by TheIdiotThatIsMe on 2009-04-12
That's a lot of bumps...

Anyways, I had the exact same issue and found a fix over [here]("http://ubuntuforums.org/showthread.php?t=981623&highlight=Xbox+360+controller").

Pretty much, open the terminal and:

$ xinput list
See which device number the Xbox controller has
$ xinput set-int-prop THATDEVICENUMBER 'Device Enabled' 32 0

---

### Post by prahs rozar on 2009-04-12
Thanks, I'll try that out now. I bumped so much because I was trying to keep it on the first page, because I many people wouldn't see it if it wasn't. They accumulated quickly over the course of a few days.

---

### Post by prahs rozar on 2009-04-12
Wow, it worked immediately, you're a lifesaver. Isn't there a way to thank users on the forum, because if there is I'd like to thank you.

---

### Post by TheIdiotThatIsMe on 2009-04-13
Haha I have no idea, but the fix was great :-) Just glad to help! Enjoy!

---

### Post by TheIdiotThatIsMe on 2009-04-17
PS I noticed that if you reboot it seems to lose the config, but if you put that last line (the device number doesn't change) into your sessions config to autorun on startup, it will work everytime.

---

