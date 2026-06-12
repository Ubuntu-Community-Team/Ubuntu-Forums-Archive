---
title: "Microsoft wireless multimedia keyborard 1.1"
date: 2011-01-22
forum: Hardware
---

### Post by kirsty.football on 2011-01-22
I am having problems getting my microsoft wireless multimedia keyboard to work wondering if any one can help. 
None of the keys are working properly for instance if I press backspace it comes up with 0 if i press 0 it does backspace all the keys are like this.

I have checked the keyboard layout which is correct (uk)

---

### Post by rupert160 on 2011-05-06
There is a very good article at: 
[http://cweiske.de/howto/xmodmap/allinone.html#whybyhand]("http://cweiske.de/howto/xmodmap/allinone.html#whybyhand")
I found that buy using xev and getting the key numbers,
then creating a ~/.Xmodmap file like he recommended I got access to the remaining keys.
this is the contents of my ~/.Xmodmap: 

rupert@jekyll:~$ cat .Xmodmap
keycode 156 = XF86Documents NoSymbol XF86Documents 
keycode 157 = XF86Pictures  NoSymbol XF86Pictures
keycode 221 = XF86Music     NoSymbol XF86Music
keycode 224 = XF86Messenger NoSymbol XF86Messenger 

i then ran (one time only) xmodmap ~/.Xmodmap

then finally I went to keyboard shortcuts in System>Preferences and mapped them.

---

