---
title: "Questions Before I Install More RAM"
date: 2010-06-01
forum: Hardware
---

### Post by physic.dude on 2010-06-01
I currently use Ubuntu in 32bit, I have 4GB of ram installed and would like to increase that to 6GB or 8GB. I have 2 more empty slots on the motherboard. Here are my questions...

Q1. Will Ubuntu 32bit recognize more then 4GB or RAM?

Q2. Will Ubuntu accept an odd amount of ram? (i.e. 5GB)

Q3. Can there be an odd amount of sticks of RAM? (i.e. If I have 3 out of 4  slots used)

Q4. Must the new RAM sticks be the EXACTLY same as the old ones? (i.e. Manufacturer  brand name)

---

### Post by lrgmmc on 2010-06-01
a2. ya it can accept an odd amount
a3. yep i have 2 2gig and a 1gig and seem to work well for past year.
a4. well you probably should but as long as they are the same type should be fine. (ie DDR2 1066 and DDR2 1066, not DDR2 1066 and DDR2 800)

---

### Post by howefield on 2010-06-01
And answer to number one is no, it won't unless you install a PAE enabled kernel.

---

### Post by cpmman on 2010-06-01
[http://www.crucial.com/](http://www.crucial.com/)

---

### Post by cascade9 on 2010-06-01
> **physic.dude said:**
> I currently use Ubuntu in 32bit, I have 4GB of ram installed and would like to increase that to 6GB or 8GB. I have 2 more empty slots on the motherboard. Here are my questions...

Q1. Will Ubuntu 32bit recognize more then 4GB or RAM?

Q2. Will Ubuntu accept an odd amount of ram? (i.e. 5GB)

Q3. Can there be an odd amount of sticks of RAM? (i.e. If I have 3 out of 4  slots used)

Q4. Must the new RAM sticks be the EXACTLY same as the old ones? (i.e. Manufacturer  brand name)

Q1- answered (thanks howefield). You are probably better off with 64bit with 3GB+ anyway. 

Q2+3- more about the motherboard/chipset/BIOS than ubuntu. If they work with odd amounts (almost all do) then ubuntu should be fine. 

Be warned, if you run 3 sticks of RAM, you wont be able to use dual-channel RAM addressing. Its a minor perfromance hit to be in single channel mode. 

Q4- No, you dont have to have exactly matching sticks. 

> **lrgmmc said:**
> a4. well you probably should but as long as they are the same type should be fine. (ie DDR2 1066 and DDR2 1066, not DDR2 1066 and DDR2 800)

On almost all motherboards, running different speed rated RAM is fine. It will run at the lowest speed (so if you have DDR2 800 and put DDR2 1066 in as well, it will still only run at 800)

---

### Post by jakepc123 on 2010-06-01
Thats all right,

Q1 is no but you may be able to go to 64 bit

everything else is yes

---

### Post by new_tolinux on 2010-06-01
On some motherboards you actually can put 2 types of RAM (e.g. DDR _or_ DDR2). In those cases it is almost never supported to mix them, so you'll have to buy RAM of the same type.
As said before: speed doesn't really matter, although it's advised to buy at least the same speed (otherwise your memory is going to be a little bit slower).

Having more than 3.25 GB of RAM on a 32-bit system is pointless. It can't be addressed, so it won't be used.

---

