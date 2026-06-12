---
title: "Only Period key not working on keyboard post upgrade to ubuntu 10.10"
date: 2011-05-15
forum: Hardware
---

### Post by Ronin_R on 2011-05-15
heyo!

I recently upgraded to 10.10 from 10.04
Post upgrade I was having problems with my keyboard.
zxcvbn keys of the lower row of keyboard were not working.

They have started working now themselves, but I cannot get period/dot(.) key to work.It wont work even with the virtual keyboard.But it does recognizes a change when I press it.Moreover,when I press it with Shift,I can see '>' greater than symbol.I am using the period key on numpad currently.

It works in my when I load my previous linux kernel image.

I tried xmodmap.
part of its output is : :

keycode  52 = z Z z Z
keycode  53 = x X x X
keycode  54 = c C c C
keycode  55 = v V v V
keycode  56 = b B b B
keycode  57 = n N n N
keycode  58 = m M m M
keycode  59 = comma less comma less
keycode  60 = period greater period greater
keycode  61 = slash question slash question
keycode  62 = Shift_R NoSymbol Shift_R
keycode  63 = KP_Multiply XF86_ClearGrab KP_Multiply XF86_ClearGrab

xev shows ::

KeymapNotify event, serial 36, synthetic NO, window 0x0,
    keys:  66  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0  


I have searched a lot.I cannot get it to work :(

Can someone guide me on the path ahead ? :-)

---

### Post by mörgæs on 2011-05-15
If it works using the previous kernel, I would simply stick to this one. You will get new kernels in a steady flow from the updates, so just wait and see if a new one works better.

---

### Post by Ronin_R on 2011-05-20
thanks for the reply bro :)

---

