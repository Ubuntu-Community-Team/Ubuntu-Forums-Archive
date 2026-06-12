---
title: "Small Logitech mouse problem"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by acorn22 on 2007-04-20
I just got a new Logitech MX 600 10 button mouse (sweet!) and I did everything in [this tutorial.]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Mouse+Buttons") Everything works great... almost.

Mainly there are two problems.
1. Middle button and right button are switched
2. Only other buttons that work are back/forward (thumb) leaving 5 buttons useless

When I try to run xbindkeys_show I get 
```
lowell@minty:~$ xbindkeys_show
exec: 3: wish: not found
lowell@minty:~$ 

```

My .xbindkeysrc  is blank. I don't know how to configure the mouse in the file. (what each key is called; what each task is called)

The mouse works great in games, though ;)

-also I am running edgy

---

### Post by robenroute on 2007-04-21
Have a look [here]("http://ubuntuforums.org/showthread.php?t=219894&highlight=logitech+mice"). Might help....

---

### Post by acorn22 on 2007-04-21
Well, The back/fwd buttons work. It's just the other 5 don't and the right button doens't.

If xbindkeys_show worked this would be alot easier

[COLOR=Red]EDIT:

[COLOR=Black]I just ran xev and found what each button is.

B:1 Left click
B:2 right click
B:3 middle click
B:4 scroll up
B:5 scroll down
B:6 back button
B:7 fw button
B:8 push tilt wheel right
B:9 push tilt wheel left
B:10 100% zoom
B:11 release [/COLOR][/COLOR][COLOR=Red][COLOR=Black]push tilt wheel left[/COLOR][/COLOR]
[COLOR=Red][COLOR=Black]B:12 release [/COLOR][/COLOR][COLOR=Red][COLOR=Black]push tilt wheel right[/COLOR][/COLOR]
[COLOR=Red][COLOR=Black]B:13 zoom in button
B:14 zoom out button

So I need to know the "commands" to put in the configuration file that are 

1. right click
2. middle click
3. scroll left
4. scroll right

for example: 

```
[/COLOR][/COLOR]"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[right]"" 
m:0x0 + b:6 
```

means history back

---

