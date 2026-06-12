---
title: "Ram Upgrade Failed."
date: 2008-11-09
forum: Hardware
---

### Post by meatcar on 2008-11-09
Last week I came across two 512 mb PC133 kingston kvr133x64sc3l/512 ram-sticks. i thought it would be nice to upgrade my laptop with those. I replaced the two 256mb pc133 with the two 512. The computer did not wanna boot. after playing around, i managed to make it boot with a 512 and a 256 stick. However, ubuntu did not wanna get past the grub menu. teh same with XP. upon restoring to my original config, it worked fine.

I attached a zipped html generated with "sudo lshw -html > ~/Desktop/hardware.html"

It specifies that my motherboard could potentially pull 1 gig, yet it did not want to do that. Do i have a dammaged RAM, is it my computers fault, or am i doing something wrong.

any help would be appreciated.

---

### Post by starcannon on 2008-11-10
I'd use Kingstons ram configurator and see if the machine requires a particular set of ram chips. Compare model numbers given by the configurator with the model numbers on the chips you have.
[http://www.kingston.com/](http://www.kingston.com/)

---

### Post by Skripka on 2008-11-10
Kingston makes good DIMMs IME, check to see if your machine needs anything special, if not give them a call.

---

### Post by meatcar on 2008-11-10
The Kingston Configurator tells me that my system maxes out at 512mb of memory. Linux tells me otherwise. Which one do I trust?

Its not like my laptop was unusable. It went through GRUB with the new chip in it. It just didnt wanna go naywhere after that.

Is it possible to plug it into your computerwhile its up?

THX

---

### Post by Skripka on 2008-11-10
> **meatcar said:**
> The Kingston Configurator tells me that my system maxes out at 512mb of memory. Linux tells me otherwise. Which one do I trust?

Its not like my laptop was unusable. It went through GRUB with the new chip in it. It just didnt wanna go naywhere after that.

Is it possible to plug it into your computerwhile its up?

THX

NO. **DO NOT** PLUG THINGS INTO THE MOTHERBOARD WHILE IT IS ELECTRICALLY HOT.  DO NOT DO IT.  I**_T *WILL* DAMAGE YOUR HARDWARE_**-BOTH DIMMS AND MOTHERBOARD.

I only yell for good reason. :)


What does your machine's manufacturer say on the topic?  Normally I'd trust the Kingston configurator-this all boils down to your particular motherboard, and its spec.

---

### Post by meatcar on 2008-11-10
Everywhere i looked it told me the max for my motherboard was 512. I guess linux just lied to me. that should deffinately be looked at, and fixed.

thanks for all your help guys.

---

