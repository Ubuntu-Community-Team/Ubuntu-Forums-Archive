---
title: "Brightness Issues under 8.10"
date: 2008-10-30
forum: Hardware
---

### Post by noab on 2008-10-30
Hello,

first of all I really want to say thank you to all the developers out there. I dowloaded the new Ubuntu just a few hours ago onto my new Laptop and I have to say: it's just incredible! Almost every thing worked out-of-the-box.

But there is one issue, I couldnt solve. (by the way: the laptop is a HP Compaq 6370s with Intel 4500 Graphic). I just cant get the thing to change the backlight brightness. Neither the applet nor the fn-keys change anything (the fn keys bring up the brightness-popup, but the display doesnt change at all). I even tried to echo a number directly to /proc/acpi/video/GFX0/DD04/brightness. Nothing.

```
root@myon:/home/dsuess# cat /proc/acpi/video/GFX0/DD04/brightness
levels:  100 51 30 37 44 51 58 65 72 79 86 93 100
current: 65
```

With this command I found out, that DD04 was the only device that seems to be working. If I echo a number onto DD04/brightness the current level actually changes, but nothing happends with the display.

Can anybody help me?
Thanks alot!

---

### Post by noab on 2008-10-31
I could not figure out if the Intel Graphic driver works correctly. GlxGears has around 500 fps

---

### Post by debzf on 2008-12-15
Hi, 

I've also got a HP6730s. It didn't work either, but now I've found out a way to sort of solve it. I copied the command from this post to see if it worked:

[http://ubuntuforums.org/showthread.php?t=982746&highlight=brightness+xrandr]("http://ubuntuforums.org/showthread.php?t=982746&highlight=brightness+xrandr")

> **blackened said:**
> You might be able to switch the backlight control to restore your function keys. Getting it to work on ac adapter is gonna take a little more work.
```
xrandr --output LVDS --set BACKLIGHT_CONTROL native
```

Although this is for a different kind of laptop, if you do this, you will be able to set the brightness of your screen with the function keys. It's not perfect though:

1. If you try to use the brightness applet, the screen won't respond, and it will take a long time to change the brightness

2. If I play ppracer, the laptop freaks out, I will display a flashing window and after a while it will crash. 

So it's not a real solution but it works most of the time. I put it in my .bash_aliases file, so I can load it if i'm on battery and I don't want to play games. Compiz works OK though. So maybe it is because ppracer will adjust the resolution?


regards,

Dirk

---

