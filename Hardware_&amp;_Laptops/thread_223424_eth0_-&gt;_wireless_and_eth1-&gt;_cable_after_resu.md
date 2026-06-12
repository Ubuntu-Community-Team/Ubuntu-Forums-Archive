---
title: "eth0 -&gt; wireless and eth1-&gt; cable after resume?"
date: 2006-07-26
forum: Hardware &amp; Laptops
---

### Post by it.henrik on 2006-07-26
Hi ppl.

I need some help here.

I am running my wifi-card at eth1 and suspend the computer when it wakes up again my wifi card is now called eth0?

What is causing this and how can I make my network cards stop changing places. 

They do not switch places again if I do another suspend and resume.

Please help :) its the lst thing that does not work on my laptop ... help me become a fully-working-linux-laptop user :)

---

### Post by it.henrik on 2006-07-27
bump

---

### Post by Zed on 2006-07-27
If you look at
```

man interfaces

```
you'll see
> 
The ifup and ifdown programs work with so-called "physical" interface names. These names are assigned to hardware by the kernel. Unfortunately it can happen that the kernel assigns different physical interface names to the same hardware at different times; for example, what was called "eth0" last time you booted is now called "eth1" and vice versa. This creates a problem if you want to configure the interfaces appropriately. A way to deal with this problem is to use mapping scripts that choose logical interface names according to the properties of the interface hardware. See the get-mac-address.sh script in the examples directory for an example of such a mapping script. See also Debian bug #101728.


I solved this problem with the advice [here.](http://ubuntuforums.org/showthread.php?t=191900)

Lots more info in the [Debian reference manual on networking.](http://www.debian.org/doc/manuals/reference/ch-gateway.en.html)

---

### Post by it.henrik on 2006-07-28
Thnx heaps :)

---

