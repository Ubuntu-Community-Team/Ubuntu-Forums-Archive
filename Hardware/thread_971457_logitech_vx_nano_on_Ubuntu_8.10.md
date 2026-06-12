---
title: "logitech vx nano on Ubuntu 8.10"
date: 2008-11-05
forum: Hardware
---

### Post by dgoosens on 2008-11-05
hi community !!!

I just did it... I upgraded to Intrepid Ibex... and it feels great !!!

and then I tried to reinstall btnx and btnx-config and realized that it is no longer available [http://www.ollisalonen.com/btnx/index.html]("http://www.ollisalonen.com/btnx/index.html") as it is no longer working with X.Org v.7.4... Damn !!

thus, here I am... looking for some other kind of app with GUI that would allow me to configure my Logitech VX nano. It is a great mouse, but I did not check the compatibility with Linux when I bought it...

Hope you guys know the answer.
Thanks a lot in advance,
dg

---

### Post by dgoosens on 2008-11-06
I found a solution that does the trick for me...
here it is:

I created an .xmodmap in my home folder with the following code:

```
pointer = 1 6 3 4 5 2 7 8 9
``` 

this way I remap button 6 to button 2 (and vice versa)

in order to figure out which buttons I needed to remap I used xev (in terminal)

by pressing the buttons, you get something like this:

```
ButtonRelease event, serial 31, synthetic NO, window 0x4800001,
    root 0x13b, subw 0x4800002, time 2386460, (31,52), root:(1437,99),
    state 0x210, **[COLOR="Red"]button 2[/COLOR]**, same_screen YES

```

that did it...
but it would be nice if it were possible to configure one's mouse easily in Ubuntu... 
and I am not the only one with this thought: [http://brainstorm.ubuntu.com/idea/120/]("http://brainstorm.ubuntu.com/idea/120/")

---

### Post by pigphish on 2008-11-14
Is that just a simple text file in the home dir called .xmodmap?

---

### Post by dgoosens on 2008-11-14
> **pigphish said:**
> Is that just a simple text file in the home dir called .xmodmap?

yes it is...

---

### Post by nekr0z on 2008-11-15
Hi there! I purchased a VX Nano two weeks ago, and it's great, I don't even feel like remapping anything. The only thing I would like to tune is to make the two buttons left to the primary button switch desktops instead of their default behaviour (that is, forward and back in Firefox).

I think it can be done in System -> Preferences, but there's only one shortcut for every action, so if I make those mouse buttons switch my desktops, I can no longer use keyboard for that. And since I sometimes use laptop without mouse, this would not be too comfortable.

Is there any way out?

---

