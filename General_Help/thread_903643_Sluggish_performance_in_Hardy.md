---
title: "Sluggish performance in Hardy"
date: 2008-08-28
forum: General Help
---

### Post by ExquisiteDeadGuy on 2008-08-28
Hey everyone,

I've been having some problem with severely sluggish performance running 64 bit Ubuntu. When doing certain things, especially switching to applications that have been idle for a while, the system slows to a crawl. The mouse cursor gets "jerky" and QuodLibet starts skipping. It'll sometimes take 1 minute or more to switch from Firefox to jEdit. If I click the Tomboy notes icon to pull up the drop-down menu, it'll sometimes take 20-40 seconds before that appears.

Overall it's so slow it becomes unusable. I can reboot the system and it's fast again for a few hours, then it goes back to being sluggish.

I've loaded up "top" on a terminal while it's being sluggish, the strange thing is, no process is using a large amount of CPU. Usually there's just a few apps using 3-10% CPU, however the "load average" at the top will be as high as 9.

My system isn't cutting edge, but it's not that slow. It's an Athlon 3000 64-bit, I have an nVidia card (I think a 7300 off the top of my head), and 1.5 gigs of RAM.

If anyone has any idea how I can diagnose and fix this sluggishness, I'd appreciate it.

---

### Post by gjoellee on 2008-08-28
[http://www.kshoster.net/?c=tipsandtricks&h=optimizehardy](http://www.kshoster.net/?c=tipsandtricks&h=optimizehardy)

---

### Post by ExquisiteDeadGuy on 2008-08-28
> **gjoellee said:**
> [http://www.kshoster.net/?c=tipsandtricks&h=optimizehardy](http://www.kshoster.net/?c=tipsandtricks&h=optimizehardy)

Thanks for the suggestion. I already did the "Stop unneeded startup programs", and my data is important so I don't want to risk data loss with the disk caching options. Please let me know if any other ideas come to mind.

---

### Post by Sycron on 2008-08-28
How much ram do you have ? Also are you using swap ?

---

### Post by ExquisiteDeadGuy on 2008-08-28
> **Sycron said:**
> How much ram do you have ? Also are you using swap ?

1.5 gigs. Yes, I think it's using swap. Here's the line from TOP:

Mem:   1545124k total,  1532440k used,    12684k free,     8980k buffers
Swap:  4096564k total,  1271500k used,  2825064k free,   155324k cached

---

### Post by Sycron on 2008-08-28
You have 4GB swap, and it is VERY MUCH ... Ubuntu needs no more than 384RAM (and you have 1.5GB).

You may fix this by disabling the swap.

type ```
sudo fdisk -l
``` and search the **linux swap** partition. Once you find it use this command.
```
swapoff /dev/your_swap_partition
```

Good luck.

---

### Post by ExquisiteDeadGuy on 2008-08-28
> **Sycron said:**
> You have 4GB swap, and it is VERY MUCH ... Ubuntu needs no more than 384RAM (and you have 1.5GB).

You may fix this by disabling the swap.

type ```
sudo fdisk -l
``` and search the **linux swap** partition. Once you find it use this command.
```
swapoff /dev/your_swap_partition
```

Good luck.

Thanks for the reply.

fdisk says:
/dev/sda2           38340       38849     4096575   82  Linux swap / Solaris

So I tried:
sudo swapoff /dev/sda2

And it says:
swapoff: /dev/sda2: Cannot allocate memory

Is there a different way I need to do this?

---

### Post by Sycron on 2008-08-28
> **ExquisiteDeadGuy said:**
> Thanks for the reply.

fdisk says:
/dev/sda2           38340       38849     4096575   82  Linux swap / Solaris

So I tried:
sudo swapoff /dev/sda2

And it says:
swapoff: /dev/sda2: Cannot allocate memory

Is there a different way I need to do this?

Excuse me,sir but i went wrong, sorry. Use this:
```
**sudo** swapoff /dev/sda2
```
Good luck&night. I'm not at home right now and I can tell you how to disable it forever... You have to do this everytime ubuntu starts...

---

### Post by ExquisiteDeadGuy on 2008-08-28
> **gjoellee said:**
> [http://www.kshoster.net/?c=tipsandtricks&h=optimizehardy](http://www.kshoster.net/?c=tipsandtricks&h=optimizehardy)

Actually I just reread that link and noticed the part about "swappiness". After some Googling, I tried this:

sudo sysctl -w vm.swappiness=10

And did:

gksudo gedit /etc/sysctl.conf

And added to the end of the file:

vm.swappiness=10


So far my performance has increased 10 fold! I'll keep you posted if I run into problems with this method.

---

