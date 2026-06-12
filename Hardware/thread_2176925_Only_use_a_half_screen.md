---
title: "Only use a half screen"
date: 2013-09-26
forum: Hardware
---

### Post by ruffo2 on 2013-09-26
Hello there, at first sry for my bad english, i'm from Germany.
So, i have installed Ubuntu on my Computer(i used Windows 8.1 before), and i like it very much!

But my second Monitore is broken at the half. My idea: Cut the screen at the breakepoint (with software not in rl), so did someone of u knew a programm or application for this?


picture of broken screen(to big for binding): [http://imgur.com/QfsMLKt](http://imgur.com/QfsMLKt)


Thanks for helping ^^

---

### Post by Kirboosy on 2013-09-26
Welcome to the forums! :D

Interesting situation to say the least...I would try manually setting screen resolutions. I don't know of any software that would do such a function.

[Forcing Monitor Resolutions]("http://askubuntu.com/questions/119843/how-to-force-multiple-monitors-correct-resolutions-for-lightdm")

Hope that helps!
~Caboose

---

### Post by ruffo2 on 2013-09-26
But only change the resolution don't change the screen height.. Or does it do when i change this manually? Because when i use the manager it dont cut.. :<
But thanks :D

---

### Post by Kirboosy on 2013-09-26
You would have to find an odd resolution that would not properly fill the screen. So instead of 1080 by 1920 it would have to be 1080 by 1700. However I don't know how well your monitor would support it. Your monitor would most likely complain that the resoltution is "Out of Range"

```
xrandr -q
```

That would list the supported screen resolutions

[X/Config/Resolution Ubuntu Wiki]("https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution")

Hope that helps!
~Caboose

---

### Post by ruffo2 on 2013-09-26
:< This don't work rly.. but i have an other idea, are there some "bouncers"? So that when i maximize a window that it only goes to the border of the bouncer?

---

### Post by Kirboosy on 2013-09-26
So I take back what I said earlier. I found a Utility that might be able to do what you need

[Devilspie Ubuntu Documentation]("https://help.ubuntu.com/community/Devilspie")

Hope that helps!
~Caboose

---

### Post by ruffo2 on 2013-09-27
okay, i will test it today, yesterday i was to tiered :=)

---

