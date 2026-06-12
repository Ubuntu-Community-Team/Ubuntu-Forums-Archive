---
title: "Installation Trouble on Thinkpad T61"
date: 2007-09-29
forum: Hardware &amp; Laptops
---

### Post by wolfmaster on 2007-09-29
Hey guys, sorry if this is the wrong forum/has been answered already, but I've spent quite a bit of time trying to figure out what is going wrong - to no avail.

I have a Thinkpad T61 with Vista installed. I created a new partition, burned the Ubuntu 7.04 iso to a disc, and attempted to run it. I initially had an error: "can't access tty", which I was able to bypass by typing modprobe piix as per someone's suggestion. The kernel continued to load, but when it tried to start up XWindow it said there was an error - it couldn't recognize my monitor. I attempted to use the alternate CD and installed Ubuntu on my parition, but obviously, I'm still getting this error. Any idea where I can get the right drivers or change the display settings? I'm completely new to Ubuntu..

Thanks in advance.

---

### Post by sc30317 on 2007-09-29
I have a T61, and found that feisty is very difficult to get working.  However, gutsy works great!  

Follow these instructions
[http://thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_Tribe_5_on_a_ThinkPad_T61](http://thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_Tribe_5_on_a_ThinkPad_T61)

---

### Post by wolfmaster on 2007-09-29
I see, I'll try installing 7.10 then. 

One question, how do I safely uninstall 7.04? Do I simply reformat the partition? Will that also remove GRUB and allow vista to boot normally? Sorry for the novice questions.

---

### Post by wolfmaster on 2007-09-29
Or am I able to upgrade 7.04 on the same partition? If I reformat the partition I have a feeling my bootloader will be screwed up.

---

### Post by swatson11 on 2007-10-03
I'm having the same issue with 7.10. Since last night I've tried both 32 and 64 bits of 7.04 and 7.10 all with this issue and it's getting incredibly frustrated. Is there any known fix? I haven't been able to find a good solution that everyone agreed on. Also the linux thinkpad wiki didn't seem to mention this issue with the t71 on its 7.10 or 7.04 page.

---

