---
title: "cannot change resolution"
date: 2008-10-25
forum: Hardware
---

### Post by kavurt on 2008-10-25
Hello everybody,

I have a Gateway laptop, 14.1", 1500 celeron, vga controller VIA cn700.

I just installed xubuntu 8.10 rc.

My problem is, my desktop is bigger than screen itself. So when I maximize applications, I cannot see their right and bottom parts on the screen.

I tried to change resolution under
Applications>Settings>Settings Manager>Display.

There are a lot of options available. But when I choose them, a screen appears, but nothing can be seen there. After a few seconds that screen disappears. But the resolution doesn't chance.

I spend whole day on google trying to find a solution. But couldn't find it.

I appreciate any help.

Thanks in advance.

---

### Post by kavurt on 2008-10-28
> **kavurt said:**
> 

My problem is, my desktop is bigger than screen itself. So when I maximize applications, I cannot see their right and bottom parts on the screen.

I tried to change resolution under
Applications>Settings>Settings Manager>Display.

There are a lot of options available. But when I choose them, a screen appears, but nothing can be seen there. After a few seconds that screen disappears. But the resolution doesn't chance.


I found a solution.

Installed Sidux and Altlinux on the same laptop. The screen was perfect on both of them. But they didn't have sound.

Xubuntu didn't have sound as well, but I just to try, copied Sidux's xorg.conf file to a pen drive. Re installed Xubuntu and copied Sidux's xorg.conf file to Xubuntu. 

It worked. The screen is fine now. 

The sound problem wasn't a big deal. After a google search, unclicked "external amplifier" through the Mixer. That solved the sound problem. 

In this case, Xubuntu was lucky. Because I was tired of installing unsuccesfully at least 20 different distributions. So I didn't dare installing once again Sidux or Altlinux to see if the sound problem was the same as Xubuntu's.

I remained with Xubuntu for now. 

But it seemed to me that, Altlinux and Sidux were faster than Xubuntu in spite of they were running KDE. 

I should try them once again.

---

