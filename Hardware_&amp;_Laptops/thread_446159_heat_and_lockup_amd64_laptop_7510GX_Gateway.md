---
title: "heat and lockup amd64 laptop 7510GX Gateway"
date: 2007-05-16
forum: Hardware &amp; Laptops
---

### Post by Jeffj on 2007-05-16
After about six months of running windows I decided to boot up Ubuntu again and upgraded to the latest version, 7.04.

I noticed it got really hot. The W and E keys especially. The chrome Gateway logo was very hot to the touch (not a black body maybe?).

I went into synaptic package manager and clicked on everything heat related.
I get a message that says frequency scaling is not supported each time I boot.

Just now the computer locked up on me. It did it once before installed the temperature
programs and I thought it might be due to high heat maybe.

I just now removed all the temperature programs I had installed.

1. What software should I be using to monitor the temperature?
What is available for controlling the temperarture on an
AMD Athlon 64 3700+ ?

2. What log can I look at to determine why I'm locking up?

---

### Post by Jeffj on 2007-11-03
I'm still having heat problems.
I did a search and found a post about decompiling and
recompiling your dsdt.

I don't feel comfortable doing that.
I found this post suggesting a simple interface,
but a forum moderator killed it because
the information page said changing
your dsdt was dangerous.

[http://ubuntuforums.org/showthread.php?t=409993](http://ubuntuforums.org/showthread.php?t=409993)

I need a solution for my specific problem, but it looks
like the dsdt issue needs to be addressed overall.

-Jeff

---

### Post by 444 on 2007-11-03
The ability to replace the DSDT has already been in Ubuntu for a while:
```

$ cat /boot/config-2.6.22-14-generic  | grep DSDT
CONFIG_ACPI_CUSTOM_DSDT_INITRD=y

```

So at least you don't have to recompile the kernel, but you'll have to figure out how to to create said DSDT table and put it in the initrd image.

Another way would be to use k8fq to manually set the speeds.

---

### Post by _Stevie_ on 2008-01-20
is k8fq working well? 
i couldnt find too much info on it.

---

