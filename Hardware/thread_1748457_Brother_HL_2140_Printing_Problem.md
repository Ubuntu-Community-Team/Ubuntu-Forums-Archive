---
title: "Brother HL 2140 Printing Problem"
date: 2011-05-03
forum: Hardware
---

### Post by oceanfirehawk on 2011-05-03
Hello all,

I have a Brother HL 2140 printer hooked up to Ubuntu 11.04 via USB. The printer shows up in the print windows as the correct model. However, when I print, the printer keeps "printing" paper with nothing on it. I was forced to stop the printer manually because it just kept going. All the pages had nothing on them. Any help?

---

### Post by aresera on 2011-05-04
Hi, got same problem here. I'm using HL-5350DN, If I choose the Recommended driver, the printer doesn't work at all. When I switched to the Foomatic one. It printed out blank pages. :(

Everything was working VERY WELL in Ubuntu 10.10

---

### Post by chopclampitt on 2011-05-04
Count me in on this , same multi blank page problem , also printer was perfect under 10.04 , Maybe not such a good idea to upgrade :(

---

### Post by mörgæs on 2011-05-04
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by coolglobal on 2011-05-04
no solution thus far...

SOLVED

Follow the instructions at Brother: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)

Will require a sudo to unpack and install the drivers (not noted in the instructions)
Will also require restart.

Then System> Admin> Printing: set HL2140 as default (the other version is broken & can be deleted after testing)
May require restart.

---

### Post by oceanfirehawk on 2011-05-08
> **coolglobal said:**
> no solution thus far...

SOLVED

Follow the instructions at Brother: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)

Will require a sudo to unpack and install the drivers (not noted in the instructions)
Will also require restart.

Then System> Admin> Printing: set HL2140 as default (the other version is broken & can be deleted after testing)
May require restart.

I will try this fix ASAP. Until then, I have a quick question. When hardware works in one ubuntu release and then stops working in a future release, is that the OS fault?

---

### Post by coolglobal on 2011-05-09
The fault could be shared by the OS & the hardware manufacturers. My only reply would be to setup an LTS (long term support) release to your satisfaction and stick with it for the duration. I find it to be the most problem free option.

---

### Post by mdshaver on 2011-05-11
There is a much easier solution. Just add the printer through standard "Printing" menu but identify the printer as a Brother HL-2170W instead of the HL-2140. This has worked in 11.04 as well as previous versions of Ubuntu.

---

### Post by Nixuntu on 2011-05-20
the default driver "Brother HL-2140 Foomatic/Postscript" is what makes it print out all them blank pages change it to "Brother HL-2140 Foomatic/hpijs-pcl5e (recommended)" and it will print just fine.

---

### Post by dneff87 on 2011-05-20
Nixuntu:

You're absolutely right. That cleared it up real fast! Thanks!

---

### Post by Owlswater on 2011-07-18
I ran into this same problem, default driver caused the printer to spit out infinite blank pages (better than infinite ruined blank paper I suppose) and switching fixed the issue. Is it just 64 bit where this doesn't work properly? Otherwise it seems like a poor default driver.

---

### Post by MyR on 2011-07-20
Nixuntu: Thanks for sharing your solution!

Would any of you [review the printer here]("http://linuxdeal.com/add-printer.php") to help out other Linux users? Thanks in advance!!

---

### Post by xandr55 on 2011-09-13
Thanks for the solution! Perhaps this thread should be marked as solved? 

Just for reference too this worked for me on 32bit xubuntu, where I had the same problem. 

Why did it change between 10.10 and 11.4?

---

