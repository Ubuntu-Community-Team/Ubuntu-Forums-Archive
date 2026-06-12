---
title: "[SOLVED] My laptop battery won't charge completely?"
date: 2008-09-09
forum: Hardware
---

### Post by Soupcan on 2008-09-09
I have an almost brand-new laptop/battery. When on battery, I only get about 1:30 to 1:45 hours of battery life. 
The information about my battery says it has a "Design Charge" of 74.6 Wh, and a "Capacity" of 67%. It never charges past 50.5 Wh. What does this mean? Is my battery broken?

---

### Post by Whiffle on 2008-09-09
What kind of laptop/battery?

---

### Post by Soupcan on 2008-09-09
HP dv6000 laptop, and a HP lithium-ion 6 cell. I think it's 6 cell; it came with the laptop.

---

### Post by Whiffle on 2008-09-09
I think the lack of battery life is a separate issue, Linux power management on laptops isn't quite "there" yet.  If I tweak my laptop enough, I can almost get it to where it uses only a couple of watts more than XP uses, so there is still alot of room for improvement, especially on a default install.

I think the low listed battery capacity might be a characteristic of that particular battery/laptop.  In this thread: [http://www.linuxforums.org/forum/linux-laptops/75587-linux-hp-dv6000-amd-laptops-5.html](http://www.linuxforums.org/forum/linux-laptops/75587-linux-hp-dv6000-amd-laptops-5.html) , there are a few other uses with that laptop that list varying battery capacities.  I'm not quite sure what I'd do.

---

### Post by tuxxy on 2008-09-09
I know the power management is relatively poor compared with other proprietary OS's, although sure it isnt terrible enough to give a 1:30 battery life :confused:

---

### Post by Soupcan on 2008-09-09
I thought 1:30 was a little low. 
I really don't understand why it doesn't last; dim screen, most things off, but it still barely lasts.
It's not much of an issue, as I almost don't need the battery. But if it is defective, I have to figure it out soon, as I have the opportunity to get a 12 cell.
Is it possible that my battery is not calibrated properly?

---

### Post by Whiffle on 2008-09-09
One way to find out is to install powertop.  Run it with sudo in a terminal, unplug your laptop, and it'll tell you how many watts its pulling.  Do the math and you can guesstimate a runtime.  

If I had to guess at anything being broken, it would be the battery.  They have alot of internal circuitry in them that governs charging, and it may detect something amiss with one or some of the cells.  The info you're getting from proc comes from the battery itself as far as I know.

For reference, my thinkpad's 6 cell battery reports a design capacity of 51.840 Wh, and a last full charge of 51.270 Wh.

---

### Post by y@w on 2008-09-09
I've actually heard that switching filesystems helps with battery life. I haven't actually tried this myself, but if I recall correctly, my friend said he got about half an hour to an hour longer after switching to reiserfs from ext3.

---

### Post by technotitclan on 2008-09-09
another thing you might want to try is draining the bat and recharging a couple of times. sometime that will give it a little bit more. honestly though if you can get a 12 cell then go for it.

---

### Post by Soupcan on 2008-09-09
It seems like my laptop just uses lots of power. The main drains were my CPU and some other bit of hardware. 

I don't really want to mess around with my filesystem; it's not that important to me if my battery isn't defective, plus I'm not that experienced.

---

### Post by Soupcan on 2008-09-09
I fixed it. I drained the battery, and charged it up. It charged *really* fast and now says it has a lifetime of around 2:15. I've done three complete discharge/recharge cycles, but apparently this one did the trick. Thanks for your help and suggestions everyone. 
Now how do I mark this as solved?

---

### Post by Chuckalakala on 2010-10-02
sorry lol. how do i delete my posts

---

