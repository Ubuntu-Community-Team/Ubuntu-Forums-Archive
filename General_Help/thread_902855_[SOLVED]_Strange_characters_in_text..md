---
title: "[SOLVED] Strange characters in text."
date: 2008-08-27
forum: General Help
---

### Post by Bruce M. on 2008-08-27
Hi Folks...

Can anyone shed any light on why I see strange characters like this in some websites:

```
starting&#65533;here!&#65533;
```

Thanks.

Have a nice day.
Bruce

---

### Post by rossjman1 on 2008-08-27
Are you seeing black emerald (i don't know what the shapes are called) shapes with white question marks? That's what I see, and this is the first time I've seen such a thing. What websites do you go to?

---

### Post by Shippou on 2008-08-27
> **rossjman1 said:**
>  What websites do you go to?

Porn sites! :lol: Just joking.

I think these are what should be called "nonprintable characters". Or maybe you are viewing cached pages. Sometimes this is the problem.

Anyway, as you can guess, these characters should be spaces.

---

### Post by Bruce M. on 2008-08-28
> **rossjman1 said:**
> Are you seeing black emerald (i don't know what the shapes are called) shapes with white question marks? That's what I see, and this is the first time I've seen such a thing. What websites do you go to?

Yes, that's them, Black with white question marks.

Can't recall, it was while Googling for information on making bootable CD's.

---

### Post by Bruce M. on 2008-08-28
> **Shippou said:**
> Porn sites! :lol: Just joking.

I think these are what should be called "nonprintable characters". Or maybe you are viewing cached pages. Sometimes this is the problem.

Anyway, as you can guess, these characters should be spaces.

No not porn sites, I don't do those. Computer is in the living room and my wife would KILL me and more importantly, they just plain don't interest me.

See above, it happened while searching for information, so the pages are not cached.

I though: maybe a UTF8 type thing, don't know how to check that.

---

### Post by aloshbennett on 2008-08-28
Bad coding + stupid fonts + your browser's character encoding?

---

### Post by rossjman1 on 2008-08-28
Hmm. I have never seen this before, but I just encountered it. [http://www.bestbuy.com/site/olspage.jsp?skuId=8967335&type=product&id=1216425209738](http://www.bestbuy.com/site/olspage.jsp?skuId=8967335&type=product&id=1216425209738) Specifications > processor info.

---

### Post by mssever on 2008-08-28
Those are the result of website authors either not specifying the character encoding and you browser guessing wrong, or specifying the wrong one. Web authors who do that should be shot, but unfortunately it's somewhat common.

There are two ways to fix this. First, complain to the webmaster. Then, work around the problem by (in Firefox) going to the View menu and choosing a different character encoding from the menu. Most of the problems I've encountered occur between UTF-8 and ISO-8859-1. You'll just have to guess until you find the correct encoding.

---

### Post by Bruce M. on 2008-08-28
> **mssever said:**
> Those are the result of website authors either not specifying the character encoding and you browser guessing wrong, or specifying the wrong one. Web authors who do that should be shot, but unfortunately it's somewhat common.

There are two ways to fix this. First, complain to the webmaster. Then, work around the problem by (in Firefox) going to the View menu and choosing a different character encoding from the menu. Most of the problems I've encountered occur between UTF-8 and ISO-8859-1. You'll just have to guess until you find the correct encoding.

Thank you.
Very much appreciated.

Have a great day.
Bruce

---

