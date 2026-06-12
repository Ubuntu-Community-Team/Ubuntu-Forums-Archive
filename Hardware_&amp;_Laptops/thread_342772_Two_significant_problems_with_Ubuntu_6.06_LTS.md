---
title: "Two significant problems with Ubuntu 6.06 LTS"
date: 2007-01-20
forum: Hardware &amp; Laptops
---

### Post by lojbanist on 2007-01-20
I recently installed Ubuntu 6.06 LTS on a HP Pavilion dv6000 laptop and am having a few problems. This is my first attempt using Linux after extensive Windows use. It runs smoothly (demonstratably faster than Windows, with a much less cumbersome install), but there are a couple of problems: 

1) (I am not sure if this is due to frequent Windows use) I can not detect what processor I am using. This is important because I recently purchased the laptop, and immediately installed Ubuntu. The sticker on the laptop says "Centrino Duo", but the processor I ordered is "Core 2 duo", which are 32 and 64 bit respectively. Therefor determining my processor is important because by knowing it I can determine which Ubuntu version to use. 

2) I can not uninstall applications. For example, when trying to uninstall "AisleRiot Solitaire" I receive an error that states, and I quote thus: 

> 'gnome-games' is not available in any software channel 

The application may not support your system architecture. 

Knowing that "architecture" can be synonymous with various kinds of computer construction I have tried uninstalling programs on both 32 and 64 bit versions of Ubuntu 6.06 LTS but neither have worked.

I hope that I am not being too pestiferous with my technical support woes; I realize that there is a stigma of Windows users/converts in the Linux community.

---

### Post by teaker1s on 2007-01-20
[http://distrocenter.linux.com/article.pl?sid=05/10/12/1952217&tid=106]("http://distrocenter.linux.com/article.pl?sid=05/10/12/1952217&tid=106")

may help and also I started a wiki page which is about dv6000 laptops
[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29#preview]("https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29#preview")

---

### Post by lojbanist on 2007-01-20
I've solved the problem of uninstalling applications. What I needed was software updates; this would eventually inform me that I was trying to uninstall a program that was a part of a GNOME package, and that I needed to use the advanced uninstaller. I did so, and it worked smoothly.

However, the problem of recognizing my processor persists; I still do not know precisely what processor I am running, and when in the "Device Manager" it is listed genericly as "Processor". Does anyone have an answer?

---

### Post by christhemonkey on 2007-01-20
Can you give the output of this command? (it should also answer your own question...)

```
cat /proc/cpuinfo 
```

---

### Post by lojbanist on 2007-01-20
Ah! I am using a Core 2 Duo after all, indicating that I am using the correct version of Ubuntu. My laptop stickers that I was provided with seem to be mislabeled. Thank you both!

---

### Post by christhemonkey on 2007-01-20
No problem!

---

