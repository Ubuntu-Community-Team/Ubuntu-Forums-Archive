---
title: "Can't Adjust Mouse Speed! - G500 Logitech Mouse"
date: 2013-05-14
forum: Hardware
---

### Post by Inject on 2013-05-14
I'm currently running Ubuntu 12.10 (64 Bit OS)

I have a G500 Logitech Mouse. The issue I'm starting to be unable to bare with is the fact that my mouse is just way to fast. So I went into mouse settings to go turn it down.
However, this is what I saw:


[IMG]http://i.imgur.com/XJQyI9N.jpg[/IMG]

How I can I make the speed any slower when it's already at the slowest speed. I also find this hard to believe since It's moving pretty damn fast.

Suggestions, Ideas, etc would be apperiated. Thank you.

---

### Post by mickee384 on 2014-01-12
I am having the same issue. My mouse is Logitech wireless mouse M317. I have the speed dialled all the way down as well. Any help will be appreciated!
Note: It is just the speed. All other settings are fine. ubuntu 13.10 32bit

---

### Post by mickee384 on 2014-01-12
The following solution worked for me, adding the following to my .profile:

```
logitech=$(xinput --list --short | grep -m1 "Logitech USB Receiver" | cut -f2 | cut -d= -f2)

xinput --set-prop "$logitech" "Device Accel Constant Deceleration" 4
```

hope this helps you!

---

