---
title: "[SOLVED] Need to Turn off Webcam Permanently (Disable gspca)"
date: 2007-09-12
forum: Hardware &amp; Laptops
---

### Post by lusankya23 on 2007-09-12
Hello,

I have a new ASUS A8 laptop and when I boot Fiesty, the built-in webcam is on by default and gets very hot. I figured out how to turn it off by running: 

```

sudo modprobe -r gspca
```

However, I want this to happen on boot so I don't have to run this script every time I turn my laptop on. Is there a way to remove the gspca module from start-up, or if need be, permanently?

Thanks!!

-Lusankya23

---

### Post by MrHippocampus on 2007-09-12
What you need to do is add the module name to the end of the "/etc/modprobe.d/blacklist" file

```
blacklist gspca
```

That will stop the module being loaded automatically, but still allow you to modprobe it yourself if you do want to use it :)

---

### Post by lusankya23 on 2007-09-12
Thanks MrHippocampus! That did the trick!!! ):P

-Lusankya23

---

### Post by trigoman05 on 2008-04-24
Sorry for bring up such an old thread, but once I upgraded to Gutsy this gspca thing stopped working. 
Does any one know any other fix for this? 
Will this issue by fixable on the new version of Ubuntu Hardy Heron?

Here's the other thread explaining what happens when I do gspca:
[http://ubuntuforums.org/showthread.php?t=502064]("http://ubuntuforums.org/showthread.php?t=502064")

---

