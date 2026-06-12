---
title: "[SOLVED] Swap Partition? Why?"
date: 2008-11-14
forum: General Help
---

### Post by radtek on 2008-11-14
I have 4 gigs of ram in my 64bit dual-core machine currently. I rarely use it all. The many times I've installed ubuntu and linux in general I've found that **not** including a swap partition breaks the network-connection and probably other progams. In fact I've only used about 2mb recently when using Transmission for multiple downloads.

The minimum I found that the system will allow me is an 8mb swap partition.

I find this to be anachronistic. Especially when memory is so plentiful and cheap and processors so fast.

Is there a plan for an option to not have a dependency on a swap partition for network-connections? 

Thanks...

Just stirring the pot...

---

### Post by Amarsingh0793 on 2008-11-14
You don't need SWAP unless you have a slower computer. 4GB RAM and a good processor means you don't really need SWAP - it's pointless with that awesome compter :)! I have a High-end Gaming machine and I use no swap at all, and everything runs flawlessly.

Hope this helped :)

---

### Post by SuperSonic4 on 2008-11-14
Just remember not everyone has a high end machine :)
Swap works very well on my laptop but is superfluous on the desktop yet both run Kubuntu hardy

---

### Post by ncanna1 on 2008-11-14
I would add at least a small swap partition just to be safe.  The swap file is equivalent to the windows page file.

---

### Post by Vadi on 2008-11-14
> **ncanna1 said:**
> I would add at least a small swap partition just to be safe.  The swap file is equivalent to the windows page file.

Quoted for truth

I have 4gb ram, but also have a 2gb swap partition (on a 250gb hd, it's fine) just to be safe.

---

### Post by damis648 on 2008-11-14
I always not only have a swap partition to be safe, but also for hibernation. Hibernating uses the swap partition, which i frequently do, so I always make a swap partition equal to the amount of RAM I have.

---

### Post by Amarsingh0793 on 2008-11-14
If you want to use SWAP with a high-end system, make sure that you do the vm swapiness stuff (the tendency of ubuntu going to swap instead of ram and vice versa). I would recommend a lower number for any system. I didn't know that hibernation on ubuntu needed swap - mine works without it :O!

---

### Post by Rocket2DMn on 2008-11-14
> **damis648 said:**
> I always not only have a swap partition to be safe, but also for hibernation. Hibernating uses the swap partition, which i frequently do, so I always make a swap partition equal to the amount of RAM I have.

A big +1
Swap is needed for hibernation, so I always recommend that users keep around at least as much swap as they have RAM.  If you don't typically hibernate your computer, maybe you should consider it - the system is completely powered off in this state, which is a big power saver (like for overnight).

---

### Post by Krupski on 2008-11-14
> **radtek said:**
> I have 4 gigs of ram in my 64bit dual-core machine currently. I rarely use it all. The many times I've installed ubuntu and linux in general I've found that **not** including a swap partition breaks the network-connection and probably other progams. In fact I've only used about 2mb recently when using Transmission for multiple downloads.

The minimum I found that the system will allow me is an 8mb swap partition.

I find this to be anachronistic. Especially when memory is so plentiful and cheap and processors so fast.

Is there a plan for an option to not have a dependency on a swap partition for network-connections? 

Thanks...

Just stirring the pot...

Machines with a lot of ram rarely need swap. The reason to have a swap partition (or swap file) is so that *IF* you use up your physical ram, Linux won't start terminating old processes to get some free ram.

Without swap to fall back on, Linux will start terminating old processes... and it doesn't know if a certain process is ESSENTIAL (either to YOU or to the OS).

You can end up with random failures or crashes if this happens.

No matter how much ram you have, you should also have a swap space setup.

Running without swap is like skydiving without a reserve chute. You probably won't need it, but if you DO..... [IMG]http://www.gunsnet.net/forums/images/eek.gif[/IMG]


-- Roger

---

### Post by Vadi on 2008-11-14
I would not recommend messing with swappiness on a high-end machine. If Ubuntu doesn't need swap, it simply won't use it.

---

### Post by Dugger5688 on 2008-11-14
So if by some off chance you run out of that 4-gigs of ram (lets say you run windows on a VM or whatever) you don't get a kernel panic. Plus HDD space is even cheaper than RAM and it just makes sense to have it available.

---

### Post by Mardoct909 on 2008-11-14
> **radtek said:**
> Especially when memory is so plentiful and cheap...

Much like hard drive space! You can afford to cough up 500 MB or more for the precaution the swap space offers.

---

### Post by SunnyRabbiera on 2008-11-14
Swap comes in handy even with high end memory, it acts like a safty net and like others said its good for hibernation

---

### Post by cdtech on 2008-11-14
Using swap is the way the Linux kernel handles the virtual memory subsystem thats incorporated into the code.

The only reason there is virtual memory in the first place is that you may not have enough RAM for all the programs running at once, and disk space was cheap. Swap is still tightly integrated into the kernel code and there should be some swap space used for this purpose. The kernel code runs smoother with some swap space.

**UPDATE::.**
Think of the older systems that need swap. You really need the integration of swap within the code for such cases. As SunnyRabbiera stated you need disk space to hibernate to as well (if you hibernate).

---

### Post by thestig_992 on 2008-11-14
Im sure if you have 4gig of ram, you also spent some money on a large hdd, so just take about a gig or two out of that, you wont notice any space missing at all.

---

### Post by radtek on 2008-11-17
Thanks guys...

Good answers. I kinda figured the integration aspect. I guess it is here to stay...

I guess a gig or so wouldn't hurt. I'm not a power user and I don't use hibernate. My paltry 8mb swap has sufficed so far so I'll wait for my next installation which could be next week or next year- depends on how I feel. Or...

I guess I could resize the Swap? Nope... Gparted doesn't allow it.

Can I add another?

---

### Post by cdtech on 2008-11-17
You could always use this guide if you wanted to add more swap:
[http://www.linuxtopia.org/online_books/redhat_enterprise_linux_sysadmin_guide/s1-swap-adding.html](http://www.linuxtopia.org/online_books/redhat_enterprise_linux_sysadmin_guide/s1-swap-adding.html)
11.2.3. Creating a Swap File

---

### Post by CatKiller on 2008-11-17
> **radtek said:**
> I guess I could resize the Swap? Nope... Gparted doesn't allow it.

It does, but you can't mess with a partition that's mounted.

```
sudo swapoff -a
``` will unmount your swap partition. ```
sudo swapon -a
``` will turn it back on again. Note that if you actually delete your swap partition and re-create it, the UUID referenced in /etc/fstab will no longer be valid, and you'll need to amend it to reflect your changes.

---

### Post by radtek on 2008-11-17
I have a 8mb swap and an extended partition that is made up of my /boot and /  andusing swapoff doesn't allow me to make the partition larger- only a mb smaller.

I'd have to resize the / in order to make room for the new swap-partition- correct? Or would that enable me to resize the original swap without creating a new swap-partition?

Not exactly up to speed with how linux flie systems are set up. I tried to go as simple as possible as before  I've run into ownership and permission problems by creating seperate / , /root and /home partitions on one machine.

I tried to unmount the / to resize and of course... I can't.

Maybe I'll need to re-install with a better partition config. Ideas?

Thanks.

---

### Post by CatKiller on 2008-11-17
> **radtek said:**
> I have a 8mb swap and an extended partition that is made up of my /boot and /  andusing swapoff doesn't allow me to make the partition larger- only a mb smaller.

I'd have to resize the / in order to make room for the new swap-partition- correct? 

That sounds about right. It depends on quite how you've partitioned the drive, of course. But yes, you'd need to have some unpartitioned space in the right place to be able to expand an existing partition.

Obviously you can't unmount / before you fiddle with it, since the program to fiddle with it would be on the / partition that you just unmounted. So you'd use a live cd - either the Ubuntu cd or the GPartEd live cd - to do that.

You might find it easier to re-install, especially since you have a separate /home partition with your config on, but it isn't essential by any means. I've had to do quite a lot of partition shuffling since I installed Ubuntu 3 years ago, but I haven't had to re-install.

---

### Post by radtek on 2008-11-17
Thanks man... Ask a side question? You've been running the same instllation such as Dapper? Or you've managed to upgrade since and fixed all the associated problems? I've always done a clean installation since I've seen some horror stories.

If anyone else has anything to add please do so. I'll put this in solved status in a while.

Thanks again

---

### Post by CatKiller on 2008-11-17
> **radtek said:**
> Thanks man... Ask a side question? You've been running the same instllation such as Dapper? Or you've managed to upgrade since and fixed all the associated problems? I've always done a clean installation since I've seen some horror stories.

Since Hoary, actually. I was thinking about switching during the Warty phase, but it was with Hoary that I actually made the leap. I was dual-booting with Windows 2000 for a while, but I found that it was only the other users of my computer that were really using Windows. I forced them onto full-time Linux and removed Windows during Dapper. I had intended to keep Windows for them, but it's just so fragile, and didn't survive the partitions moving about. Since I wasn't using it anyway, I couldn't really be bothered to re-install it or otherwise fix it. So where it was is now an ext3 partition that I use for keeping music on.

Upgrades each time. Minor problems on a couple of the updates, but nothing that couldn't be fixed fairly quickly. I seem to recall that Edgy was the worst - I don't know if that's because it was particularly bad, or because experience with Ubuntu has made problems of similar complexity seem more straightforward. I'm still using my hand-tweaked xorg.conf, though :)

---

### Post by dcstar on 2008-11-18
> **radtek said:**
> 
........
If anyone else has anything to add please do so. I'll put this in solved status in a while.


[http://ubuntuforums.org/showpost.php?p=2528643&postcount=2](http://ubuntuforums.org/showpost.php?p=2528643&postcount=2)

---

