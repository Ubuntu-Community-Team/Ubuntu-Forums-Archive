---
title: "Logitech G11 keys"
date: 2007-12-30
forum: Hardware &amp; Laptops
---

### Post by menllyos on 2007-12-30
I recently switched from xp to linux, and i have a G11 keyboard. I dont care about the special G keys and i managed to get the multimedia keys working in amarok by using their ¨Global Shortcuts¨ settings. In the System -> preferences -> keyboard -> layout, i chose a generic 105 key keyboard. 

I got 1 problem with this keyboard; 
The key that has the " (quotation mark) and ' (apostrophe) charactar on it doesnt work. if i type both i get a ¨ (umlaut) and ´ (prime) char. Especially the first one is pretty annoying cause i use it a lot in google to search for strings etc.  any way to fix this ?

EDIT:

ok i found out just now that pressing alt + key and alt + shift + key does give me the quotation mark and the apostrophe... 
is there any way to turn this the other way, that a normal pressing gives me the quotation mark and the apostrope, and that using the alt and alt + shift gives me the umlaut and prime char ?

---

### Post by menllyos on 2007-12-30
ok problems solved. 

Here is how i did it.

First i set the keyboard preference (System -> Preferences -> Keyboard -> layouts) to Generic 105 key with US English International (with dead keys) layout because i knew that my multimedia keys worked under that layout. Then i applied this code in a terminal in my home directory as seen in the [Logitech G15 guide]("https://help.ubuntu.com/community/LogitechG15"):

```
xmodmap -pke > .Xmodmap
```

Make a backup of this file, for example .xmodmap-old. It should contain a few X86Audio lines (from key code 129 and further).

Then i changed to Generic 105 Key with US English default layout. This solved the " and ' key for me. Delete the .xmodmap file and logout and login again. Then do this code again in your home directory. 
 
```
xmodmap -pke > .Xmodmap
```

You should now have a different xmodmap file. 

Now open both xmodmap files, .xmodmap and .xmodmap-old, with gedit or something similar. Copy lines from keycode 129 till the end from  .xmodmap-old and overwrite keycode line 129 and further in the new xmodmap file. This makes sure that the multimedia keys (the X86Audio lines) will also work with the new layout.

Now log out and log in again for changes to take effect. It should all work now. 

ps. It might also be possible to keep the US English International layout and change the " and ' keys manually in the .xmodmap file, but i am not sure of that.

---

