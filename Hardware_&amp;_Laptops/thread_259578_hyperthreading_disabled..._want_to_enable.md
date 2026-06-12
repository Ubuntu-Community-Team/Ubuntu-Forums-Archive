---
title: "hyperthreading disabled... want to enable"
date: 2006-09-17
forum: Hardware &amp; Laptops
---

### Post by d1sturbanc3 on 2006-09-17
I migrated from gentoo to ubuntu for my desktop server.
I was looking through dmesg, and I notice I got the line

```

[42949374.130000] CPU: Hyper-Threading is disabled 
```

Anyone know how to fix this? Thanks

---

### Post by nalmeth on 2006-09-17
I think you need to install the linux-686 package, which will install the 686-kernel with hyperthreading..

Look into it or await a better answer :)

---

### Post by d1sturbanc3 on 2006-09-17
I installed from the 686 server edition cd... I guess there is no way to configure the kernel. :'( I kind of miss gentoo / arch now.

---

### Post by nalmeth on 2006-09-17
> I installed from the 686 server edition cd... I guess there is no way to configure the kernel. :'( I kind of miss gentoo / arch now.
You mean you installed from the 64-bit server edition? 

It's still linux, you can configure all you want. You just don't HAVE to :-)

---

### Post by -deadcats on 2006-09-17
I agree with the previous poster. For someone coming from Gentoo/Arch, running Synaptic, doing a search on "linux" and installing the proper 686 and 686-SMP kernel packages should be a piece of cake! =)

You can do it! Come on, man! :)

regards,
-dc

---

### Post by d1sturbanc3 on 2006-09-17
> **nalmeth said:**
> You mean you installed from the 64-bit server edition? 

It's still linux, you can configure all you want. You just don't HAVE to :-)

oops.. I ment the x86 server.. no I didn't do the 64 bit edtion. I have a P4 with hyperthreading. I just want it to work.

> **-deadcats said:**
> I agree with the previous poster. For someone coming from Gentoo/Arch, running Synaptic, doing a search on "linux" and installing the proper 686 and 686-SMP kernel packages should be a piece of cake! =)

You can do it! Come on, man! :)

regards,
-dc

Any way to get the source of the kernel? I like the part where it finds all my hardware and stuff.. I just want to add to it.

---

### Post by Omnios on 2006-09-17
> **-deadcats said:**
> I agree with the previous poster. For someone coming from Gentoo/Arch, running Synaptic, doing a search on "linux" and installing the proper 686 and 686-SMP kernel packages should be a piece of cake! =)

You can do it! Come on, man! :)

regards,
-dc

Yo ucan updgrade change the kernel. The -SML version is for dual core. You can do a kernel search with synaptic and read up on what they are for.

---

### Post by Scunizi on 2006-09-17
Go to System/Admin/Synaptic and search for 686.  You'll see the 686 kernals listed. Pick the newest and right mouse click/install Apply and away you go!  You'll have to do a reboot though.

---

### Post by tommcd on 2006-09-18
See this thread:
[http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)
All you need to know. Just install from terminal:
sudo apt-get install linux-686-smp
or do the same via synaptic.

---

