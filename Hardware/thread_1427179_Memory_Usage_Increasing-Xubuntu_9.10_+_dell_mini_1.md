---
title: "Memory Usage Increasing-Xubuntu 9.10 + dell mini 10v..."
date: 2010-03-11
forum: Hardware
---

### Post by vickoxy on 2010-03-11
Hi,
i noticed that my mini 10v uses with the time more and more RAM. After restart, it starts with 10-11% (100-110 MB), then, when i work with some programs, it uses RAM as it should be, but when i close all programs, it stays then at e.g. 142 MB. After then increases to 144.. and so on.
I do not use stand by-just leave the computer to be always on.

The only program that is on is conky (i noticed with multiple conkys and lua scripts, the ram usage increases much faster).

Any idea what this is?

I started with 108 MB Ram using, and after each google-chrome or other session it goes for 1-2 MB up-110, 112, 114, 116... MB

Is there some fix for this?

---

### Post by vickoxy on 2010-03-11
After logout/login ram in idle goes back to 8-10 %/98-104 Mb, but then it increases again.

So, it is definitely system issue. Or?

---

### Post by snowpine on 2010-03-11
It is not an "issue" at all. I am guessing you have at least 1gb ram, and you are using less than 20% of it. Linux is designed to use all of your available ram to make the computer run faster. What's happening in this case is that the data from Chrome (or other applications) is "cached" in case you open that same page again. If your ram starts to fill up and another application needs it, Linux will dump whatever's in the cache to make room.

In other words, unused ram is wasted ram... you should see no drop in performance unless your ram is approaching 100% and you start using swap heavily.

---

### Post by vickoxy on 2010-03-11
> **snowpine said:**
> It is not an "issue" at all. I am guessing you have at least 1gb ram, and you are using less than 20% of it. Linux is designed to use all of your available ram to make the computer run faster. What's happening in this case is that the data from Chrome (or other applications) is "cached" in case you open that same page again. If your ram starts to fill up and another application needs it, Linux will dump whatever's in the cache to make room.

In other words, unused ram is wasted ram... you should see no drop in performance unless your ram is approaching 100% and you start using swap heavily.

Thanks for answer-i didn´t notice-that is true - any drop in performance. Only this cache was growing much faster with three conkys running at the same time - and then i noticed that. But it was probably lua script causing this memory leak...

---

