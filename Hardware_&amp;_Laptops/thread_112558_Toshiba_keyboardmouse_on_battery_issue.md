---
title: "Toshiba keyboard/mouse on battery issue"
date: 2006-01-04
forum: Hardware &amp; Laptops
---

### Post by cuda70383 on 2006-01-04
hi:
when i first installed ubuntu on my toshiba tecra 9000 3 weeks ago, my mouse & keyboard worked fine while i was running on the battery.

however, now, they usually freeze for a few seconds, then un-freeze, then freeze again.  once i plug the power cord in again, it works fine?????? 

i've also tested another battery, and it does the same thing, as i thought maybe the cell was going bad.

i've read other posts in here @ jerky & jumpy keyboard issues, but none dealing with the battery issue that i have.

any ideas would be appreciated!

thanks!

---

### Post by 23meg on 2006-01-04
What's your processor? Is powernowd running? If not sure, type ```
ps -e |grep powernowd

```If there's no output, it's not. Try killing powernowd with ```
sudo killall powernowd
``` and see if the same behavior persists.

---

### Post by cuda70383 on 2006-01-05
processor is a pIII (i think 1.2ghz), i tried to look it up in the system propeties, but it didn't show speed.  only ram, drives, etc.

will try this tonite when i get home from work.

thx for the quick repy!

---

### Post by cuda70383 on 2006-01-06
darn.....this didn't work.....any other ideas would be appreciated.

thanks again.

---

### Post by nerval on 2006-01-06
I will give some options, if a hassle sorry for it.

1) Connect an external mouse & keyboard and then try it again.
1a) If problem occurs again go to (2)
1b) If there is no problem, it might be some internal issue. I hope it is still under warranty. 

2) Toshiba has serious "heating" issues, I know it sounds weird but I solve it by placing a book under it; so the fans has can get air easily. (I know it sounds stupid, but that how it works on Toshiba P30/P35 non-celeron)

3) The problem might also from your charger, they have made many (stupid) issues where their charger were either givin' too much (140-150) or too less (80-90) watt.  That might had messed it up too. (I had a kind of a similar problem on this)

---

### Post by cuda70383 on 2006-01-07
thanks for the ideas and advice on the toshiba's running hot.  i'll keep that in mind.

the issue happens instantly when i disconnect the power cord.  there isn't a delay as if the 'puter is heating up and then the mouse issues. 

right when i unplug it, the mouse begins jumping and keyboard is erratic.

thanks again!

---

### Post by nerval on 2006-01-08
as far as i can see it's a hardware issue, have u tried a live-version of any distro? (knoppix or even ubuntu live) If same problem again, then it's not because of ubuntu.

so what is obvious is : "Without the power cord, there is not in half power to support all devices of the laptop".

Problems related to it can be following:
a) Battery
U said u tried a different one, so it's not because of your battery.

b) The power circulation
I know it sounds weird, but u or the the technician who will try to fix your laptop will do this : open the computer, see everything is in place, every cord is connected properly.

c) Mouse & Keyboard 
If you have an extra mouse or keyboard, connect it to your computer and see if the problem still occurs. Then the problem might be about the mice & keyboard of your comp.

Good luck cuda :)
Onur

---

