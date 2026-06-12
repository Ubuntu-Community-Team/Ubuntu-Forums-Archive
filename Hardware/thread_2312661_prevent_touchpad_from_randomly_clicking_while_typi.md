---
title: "prevent touchpad from randomly clicking while typing"
date: 2016-02-06
forum: Hardware
---

### Post by P3t3r on 2016-02-06
I've recently re-started using Ubuntu, and I keep struggling with one little problem that seems small and insignificant at first but still takes a heavy toll on my productivity. It relates to my touch pad.

While typing, every few lines (about once or twice per minute), I seem to accidentally tap my touch pad (probably a slight touch with the base of my thumb). Which means my cursor is suddenly at a different location, meaning sentences get messed up and I need to remove what I typed wrong, move the cursor manually to the right position, and start typing again. Not much work but given that this happens about every minute, it really takes a toll on my productivity.

On windows, I never have this problem. Something in the driver is configured to ignore taps (not button clicks) if a letter has been typed less than (2?) seconds before it. The Linux driver doesn't seem to have this mechanism active (at least by default), resulting in the behavior above. I currently need to switch back to Windows to type my reports after doing my computations on Linux, which is also somewhat inconvenient. 

Is there any way to mimic such a feature in Ubuntu? I'm using an Asus G501 laptop, but I've noticed it on my older laptop as well (although its touch pad is less sensitive so it only happened every few minutes).

---

### Post by sudodus on 2016-02-06
The easiest way is to turn off the touchpad completely. It works well if you have a mouse.

Click on the tool icon (a cog wheel and a wrench) and select 'Mouse and Touchpad'.

Click on the switch at the right part of the window to turn off the touchpad.

-o-

If you need the touchpad, you can try how it works if you turn off 'Tap to click' and maybe 'Two finger scroll'.

-o-

If you use light-weight flavours of Ubuntu, for example Lubuntu and Xubuntu, you can use

```
synclient touchpadoff=1  # turn it off
```
```
synclient touchpadoff=0  # turn it on
```
```
synclient touchpadoff=2  # only tapping and scrolling turned off
```

See more details at ```
man synaptics
```

***Edit:***

You can try using ***syndaemon*** to set the 'idle-time' before enabling the touchpad after a key press.

See details at ```
man syndaemon
```

(syndaemon works with Lubuntu and Xubuntu, but I have not tested it in standard Ubuntu.)

---

### Post by ajgreeny on 2016-02-06
On my old netbook where I need the scroll and touchpad but not the tap-to-click I use command ```
synclient MaxTapTime=0
``` which I have put into a script which I add to startup applications and run at session start, ie login.

---

### Post by vasa1 on 2016-02-06
syndaemon looks interesting.

BTW, there's 
[How to fix a too sensitive touchpad on Linux]("https://blog.laimbock.com/2014/11/23/howto-fix-a-too-sensitive-touchpad-on-linux/comment-page-1/") as well.

---

