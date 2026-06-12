---
title: "Dell Inspiron 2500 keyboard mysteriously stopped working"
date: 2007-08-10
forum: Hardware &amp; Laptops
---

### Post by echomikeromeo on 2007-08-10
Completely out of the blue this morning, the built-in keyboard on my Dell Inspiron 2500 laptop stopped responding. Having plugged in an external keyboard (which works just fine), the only thing I could think of to do was to check the xorg.conf file - but it doesn't seem as if there's anything out of the ordinary there. The trackpad works fine; everything else works fine - any idea what's wrong with the keyboard, or any idea what I can do to find out?

---

### Post by SaiGoN DraGoN on 2007-09-03
i had the same problem; i plugged my wireless keyboard and it worked just fine but after i restart none of my keyboards would work (built in and wireless) I searched some threads about it and it said something about finding /.kde/share/config  and modify the file kaccessrc   and change the line SlowKeys=True  to SlowKeys=false     i browsed but there was no file named kaccessrc on the folder  /.kde/share/config 
so i browsed  through System>preferences>keyboard  and set to default but it did not work either, so i looked for such file but even if i could find it i could not type anything because none of my keyboards worked. Here comes the answer :
[COLOR="Red"]**System>Preferences>Accessibility>Keyboard accessibility>Basic**  [/COLOR]     [COLOR="Red"] disable [/COLOR]Slowkeys    (change SlowKeys=true to SlowKeys=false)...then start typing again.


Note: i did all this only using my mouse, remember that keyboard did not work.

Hopefully it will work for you!!!
Good luck!:guitar:

---

### Post by echomikeromeo on 2007-09-03
Thanks, though it did just mysteriously start working again yesterday. Go figure...

---

### Post by Cx90 on 2007-11-30
I've got an old 2500 that I'm using with Ubuntu. I had this problem before, and it turns out the fix for me was that the keyboard became "unplugged" from whatever it was supposed to be plugged into to begin with. It wasn't an Ubuntu issue. I took off the cover surrounding the keyboard and right above the touchpad i could tell that the plug was actually unplugged. perhaps yours is loose?

---

