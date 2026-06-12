---
title: "Problems with memory, 4gb is not available"
date: 2008-10-04
forum: Hardware
---

### Post by M2_ on 2008-10-04
Hello!
I have a problem with my memory, and it's pretty strange. I have an MSI MS-7176 motherboard, it is expected to carry up to 4gb of RAM, but today i bought 2x2gb of DDR2-800U, and when i set it up and tried to boot ubuntu (8.04), it did id very very slowly, and with some errors about drivers.
If i insert only one of those, that mean 2gb at all, everything's great. But i really need more than 2gb, because of virtual machine needer for my work.
So, i tried to insert memory that way: 2gb + 512mb (i still have previously installed 512+512). That works, BIOS shows me that it is 2,5gb memory, but when i try to boot ubuntu it happens too slowl. The first init level was loading at about 20 minutes.
The problem may be that there are different frequencies of 2gb and 512mb planks: 553 and 800 Mhz. But why both 2gb planks installed do not work properly?

I compiled new kernel with 4gb support. But actually BIOS tells me that i have 3,4gb, when it's 2+2gb installed.

So, that is my problem. I suspect my motherboard in this, because it seems not to allow 4gb, or BIOS does. But I couldn't find option to allow this.

Besides, i tried to boot into Windows (SP2, 32bit), and it's ok there with any installed memory planks.
And i tried to install both 2gb planks, and install ubuntu once more, but the installator didn't succseeded to manage with this. The problems were similar to problems with booting from hard disk.

Hope for your help.
Gratz!
       M2

---

