---
title: "Toshiba multimedia keys"
date: 2008-11-09
forum: Hardware
---

### Post by Gaspacho on 2008-11-09
Hi there,

I have brand new Toshiba U400-138 laptop. I loaded the system from Live CD and was happy to find out that everything works flawlessly - even the multimedia keys.

But after the system installation the keys for muting, launching media player and others stopped to work. I even re-set them from System-> Preferences -> Keyboard Shortcuts but they still do not want to work. Anyone have similar problem or solution?

Thx in advance!

P.S: The volume wheel works.

---

### Post by elbeta on 2008-11-10
i tried to configure the multimedia key for Rhythmbox, and i guess that that key is deactivated, because doesn't respond.

I have a Satellite A215-SP5811

---

### Post by Shwefty on 2008-11-10
I'm glad to see all of us Satellite users have this problem!  My screen dimming functionality doesn't work either.  (But go volume wheel!)

---

### Post by Olnex on 2008-12-29
> **Shwefty said:**
> I'm glad to see all of us Satellite users have this problem!  My screen dimming functionality doesn't work either.  (But go volume wheel!)

So why are you GLAD because other people also have the same problem? :D

---

### Post by looktowhere on 2008-12-30
Hola..
I have a toshiba A300 satellite.. I have the exact SAME problem with 8.10
the volume wheel works.. If i set the preferences then the mute works only until i use the volume wheel.. :D 
Am glad to see am not the only one....
:D

---

### Post by matt.cohenprice on 2009-01-05
Toshiba M55 user here. I don't have a volume wheel, just a play/pause, stop, forward, back, media player, and internet button on the right side of my keyboard. When I was in Windows, they would only work with Windows Media Player and WinDVD. Now in Linux, they don't work at all.

Tried installing Keytouch and Keytouch editor, which is supposed to allow you to figure out what input your atypical function keys come in on and do a custom mapping, but none of the input events keytouch located were associated with my multimedia keys.

Would love to see them work with Banshee, which is what I use for music now, or VLC, which I use for DVDs, but not sure where to look next....

---

### Post by Olnex on 2009-01-05
Now I'm using Archlinux with Gnome desktop, apart from the bluetooth module(I haven't got time to deal with it), everything works very well, including suspend/hibernate/resume, power management, volume wheel and ALL the multimedia keys.

---

### Post by Olnex on 2009-01-05
Also, I forgot to mention, camera, wifi, and most importantly, built-in mic and external mic jack also work well.
But, the fingerprint reader does not work, maybe because I didn't install proper driver, it works under Opensuse 11.1 out of the box, so I believe its hardware is supported by Linux, just need the right drivers.
Haven't tried the wifi switch yet.

---

### Post by bodymind on 2009-01-07
You can do this... in any distribution:

to find out wich button is which... just run this on a terminal and press the buttons one by one and close the program:

```
xev | sed -n 's/^.*keycode *\([0-9]\+\).*$/keycode \1 = /p' | uniq
```

you will have a result like this:

```

keycode 126 =
keycode 133 =

```

then just edit/create the file in your home

```
gedit ~/.Xmodmap
```

and put these lines in that file:
the number of keycode number is assignated to an action!
```

keycode 222 = XF86PowerOff
keycode 223 = XF86Sleep
keycode 236 = XF86Mail
keycode 229 = XF86Search
keycode 230 = XF86Favorites
keycode 178 = XF86WWW

keycode 162 = XF86AudioPlay
keycode 164 = XF86AudioStop
keycode 160 = XF86AudioMute
keycode 144 = XF86AudioPrev
keycode 153 = XF86AudioNext
keycode 176 = XF86AudioRaiseVolume
keycode 174 = XF86AudioLowerVolume

```

and then run:
```
/usr/bin/xmodmap ~/.Xmodmap
```

to automatize this edit/create the file in your home:

```
gedit ~/.xsession
```

and write this:

```
/usr/bin/xmodmap $HOME/.Xmodmap
```

:popcorn:

from:
[http://en.gentoo-wiki.com/wiki/Multimedia_Keys](http://en.gentoo-wiki.com/wiki/Multimedia_Keys)

---

### Post by Abalidoth on 2009-05-19
I installed Jaunty on my brand new Toshiba Satellite a305 a week or two ago. I loaded it up and everything worked fine, including the multimedia buttons. In fact, they performed just fine with Rhythmbox.
But recently, they don't work at all. When I run xev, it doesn't recognize any of them except the mute key. I can't get the system to acknowledge the presence of these keys no matter what I do.
If these keys had never worked, I wouldn't bother, but I'm a little frustrated that they would *stop* working.

---

### Post by ChemShock on 2009-06-03
All of my multimedia keys are all one input by default.

Need a different keyboard layout?

Toshiba Satellite A105-S4074

---

### Post by lisati on 2009-06-03
> **ChemShock said:**
> All of my multimedia keys are all one input by default.

Need a different keyboard layout?

Toshiba Satellite A105-S4074

On my M200 they're between my keyboard and screen together with the power button, i haven't used them recently other than turning the machine on. The A100 I recently gave to a nephew didn't have any at all.

---

### Post by ChemShock on 2009-06-03
My multimedia keys are left most to the keyboard and under the power button. Did you get the Fn key to work separately?

I know the Fn key is suppose to initiate special commands but i don't want it that way. I want to use it like the super, ctrl, alt, and shift like keyes as part of a command

---

### Post by Garibaldi3489 on 2009-06-12
I just installed Linux Mint 7 (which is heavily based on Ubuntu 9.04) on my Toshiba Satellite a205 last week. I have been also have problems with my multimedia keys - they were detected correctly and work great in Rhythmbox but it seems that after I put the computer into hibernate and bring it out again, it cannot see the multimedia keys at all. If I do
```
xev | sed -n 's/^.*keycode *\([0-9]\+\).*$/keycode \1 = /p' | uniq
```

and hit any of the keys, nothing is printed to the console or window. If I restart they work again. Any ideas on why this is happening or how to fix it?

---

