---
title: "Super key in beryl not working after mapping with xmodmap"
date: 2007-01-01
forum: Hardware &amp; Laptops
---

### Post by mgchan on 2007-01-01
Running Gnome with Beryl on Edgy.  I used xmodmap to map one of my keys (the Access IBM button on my Thinkpad X40) to "Super_R" (I've also tried "Super_L"), and now when I grab the key with beryl-settings, it will say "Super_R" in the box.  However, it does not appear to function as the Super key, and even when I set beryl to run a command with the Super_R that I grabbed, nothing happens.  Is there something else I need to do to activate this?

Even when I switch back to metacity and assign the Super_R key to, say, my home folder, nothing works (although it does correctly grab the key).

---

### Post by jpkotta on 2007-01-01
I'm gonna guess that it's because super is usually a modifier key.  Maybe if you remove it from the modifiers with xmodmap it will work as just a key.  

Show the modifers:
```
xmodmap
```

Remove a modifier:
```
xmodmap -e 'remove mod4 = Super_L'
```

Add a modifier:
```
xmodmap -e 'add mod4 = Super_L'
```

I say it's better to use as a catch-all modifier for all window manager bindings.  For example, open your $HOME with Super-Home.  This is what I do, and it works very well because there are essentially no applications that use Super.

---

