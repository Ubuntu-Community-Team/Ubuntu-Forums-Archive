---
title: "Couldn't able to install ubuntu"
date: 2010-01-31
forum: Hardware
---

### Post by veda87 on 2010-01-31
Recently I brought Dell 1555 laptop. I need to install ubuntu in it. 
I tried installing but I couldn't able to see after I opted for install ubuntu.

I downloaded ubuntu-9.10 from the site and tried installing it. When I started it, It propmpted me like
[B]
Try ubuntu without causing changes
Install ubuntu
memory test
boot from hard disk[/B]

When I tried **install ubuntu**, The cursor blinks for some time and then a blank bright screen. i am not able to see anything.

I even tried noapic, nolapic, apic=off which are present under f6 options... No fruitful result.

this is the bootup line: ```
file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.lz quiet splash --
```

Can anyone tell me like what should I do inorder to install...

---

### Post by JK3mp on 2010-01-31
***BUMP/METOO***

I got the same thing on my new Dell. I believe its related to a topic on Backtrack's forums, I had a similiar issue with backtrack where startx would cause blank screen but fixvesa would fix it. So its def something to do with graphics i believe. I also get in 9.10 a blank screen for install but for live boot blank screen BUT sound of desktop loading, so assume its loading but the picture isn't coming up. Any and All help appreciated on this matter. I saw a bug report on Jaunty about this same topic, but didn't look like it went anywhere =(.

---

### Post by JK3mp on 2010-02-01
Tried using nomodeset-- as a kernel parameter but had no luck. Only change is the splash will come up. But still leads to a blank screen. Will keep trying...

---

### Post by JK3mp on 2010-02-01
Alright. So i was able to live boot into "Safe Graphical Mode" ON menu hit F4 or F6 i believe and there's a option for it. Then after that i installed and it worked fine from there. Additional suggestions i followed was removing quite and splash from the boot arguments. This didn't work for me, but if safe graphical mode doesn't work for you give it a try. nomodeset might also have a better result for you. Best of luck!

---

