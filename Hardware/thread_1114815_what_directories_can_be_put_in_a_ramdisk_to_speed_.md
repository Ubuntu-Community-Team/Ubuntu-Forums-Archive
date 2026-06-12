---
title: "what directories can be put in a ramdisk to speed up things?"
date: 2009-04-03
forum: Hardware
---

### Post by Stefan_xfce on 2009-04-03
Hi,

I'm not a native speaker of English, so please excuse any occasional mistakes.

I bought an Asus Eee 1000h and installed Ubuntu 8.10 on it, everything works to my satisfaction after some tweaking (installing the array kernel, finding out how to adress external monitors with xrandr, etc.).

Since I decided to use it as my only computer from now on and sell my other desktop pc, I had the plan of putting additional ram in it, so I obtained a 2 GB ram bar and have plenty of ram now.

Since I'm a standard internet and office user, I actually don't really need that much ram, so I was thinking of trying out to put some directories or files on a ramdisk to speed up the usage of ubuntu/gnome. (Although I can't really complain about the performance now.)

So what I did already, was putting the firefox cache onto a ramdisk, that works pretty fine so far and without any issues.

My actual question now is: What other directories / files are worth putting on a ramdisk to increase speed? How about /var, /tmp, etc.?
Would it make sense to do that? 

BTW: I use the tmpfs method to create a ramdisk, that's easiest for me.

Thanks for your help or sharing your experiences,

cheers,
 Stefan

---

### Post by binbash on 2009-04-03
putting firefox cache to ramdisk will cause you fail on firefox restore.

You can put /usr/bin to ramdisk

---

### Post by Stefan_xfce on 2009-04-03
> **binbash said:**
> 

You can put /usr/bin to ramdisk

Really? Is there any documentation for this?

---

