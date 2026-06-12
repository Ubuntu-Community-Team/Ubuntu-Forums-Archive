---
title: "shift key sometimes not working"
date: 2017-05-16
forum: Hardware
---

### Post by jduns on 2017-05-16
i have kubuntu 17.04. in this 6 days the shift key ***sometimes*** does not  work. this issue is with only with kubuntu, not with pclinuxos or  windows10. This happens within the same session. For example, I can not  select more caracters by holding shift key, or I can not write brackets  or question mark. 
and, it's curious in clementine [and in login screen] shift key works always. shift key works normally when i logging as another user.
Thanks for help

my keyboard: logitech k120, italian

running xev and pressing shift left (when shift key is not working)
     ```

KeyRelease event, serial 40, synthetic NO, window 0x4400001, 
  root 0x49d, subw 0x0, time 1033483, (61,-19), root:(724,41),
  state 0x1, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
  XLookupString gives 0 bytes: 
  XFilterEvent returns: False

```

and the code of xev when shift key is working:
     ```

KeyRelease event, serial 40, synthetic NO, window 0x4600001,
   root 0x49d, subw 0x0, time 1860940, (-535,981), root:(113,1010),
   state 0x11, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
   XLookupString gives 0 bytes: 
   XFilterEvent returns: False

```

---

### Post by jduns on 2017-05-17
Now I must "always" say: always shift key, left or right, is not working. Only in my main account, in other user is working normally.
So the problem is: where are stored the wrong user settings?

---

