---
title: "very slow after more RAM installed"
date: 2008-08-07
forum: Hardware
---

### Post by stinkinrich88 on 2008-08-07
Hello,

I used to have 2GB of RAM, I now bought the same RAM again to give me 4GB. My mobo is fine with it, Windows XP is fine with it, but Ubuntu (64bit) takes ages to boot (like 20-30mins) and is very slow. The same happened for the live CD, too. What can I do?

Thanks!

p.s. I've done 30mins of memory testing and found no problems

---

### Post by tamoneya on 2008-08-07
what is the speed of both the RAM sticks.  Also what is the configuration? 2x2GB ? 4x1GB?

---

### Post by stinkinrich88 on 2008-08-07
> **tamoneya said:**
> what is the speed of both the RAM sticks.  Also what is the configuration? 2x2GB ? 4x1GB?

I have 4x 1GB OCZ DDR2 800MHz/PC2-6400 CL4(4-4-4-15) 2.2V

When I just 2 sticks it worked fine, but now that I've added another 2 it's slow

---

### Post by tamoneya on 2008-08-07
> **stinkinrich88 said:**
> I have 4x 1GB OCZ DDR2 800MHz/PC2-6400 CL4(4-4-4-15) 2.2V

When I just 2 sticks it worked fine, but now that I've added another 2 it's slow

Everything seems okay there.  Why dont you try installing boot chart so that we can figure out what is slow.  [http://www.bootchart.org/index.html](http://www.bootchart.org/index.html)

Post the png file in /var/log/bootchart after installing and then rebooting.  It will probably take a while to get all that done but I will keep watching the thread until you can get that.

---

### Post by kevmitch on 2008-08-07
It also might be worth while to try booting with each stick individually to see if its an issue with a particular stick.

---

### Post by doas777 on 2008-08-07
as much as I hate to say it, you may wanna RMA. it sucks I know, but unless you've OC'd it, and can undo those changes, the problem is likely out of your hands, unless one of the geniuses around here recognizes it as a known issue.

---

### Post by stinkinrich88 on 2008-08-07
ahhh suxx, alright, check this out:

I tried just three sticks (3GB) and ubuntu works fine and recognises the 3gigs fine. I swapped the new stick to check if one was faulty and it was still fine (no faulty sticks). 

I'll sort out a bootchart for you tomorrow if you want. But I've tried installing bootchart before and it didn't produce the png! Anyway, if it helps, I watched it booting with 4 sticks in recovery mode and I can confirm that everything is very slow (i.e. it does not hang at a certain point, it boots smoothly but slowly).

---

### Post by tamoneya on 2008-08-07
if it wasnt for the fact that it worked okay in windows I would say there is something messed up in the BIOS and that you should flash it.

---

### Post by rad_sci_guy on 2008-08-07
I did the same thing going from 2 gig to 4 gig with the same configuration of ram as you did (it was OCZ as well). I noticed that my system was also slow (it's 64 bit as well) though not as slow as you described.  I did a clean install of ubuntu and now things are working better than ever.  My boot up after logging in seems a touch slower than it was with Gutsy but menus, programs and files transfers are faster than ever.

If it's not a big deal you may want to try a fresh install and see how it takes.

---

### Post by SuperSonic4 on 2008-08-07
My motherboard manual says you should clear the CMOS if you have any problems

---

### Post by stinkinrich88 on 2008-08-08
Hello,

thanks for all your help, I cleared cmos and had no luck. I noticed, however, that BIOS was detecting all 4 cards as 5-5-5-14 800 timings but I bought 4-4-4-15 800 timing ram (here is the product: [http://www.ebuyer.com/product/118306]("http://www.ebuyer.com/product/118306")

I tried manually setting the timings to 4-4-4-15 and BIOS wouldn't even boot, just a black screen until I cleared cmos again. 

Also, with 4 sticks of RAM just after grub it says "kernel direct mapping tables up to 12c000000 @ 8000-e000" but with 3 sticks it says different numbers. Ooh, and when I pulled out my 4th stick (after waiting ages for it to try to boot with 4) it was quite hot! 

p.s. As usual (for me) bootchart doesn't work. /var/log/bootchart is always empty.

---

### Post by doas777 on 2008-08-08
are all 4 sticks unbuffered?

---

### Post by stinkinrich88 on 2008-08-08
> **doas777 said:**
> are all 4 sticks unbuffered?

Sorry, dude, I don't know what that means. They're all straight from the packet, I haven't tried to overclock them or anything. They were both bought from this link:

[http://www.ebuyer.com/product/118306](http://www.ebuyer.com/product/118306)

---

### Post by stinkinrich88 on 2008-08-08
I've semi-solved the problem. I flashed my BIOS with a firmware upgrade and now I can boot Ubuntu at full speed! Trouble is, just before the login screen shows (I get an orange background, though) my computer totally freezes. However, the live cd works totally fine! 

Any ideas?

---

### Post by mikjp on 2008-08-08
You don't usually need any bootcharts to locate the problem, just disable the splashscreen by editing /boot/grub/menu.lst and you will see what the "#"%¤ your hardware spends time on. Probably it is not calculating fractals. You can still do the same to locate the point where your system freezes.

greetings,

mikko

---

### Post by doas777 on 2008-08-08
> **stinkinrich88 said:**
> Sorry, dude, I don't know what that means. They're all straight from the packet, I haven't tried to overclock them or anything. They were both bought from this link:

[http://www.ebuyer.com/product/118306](http://www.ebuyer.com/product/118306)

oh i see. I was under the impression that you already had 2 sticks before purchasing 2 more. 

I've had issues mixing buffering and unbuffered ram, thus my question. Glad the flash is helping out.

---

