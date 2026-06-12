---
title: "Keyboard woes, HP Mini"
date: 2015-05-22
forum: Hardware
---

### Post by LiamG on 2015-05-22
&#65279;I have been using Lubuntu on my HP mini 110-1000 for about a year. I started on 14.10 and now upgraded to 15.04. It generally works well, except that the keyboard has a lot of quirks. Some keys dont work, especially capitalized keys and punctuation marks, or work very inconsistently. It feels exactly like a physical problem with the keyboard, only I am sure that it is not, because if I boot my computer without Lubuntu (ie. on a USB startup disk) it works perfectly. Had anyone encountered this before? Is there anything I can do to fix it?

---

### Post by thatredbird on 2015-05-22
If it is specific keys for the manufacturer you could specifically set those keys up in the keyboard settings(in openbox).  This is a basic over view [http://openbox.org/wiki/Help:Bindings](http://openbox.org/wiki/Help:Bindings) .  The other choice is to play around with keyboard layouts, there should be several options. this page also has documentation.  [https://help.ubuntu.com/community/Lubuntu/Keyboard#Keyboard_Layouts](https://help.ubuntu.com/community/Lubuntu/Keyboard#Keyboard_Layouts)

---

### Post by kerry_s on 2015-05-22
try xubuntu 15.04, 14 lts will also work, but 15 is so much nicer.

i have the hp mini 210-1010nr, under xubuntu everything works, even the f4 key for display.
it's the only one i found to have everything working on the keyboard. i'm currently trying ubuntu-mate & it's f4 key opens the menu.
other than that, ubuntu-mate also works fine on the hp mini, better than lubuntu, which felt like a clug of apps that are trying to work together, but your bouncing here and there to find the right settings.

---

### Post by kerry_s on 2015-05-22
i don't know if you know, but if you install zram-config you can maximize your ram. your's is like mine 2gb max ram. hope you have 2gb cause it's totally worth the upgrade, also using a ssd gives a great performance boost.

---

### Post by LiamG on 2015-06-01
Thanks for the suggestions, everyone. (Kerry, zram_config is fantastic!)

I did look at keyboard layouts and found a better one (International AltGr dead keys). Things are working better now, but not perfectly. Some of the capitalizations and punctuation marks only work after I depress the shift keys. I have to press shift, press the key and then lift my finger off shift before the letter comes through. Most others work as normal. Is this something to do with the mapping?

---

### Post by gordintoronto on 2015-06-02
Where are you located? What keyboard did you specify when you installed? Is the problem consistent, or it comes and goes? (Which might indicate a loose connector or dirt in the connection, or even a "cold joint".) I assume that if one of the letter keys never works, the computer would be unusable...

+1 to the Xubuntu suggestion.

---

