---
title: "Problem with keyboard (Acer TravelMate 4002LMi)"
date: 2006-08-09
forum: Hardware &amp; Laptops
---

### Post by ch4 on 2006-08-09
Hi,
finally, I had the courage to take a glimpse into the world of Linux with Ubuntu 6.06.

After installing it, I noticed some problems with my keyboard. I use Ubuntu on my Laptop, an Acer Travelmate 4002LMi.

1) It sometimes happens that when I press a key, lets say "a" (but it can by any key, even Blank or Backspace), that this "a" reappears very often, e.g. "aaaaaaaaaaaaa" instead of appearing only once (the number varies). In this time when they appear (maybe half a second - sounds like little but if one writes fast, one will notice it very clearly) the keyboard does not react. Only after all these "aaaaaaaaaaaaa" appeared in turn, one can continue typing (i.e. using the backspace-key to get rid of all these unneccessary "a").

2) It sometimes happens that when I type on my keyboard, the keys are not taken (i.e. nothing happens). Then I have to wait a little moment before I am able to continue writing. This often (but not always) occurs when I type rather fast and a bit stronger.

I never had these problems with Windows.

This is very annoying and I hope you can help me, beside that I like Ubuntu very much.
Thanks!

---

### Post by ch4 on 2006-08-09
Can nobody help me? :( 
These keyboard problems are really annoying

---

### Post by ch4 on 2006-08-31
Someone help me please!:sad:

---

### Post by tiger015 on 2006-09-24
Sorry buddy.I can't help but I  also get similar problems. Some of my key characters do not cause any input on Ubuntu though they work perfectly well  in Windows. I have Acer travelmate 4502 WLmi

---

### Post by tiger015 on 2006-09-24
OK try this. It works for me. The problem is the conflict between keyboard and battery status. You'll have to remove the battery status. For that do:

sudo rmmod acpi_sbs

this should make your keybaord work. To get back battery status and unsound keyboard do:

sudo modprobe acpi_sbs

---

