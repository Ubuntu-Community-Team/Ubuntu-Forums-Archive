---
title: "Wacom Graphire4 doesn't work properly in Karmic"
date: 2009-12-28
forum: Hardware
---

### Post by pdonadeo on 2009-12-28
Hi to all, I'm in trouble with my Wacom Graphire4 in Karmic. The situation is this: with a fresh new Ubuntu 9.10 installed (no upgrade) the Wacom tablet isn't even seen by the system.

Following [this post]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176") by Favux I was able so see the tablet via [FONT=Courier New]**xsetwacom list**[/FONT], but still have problems configuring pad button events.

I decided to switch to a text console (CTRL + ALT + F1) and turn Xorg off completely:

```
$ sudo service gdm stop
```

and try with:

```
$ wacdump /dev/input/wacom
```

but wacdump died with a segfault!

I decided to downgrade the wacom packages to the Jaunty version installing the versione 1:0.8.2.2-0ubuntu2:
[http://packages.ubuntu.com/jaunty/wacom-tools](http://packages.ubuntu.com/jaunty/wacom-tools)
and
[http://packages.ubuntu.com/jaunty/xserver-xorg-input-wacom](http://packages.ubuntu.com/jaunty/xserver-xorg-input-wacom)

In console wacdump works as expected (no more segfaults) and the tablet seems to generate all the correct events. So the tablet (I mean the hardware) works, it's something :-)

Next step: using xsetwacom to configure the tablet, and here are the problems: the software stack, I don't know where, can't associate the pad buttons and the scroll wheel on the Graphire4 to mouse button events.

Example:

```

xsetwacom set pad Button1 "core key A space"
xsetwacom set pad Button2 "core key B space"
xsetwacom set pad RelWDn "core key C space"
xsetwacom set pad RelWUp "core key D space"

```

produces the expected (dummy) result of printing a letter followed by a space on the terminal (under X) when the corresponding event occurs.

But when I try to associate the standard X events:

```

xsetwacom set pad Button1 "button 1"
xsetwacom set pad Button2 "button 3"
xsetwacom set pad RelWDn "button 5"
xsetwacom set pad RelWUp "button 4"

```

it simply doesn't work! I can't be more precise because **everything** seems to work but the generation of the low level mouse button events.


I have already searched extensively in this forum and I made some progresses, but I'm stuck here. Any ideas?

---

### Post by pdonadeo on 2010-01-07
Quick check: still no ideas? Am I the only one with this problem configuring Wacom Graphire4 in Karmic?

---

### Post by punong_bisyonaryo on 2010-01-12
Hi! I'm also curious about this, because I had just borrowed a Graphire4 tablet, and a quick search before plugging it in led me here.:)

---

### Post by pyrofreek_9 on 2010-02-19
Hi, any luck on this? I've been tinkering with it for a while now with no luck!

---

### Post by Favux on 2010-02-19
Hi pyrofreek_9,

There was/is a bug(s) in the code.  I think they partially fixed it with linuxwacom 0.8.5-10 and xf86-input-wacom 0.10-4(or later?).  But I think they just found another problem with the button code.  So you might want to wait for 0.8.5-11.

Basically it isn't/wasn't counting the buttons right and was cutting off at four where the, e.g.:  scroll wheel down was reporting as button 5.  I think they've tried to revise the code so it will handle at least 7 buttons.

---

### Post by pdonadeo on 2010-02-21
Thanks, Favux! I'm going to wait for 0.8.5-11, hoping to gain back a fully working tablet.

---

### Post by hawk88 on 2010-02-22
I down't know if there is an solution yet but it "fixed" this way
```

# xsetwacom set "stylus pad" RelWUp "core key pagedown"
# xsetwacom set "stylus pad" RelWDn "core key pageup"

```

( if stylus pad is not working try pad otherwise check the output from xinput --list )

---

