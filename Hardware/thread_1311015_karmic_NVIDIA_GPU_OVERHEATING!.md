---
title: "karmic NVIDIA GPU OVERHEATING!"
date: 2009-11-02
forum: Hardware
---

### Post by krantix on 2009-11-02
Since karmic, my toshiba laptop won't load its custom and fixed DSDT, therefore the laptop runs the GPU as high as 120 degrees. Is there any easy way to load a custom dsdt and avoid overheating?

---

### Post by JEP on 2009-11-13
I have the same problem with a Toshiba P100. I saw a possible solution here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337)

although this refers to Acer laptops. Someone near the bottom says it also fixed his Toshiba m105...

Link to patched kernel here:

[http://people.canonical.com/~apw/lp451337-karmic/](http://people.canonical.com/~apw/lp451337-karmic/)

But I now have a later kernel, 2.6.31-15 and I still have the issue. Does this mean the fix did not make it into the newer kernel? Maybe I should downgrade and try it?

---

### Post by JEP on 2009-11-19
Tried everything I could think of, no luck.  I have filed a bug here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/484875](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/484875)

We'll see if anyone looks at it.

---

