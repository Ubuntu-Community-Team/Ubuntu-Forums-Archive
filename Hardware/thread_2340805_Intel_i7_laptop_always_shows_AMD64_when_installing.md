---
title: "Intel i7 laptop always shows AMD64 when installing updates"
date: 2016-10-22
forum: Hardware
---

### Post by jimstar792 on 2016-10-22
Hi, 

I have been noticing something strange every time I install updates. As the title of this post suggests, when I install updates I notice AMD64 being mentioned. I have ran commands to show that my ASUS laptop is indeed using Intel i7 CPU but I have been unable to work out why AMD64 keeps getting a mention. On my older laptop updates always refers to the correct CPU. 

Can anyone help me understand what's going on? I bought the laptop 2nd hand earlier this year but I only recently decided to look at the screws on the bottom of my laptop and notice that they all look scratched - so i am worried that the seller swapped out the Intel i7 for AMD64, is this possible?

I am trying to work out which monitor would best work with my laptop - Freesync of GSync (?) for photography editing and gaming. 

Thank you in advance for any help with this. 

Jimstar79

---

### Post by howefield on 2016-10-22
amd64 is simply a historical naming convention that is used for 64 bit packages as AMD "invented" the technology, just as i386 (as in Intel 386) is used for 32 bit packages but are good for AMD machines also. In other words it is only a label and are good for both Intel and AMD machines.

What is the output of..

```
cat /proc/cpuinfo  | grep 'name'| uniq
```

---

### Post by jimstar792 on 2016-10-22
Hi Howefield - thanks for the response. Yes, of course you're right  it is i386 and AMD. 

OK, here's the output for the above command:

model name : Intel (R) Core(TM i7-550U CPU @ 2.40GHZ

I think it means that everything is OK. That's quite a relief. Thanks for your help. 

I will mark this thread as solved (when I find a way to)

---

### Post by howefield on 2016-10-22
> **jimstar792 said:**
> Hi Howefield - thanks for the response. Yes, of course you're right  it is i386 and AMD.

You're welcome.

> model name : Intel (R) Core(TM i7-550U CPU @ 2.40GHZ ... I think it means that everything is OK. That's quite a relief. Thanks for your help. 

Yes, most assuredly an Intel processor, more info here :

[http://ark.intel.com/products/85214/Intel-Core-i7-5500U-Processor-4M-Cache-up-to-3_00-GHz](http://ark.intel.com/products/85214/Intel-Core-i7-5500U-Processor-4M-Cache-up-to-3_00-GHz)

---

### Post by jimstar792 on 2016-10-22
Hey thanks for the link. That's really interesting actually because I was recently in touch with ASUS and they informed me that the maximum resolution monitor supported by my laptop was 1920x1080 yet in the link you sent me it says 2560x1600@60Hz over HDMI 1.4. Now that would be really excellent for my photography. Hmmm. Anyway, that's something else entirely. 


Thanks again, Howefield, have a good weekend.

---

