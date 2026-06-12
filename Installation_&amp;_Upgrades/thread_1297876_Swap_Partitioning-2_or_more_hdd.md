---
title: "Swap Partitioning-2 or more hdd"
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by donato roque on 2009-10-22
I'm fresh installing Ubuntu 9.10 when it comes out, and I'm refreshing my knowledge on properly partitioning my 3 hdds.  

    Am I correct to create a swap partition on each of the hard drives?  I don't dual boot and my HOME is on a separate partition.  This is just a home desktop. 

    Thank you. I appreciate your answers and opinion.

---

### Post by wamanning on 2009-10-22
will you have multiple OSes installed concurrently?

if you do, and each OS is on a separate drive/partition, it makes sense for each OS to have it's own swap partition on the same physical drive as the host OS.  that said, there's nothing technically to preclude each OS's unique /etc/fstab reference a common swap partition - as long as the OSes cant be booted up concurrently!

if you have just one OS installed, but bits spread across multiple drives/partitions then you only need the one swap file as referenced in /etc/fstab

IMO it makes sense to have a dedicated swap for each drive/partition where you have an OS installed.

---

### Post by dandnsmith on 2009-10-22
Several years back I noticed that, where I'd created swap for 2 installs on different HDDs, both swaps were getting 'mounted' for use.

I don't know whether this is general behaviour nowadays.

---

### Post by dabl on 2009-10-22
> **donato roque said:**
> 

    Am I correct to create a swap partition on each of the hard drives? 

I would say "no", although I'm not sure "correct/incorrect" is the right paradigm for the topic.

The installer will find and set up _all_ swap partitions on all drives that are present during installation.  Therefore, there is normally no reason to have more than a single swap partition of sufficient size on a given computer, regardless of the number of hard drives and partitions. Having more than that adds complexity, but no performance enhancement.  :)

---

### Post by donato roque on 2009-10-22
Thank you for the reply.  
No need to worry then.  Just have to know what the installer is doing.

---

