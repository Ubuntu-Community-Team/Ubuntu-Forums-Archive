---
title: "Fixed GRUB (on MBR), but display broken"
date: 2005-07-01
forum: Hardware &amp; Laptops
---

### Post by jc3835 on 2005-07-01
Couldn't figure out how to word this better to fit in title... hate when titles are non-descriptive...  [-X 

Anyway, I installed Ubuntu, worked great (Dell Latitude c840) and then I went and installed Windows2000... I know, shame on me again.
But Win2000 is needed for work, and I had to.
I also know Windows likes to be first, and I did it in the more difficult order. I also put Windows on the second partition on the same hard drive. Once again, more difficult.
So when I installed Win2000, GRUB was hosed, and it would boot straight into Win2000.
So....
I followed this HOWTO:
[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

GRUB then worked great, problem solved, right? NO!  :-x 

Selecting either of the two kernels (386,686) works, to the point where I am supposed to get the Ubuntu display to log in. The screen is JACKED, don't know how to describe it other than the basic Ubuntu colors are there, but no text, it's all smeared and whatnot.
But, the music plays, I CAN login by typing my username/password, even though I can't SEE anything.

Any ideas?

And... I'm spent... sorry about the length

JC

---

### Post by intangible on 2005-07-01
That's a bit odd :D

Have you tried "CTRL-ALT-F1" and then **sudo dpkg-reconfigure xserver-xorg**  ?

---

### Post by jc3835 on 2005-07-01
What I "tried" was re-slicking the entire hard drive, installing Win2000, then Ubuntu... So it's working now.   :grin: 
It was a newly loaded computer, so I didn't lose any sleep over wiping it out immediately and starting fresh.
I will, however, keep all suggestions in mind in case it happens again and I can't simply start over.

Thanks!

JC

---

### Post by intangible on 2005-07-01
:lol:  Well, glad you got it working :D

---

