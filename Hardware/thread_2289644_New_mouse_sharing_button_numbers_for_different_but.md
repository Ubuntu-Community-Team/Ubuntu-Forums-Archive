---
title: "New mouse sharing button numbers for different buttons"
date: 2015-08-05
forum: Hardware
---

### Post by amgeddis on 2015-08-05
Coming here for help after googling hasn't shown any obviously helpful suggestions for fix.

I just got a new mouse today and all but one button is working correctly.  The one button in question is right next to the left click and it is being treated the same as left click.  Anyone have any ideas how to fix this?

Xev shows this same output for both button presses:

> ButtonPress event, serial 39, synthetic NO, window 0x4000001,    root 0x293, subw 0x0, time 2787414, (86,49), root:(115,164),
    state 0x10, button 1, same_screen YES


ButtonRelease event, serial 39, synthetic NO, window 0x4000001,
    root 0x293, subw 0x0, time 2787444, (86,49), root:(115,164),
    state 0x110, button 1, same_screen YES

Here's my mouse and the button in question is number 7:
[IMG]http://ecx.images-amazon.com/images/I/81pvoymnAXL._SL1500_.jpg[/IMG]

Edit:  It actually looks like the button is being registered as a double left click... going by the button name of X2 it's "working as intended".

So rephrasing the question:  Anyone know how to change it from being a double click to being its own independent button?

---

### Post by CantankRus on 2015-08-07
You can't. It just replicates a double click.
PS I just received the same mouse from ebay for  AU $7.95
The mouse seems fine for the price but with a lowest dpi of 1000(red) 
and with the pointer speed set as low as it goes in settings, it still moves to fast.
Need a mouse that goes down to 400 dpi. 1000 is way to high for the lowest dpi setting.

---

### Post by amgeddis on 2015-08-07
> **CantankRus said:**
> You can't. It just replicates a double click.
PS I just received the same mouse from ebay for  AU $7.95
The mouse seems fine for the price but with a lowest dpi of 1000(red) 
and with the pointer speed set as low as it goes in settings, it still moves to fast.
Need a mouse that goes down to 400 dpi. 1000 is way to high for the lowest dpi setting.
Thanks for the reply and you're right it looks like that button can only ever do a double click.  I bought the mouse because I needed just one more button to comfortably play a video game and I already have a nice perixx mouse with forward and back buttons.  I don't think it's worth sending it back since it was only $12 so I'm keeping it in case I ever need a backup.

I guess I'll buy myself a Logitech G300 since it looks like it fits the bill and only needs a little tweak to work correctly on linux.

---

