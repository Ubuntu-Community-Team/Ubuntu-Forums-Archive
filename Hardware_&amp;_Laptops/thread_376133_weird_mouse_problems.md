---
title: "weird mouse problems"
date: 2007-03-04
forum: Hardware &amp; Laptops
---

### Post by Arkleseizure on 2007-03-04
Hi there.

I'm having a weird problem wth my USB mouse, and I can't figure out what's wrong. For the record, I'm sure my mouse is not broken as it works fine in Windows and any live distribution I boot. Up to a few days ago (Friday to be exact) everything was fine; since then my mouse is a mess. I must admit I don't remember if I made any updates on that day.

After bootup, my mouse acts really weird. when I move the mouse, the cursor only moves up and down, and xev shows that the mouse movements are misinterpreted as button clicks. sometimes (around 10%) the mouse works fine after the system booted, but most times it just jerks around.

For some reason the mouse (a Genius Netscroll+ Superior) doesn't work with a PS/2 adapter; however, when I connect an older PS/2 mouse, boot the system, and then connect my Genius mouse, everything works fine.

I've found very few references to this problem, but it didn't lead me anywhere. Any ideas?

Thanks!

---

### Post by scarnia on 2007-03-16
I ve the same problem when compiling new 2.6.20 kernel.

Could anyone help? I boot in 2.6.17 kernel and it works fine, but in 2.6.20 it only move as up and down.

---

### Post by mwshook on 2007-04-22
I upgraded to Feisty, and I have not been able to get my middle button (on the scroll wheel) to work.

At first, I thought it was an xorg.conf problem, and I messed with those settings all day, to no avail. Then I discovered the "xev" program.

The left mouse button shows up as "button 1" , the right button is "button 3" , scroll up is "button 4" , and scroll down is "button 5"

When I click the scroll wheel, nothing happens in the xev terminal. It doesn't seem to recognize this button is even there. Could this still be due to a misconfigured xorg.conf? Is it a new bug in Feisty? Or did that button coincidentally break at the same time I upgraded?

My mouse is a $5 USB model called (no kidding) "I-Rocks IR 7300." It's a pretty generic scroll mouse.

The mouse section of my xorg.conf is below. I've tinkered with it a lot, getting suggestions from posts on this forum, but nothing really changed, except when sometimes X wouldn't start ;-)

>  
Section "InputDevice"
     # generated from default
     Identifier     "Mouse0"
     Driver         "mouse"
     Option	    "CorePointer"
#    Option         "Protocol" "auto"
     Option	    "Protocol" "ExplorerPS/2"
#    Option         "Device" "/dev/psaux"
     Option	    "Device" "/dev/input/mice"
     Option         "Emulate3Buttons" "true"
     Option	    "Buttons" "5"
     Option	    "ButtonMapping" "1 2 3"
     Option         "ZAxisMapping" "4 5"
 EndSection


---

### Post by Arkleseizure on 2007-04-23
> **mwshook said:**
> I upgraded to Feisty, and I have not been able to get my middle button (on the scroll wheel) to work.

At first, I thought it was an xorg.conf problem, and I messed with those settings all day, to no avail. Then I discovered the "xev" program.

The left mouse button shows up as "button 1" , the right button is "button 3" , scroll up is "button 4" , and scroll down is "button 5"

When I click the scroll wheel, nothing happens in the xev terminal. It doesn't seem to recognize this button is even there. Could this still be due to a misconfigured xorg.conf? Is it a new bug in Feisty? Or did that button coincidentally break at the same time I upgraded?

My mouse is a $5 USB model called (no kidding) "I-Rocks IR 7300." It's a pretty generic scroll mouse.

The mouse section of my xorg.conf is below. I've tinkered with it a lot, getting suggestions from posts on this forum, but nothing really changed, except when sometimes X wouldn't start ;-)

My original problem resolved itself the hard way (my cat chewed on the mouse cable, so I needed a new one), but if you can't get all mouse buttons to work it might be worth a try to use the evdev driver instead. There's a guide for the Logitech mice, but it applies for others, too.

[http://ubuntuforums.org/showthread.php?t=219894&highlight=evdev](http://ubuntuforums.org/showthread.php?t=219894&highlight=evdev)

---

