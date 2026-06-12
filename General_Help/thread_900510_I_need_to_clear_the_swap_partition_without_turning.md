---
title: "I need to clear the swap partition without turning it off"
date: 2008-08-25
forum: General Help
---

### Post by Keyper7 on 2008-08-25
Okay, let's see if someone here can help me with this quite bizarre situation.

Hibernation is working perfectly in my machine and I noticed an unexpected benefit from using it: it apparently cleans memory leaks. When I wake up my computer, the RAM is at the minimum possible usage. There's one catch, though: the leaks stay in the swap partition and when I hibernate several times they start to accumulate.

So I need a way to clear the swap partition. Using swapoff does not work because when I do that all the contents are brought back to the RAM. I need to throw everything away and never see it again. I'm 100% sure that everything there is disposable.

---

### Post by WRDN on 2008-08-25
You could try wiping it by [writing zero's to it]("http://www.iusmentis.com/security/filewiping/wipeswap/#Linux").

> 
To wipe the partition, first turn it off so it is no longer in use. Then fill the partition with zeroes or random data. For example:

   1. swapoff /dev/[device]
   2. dd if=/dev/zero of=/dev/[device]


EDIT: As finer recliner said below, ensure you enter the right partition for swap. To find it, type "sudo fdisk -l" in the Terminal, and the devices will be listed.

---

### Post by finer recliner on 2008-08-25
> **WRDN said:**
> You could try wiping it by [writing zero's to it]("http://www.iusmentis.com/security/filewiping/wipeswap/#Linux").

omg please be super careful with the dd command. if you accidentally write to the wrong partition, you could overwrite personal files.

---

### Post by sdennie on 2008-08-25
I don't really understand this request.  If you have applications leaking memory, wiping the swap with dd won't fix the problem (and will probably crash your machine).  I would try to identify what applications are leaking memory and either shut them down before hibernating or file bugs against them.

---

### Post by mssever on 2008-08-25
> **vor said:**
> I don't really understand this request.  If you have applications leaking memory, wiping the swap with dd won't fix the problem (and will probably crash your machine).  I would try to identify what applications are leaking memory and either shut them down before hibernating or file bugs against them.
I second that. If you do a ```
sudo swapoff -a; sudo swapon -a
```and your RAM use increases, you've proved that hibernating has absolutely nothing to do with your memory leaks. Remember, swap is nothing more than a way to store RAM to disk. When resuming from hibernation, the kernel won't necessarily bring back stuff from swap until it's needed. What's in swap might not be your memory leaks. It could be somethign else, and there's no easy way to tell what it is. If you write zeros to a swap partition *that's not currently in use*, and do it right, you won't crash anything, but you won't gain anything, either.

---

### Post by Keyper7 on 2008-08-25
[quote=WRDN]You could try wiping it by writing zero's to it.[/quote]

Like I said in the original post, swapoff is not an option because it brings everything back to the RAM. I just want to get rid of it.

[quote=vor]I don't really understand this request. If you have applications leaking memory, wiping the swap with dd won't fix the problem (and will probably crash your machine). I would try to identify what applications are leaking memory and either shut them down before hibernating or file bugs against them.[/quote]

I firmly believe that the residue left in swap after I resume for hibernation is **not being used**. I have tons of free RAM when I resume. My best guess is that the hibernation process apparently identified that such residue was not necessary to resume and therefore never brought it back. And it never touches it again (no hd activity whatsoever). Perhaps it's not leakage, it's simply memory previously cached by programs. Regardless of what it is, I'm almost completely sure that it can be deleted because it's never touched again as far as I can observe by watching the (absent) hd activity for hours and hours while noticing no problems.

[quote=mssever]If you write zeros to a swap partition that's not currently in use, and do it right, you won't crash anything[/quote]

That's exactly what I want to know. I'm pretty sure it's not in use so I want to try wiping it. But I can't use swapoff because it will bring everything back to the RAM.

[quote=mssever]but you won't gain anything, either.[/quote]

I need to empty the swap partition. It's filling up more after each hibernation and I'm worried that hibernation might start to fail after it completely fills up.

---

### Post by mssever on 2008-08-25
> **Keyper7 said:**
> I firmly believe that the residue left in swap after I resume for hibernation is **not being used**. I have tons of free RAM when I resume. My best guess is that the hibernation process apparently identified that such residue was not necessary to resume and therefore never brought it back. And it never touches it again (no hd activity whatsoever). Perhaps it's not leakage, it's simply memory previously cached by programs. Regardless of what it is, I'm almost completely sure that it can be deleted because it's never touched again as far as I can observe by watching the (absent) hd activity for hours and hours while noticing no problems.That memory might not be used right now, but what happens if, down the road, some program tries to access that memory? You can't know that that won't happen, and if you've cleared the memory, the best possible outcome is that the program will crash. The program might accept the bad data, instead of crashing, and that could have disastrous consequences.

What you're asking to do is very dangerous and could hose your system. You can't know it's safe to do unless you actually analyze the data on your swap partition and determine exactly how and why it got there. That's too difficult to be feasible.

> That's exactly what I want to know. I'm pretty sure it's not in use so I want to try wiping it. But I can't use swapoff because it will bring everything back to the RAM.

I need to empty the swap partition. It's filling up more after each hibernation and I'm worried that hibernation might start to fail after it completely fills up.
You can try using dd to overwrite your partition (if the kernel will let you do it). BUT DON'T DO IT!

The proper solution is to find out which program(s) is/are responsible for your memory problems and deal with the problem that way (file bug reports, restart the offending program(s), etc.).

---

### Post by Keyper7 on 2008-08-25
Thanks for the answer.

My best bet is that the residue left is from caching. The system, instead of pulling the whole previous cache back from the swap, starts caching everything again. I even think that this is in fact the correct resume behavior (being minimal and not bringing back something that can simply be allocated again on demand). However, due to some bug the swap is not cleaned afterwards. If that's the case, it's not a memory per se, just an hibernation problem.

Anyway, I'm willing to take a risk because I plan on reinstalling my system soon anyway. But I believe dd will not work before a swapoff...

---

### Post by mssever on 2008-08-25
> **Keyper7 said:**
> But I believe dd will not work before a swapoff...
If that's the case, there's probably no way to do what you're asking. The kernel is--understandably--quite particular about what it allows outside processes to do with memory.

---

### Post by Jonie on 2008-08-25
I am not a kernel guru but I don't see anything wrong here.

All data that goes into swap is being cached first. It may seem nonsense to keep something that we want just to throw away, but this way the large system cache can used as if it were RAM and at the same time the cache size is not going to be reduced. I guess that if you hibernate, cache data (in this case data to be swapped) is being commited to disk (i.e. actual swapping occurs). After a couple of suspends more data is swapped to disk, but I doubt if these are memory leaks - this way you simply free more RAM at the cost of swap space.

If this interferes with the way you want to use your computer - adjust vm.swappiness parameter, but don't do it if you are not absolutely sure what you're doing.

---

### Post by Keyper7 on 2008-08-25
> **Jonie said:**
> this way you simply free more RAM at the cost of swap space.

The problem is that, after weeks of using hibernation, I have a very strong impression that the data left in the swap space is not used or even accessed again. **Ever**. Whatever programs did the caching in the first place start doing new caching all over again, directly in the RAM, and completely ignore the caching that's been left in swap.

Of course I'm just speculating, but it really seems that's the case.

---

### Post by mc4man on 2008-08-26
What would happen if you had 2 mounted swap partitions or 1 and a swap file? I would think you could wipe/use them individually at your leisure.
(unequal sizes

---

### Post by Keyper7 on 2008-08-26
> **mc4man said:**
> What would happen if you had 2 mounted swap partitions or 1 and a swap file? I would think you could wipe/use them individually at your leisure.
(unequal sizes

Hmm, how exactly I'd manage that? It seems that I'd have to unmount before wiping it anyway, bringing again the problem of everything returning to RAM.

---

