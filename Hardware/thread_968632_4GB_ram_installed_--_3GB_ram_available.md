---
title: "4GB ram installed -- 3GB ram available"
date: 2008-11-02
forum: Hardware
---

### Post by Convert on 2008-11-02
OK, here's a hardware/BIOS question.  I have a Sony VGN-SZ650N/C notebook.  I have updated the BIOS with Sony's latest, greatest.  The BIOS update from Sony was suppose to allow the laptop to use 4GB of ram.  When I go into the BIOS setup program, the status screen shows 4GB of ram installed.

I have this computer set up to dual boot Windows XP and Ubuntu 8.0.4.  Both operating systems only show 3GB of ram available.

Why doesn't the last 1GB of ram show up as available in the systems?  The BIOS setup program sees it.  The operating systems don't.  Any ideas?

---

### Post by bep on 2008-11-02
With the 32 bit version that is all you get. If you have a 64 bit cpu you can install the 64 bit Ubuntu.

---

### Post by tuxxy on 2008-11-02
You need to install the 64-bit Uubuntu to access all your 4GB RAM :)

---

### Post by hstenzel on 2008-11-05
That's not entirely true.  One way to access more than 3GB of ram may be to use the 64-bit version.  Another way is to use a 32-bit PAE-enabled kernel, such as Ubuntu's linux-image-server.  Lastly, some chipsets will only allow you to access 3GB even if you have 4 installed.

So it's a mixed bag.

---

### Post by stinger30au on 2008-11-05
> **hstenzel said:**
> That's not entirely true.  One way to access more than 3GB of ram may be to use the 64-bit version.  Another way is to use a 32-bit PAE-enabled kernel, such as Ubuntu's linux-image-server.  Lastly, some chipsets will only allow you to access 3GB even if you have 4 installed.

So it's a mixed bag.


true, you can install the ubntu server edition and one it is installed you can install a GUI ontop of it and get round it this way

---

### Post by damis648 on 2008-11-05
Or run the server kernel:
```
sudo apt-get install linux-server linux-headers-server 
```

You could also compile your own kernel, but that is a very long and more advanced task. See at: [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

EDIT: Wrong package :-P Fixed.

---

### Post by Yezinki on 2008-11-05
> **Convert said:**
> OK, here's a hardware/BIOS question.  I have a Sony VGN-SZ650N/C notebook.  I have updated the BIOS with Sony's latest, greatest.  The BIOS update from Sony was suppose to allow the laptop to use 4GB of ram.  When I go into the BIOS setup program, the status screen shows 4GB of ram installed.

I have this computer set up to dual boot Windows XP and Ubuntu 8.0.4.  Both operating systems only show 3GB of ram available.

Why doesn't the last 1GB of ram show up as available in the systems?  The BIOS setup program sees it.  The operating systems don't.  Any ideas?

Install SP4 for XP.......than the issue shall be resolved!

Regards,

Yezinki,

---

### Post by jollo on 2008-11-14
> **damis648 said:**
> Or run the server kernel:
```
sudo apt-get install linux-server linux-headers-server 
```



Hi damis648, could you please clarify a bit because I am very interested about the solution you suggested. Sorry in advance for the newbie questions...

Running a server kernel on a 8.10 32bit desktop installation is safe? Just installing it with Syn-apt-ic will *replace* my current desktop kernel or will I have to enable it somehow?

Server kernel is compiled by default with PAE enabled?

What performance toll will address extension put on overall performance? 

Any other way to enable PAE on 32bit short of recompiling the kernel (or switching to 64bit)?

Thanks in advance!

---

### Post by Convert on 2008-11-14
Thanks everyone for the responses.  Using the server kernel seems most promising.  However, I'm still wondering about why 32 bit Linux by default doesn't address up to the 4 GB limit for a 32 bit operating system?  The PAE thing is to allow getting past the 4 GB limit.  I'm not really trying to get past it, I'm just trying to get up to it.  Obviously Linux is only coded to address 3 GB of RAM.  What I don't understand is why? (since I would think it would be just as easy(?) to allow the full 4 GB of address space a 32 bit processor would support)

---

### Post by Convert on 2008-11-14
> **Yezinki said:**
> Install SP4 for XP.......than the issue shall be resolved!

Regards,

Yezinki,

There is no service pack 4 for XP (or was that sarcasm about the limits of XP? --- if so, Linux seems to be at the same limit considering they both only support the same amount of physical RAM out of the box).

---

### Post by kalana on 2009-09-29
I know this thread is really old, but still I have the same question. PAE is there to access more than 4GB as it's in [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension). But still everybody says 32bit can't support 4GB and it will show 3GB only. Can anyone share a good technical explanation about this. 

Thanks..

Kal

---

### Post by edup_pt on 2010-02-20
Hello,

I dont know if its too late for you but maybe for future search like mine today. 

The solution was already talked in this thread, but here explains exactly how to do that and confirms that it works:

[http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/](http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/)


Best Regards,

---

### Post by hxcobd on 2010-02-20
> **Convert said:**
> Thanks everyone for the responses.  Using the server kernel seems most promising.  However, I'm still wondering about why 32 bit Linux by default doesn't address up to the 4 GB limit for a 32 bit operating system?  The PAE thing is to allow getting past the 4 GB limit.  I'm not really trying to get past it, I'm just trying to get up to it.  Obviously Linux is only coded to address 3 GB of RAM.  What I don't understand is why? (since I would think it would be just as easy(?) to allow the full 4 GB of address space a 32 bit processor would support)

This is true for all operating systems, not just linux.

---

