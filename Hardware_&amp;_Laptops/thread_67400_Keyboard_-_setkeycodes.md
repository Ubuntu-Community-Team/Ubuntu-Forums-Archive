---
title: "Keyboard - setkeycodes"
date: 2005-09-20
forum: Hardware &amp; Laptops
---

### Post by tanguy15 on 2005-09-20
Hello,

I used 'sudo setkeycodes e02f 130' to attribute a keycode to an unknown key. I had checked before with 'sudo getkeycodes' that 130 is available. 

Then, when I check again 'sudo getkeycodes', 130 corresponds to e02f, but when using 'xev', I get another keycode for that key!

I also tried what is explained with keyboard.c in this post [http://ubuntuforums.org/showthread.php?t=27039&highlight=setkeycodes](http://ubuntuforums.org/showthread.php?t=27039&highlight=setkeycodes)
but it doesn't work either.

Any reason for that, and what to do to get the right keycode ?

Thanks.

Tanguy

---

