---
title: "Setting up my new Dell M1210"
date: 2007-04-29
forum: Hardware &amp; Laptops
---

### Post by roncrump on 2007-04-29
Hi,

I am expecting delivery of a new notebook in a day or so - a Dell XPS M1210 - so I thought I'd post and see if their were any traps I could avoid falling in to while setting it up.

I want to end up with:
(1) a dual-booting system - Feisty as primary OS, but I need Windows occasionally for work stuff;
(2) a separate /home partition;
(3) a partition that both Windows and Ubuntu can see;
(4) wireless and wired networking; and
(5) continued  access to the Dell MediaDirect software.

I think that's it.

Any pointers gratefully received from anybody with experience of this system or similar.

Cheers,
Ron.

---

### Post by Alfdog on 2007-04-30
I think the media direct might be your only obstacle, as it uses it's own partition.

---

### Post by roncrump on 2007-04-30
> **Alfdog said:**
> I think the media direct might be your only obstacle, as it uses it's own partition.
So I need to try to leave that partition alone?
Do you know if it reads media from other partitions (eg windows or /home)?

Ron.

---

### Post by Alfdog on 2007-04-30
Do a little searching, but basically GRUB (Ubuntu's bootloader) kills the media direct partition.  It might be possible to make it work, but don't think it's really worth the hassle.

---

### Post by gohanssjn on 2007-05-01
I run Vista and Ubuntu on a Dell 1210.

I am set up like this:

C:\ Vista
E:\ Everything Else
\Ubuntu
[Logical Partition] with Ubuntu-swap, then MediaDirect.

I just told Ubunto to install GRUB to hd(0,2), the Ubuntu partition, instead of the drives MBR.  Works fine, but you lose Hibernation in Vista since it is no longer the boot partition.  MediaDirect works like a charm too.

Let me know if you have anymore questions on the subject.

Oh, and I have tried using the Vista bootloader, BCD, to keep Hibernation in Vista, but it will not boot Ubuntu, and I cannot figure out why.  Neither can anyone else I talk to >.>

---

### Post by gardara on 2007-05-01
I have a m1210 and I have my partitioning set up like this:

[IMG]http://www.psychocats.net/ubuntu/images/partitioning5.png[/IMG]

You should check out [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) for partitioning planning :)

---

### Post by gohanssjn on 2007-05-01
> **gardara said:**
> I have a m1210 and I have my partitioning set up like this:

[IMG]http://www.psychocats.net/ubuntu/images/partitioning5.png[/IMG]

You should check out [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) for partitioning planning :)

Get rid of MediaDirect?

Does the MediaDirect button do anything now?  That's one thing I HATE, is a dead button on a laptop.  Man, I can be so picky...

---

### Post by gardara on 2007-05-01
> **gohanssjn said:**
> Get rid of MediaDirect?

Does the MediaDirect button do anything now?  That's one thing I HATE, is a dead button on a laptop.  Man, I can be so picky...

The media direct button opens windows media center when I have booted up windows xp media center edition (that came with the laptop). 
The button doesn't do anything by default in ubuntu but you can bind it to some operation, for example let it open your music or videoplayer.... or maby some of those media center apps for linux...

:)

---

### Post by roncrump on 2007-05-02
> **gohanssjn said:**
> 
...(snip)...
I just told Ubunto to install GRUB to hd(0,2), the Ubuntu partition, instead of the drives MBR.  Works fine, but you lose Hibernation in Vista since it is no longer the boot partition.  MediaDirect works like a charm too.

Let me know if you have anymore questions on the subject.

Oh, and I have tried using the Vista bootloader, BCD, to keep Hibernation in Vista, but it will not boot Ubuntu, and I cannot figure out why.  Neither can anyone else I talk to >.>

So did you install from the standard or alternative CD to get control over where GRUB was put?

Have you tried grldr (grub4dos) as a way of doing this? It is mentioned in another post on m1210 installations that I have read over the last couple of days, and looks promising (if only I understood it).

Ron.

---

### Post by newtimes on 2007-06-08
what about the wi-fi catcher? does it work. and I dont ever use media direct so I dont care about it.

I have another harddrive I want to use because this one belongs to my job. they put a new one on  my m1210 so I have the new original one I want to use for ubuntu.  does anybody know what else works
and doesint work.  Thanks

---

