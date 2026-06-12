---
title: "xbindkeys giving wrong mapping information"
date: 2010-04-07
forum: Hardware
---

### Post by narnie on 2010-04-07
Hello,

I'm having a problem with xbindkeys giving the wrong mapping information, hence I can't get it work at all when trying new mappings from this machine.

From another computer, I have some definitions for xbindkeys (made with xbindkeys-config). These key codes work correctly on this computer I'm having difficulty with.

From the config file for example:

```
#esword_split
"~/scripts/esword_split"
#    m:0x1d + c:39
    Control+Shift+Alt+Mod2 + s 

```
will work and run the script I have made.

However, if you run

xbindkeys -k one gets this:

```
"NoCommand"
    m:0x201d + c:39
    Control+Shift+Alt+Mod2 + s

```
**Notice the to different m: values**. The one obtained with xbindkeys -k is inaccurate and won't work. Hence, I can define no new keyboard commands.

In the working example above, if one comments out the m: line like this:

```
#esword_split
"~/scripts/esword_split"
#    m:0x1d + c:39
    Control+Shift+Alt+Mod2 + s 

```
It breaks and won't work. Commenting out the more human readable line like this:

```
#esword_split
"~/scripts/esword_split"
    m:0x1d + c:39
#    Control+Shift+Alt+Mod2 + s 

```

Allows it to work.

Sadly, nothing is reading correctly with xbindkeys -k

This is a toshiba satellite A505-S6965 laptop.

Is there any other way to more accurately obtain keyboard bindings?

Not sure to proceed from here.

Thanks,
Narnie

---

### Post by narnie on 2010-04-08
Figured out the problem.

For some reason, my keymap was set for Ireland instead of Generic 104. Don't ask me how.

After resetting to the correct one (and applying it to system), all is good and xbindkeys -k maps the correct keycodes. YEA!!!

Narnie

---

