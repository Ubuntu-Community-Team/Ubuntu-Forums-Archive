---
title: "Mouse button funcionatily"
date: 2006-06-01
forum: Hardware &amp; Laptops
---

### Post by Michael%S on 2006-06-01
When I started using Ubuntu a couple of months ago I had [this problem]("http://ubuntuforums.org/showthread.php?t=132384"). Now that I upgraded to Dapper I have pretty much the same problem, except the old solution doesn't work any more.
I tried using the setup I used before. The closest I got to full functionality was the side buttons acting as additional copies of button 1 and the scrollwheel working for some things but not for actual scrolling (it could at least be used to change zoom/font size in Firefox and in the document viewer). Right now neither work.
I used xev a little to try and get an idea of what mapping to use. One time it said the side buttons were 8 and 9, so now I have this setup which doesn't work:
```
Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
    Option        "Emulate3Buttons"    "false"
    Option        "Buttons"        "9"
    Option        "ZAxisMapping"        "6 7"
EndSection
```
Needless to say, I tried less ridiculous things before resorting to this. I'm kinda at a loss. I'm probably switching to a different mouse very soon (maybe even today) but I really want to try and solve this problem first. Any ideas?

---

### Post by Michael%S on 2006-06-01
Okay, the scrollwheel actually does do something now, and that is back and forward in firefox. At least it does something.
I forgot to mention: xvkbd, which I set to start with each session originally when I set up the side buttons, now actually opens a window each session.

---

### Post by Michael%S on 2006-06-01
It's officially not the old mouse's fault. I've switched to a new mouse with just the regular two buttons and mouse wheel (as far as I can tell) and yet still all I can the scrollwheel to do in firefox is to go back and forwards. It doesn't even matter what I set ZAxisMapping to - "4 5", "6 7", it's all the same. ](*,)

---

### Post by Strid on 2006-06-01
I had the same problem. I use a Logitech MX 510 USB with with a USB>PS/2 converter.

I got it right via this post:

[http://www.ubuntuforums.org/showpost.php?p=1068222&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1068222&postcount=2)

---

### Post by Michael%S on 2006-06-02
Still on that new and simpler mouse, I haven't gotten scrollwheel functionality back yet. It doesn't do back and forward in Firefox anymore because that was actually a Firefox thing that can be changed via about:config. I've tried all kinds of configurations of xorg.conf, including things like
```
    Option        "Buttons"        "5"
    Option        "ButtonMapping"        "1 2 3"
    Option        "ZAxisMapping"        "6 7"
```
and it doesn't even change anything. I can scroll in most apps by placing the cursor on the scrollbar and then using the scrollwheel, but in Firefox I don't even get that.
It's pretty hard to use my computer this way.

---

### Post by Michael%S on 2006-06-02
Okay, I got some help on #ubuntu and the problem is solved.
Just for documentation, here are the things that I did that made it work (not that I understand exactly what they do):
```
xmodmap -pp
```
and then
```
xmodmap -e "pointer = 1 2 3 9 10 4 5 6 7 8 11"|xrefresh
```

---

### Post by Michael%S on 2006-06-02
Okay, problem not as solved as I thought. Like I was told I might when I got that help on #ubuntu, I need to run the xmodmap -e command every time I log in. I put it in the startup list but disabled and now when I went there to get the command it took off the **"**, making the command useless...

---

### Post by Michael%S on 2006-06-02
A more experienced friend of mine suggested I place the xmodmap -e command in ~/.xinitrc, so I tried this, but it didn't change a thing. I tried it both with and without the xrefresh command after it.

---

### Post by lukeluke on 2006-06-02
[QUOTE=Strid]I had the same problem. I use a Logitech MX 510 USB with with a USB>PS/2 converter.

I got it right via this post:

[http://www.ubuntuforums.org/showpost.php?p=1068222&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1068222&postcount=2)[/QUOTE]

Yep! Work perfectly for my mouse too! :D

---

### Post by Michael%S on 2006-06-03
Okay, weird. I shut down earlier (had to do some dust cleaning, I was too lazy for over two months and the situation here was getting scary) and then when I booted again the problem was simply gone. Of course a screen resolution problem I used to have replaced it, but still, the mouse problem is gone, even after I reconfigured X with the dpkg-reconfigure thingy. ](*,)
Now I suppose I aught to open a new thread about the resolution thing. :-k

---

