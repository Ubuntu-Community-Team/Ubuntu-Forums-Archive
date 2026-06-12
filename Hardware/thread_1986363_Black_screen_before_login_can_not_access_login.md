---
title: "Black screen before login can not access login"
date: 2012-05-24
forum: Hardware
---

### Post by jcer93705 on 2012-05-24
Hi I'm on xubuntu live right now. I can not get into my xubuntu few hours before that happend I installed ati driver and which work well games fps were between 80 and 90 then it stop working. But when i push power button once it show letter but to fast for me to catch what it say. Can someone help me?

---

### Post by wilee-nilee on 2012-05-24
> **jcer93705 said:**
> Hi I'm on xubuntu live right now. I can not get into my xubuntu few hours before that happend I installed ati driver and which work well games fps were between 80 and 90 then it stop working. But when i push power button once it show letter but to fast for me to catch what it say. Can someone help me?


Use the shift key at powering on to access the grub menu and take a look at this thread on inserting a per session nomodeset.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Bobrm2 on 2012-06-21
I'm stabbing in the dark here, saw the post title and stepped in.

  I, after running 11.10 attempted to upgrade to 12.04, somehow have lost it all, completely back to NOT being able to even load to GRUB, as far as I can tell, because the monitor flashes the Archer/American Megatrends logos, then goes black with a "No Signal" indicator.


  Have tried as instructed above. Shift key has no effect, and since I can't get to GRUB F6 isn't even a consideration.

  I don't know if I have a hardware problem, a failed video card, don't think so. I have also switched monitors and cables to see if the problem is there.

  Don't believe there is anything left of the partition table; GParted's ISO will not load either. Have live CD's of everything back to 9.10.

  The mother boards startup disk (ECS IC780M-A) has no apperant effect, but I suspect information needed is hidden behind the "Black" Screen. Screen returns to hibernation.

  So, I have no access to a terminal, on that Machine. Don't have any idea as to the condition of the Partition table,and can't see the ECS instructions. Also, haven't access to nomodtest (at least I don't know how to invoke it).

  The Video card is an: EVGA 01G-P3-1235-LR GeForce GT240.

  Processor: AMD Phenom X$ 9750 Quad Core 2.40GHz, 4MB of Cache, (two sticks installed).

  Can't think of anything else. Your help appreciated

Bob

---

### Post by sandraalvarez on 2012-06-21
am sure you already did basic troubleshooting there. i think it's best to call technical support at this time...

---

### Post by QIII on 2012-06-21
Did you do
```
sudo aticonfig --initial
```
after you installed the driver and before you rebooted?

---

### Post by Bobrm2 on 2012-06-21
No, can't get to a terminal. Have tried to run the Motherboard setup disk, ?? Have a call into ECS support, not even sure that's where the problem is. Could be the GeForce video card or the way the newer versions of Ubuntu are configured??

no Idea where or how to trouble shoot the problem. A process of elimanation i.e. MB/Video card/software. Thanks

Bob

---

### Post by QIII on 2012-06-21
My response was intended for [jcer93705]("http://ubuntuforums.org/member.php?u=384578"), but I see now his post was 4 weeks old.

His was about and ATI card, yours about NVIDIA.  In the future it would be best to start a new thread with your own issue rather than hijacking another's and bringing an older, unrelated one back to the top.

---

### Post by Bobrm2 on 2012-06-21
I except your chastisement, if you will note that I admitted to stepping into this post. Have a nice evening.

---

