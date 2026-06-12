---
title: "Taking a screenshot via command line"
date: 2008-08-18
forum: General Help
---

### Post by markeee on 2008-08-18
Hi,

Having trouble finding out how to take a screenshot of a specific area.

I've used scrot etc, but it takes a screenshot of the whole desktop, I'm trying to take a screenshot of a specific window/app (firefox).

Anyone got any ideas?

Thanks

mappo

---

### Post by ad_267 on 2008-08-18
Not sure if this is what you're after as you still have to select the window with your mouse, so it wouldn't be useful for a script or anything. From the scrot manpage:
> -s, --select
            Interactively select a window or rectangle with the mouse.

---

### Post by markeee on 2008-08-18
thanks for replying buddy

it does what i want as you say, but with the use of a mouse!

im out of ideas for this, I know the photos could be edited manually, but then if this was happening my script would become pointless

---

### Post by amo-ej1 on 2008-08-18
If it's meant to be a screenshot of one application which stays open you could use import (man import) there you can specify the window id. 

```

edb@lapedb:~$ import -window 0x262bf1e bla.jpg

```

This takes a screenshot of the window with windows id '0x262bf1e', now how can you get to know the window id ? (here's the tricky one), use for example xwininfo, this will allow you to click on one window and will give you some information including the window id. So this is useful for one application which stays open all the time.

---

### Post by markeee on 2008-08-18
is there no way i could grab the window id, without clicking..no thinking about it there wouldn't be


this all sounds good, and would work-but requires input, im after making the script automate what i need=]

---

### Post by amo-ej1 on 2008-08-18
```

xwininfo -tree -root 

```

give you a list of all known windows, you could throw a regexp against the output if you know the window title or find some other way to identify it.

---

### Post by markeee on 2008-08-18
thanks

will get to it

mapp

---

### Post by markeee on 2008-08-18
mark@dimension:~$ xwininfo -tree root
xwininfo:  unable to open display ''
usage:  xwininfo [-options ...]


how can i fix that? i have display set?!

---

### Post by amo-ej1 on 2008-08-18
'-root' not 'root'

How are you running it ? Are you running it remote or from another shell or something ? If you simply run it from an xterm it should have the display variable set (echo $DISPLAY to verify), otherwise you might need to set it youself to point to the xserver to query. (it is also a setting import will need).

---

### Post by LinuxRocks713 on 2008-08-18
Try this solution:

```

xwd | xwdtopnm | pnmtopng > /tmp/screeeeenshot.png

```

Your new shiny screenshot is in /tmp/screeeeenshot.png.

---

### Post by markeee on 2008-08-18
> **amo-ej1 said:**
> '-root' not 'root'

How are you running it ? Are you running it remote or from another shell or something ? If you simply run it from an xterm it should have the display variable set (echo $DISPLAY to verify), otherwise you might need to set it youself to point to the xserver to query. (it is also a setting import will need).

ive set display to :3 - vncserver running on 3, but im getting errors now

What can i do to fix this?!

thanks

---

### Post by markeee on 2008-08-18
I'm sure it's a really simple problem/solution...just cant figure it out:)

---

### Post by vanwarantion on 2008-09-30
Try this;

import -window `xwininfo -name Transmission|grep xwininfo|cut -d ' ' -f 4` hede.jpg

(i used "Transmission" for window name and "hede.jpg" for output filename)

ps: You may gonna have to find your window name by using xwininfo command. Use "man xwininfo" for detailed usage instructions for that utility.

---

