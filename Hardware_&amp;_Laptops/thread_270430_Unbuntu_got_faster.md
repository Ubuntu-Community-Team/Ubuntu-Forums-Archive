---
title: "Unbuntu got faster"
date: 2006-10-03
forum: Hardware &amp; Laptops
---

### Post by SirShaggy on 2006-10-03
I have a Compaq Presario 2535QV notebook. It has a Pentium 4 2.4GHz CPU with 1024MB or RAM and is usually a dog. I initially installed Ubuntu out of the box. I ran it for the last three months that way. Learning the ins and outs as I went. Tonight, I decided to try out several tweaks and performance modifications I read about here on the forums. I have to say, WOW! My laptop is the fastest I have seen it.
I made the /boot partition ext2 FS, I installed the 686 kernel and restricted modules.
I installed prelink, I profiled the boot, configured hdparm, reduced the GTK popup menu delay, I enabled CFQ, reduced the tendency to use swap, cleaned up and deleted unused/unnecessary files and reset my readahead. It took me about 2 hours to do it all. It was a huge success for me, maybe you'd like to see the links I found. All of them say there are risks, I suggest reading through the list and look around the forums for people who had trouble. That way you know how to fix your box if something breaks!

10/03/06 3:41
I just edited these links, I had a duplicate. Sorry about that:-D 
this first one is for reprofiling bootup and resetting readahead:
[http://ubuntuforums.org/showthread.php?t=254263&highlight=ubuntu+tweaks](http://ubuntuforums.org/showthread.php?t=254263&highlight=ubuntu+tweaks)

next, setup Prelinking:
[http://ubuntuforums.org/showthread.php?t=74197](http://ubuntuforums.org/showthread.php?t=74197)

Next, set swappiness, enable CFQ and reduce GTK menu delay:
[http://ubuntudemon.wordpress.com/2006/07/14/desktop-performance-tweaks/](http://ubuntudemon.wordpress.com/2006/07/14/desktop-performance-tweaks/)

Enable DMA , tweak ext3 FS and clean up junk files:
[http://www.ubuntuforums.org/showthread.php?t=189192](http://www.ubuntuforums.org/showthread.php?t=189192)

Setup HDPARM: The first link is a tutorial, second shows all.
[http://articles.techrepublic.com.com/5100-10877_11-5551745.html](http://articles.techrepublic.com.com/5100-10877_11-5551745.html)
[http://www.die.net/doc/linux/man/man8/hdparm.8.html](http://www.die.net/doc/linux/man/man8/hdparm.8.html)

I also found a link to improve OpenOffice a bit:
[http://openoffice.blogs.com/openoffice/memory/index.html](http://openoffice.blogs.com/openoffice/memory/index.html)

Lastly, I just tweaked my broadband connection following this guide:
[http://ubuntuforums.org/showthread.php?t=251509&highlight=How+To%3A+Tweak+Linux+for+broadband](http://ubuntuforums.org/showthread.php?t=251509&highlight=How+To%3A+Tweak+Linux+for+broadband)

Most of these are around here, on the forum. I just thought this may be handy for someone to have the links all together.

SirShaggy

UPDATE: I ended up saving 23 minutes of battery time and increased performance! Recesntly, I installed a 7200 RPM Hard Drive
with 8Mb cache and a P4 2.8GHz CPU for even more performance. These two chances took the 23 minutes back from me, but made my
laptop even faster yet. All in all, Ubuntu is a fun, fast and stable distro. Just plan out your install and you will have a
good performing box.

---

### Post by Rui Pais on 2006-10-03
hi, your 3rd link is wrong (duplicate of 4th...)

---

### Post by xyz on 2006-10-04
Thanks SirShaggy for putting this up all on  page!
Nice job!

---

### Post by SirShaggy on 2006-10-04
I know the information is all over the forums and web, I just got tired of always searching for it. I think this may save someone some time. There are other modifications and tweaks that I have seen, I haven't done them and haven't found them again to try:(

---

### Post by Rui Pais on 2006-10-05
Hi again, check this post [here]("http://ubuntuforums.org/showthread.php?p=1096263#post1096263") too. 
It has a lot of suggestions.

Rui.

---

### Post by xyz on 2006-10-05
Thanks again! I had done quite a bit of tweaking before but prelinking and ubuntu_demon's site made an incredible difference on my box which was not that slow to begin with...or so I thought!
In fact I made a system backup immediately after the tweaking job!

Could you please take a look at this...
> th@luser:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           486        480          6          0         26        228
-/+ buffers/cache:        226        260
Swap:         1419          0       1419

I got this by setting swapniness to 0...is it OK according to my specs?
Toshiba Satellite A 40 (2 years old)
2.7 GHz - 512 RAM Dual Boot 80G HD

Thanks for reading!

---

### Post by SirShaggy on 2006-10-05
> **xyz said:**
> Thanks again! I had done quite a bit of tweaking before but prelinking and ubuntu_demon's site made an incredible difference on my box which was not that slow to begin with...or so I thought!
In fact I made a system backup immediately after the tweaking job!

Could you please take a look at this...


I got this by setting swapniness to 0...is it OK according to my specs?
Toshiba Satellite A 40 (2 years old)
2.7 GHz - 512 RAM Dual Boot 80G HD

Thanks for reading!


IMO, I think you are fine, albeit, very close to maxed out! You shaould have the best performance at this point, but you are running with only 6MB free! I you start to notice hanging applications, slow loading apps, or error with downloads, maybe change swappiness to =10 instead of =0. If you generally always do the same thing daily, ie. Start Firefox/Thunderbird/Office and ????/ and just plug away, you'll be OK. If you always do different stuff daily as most people do, watch it very close for errors. Ubuntu seems to work very well at optimizing itself and you really should be fine. BTW, a laptop using RAM instead of SWAP save battery energy! My battery times went up about 22 minutes when I added the second 512MB stick of RAM and changed swappiness=0!

---

### Post by xyz on 2006-10-07
Thanks SirShaggy for your tips and advice.	
I might just raise it to 10 and see what happens. Actually I often use this laptop on AC.
I got a laptop not only to be mobile with it but also because I've got very little space where I live.

---

