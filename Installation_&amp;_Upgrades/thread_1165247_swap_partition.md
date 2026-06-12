---
title: "swap partition"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by rishabh_destiny on 2009-05-20
I have dell inspiron 1525 with 2gig ram. I'm using jaunty. Prior to it, i was using hardy. My question is, I didn't made any swap partitions ever. 
My hardy was running smoothly... But i'm facing some glitches in jaunty. It is not at all that smooth.... It stucks everytime for few secs... I've bypassed the video card check to enable compiz. Is it due to this?? Or due to the fact that i have no swap?? If, du to compiz, how to resolve and get that smoothness back?? And if due to swap, i would like to ask:

1. Is swap recommended?
2. Is swap mandatory?
3. How do i now define swap after i've already installed without swap?

---

### Post by pennacook on 2009-05-20
compiz typically is more memory intensive. 

1. Is swap recommended?
  I could go either way on this. It is highly suggested.
2. Is swap mandatory?
   See 1.
3. How do i now define swap after i've already installed without swap? 
  Can add partition as type swap, add to /etc/fstab and reboot. Or you can set up a swapfile with mkswap, add to /etc/fstab and then use swapon to turn it on.

Check out your free -m and top output before and after to see your memory usage.

---

### Post by rishabh_destiny on 2009-05-20
Still not clear how to add swap. Do I have to create a seperate partition for that? I double boot ubuntu with vista and the partition of ubuntu is of 10 gb. 
Following is the output of my terminal:

rishabh@rishabh-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2004        807       1196          0         41        331
-/+ buffers/cache:        435       1568
Swap:            0          0          0
rishabh@rishabh-laptop:~$ mkswap
mkswap: error: Nowhere to set up swap on?
Usage: mkswap [-c] [-v0|-v1] [-pPAGESZ] [-L label] [-U UUID] /dev/name [blocks]

---

### Post by khelben1979 on 2009-05-20
> **rishabh_destiny said:**
> Still not clear how to add swap. Do I have to create a seperate partition for that?

Yes! That is to recommend.

[Ubuntu documentation on SwapFaq]("https://help.ubuntu.com/community/SwapFaq")

---

### Post by logos34 on 2009-05-20
With that much ram, technically you don't need a swap--unless you want to hibernate.

But you could try making a [small swap *file * ]("https://help.ubuntu.com/community/SwapFaq#Example%20of%20making%20a%20swap%20file")(which does not need a separate fpartition) to see if that helps with your issues.

---

### Post by rishabh_destiny on 2009-05-21
> **logos34 said:**
> With that much ram, technically you don't need a swap--unless you want to hibernate.

But you could try making a [small swap *file * ]("https://help.ubuntu.com/community/SwapFaq#Example%20of%20making%20a%20swap%20file")(which does not need a separate fpartition) to see if that helps with your issues.

I know. Even my hardy was working so smoothly with compiz enabled. But why is jaunty not working that smooth?

---

