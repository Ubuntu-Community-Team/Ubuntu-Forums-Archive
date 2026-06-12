---
title: "Slow speeds after RAM upgrade"
date: 2006-10-13
forum: Hardware &amp; Laptops
---

### Post by philbob on 2006-10-13
Hi,

Im just trying to install Ubuntu Dapper (6.06) on an Asus p4c800-e mb, with a 2.8Ghz Intel HT processor. 

All works fine with my original 1Gb ram (2x 512MB sticks) of DDR pc3200 running in dual channel mode.

However when I put in a 2nd pair of 512MB memory of the same spec, everything runs at about 1/4 or less of the speed!

The RAM passes the mem tests ok and windows runs fine, as it boots in usual time & runs slightly better than before - as to be expected.

I did leave the Ubuntu install to complete, & it took about an hour (took about 10-15 mins with just the 1GB), and everything runs slow.

So I was wondering if anyone could make any suggestions to possible causes/solutions for Ubuntu?

If you need any more info please let me know. Thanks!

---

### Post by diepruis on 2006-10-13
<< Sorry, misread your post. >>

---

### Post by Kateikyoushi on 2006-10-13
Are you using XGL and compiz ?

---

### Post by PriceChild on 2006-10-13
Are both sticks of RAM the same frequency?

*moves to Hardware and Laptops*

---

### Post by philbob on 2006-10-13
Hi Kateikyoushi & PriceChild


@Kateikyoushi:
I don't think so - Im running the default install (sorry I'm new-ish to linux, so am not sure).

To note: Things run super slow even if I run the text installer, so I don't think its a graphics related issue.


@PriceChild:
All 4 RAM modules are DDR400, & each are paired up. 

One thing I have just realised - my old RAM was ECC, where-as the new RAM is non-ECC. From what I can tell the mobo has put everything into non-ECC mode, not sure if this could be the possible cause? I wouldn't of thought so, but thats just a guess...

---

### Post by Kateikyoushi on 2006-10-13
I found [this thread]("http://www.ubuntuforums.org/archive/index.php/t-210615.html") quite similar that's why I thought.
A pity they did not figure out how what actually solved it.

---

### Post by philbob on 2006-10-13
I did spot that thread while searching, thanks for pointing it out though.

I'm starting to feel like this guy ](*,)!

Ahh well, back to windows for now while I search for the solution to this.

---

### Post by visionaire on 2007-10-19
Hi i just upgrade RAM from 512 to 1G and also have this slowness, it's awful :(
in both dual and single channel, it's the same, it's almost immpisble to my pc, it's not a laptop by the way, windows runs ok, all the RAM is detected

Any help please! don't want to drop kubuntu :(

---

### Post by Salvador Staniol on 2007-10-28
Same here,

went from 2 x 512 corsair twinx3200-c2 to 4 x 1024 corsair twinx3200-c2 on Asus p4c800 deluxe.

has anybody with this sort of problem tried to reinstall ubuntu?

---

### Post by drygal on 2008-01-23
Hi All,

I have the same problem. This is so annoying. I've put them in all possible combinations, reinstalled Ubuntu 5 times and still nothing. It works fine on two sticks 512 each (no matter which ones). You can see this from the very start when the system boots up. 

Any idea, anyone? Help !!! :-?

---

### Post by drygal on 2008-01-26
I have a solution for my case. After reading [http://stason.org/TULARC/os/linux-faq/086-Why-Does-the-System-Slow-to-a-Crawl-When-Adding-More-Memory.html](http://stason.org/TULARC/os/linux-faq/086-Why-Does-the-System-Slow-to-a-Crawl-When-Adding-More-Memory.html) I followed the topic further and it turned out that it was BIOS fault. After flashing to a new version it works perfectly.

---

