---
title: "Backlight Brightness?"
date: 2008-05-01
forum: Hardware
---

### Post by omnibot on 2008-05-01
New to Ubuntu, installed last night and am finding it very internesting. :)

One problem I am having is that the first time I let my lappy go idle, the backlight dimmed and when I resumed use the brightness did not come back. 
fn+f8 is not working. 

I have tried disabling the dim under power managment and reboot, no change. 

I found a tool called "xbacklight" in synaptic but I can't figure out how to use it. 
Any help, ideas or more info on xbacklight greatly appreciated. 

This is on a Compaq (HP) Presario C700 with ATI Radeon, if that helps

---

### Post by nuskak on 2008-05-09
I've the same problem with this laptop.

The fn brightness keys don't work. I've also tried to add a special button on the top bar, but it also doesn't works.

Someone can help us?

---

### Post by wwbdd on 2008-05-09
I have not had this issue, but there are setting you can change under System->Preferences->Power Management.  You can change the options for both when the system is on power and on battery.  I have also added the brightness applet to the panel, and I can manually change the brightness easily from the panel.

Hope that helps.

---

### Post by cooldudevamsee on 2008-05-18
Map your brightness controls to keyboard shortcuts.

[Control your laptop brightness using keyboard shortcuts]("http://ubuntu-snippets.blogspot.com/2008/05/control-your-laptop-brightness-using.html")

---

### Post by BSOD64 on 2011-10-14
to use xbacklight type in a terminal:
```

xbacklight -set <percentage>

```
example:
```

xbacklight -set 0
xbacklight -set 100

```

---

