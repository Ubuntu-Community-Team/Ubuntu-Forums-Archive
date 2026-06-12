---
title: "HP 6230 woes"
date: 2006-07-05
forum: Hardware &amp; Laptops
---

### Post by Zodiac on 2006-07-05
When installing Linux on my brand new HP 6230 I am having some networking problems.

I can't get my ethernet working... it detects my card okay, but I cannot seem to get it working.

Does anyone have any suggestions on steps I can take to get this working?

My card is a:

**Broadcom NetXtreme BCM5751 Gigabit Ethernet**

Any help is greatly appreciated!

Thanks!

---

### Post by tonyr on 2006-07-05
The bad news is that some **Broadcom**'s do not seem to work well, or at all,
in 6.0.6.  There is considerable discussion about it in these forums.  Search on
**broadcom**.  I only found one reference to 5751, and it was not good.  There
is a  [Broadcom Howto]("http://www.ubuntuforums.org/showthread.php?t=185174") thread, but you should expect to be disappointed.  
Sorry to be so negative.  Good luck.

---

### Post by Zodiac on 2006-07-06
So far no luck :(... 

and this isn't even a wireless connection... this is wired. Without internet this is really hard to fix. 

Sigh.

Looks like Dapper isn't going to work. Is there a distro that will maybe?

---

### Post by gotfoo on 2006-07-06
Or try this [howto ]("http://www.ubuntuforums.org/showthread.php?t=190177").

---

### Post by Zodiac on 2006-07-06
[QUOTE=gotfoo]Or try this [howto ]("http://www.ubuntuforums.org/showthread.php?t=190177").[/QUOTE]

But the card isn't a wireless one...

---

### Post by gotfoo on 2006-07-06
Sorry about that.

It's just that so many posts are about wireless issues that I just assumed...](*,)

---

### Post by Zodiac on 2006-07-06
No no, its understandable...

Still, if anyone else has any options, I would be grateful...

---

### Post by christian.convey on 2006-07-06
I've heard that when people have problems with wired ethernet cards, it's sometimes worth forcing the kernel to use the "forcedeth" driver rather than whatever one it was using for the card.  I don't know if that approach is still valid, or how you do it, but at least it gives you a term to google.  Good luck.

---

