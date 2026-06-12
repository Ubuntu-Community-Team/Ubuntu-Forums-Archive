---
title: "[SOLVED] How to bind the Right-klick key?"
date: 2008-03-25
forum: Hardware &amp; Laptops
---

### Post by x300 on 2008-03-25
So, on my new laptop (ThinkPad T61) the right-click key (next to AltGr, not the mouse) does not work! This is why i want to bind it to do right klick! (And also bind the annoying next-page, prev-page that ThinkPad has with the arrow-keys).

Using xev i find that the keycode is 227, and using another computer i find that the binding should be Menu (that is now NoSymbol).

The big question is: How do I bind 227 to Menu.

---

### Post by Whiffle on 2008-03-25
Thats weird on the right click key.  Could you post up /etc/X11/xorg.conf ?

On binding the arrow keys, make a file called ~/.Xmodmap and put this in it:
```

keycode 233 = XF86Forward
keycode 234 = XF86Back

```

Gnome should pick that up the next time you log in and then you can bind them to anything you like.  

More info here:
[http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work#xmodmap_configuration](http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work#xmodmap_configuration)

---

### Post by x300 on 2008-03-25
Thanks, it was exactly what I was looking for!

It didn't work with F35 instead as Menu, and the forward, backward-buttons didn't work, but with Menu and binding f/b to page up/down everyting workes perfect! 

I just can't belive that my google-skills failed, when I didn't find that page on my own :P

---

### Post by Whiffle on 2008-03-25
I think the thinkwiki address should be included on every new thinkpad, its gots gobs of great information :)   Their search sucks, but i just search it w/ google.

---

