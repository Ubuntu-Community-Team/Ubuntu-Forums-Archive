---
title: "Dell Inspiron 8600 Suspend Issue on Karmic"
date: 2010-03-15
forum: Hardware
---

### Post by Igneo676 on 2010-03-15
Well, installed Ubuntu 9.10 after wiping windows off my fiancee's laptop, a Dell Inspiron 8600. Not quite as inspiring as I discovered that the suspend function doesn't work (which should have been the very first thing I checked on a LAPTOP but regardless)

It results in a black screen whenever it wakes back up, and me stuck scratching my head. Help?

---

### Post by Igneo676 on 2010-03-18
Well, just so everyone else knows where I am on this...
...changed sleep modules to kernel, cut out the Dell Inspiron section of the quirks.fdi...
...still no luck

---

### Post by Igneo676 on 2010-03-21
Ok, newest and better update...

...tried to hibernate and discovered that it shared the same issue as suspend, but with error messages. One of these days I'll have the laptop in front of me as I type this instead of pure recollection, however, it gave an error of how device (insert series of 0's) didn't cool down, (maybe it was "Thaw") and then when turning on it recorded the same thing about initialization.

For some reason, following the Ubuntu bug reporting system and the solutions contained therein didn't fix the issue...

...anyways, maybe this helps people help me help her :)

---

