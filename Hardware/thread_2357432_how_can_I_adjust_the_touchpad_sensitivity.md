---
title: "how can I adjust the touchpad sensitivity"
date: 2017-04-02
forum: Hardware
---

### Post by aneblanc on 2017-04-02
How can I adjust/decrease the sensitivity of the touchpad on my new HP Stream?

---

### Post by RobGoss on 2017-04-03
Hello and welcome, What version of Ubuntu are you currently using?

---

### Post by mikewiz38 on 2017-04-13
Not the original poster...but let's say we were using Ubuntu Gnome with libinput?

---

### Post by efflandt on 2017-04-13
Typically you would use **xset** in general, or if you want to set that for a specific device you can use **xinput**. In my case I use xinput to reduce acceleration of my mouse (which is way too fast by default in 16.04 & 16.10) while leaving mousepad sensitivity unchanged in case I use wireless/BT keyboard with mousepad.

Once you find something that works, you can add a Startup Application with the command. In Unity you would go to the top icon in Unity bar (Search your computer) and start to search for "start" which should list "Startup Applications". But I am not sure how you would find that in Gnome.

---

### Post by mikewiz38 on 2017-04-14
> **efflandt said:**
> Typically you would use **xset** in general, or if you want to set that for a specific device you can use **xinput**. In my case I use xinput to reduce acceleration of my mouse (which is way too fast by default in 16.04 & 16.10) while leaving mousepad sensitivity unchanged in case I use wireless/BT keyboard with mousepad.

Once you find something that works, you can add a Startup Application with the command. In Unity you would go to the top icon in Unity bar (Search your computer) and start to search for "start" which should list "Startup Applications". But I am not sure how you would find that in Gnome.

Thanks for the response.  I've been using xinput set-props, but unfortunately, I can't seem to get the right combination of something that would make it usable.  I have a hard time believing that others haven't had the same problem as I do, as my laptop is nothing unique or special.  


It's odd because in Windows, it works perfect right out of the box and with no adjustments needed...everything feels so natural.  But on Ubuntu/Linux, it's overly sensitive and just doesn't feel natural.

---

### Post by efflandt on 2017-04-15
To set mouse or mousepad sensitivity with xinput you would use --set-ptr-feedback (begins with double dash).

--set-ptr-feedback device threshold num denom
device = id listed for that device if you just type xinput
threshold = pixels in short period of time until acceleration (I think default is now 5)
num = acceleration relative to denom (I think default now is 5 1 too fast for me, was 2 1 before 16.04)

My mouse is id=11, so I use:```
xinput --set-ptr-feedback 11 5 2 1
```

---

### Post by Autodave on 2017-04-16
Or just go into *Settings *and adjust it.

---

