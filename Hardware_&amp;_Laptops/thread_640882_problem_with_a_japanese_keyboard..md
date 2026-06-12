---
title: "problem with a japanese keyboard."
date: 2007-12-14
forum: Hardware &amp; Laptops
---

### Post by kjus on 2007-12-14
Hi,

I'm using a japanese keyboard on my laptop (ibm T42), but with a french layout. 
All is working well, except one thing : I would want to map the key which is the second one to the right of the space bar (for example, see [http://upload.wikimedia.org/wikipedia/commons/thumb/2/29/Japanese_keyboards.jpg/800px-Japanese_keyboards.jpg](http://upload.wikimedia.org/wikipedia/commons/thumb/2/29/Japanese_keyboards.jpg/800px-Japanese_keyboards.jpg) ) to the "alt-gr" function.
The keycode for this key is 208, so I've put "keycode 208 = Mode_switch" into my .Xmodmap.
Here the problem comes : when I use xev to see whether the mapping of the key is correct or not, and when I press the key, I get the following lines, WITHOUT having released yet the key. Thus, the problem seems to be that there is a KeyRelease event, BEFORE I actually release the key.

```

KeyPress event, serial 27, synthetic NO, window 0x1600001,
    root 0x59, subw 0x0, time 3675238146, (120,150), root:(125,199),
    state 0x0, keycode 208 (keysym 0xff7e, Mode_switch), same_screen YES,
    XKeysymToKeycode returns keycode: 131
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 27, synthetic NO, window 0x1600001,
    root 0x59, subw 0x0, time 3675238146, (120,150), root:(125,199),
    state 0x2000, keycode 208 (keysym 0xff7e, Mode_switch), same_screen YES,
    XKeysymToKeycode returns keycode: 131
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

After using Ubuntu Gutsy, I was using Breezy (yes, that's old), without any problem (and with the same method)
In the preferences>keyboard options, I've chosen pc105 keys and the "french other" layout.

Any help is welcome :)

---

### Post by monti on 2008-05-12
I'm having the [exact same problem](http://ubuntuforums.org/showthread.php?p=4940902).  Did you ever solve it?

---

