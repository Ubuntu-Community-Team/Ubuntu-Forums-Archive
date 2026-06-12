---
title: "4 GB of RAM on 32-Bit Ubuntu..."
date: 2008-12-13
forum: Installation &amp; Upgrades
---

### Post by pacmanghostx on 2008-12-13
So, my aunt gave me her four-year-old Dell after she upgraded, and I'm planning to install 32-Bit 8.04.  I'm curious as to 32-Bit being able to support the 4 GB of memory I have on hand, or will 32-Bit be limited to some strange number like 3.25 GB?

Also, I don't really want to install 64-Bit as right now I only have 512 MB of RAM at this time.

---

### Post by pacmanghostx on 2008-12-13
My apologies, wrong thread...

---

### Post by pacmanghostx on 2008-12-13
So, my aunt gave me her four-year-old Dell after she upgraded, and I'm planning to install 32-Bit 8.04.  I'm curious as to 32-Bit being able to support the full 4 GB of memory I have on hand, or will 32-Bit be limited to some strange number like 3.25 GB?

Also, I don't really want to install 64-Bit as right now I only have 512 MB of RAM at this time and I'm not 100% sure if my processor supports 64-Bit.

---

### Post by lukjad on 2008-12-13
I think that you can get about 3.5 gigs to be recognized, but if you put 4 gigs on, it *should* still work, though the full 4 gigs will not be used.

EDIT: I found out that there is something called PAE that you can enable that allows for up to 64 GiB of RAM.

---

### Post by logos34 on 2008-12-13
try this workaround:

[http://www.yellow-bricks.com/2008/11/12/ubuntu-32bit-and-4gb-of-memory/](http://www.yellow-bricks.com/2008/11/12/ubuntu-32bit-and-4gb-of-memory/)
[http://samiux.wordpress.com/2008/06/15/use-more-than-3gb-ram-on-32-bit-ubuntu-804/](http://samiux.wordpress.com/2008/06/15/use-more-than-3gb-ram-on-32-bit-ubuntu-804/)

I don't even know you could do that until now.  

So I guess you just boot the server kernel and use that.  You can then add desktop for gui.

sudo apt-get install ubuntu-desktop

let us know how it goes

---

### Post by Kilz on 2008-12-13
> **pacmanghostx said:**
> So, my aunt gave me her four-year-old Dell after she upgraded, and I'm planning to install 32-Bit 8.04.  I'm curious as to 32-Bit being able to support the 4 GB of memory I have on hand, or will 32-Bit be limited to some strange number like 3.25 GB?

**Also, I don't really want to install 64-Bit as right now I only have 512 MB of RAM at this time**.

This statement makes no sense. If you dont have 4GB why did you even ask the question. If you have 4g, even outside of the machine at present you should install the 64bit version. Even on 512, with a swap it should run ok. But if you have the ram not installed, well install it.

---

### Post by pacmanghostx on 2008-12-13
Sounds good, and I cheack my BIOS; no 64-Bit Support.

Thanks for the advice. *thanked*

---

### Post by ke9vee on 2008-12-13
> **pacmanghostx said:**
> So, my aunt gave me her four-year-old Dell after she upgraded, and I'm planning to install 32-Bit 8.04.  I'm curious as to 32-Bit being able to support the 4 GB of memory I have on hand, or will 32-Bit be limited to some strange number like 3.25 GB?

Yes. My 32-bit Ubuntu install on a laptop with 4Gb of memory reports less than 4Gb. Something like 3.5 as I recall.

---

### Post by damis648 on 2008-12-13
Please do not post duplicate threads.

---

### Post by zgornel on 2008-12-13
> **pacmanghostx said:**
> So, my aunt gave me her four-year-old Dell after she upgraded, and I'm planning to install 32-Bit 8.04.  I'm curious as to 32-Bit being able to support the 4 GB of memory I have on hand, or will 32-Bit be limited to some strange number like 3.25 GB?

Also, I don't really want to install 64-Bit as right now I only have 512 MB of RAM at this time.

Does the system even support 4GB of ram ? If it does, only 3.2-3.5 will be actually used on a 32 bit OS. If you want all 4GB to be available, install a 64 bit OS if the processor supports it.

---

### Post by damis648 on 2008-12-13
Please do not post duplicate threads.

You could either
1. Install the server kernel, as the above user suggested.
2. Install 64-bit Ubuntu.
or
3. Compile your own kernel with support for 64GB RAM, but this is an advanced task.

---

### Post by pacmanghostx on 2008-12-13
> **Kilz said:**
> This statement makes no sense. If you dont have 4GB why did you even ask the question. If you have 4g, even outside of the machine at present you should install the 64bit version. Even on 512, with a swap it should run ok. But if you have the ram not installed, well install it.

I asked because I have the RAM, I'm just wondering what I can install.

And yes, by computer supports 4 GB, but the CPU doesn't support 64-Bit. Go figure.

---

### Post by sdennie on 2008-12-13
To re-iterate what damis648 said, see this guide: [ Ubuntu with 4GB+ of memory]("http://ubuntuforums.org/showthread.php?t=855511")

---

### Post by CyberPrime on 2008-12-13
Yea, the mobo might support it just fine, but if you are using a 32Bit OS then it won't support it (It depends on your Video card and other cards, but it should be about 2.75 (Nice Graphics cards with lots of memory) to 3.5 (crappy graphics cards and other cards).)

Put in the 4 gigs, see how much you get and adjust from there. But yea, unless you wanna spring for a new 64 bit CPU or compile your own kernel (if you don't know the answer to a question like this then it would prove difficult) then you won't get the full 4GB. Sorry.

HAND

---

