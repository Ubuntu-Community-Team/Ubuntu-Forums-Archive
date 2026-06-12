---
title: "black screen with beep at loading of ubuntu"
date: 2013-02-27
forum: Hardware
---

### Post by yoyohoneysingh on 2013-02-27
hey..
i had installed ubuntu 12.10 on external harddisk. when i boot it on my windows 7 desktop it is working properly but when i boot it with my hp ultrabook it's giving beep at loading of ubuntu screen and giving a black screen. 
can anyone help me out of this. Thanks.

---

### Post by TheFu on 2013-02-27
Are the graphics cards on both machines in the same family?
Trying to use an ATI driver with nvidia or Intel GPU doesn't work well at all.

---

### Post by foresthill on 2013-02-27
I love the idea of being able to install Ubuntu once on an external hard drive, then being able to plug that external hard drive into any desktop or laptop and then being able to boot right up into Ubuntu.

Unfortunately, it's not that simple (not yet anyway). So due to hardware differences, AFAIK, you're only going to boot up successfully from the same machine the you did the original installation on, or one nearly identical (though I'm not positive even this would work).

---

### Post by TheFu on 2013-02-27
> **foresthill said:**
> I love the idea of being able to install Ubuntu once on an external hard drive, then being able to plug that external hard drive into any desktop or laptop and then being able to boot right up into Ubuntu.

Unfortunately, it's not that simple (not yet anyway). So due to hardware differences, AFAIK, you're only going to boot up successfully from the same machine the you did the original installation on, or one nearly identical (though I'm not positive even this would work).

I'd point out that if the machines you are moving between have similar family of video cards, it is most definitely possible to move installations around. I've done this 3 times ... as I migrated from a Core 2 Duo to a Core i5 to another Core i5.  The key was that they all had nvidia cards.  

If non-proprietary video drivers were used, I think there will be better luck with migrations.

However, Ubuntu does remember network cards, so if a different NIC happens, it will create a new eth{NN} interface. This is based on the MAC.

---

