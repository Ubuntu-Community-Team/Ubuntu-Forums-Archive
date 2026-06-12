---
title: "Trouble with monitors/dual screen"
date: 2010-10-02
forum: Hardware
---

### Post by xieon on 2010-10-02
[COLOR=Red]**solved**[/COLOR]

I have two monitors, and I initially had them side by side, where windows would maximize and stay in that monitor. 

I installed compiz config to use the cube effect, however, after it first shut off the second monitor, then it made them into one big monitor. 

After removing compiz, I tried to use the Ubuntu monitor program but it told me that my drivers couldn't support it, and to use my nvidia monitor program.
```
It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?
```I used the nvidia app however I can only use 1 big screen. I want to have them be separate with the ability to move windows between the two.

Any help is great, I'm brand new with linix

[COLOR=Red][B]Edit: 
This has been fixed.[/B][/COLOR]

I had to disable the neaveau driver by blacklisting it, then updating to the latest nvidia driver.
All  can be seen here for anyone else who has the problem:
[http://www.youtube.com/watch?v=Sh4ZmBdFCuU](http://www.youtube.com/watch?v=Sh4ZmBdFCuU)

Now windows will maximize and stay in that screen, and you can still move between screens.

[COLOR=Red]Note:Read NOTE [/COLOR]- This will fix it, but you CANNOT use the cube feature, or many others of compiz config

---

