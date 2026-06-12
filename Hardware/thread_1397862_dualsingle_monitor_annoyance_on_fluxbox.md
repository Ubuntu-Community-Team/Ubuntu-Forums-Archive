---
title: "dual/single monitor annoyance on fluxbox"
date: 2010-02-03
forum: Hardware
---

### Post by tanyeun on 2010-02-03
hi guys,

I am using IBM X61 with external monitor at home
which I don't need when I am in school
something bothers me is that
some program for example firefox I turn it off
on the external screen
when I turn it on using my laptop without external monitor
it will not show up on my laptop screen

it really bothers me
I have to remember to turn off every program 
I used on my laptop screen
if not, next time if I use it without external monitor
I have no way to access it bcs the program is open 
outside my laptop screen

I am not sure it's x-server's issue or fluxbox's issue
any idea to fix this?

thx,

David

---

### Post by tanyeun on 2010-02-12
I figured out a simple solution
no matter what extension of external screen
just type
```
xrandr --output VGA --off
```
after removing the external screen
that way the WM will scale everything back to small screen

---

