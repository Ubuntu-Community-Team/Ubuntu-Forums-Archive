---
title: "External keypad and xmodmap"
date: 2008-12-27
forum: Hardware
---

### Post by Terudon on 2008-12-27
Hi all, 

I normally only read the forums (something about lurking that makes you think you solved the problem yourself :P) but here is a problem which not a lot of people seem to have.

I bought an external keypad the other day, for use next to my wacom tablet (which now thanks to lurking works, yay). The keypad is for binding keyboard shortcuts. Why? Well I'll get into that if someone is too curious :P

For a couple of reasons, I need the "0" on it to be a/the "Shift" key. Using Xmodmap I did this. I sorta works, only with some weird quirks. When testing with Tab it doesn't seem to recognize Shift-Tab on the first try, but keeping my 0/makeshift-shift key pressed en pressing Tab again DOES scroll backwords through links like it's supposed too (and every subsequent tab press after it). Strange!

xmodmapping some other keys, changing "+" and "-" to "up" and "down" (again for my own reasons), broke some metacity-shortkeys using "up" and "down" from the original keyboard and only works with the newly created keys.

Also, Is there a way using  ~./Xmodmap editing to distinguish, for instance, the enter key of the 'normal' keyboard from the external "enter" key on the external keypad?

A lot of questions packed into 1 here but basically: my comprehension of xmodmap isn't fully developed, anyone to shed a light?

Thanks!

Artist Formerly Known As Windows User :lolflag:

---

### Post by Terudon on 2009-01-18
Bump with a twist!

Is there a way so that you can intercept the input coming from a usb device such as this numpad? If it doesn't bind the enter key to enter-key functionality in the first place, we don't have to distinguish between numpad-enter and keyboard-enter.

If there is any unclarity about any of this just ask.

Thanks,

Teru

---

