---
title: "HP dv9000 with Ubuntu 10.04 monitor issues"
date: 2012-05-28
forum: Hardware
---

### Post by ntzrmtthihu777 on 2012-05-28
Hello all.

First off, let me say I'm a total linux noob (less than a week's worth of experience). However, I love what I'm discovering about this OS.

As the title of this thread states, I'm running Ubuntu 10.04 on a HP Pavillion dv9000 and still have a few kinks to iron out...got multitouch to work (in part) on the synaptics touchpad, a few emulators for my fav games, hebrew & greek typing set up.

One problem I have not been able to resolve: my display is a bit "fuzzy". If you were to represent the pixels as letters, it would look something like this:

[FONT=Courier New]pixel window window pixel[/FONT]
[FONT=Courier New]dow pixel window window pixel
  [/FONT][FONT=Courier New]ow pixel window window pixel
[/FONT][FONT=Courier New]w pixel window window pixel[/FONT]
[FONT=Courier New]pixel window window pixel[/FONT]
[FONT=Courier New]dow pixel window window pixel
  [/FONT][FONT=Courier New]ow pixel window window pixel
[/FONT][FONT=Courier New]w pixel window window pixel[/FONT]

A slight horizontal zigzag, more prominent on the vertical lines. I'd post a screenshot, but I think it would not display the problem.

I can still use it without any problem, it's just very annoying and will detract from any display-intensive program I use (videos, art applications, CAD [any suggestions as to a good program?]) 

Remember, I'm still a noob and not ashamed to admit it!

Edit:
Out of curiosity I took a screenshot and viewed it on another laptop, and it looks perfect, so a screenshot would not be of assistance in troubleshooting

---

### Post by ntzrmtthihu777 on 2012-05-28
Figured it out! All I had to do was to open System>Administration>Hardware Drivers and install NVIDIA accelerated graphics driver (version current) [Recommended]

Like I said, total noob! Hopefully this post will help others with the same problem in the future.

---

