---
title: "memtest on Live CD reboots computer"
date: 2009-10-27
forum: Hardware
---

### Post by Volt9000 on 2009-10-27
My wife's computer has been flaking out lately so I started checking the hardware. Long story short I finally got the damn thing to boot, although I really have no idea how since I really didn't change anything.

Anyways, it's starting to seem more and more like the RAM is the culprit, so I fired up my Live CD and tried running memtest. To my dismay, this just restarts the computer. :(

Although to me this would seem like it definitively points to RAM, I want to be sure. I tried pulling each of the sticks out one at a time, putting them into different slots, but to no avail. No matter what I try,the system keeps rebooting as soon as I select the "Test memory" option.

Now this is starting to worry me, as it's very unlikely for BOTH sticks to fail at once, and this problem happens regardless of which stick is in the system. So I'm starting to suspect maybe this is more of a motherboard issue...?

Anyone have any advice?

---

### Post by Volt9000 on 2009-10-27
More info:
I can boot into a live session just fine. When I can boot, that is.

Sometimes if I restart, the system won't boot but give me 1 long then 2 short beep codes. According to the manual that's supposed to be the video card, but I've ruled that out because I've tried with another known working video card and it may or may not give me the same beep code.

---

### Post by Volt9000 on 2009-10-29
*bump*
Any takers?

---

### Post by jasonab on 2009-10-30
If you can get into the bios try adjusting the frequency of the ram down to a lower level. Say from 200 to 166,133 or 100. You might need to press a special key combonation in the BIOS to see an option that will allow you to do that (Gigabyte mobos it's Control+F1). 

Then try running the test again and if you're having greater success booting. What motherboard is it though?

My instinct also says motherboard (going on the information I have). My other personality says try another powersupply but he always says that.

---

### Post by Volt9000 on 2009-10-30
> **jasonab said:**
> If you can get into the bios try adjusting the frequency of the ram down to a lower level. Say from 200 to 166,133 or 100. You might need to press a special key combonation in the BIOS to see an option that will allow you to do that (Gigabyte mobos it's Control+F1). 

Then try running the test again and if you're having greater success booting. What motherboard is it though?

My instinct also says motherboard (going on the information I have). My other personality says try another powersupply but he always says that.

That's for the reply.

I don't believe it's RAM. I just tried a BRAND NEW stick of RAM, fresh bought, and it does the same thing.

As for the power supply, I just happened to replace it as well (it was long overdue in this system.)

If it is the mobo, the problem is I can't find any Socket 939 mobos ANYWHERE! Nobody sells them anymore.
Pretty stupid, seeing as how I can buy PC133 SDRAM, which has gotta be around a decade old, but not a Socket 939 motherboard, which is half that.

---

### Post by jasonab on 2009-10-31
I hear you. I have a dead Socket 939 Gigabye K8N-SLI motherboard in my cupboard. It died just week after the warrenty expired and I was in the same boat you're in now. It rather annoys me that some of the modern hardware doesn't live past 5 years.

Maybe you can get your wife a cheap Celeron with motherboard and ram or something for Christmas.

---

### Post by JBAlaska on 2009-10-31
Maybe this [Link](http://www.google.com/products/catalog?hl=en&client=firefox-a&rls=com.ubuntu:en-US:official&hs=EyV&q=939+mb+buy&um=1&ie=UTF-8&cid=2994599821039686783&ei=BQzsStyLNZPOsgP66uX1Aw&sa=X&oi=product_catalog_result&ct=result&resnum=2&ved=0CBkQ8wIwAQ#ps-sellers) will help.
MSI K8N Neo4-F - motherboard - ATX - nForce4 - Socket 939 $14.00 USD

---

### Post by Volt9000 on 2009-10-31
> **JBAlaska said:**
> Maybe this [Link](http://www.google.com/products/catalog?hl=en&client=firefox-a&rls=com.ubuntu:en-US:official&hs=EyV&q=939+mb+buy&um=1&ie=UTF-8&cid=2994599821039686783&ei=BQzsStyLNZPOsgP66uX1Aw&sa=X&oi=product_catalog_result&ct=result&resnum=2&ved=0CBkQ8wIwAQ#ps-sellers) will help.
MSI K8N Neo4-F - motherboard - ATX - nForce4 - Socket 939 $14.00 USD


Thanks, but I live in Canada.
What that means is, we get raped on anything that gets imported from the US. The cost of any item goes up drastically, sometimes DOUBLED, thanks to duties, shipping, taxes, etc.

---

