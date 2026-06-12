---
title: "Questions about Ubuntu 64bit edition"
date: 2009-08-27
forum: Hardware
---

### Post by Rackstar on 2009-08-27
Hi,

I was planning to boost my RAM on my laptop to 4GB. But when I did, I noticed that only 3GB was addressed. (I thought the 32bit edition of Ubuntu could handle 4GB, and windows only 3GB, apparently I was wrong)

So I checked my processor (Intel T5500), and I saw that I can run the 64bit version of Ubuntu.

I have some questions:
1) Can I install 32bit software onto 64bit ubuntu?
2) Can I use 32bit drivers (Nvidia Geforce Go 7300) if the 64 bit drivers get buggy?
3) I read about problems with flash in 64bit, but again, can I install 32bit, if I notice troubles?
4)  Will I notice a difference in speed (or something else on that matter)?

Thanks!

---

### Post by Menthu_Rae on 2009-08-27
> **Rackstar said:**
> Hi,

I was planning to boost my RAM on my laptop to 4GB. But when I did, I noticed that only 3GB was addressed. (I thought the 32bit edition of Ubuntu could handle 4GB, and windows only 3GB, apparently I was wrong)

So I checked my processor (Intel T5500), and I saw that I can run the 64bit version of Ubuntu.

Yep, you can run 64-bit as you know:

[http://processorfinder.intel.com/details.aspx?sSpec=SL9SH](http://processorfinder.intel.com/details.aspx?sSpec=SL9SH)

:)

> **Rackstar said:**
> I have some questions:
1) Can I install 32bit software onto 64bit ubuntu?

Yes you can, but it won't always work or work how it's intended. If you want to manually install something, you can download the .deb and use:

```
sudo dpkg --force-architecture -i filename.deb
```

> **Rackstar said:**
> 2) Can I use 32bit drivers (Nvidia Geforce Go 7300) if the 64 bit drivers get buggy?

I'm sure the 64-bit drivers would be fine? I have no issues with nvidia drivers on 3 of my 64-bit Ubuntu 9.04 systems. :)

> **Rackstar said:**
> 3) I read about problems with flash in 64bit, but again, can I install 32bit, if I notice troubles?

There is a 64-bit flash prerelease available:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Install guide here:

[http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html](http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html)

I'm using it on my desktop system and it works fine.

> **Rackstar said:**
> 4)  Will I notice a difference in speed (or something else on that matter)?

Thanks!

You won't really notice a difference unless you're using very CPU-intensive or RAM-intensive apps. Ubuntu 64-bit is (in my experience at least) just as stable, fast and reliable as the 32-bit version. :popcorn:

---

### Post by Rackstar on 2009-08-27
Wow, thanks for your time! :)

So Flash 64, normally wouldn't be a problem? And if it would... I could install the 32bit version? (As I understood)

I almost never use Wine, unless for some small tools. I read about the latest Wine versions 'added support for 64bit' but does this mean it runs as smooth as normal?

I wanted to add more RAM to my system, because I often use Bibble (RAW converter, photo library system, image editor), which takes a lot of RAM.

So besides the ability to address more memory, there aren't much advantages to 64bit?

---

### Post by Grenage on 2009-08-27
There aren't many other advantages, native AMD64 apps can be faster; I recommend using 64.

---

### Post by Rackstar on 2009-08-27
64bit is the future ofcourse. But I don't want to get myself into trouble again by doing special, when it's not really necessary :)

But as I get a lot of questions about 64bit etc, it's probably best to try it out at least. (I really was suprised my processor could handle that, I thought you have to had some sort of special processors).

If somebody else has their opinion, please share. I'm eager to learn.

Why is it, that 64bit is still something 'exotic'?

Thanks, excellent help, once again!

---

### Post by Grenage on 2009-08-27
> Why is it, that 64bit is still something 'exotic'?

It was 5 years ago, but it's **very** common now.

---

### Post by Rackstar on 2009-08-27
> **Grenage said:**
> It was 5 years ago, but it's **very** common now.

Ok, thanks! Apparently I'm a little outdated myself :)

---

### Post by Grenage on 2009-08-27
Well most people do use x32, and it's all they need; Any New or modern machine should ideally be x64. :)

---

