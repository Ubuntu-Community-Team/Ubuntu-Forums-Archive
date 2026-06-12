---
title: "Amilo M1450G Sound"
date: 2006-06-05
forum: Hardware &amp; Laptops
---

### Post by deunido on 2006-06-05
I have a Fujitsu-Siemens Amilo M1450G.
I install the Kubuntu 6.06 without problem, but the sound card doesn't work, and I don't find so much information about how to solve it.
Anyone has the same problem and knows how to solve it??
Thanks in advance

---

### Post by alfredhitzkopf on 2006-07-27
ive got the same problem but im sorry that i dont have a solution for you. hope someone does.

---

### Post by alfredhitzkopf on 2006-07-31
Do you have a solution for the problem yet?

---

### Post by Kingskid on 2007-07-02
I want to join the crowd - I've just installed Ubuntu 7.04 on this very same laptop and no sound. Plus I got only 1024x768 resolution.
Any advice will be appreciated!

---

### Post by Johnsie on 2007-07-02
for the resolution problem you can try:

> sudo dpkg-reconfigure xserver-xorg 

and making sure your real resolution is the only resolution you tick when given that option.  The new version of Ubuntu that is coming might be better at monitor detection.

---

### Post by Kingskid on 2007-07-03
Thanx for the hint! But there is no driver for my card. This Fujitsu uses Intel which I didn't find in the menu. (Sorry I might be talking nonsense but I'm no guru). Any more advice? Tx!

---

### Post by Kingskid on 2007-07-09
I did it :) Check this thread:

[http://ubuntuforums.org/showthread.php?t=491007&highlight=no+sound+acer](http://ubuntuforums.org/showthread.php?t=491007&highlight=no+sound+acer)

Plus the resolution was solved by installinh application 915resolution through Synaptic.

---

