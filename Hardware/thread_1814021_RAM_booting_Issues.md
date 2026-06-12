---
title: "RAM booting Issues"
date: 2011-07-28
forum: Hardware
---

### Post by climhazzard36 on 2011-07-28
I CAN boot with module A in ANY slot on its own
I CAN'T boot with module B if its in any slot on its own.
I suspect module B is broke.
 
When:
 
No Modules installed: Black screen for 10 seconds then FAIL
 
Module A is in slot 1 and B in slot 2 = FAIL TO BOOT
Module A is in slot 1 and B in slot 3 = FAIL TO BOOT
Module A is in slot 1 and B in slot 4 = FAIL TO BOOT
 
Module B is in slot 1 and A in slot 2 = BOOT 
Module B is in slot 1 and A in slot 3 = BOOT
Module B is in slot 1 and A iin slot 4 = BOOT
 
Module A is in slot 2 and B is in slot 3 = FAIL TO BOOT
Module B is in slot 2 and A is in slot 3 =  FAIL TO BOOT
 
Module A in slot 2 and B in slot 4 = FAIL TO BOOT
Module B in slot 2 and B in slot 4 = FAIL TO BOOT
 
Memtest with just A in slot 1 = PASS 100%
memtest with A in slot 1 and B in slot 3 - PASS 100%
 
I am really confused here, any help would be great!

---

### Post by jerrrys on 2011-07-28
ok, to be sure im on the right page.  Module A and module b are ram sticks and the slots are the ram stick slots.

so before going further, would you please verify that is right thinking on my part.

also this looks like its working

Module B is in slot 1 and A in slot 2 = BOOT 
Module B is in slot 1 and A in slot 3 = BOOT
Module B is in slot 1 and A in slot 4 = BOOT

is that correct?

EDIT:  if this is ram sticks, are they the same brand/model.  if not, that can also mess with you

---

### Post by climhazzard36 on 2011-07-29
Yes thats correct, they are also identical sticks. Strangely soon after this, module B failed to boot in any configuration which means it must of finally died.

What worried me however is that it passed memtest86 just before, is there an explanation for this?

regards, Jamie.

---

### Post by jerrrys on 2011-07-29
did you let memtest86 run its course.  it takes a loooong time

---

### Post by climhazzard36 on 2011-07-29
yeah I let it complete 3 times with 0 errors. 

Iv'e ordered 2x2GB Ripjawx's 1600, so when they come i'll do like 10 runs in each dual chan, then 5ish runs on theyre own to test, just to make sure its not my board.

My memory is not on my mobo'scompatable memory list even though spec wise it was compatable, maybe I was just unlucky haha.

---

### Post by jerrrys on 2011-07-29
best of luck

---

