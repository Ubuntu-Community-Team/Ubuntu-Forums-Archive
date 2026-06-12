---
title: "[SOLVED] Compiling kernel specifying Pentium M"
date: 2007-06-16
forum: Hardware &amp; Laptops
---

### Post by saul_2110 on 2007-06-16
Hi. I have Celeron M laptop. I want to compile the kernel for some other thing and fooling around I found that I could specify the type of processor. Even though there wasn't Celeron M, I could select Pentium M (I read a little and Celeron M is based on Pentium M). Expect a little improvement, could I try it without blowing away my hardware?
Thanks.

---

### Post by hardyn on 2007-06-16
i don't think you will damage anything, its more question if it will boot or not.

---

### Post by saul_2110 on 2007-06-17
Thanks. I tried and it did boot although I got the message 

```
intel_rng: FWH not detected
```

I'm not sure if it is due to the change in the processor specification (Pentium M) in the kernel but it looks like it (the "intel" part of it).

---

### Post by saul_2110 on 2007-06-17
Hi again, just to complete information...
Even when running the default kernel (2.6.20-16-generic), the message 

```
intel_rng: FWH not detected
```

still  appears.

---

### Post by IntuitiveNipple on 2007-06-17
This shouldn't be a problem. **Intel_rng** is the Intel hardware Random Number Generator. **FWH** is the FirmWare Hub through which the RNG, if present, is accessed.

It is probable that your system doesn't have the harware RNG. You could simply stop the Intel_rng module being loaded by adding it to the modules blacklist.

---

### Post by Lord Illidan on 2007-06-17
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/102982](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/102982)

---

### Post by saul_2110 on 2007-06-17
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/102982](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/102982) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **IntuitiveNipple said:**
>  You could simply stop the Intel_rng module being loaded by adding it to the modules blacklist.

blacklist is at /etc/modprobe.d/blacklist [for those who don't know where it is... I didn't ;)

I tried that. The messaged doesn't appear anymore. Also put the comment on Lanchpad. 
Thanks.

---

