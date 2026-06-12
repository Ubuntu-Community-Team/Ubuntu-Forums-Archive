---
title: "8 gig ram on 32bit Ubuntu"
date: 2012-12-13
forum: Hardware
---

### Post by Heeter on 2012-12-13
Hi all,

I am receiving some ram from  a friend of mine that will work on my machine, my motherboard can take it.

Just found out it is a total 2 x 4gig (8gig total) sticks.

Question: will it help my 32 bit ubuntu 12.10 setup? Or should I just stick with what I have currently? (2 gig currently) Will it have a profound effect overall?

Thanks 

Heeter

---

### Post by lildigiman on 2012-12-13
32 bit operating systems cannot see more than about 3.5 GB of ram. You'll need a 64 bit operating system to support more than 4 GB.

---

### Post by haqking on 2012-12-13
> **lildigiman said:**
> 32 bit operating systems cannot see more than about 3.5 GB of ram. You'll need a 64 bit operating system to support more than 4 GB.

Since 10.04 i believe it is PAE out of the box so will see all 8 gig. It doesnt have to be a 64 bit OS, as long as PAE is present

However to the OP, if i was you if possible take full advantage and upgrade to x64

---

### Post by Heeter on 2012-12-13
Great, thanks for the response, guys


Heeter

---

### Post by lildigiman on 2012-12-13
> **haqking said:**
> Since 10.04 i believe it is PAE out of the box so will see all 8 gig. It doesnt have to be a 64 bit OS, as long as PAE is present

However to the OP, if i was you if possible take full advantage and upgrade to x64

Interesting... I didn't have PAE when I had booted both 32 and 64...

Regardless, I fully agree that anyone should take full advantage of their 64 bit processors.

---

### Post by haqking on 2012-12-13
> **lildigiman said:**
> Interesting... I didn't have PAE when I had booted both 32 and 64...

Regardless, I fully agree that anyone should take full advantage of their 64 bit processors.

Well you wont have PAE with x64, Physical Address extensions is or should be present in the kernel for 32 bit versions since 10.04, though I would need to check that, however for the OP with 12.10 PAE should already be present and so will or should support the RAM,.

[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

---

### Post by lildigiman on 2012-12-13
> **haqking said:**
> Well you wont have PAE with x64, Physical Address extensions is or should be present in the kernel for 32 bit versions since 10.04, though I would need to check that, however for the OP with 12.10 PAE should already be present and so will or should support the RAM,.

[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

Haha, yes I know 64 wouldn't have PAE, but I'm surprised I didn't remember it in my 32 bit 10.10.

---

### Post by Heeter on 2012-12-14
It took forever, but I finally did move to 12.10 64bit from 32bit.

Other than Adobe reader refusing to work, everything else seems to be fine. Sorry, not used to 64bit ubuntu.

I will be using all of the ram that my friend will be sending me.

Thanks again


Heeter

---

### Post by haqking on 2012-12-14
> **Heeter said:**
> It took forever, but I finally did move to 12.10 64bit from 32bit.

Other than Adobe reader refusing to work, everything else seems to be fine. Sorry, not used to 64bit ubuntu.

I will be using all of the ram that my friend will be sending me.

Thanks again


Heeter


Welcome, remember to use thread tools to mark the thread as solved.

Cheers

---

