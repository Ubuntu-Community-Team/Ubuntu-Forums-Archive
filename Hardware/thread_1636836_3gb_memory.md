---
title: "3gb memory"
date: 2010-12-03
forum: Hardware
---

### Post by trixman on 2010-12-03
a friend ordered a new dell ispiron computer with memory of 3gb and hard drive of 320 is that enough memory for linux in the future.
she might install linux mint 9 


thanks
;)

---

### Post by tommcd on 2010-12-03
Yes, that is plenty enough memory. I only have 2GB memory in my desktop, and 1.5GB in my laptop. I almost never touch my swap partition:
```

tom[data]$ free -m
             total       used       free     shared    buffers     cached
Mem:          2000       1840        159          0         74       1265
-/+ buffers/cache:        500       1500
Swap:          956          0        956

```
If your friend will be running additional operating systems in virtual machines, then more memory would be beneficial, but not absolutely necessary.

As for the future, I would think that 3GB memory will be more than adequate for a few years at least.

---

### Post by trixman on 2010-12-04
> **tommcd said:**
> Yes, that is plenty enough memory. I only have 2GB memory in my desktop, and 1.5GB in my laptop. I almost never touch my swap partition:
```

tom[data]$ free -m
             total       used       free     shared    buffers     cached
Mem:          2000       1840        159          0         74       1265
-/+ buffers/cache:        500       1500
Swap:          956          0        956

```
If your friend will be running additional operating systems in virtual machines, then more memory would be beneficial, but not absolutely necessary.

As for the future, I would think that 3GB memory will be more than adequate for a few years at least.

thanks for the help
what would you install on a brand new machine
linux mint 9 or ubuntu 10.04 ?

thanks

---

### Post by tommcd on 2010-12-05
> **trixman said:**
> 
what would you install on a brand new machine
linux mint 9 or ubuntu 10.04 ?

I have never actually used Mint. Many people around here do like, and even prefer Mint though.
As far as performance and hardware compatibility is concerned, there is really no difference between Ubuntu and Mint. They both use the same Ubuntu kernel. I don't believe the Mint developers modify the Ubuntu kernel in any way.
The main advantage to using Mint is they add a few extra beginner friendly configuration tools, and they add multimedia codecs out of the box.
Your friend may be interested in these tutorials for installing Ubuntu and Mint:
[http://howtoforge.com/the-perfect-desktop-ubuntu-10.10-maverick-meerkat](http://howtoforge.com/the-perfect-desktop-ubuntu-10.10-maverick-meerkat)
[http://howtoforge.com/the-perfect-desktop-linux-mint-10-julia](http://howtoforge.com/the-perfect-desktop-linux-mint-10-julia)
(Note: You do not need all of the software that they install in those tutorials. Much of the software they install on those How To Forge tutorials is redundant.)

As far as Ubuntu is concerned, my preference would be to go with 10.10 instead of 10.04. For a new system, 10.10 will have a newer kernel and newer hardware drivers that would be beneficial for newer hardware. The applications in 10.10 will be newer as well. Likewise, for Mint, I would go with Mint 10 instead of Mint 9 as in the tutorial I linked to.

Write back if you need more help.

---

### Post by trixman on 2010-12-26
> **tommcd said:**
> I have never actually used Mint. Many people around here do like, and even prefer Mint though.
As far as performance and hardware compatibility is concerned, there is really no difference between Ubuntu and Mint. They both use the same Ubuntu kernel. I don't believe the Mint developers modify the Ubuntu kernel in any way.
The main advantage to using Mint is they add a few extra beginner friendly configuration tools, and they add multimedia codecs out of the box.
Your friend may be interested in these tutorials for installing Ubuntu and Mint:
[http://howtoforge.com/the-perfect-desktop-ubuntu-10.10-maverick-meerkat](http://howtoforge.com/the-perfect-desktop-ubuntu-10.10-maverick-meerkat)
[http://howtoforge.com/the-perfect-desktop-linux-mint-10-julia](http://howtoforge.com/the-perfect-desktop-linux-mint-10-julia)
(Note: You do not need all of the software that they install in those tutorials. Much of the software they install on those How To Forge tutorials is redundant.)

As far as Ubuntu is concerned, my preference would be to go with 10.10 instead of 10.04. For a new system, 10.10 will have a newer kernel and newer hardware drivers that would be beneficial for newer hardware. The applications in 10.10 will be newer as well. Likewise, for Mint, I would go with Mint 10 instead of Mint 9 as in the tutorial I linked to.

Write back if you need more help.

thanks for the help. she decided on MInt 10 and it works fine. 
coming from windows machines i am amazed at how well a pc can run with 1 mb of memory. and you are so right about the 3 memory it never touches her swap at all. 

thanks so much. i like both mint & ubuntu. 
;)

---

