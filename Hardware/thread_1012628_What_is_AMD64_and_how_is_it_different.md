---
title: "What is AMD64 and how is it different?"
date: 2008-12-16
forum: Hardware
---

### Post by xarte on 2008-12-16
For some reason I thought of 64 bit computing as 'new' or even 'bleeding edge' so I was gobsmacked to discover that my 4 year old laptop has a 64 bit processor, AMD64. At first I thought it was just meaningless number (maybe that it was as-fast-as or something) until I googled it and see that it is in fact a 64 bit processor.

The pages I found aren't all that helpful though.

Can someone please explain, fairly succinctly for my tired brain

1. what makes the 64 bit processor different 
2.why there is a special edition of some distros for it
3. why the generic edition appears to run fine on it
4. if there are advantages for running the purpose built edition.

I think that about covers it. In short, what do I need to know about my processor?

(How cool is the internet? Don't you love that you can just put a question out there and be fairly confident that someone is going to answer? I love that I'm old enough to still be amazed by technology.)

---

### Post by jespdj on 2008-12-16
Some links for you:

[Advantages and Disadvantages of 64bit. (Plus install Guides)](http://ubuntuforums.org/showthread.php?t=765428) (sticky in the [x86 64-bit Users](http://ubuntuforums.org/forumdisplay.php?f=343) forum).
[x86-64](http://en.wikipedia.org/wiki/X86-64) (Wikipedia)

Most important points of 64-bit processors:
[LIST]
[*]**32-bit processors are limited to 4 GB address space.** That means you can't use more than 4 GB RAM (and in practice, not more than about 3.5 GB).
[*]**An AMD or Intel processor in 64-bit mode is faster.** There are a number of technical reasons for this (more and larger internal registers, a more efficient way of calling subroutines, etc).
[/LIST]

64-bit processors are not that new or bleeding edge anymore. Almost all AMD and Intel processors for laptops and desktops from the last three years or so have 64-bit capabilities.

> **xarte said:**
> The pages I found aren't all that helpful though.
What did you find and why was it not helpful to you?

---

### Post by xarte on 2008-12-16
oh, wonderful. That's a really good post and I can actually read it without my eyes bleeding. I'll click through to some of the linked threads later.

The Wikipedia page was a bit too techy and wordy for me, and the amd page was a sales pitch. Usually my search skills are better than that, but I've been running on too little sleep for far too long, and apathy set in.

---

### Post by sdennie on 2008-12-16
> **jespdj said:**
> 
Most important points of 64-bit processors:
[LIST]
[*]**32-bit processors are limited to 4 GB address space.** That means you can't use more than 4 GB RAM (and in practice, not more than about 3.5 GB).
[*]**An AMD or Intel processor in 64-bit mode is faster.** There are a number of technical reasons for this (more and larger internal registers, a more efficient way of calling subroutines, etc).
[/LIST]


These two statements might be slightly misleading.  It's certainly easiest to use 4G or more of RAM with a 64bit install but, it's possible to use up to 64G on a 32 bit install: [ Ubuntu with 4GB+ of memory]("http://ubuntuforums.org/showthread.php?t=855511")

As for the things being faster in 64bit, yes, some applications will be faster (some possibly even by a lot) but, normal desktop applications aren't likely to see any noticeable speedup between 32bit and 64bit.  Just because an architecture looks superior on paper doesn't necessarily mean that it will be faster in practice.  :)

---

