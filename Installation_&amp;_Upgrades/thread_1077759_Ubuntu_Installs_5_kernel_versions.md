---
title: "Ubuntu Installs 5 kernel versions"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by EdSquareCat on 2009-02-22
Why does Ubuntu install 5 different kernel versions to boot up? What is the difference between using different versions? I just use the top-most one and it seems to work fine, but I don't know the difference.  The one below that boots to text-only mode. I want to comment some out in my menu.lst if I'm not going to use them (It's very cluttered :D)  Also, what is different in recovery mode?  What is the memtest86+ option?

---

### Post by jocko on 2009-02-22
> **EdSquareCat said:**
> Why does Ubuntu install 5 different kernel versions to boot up? What is the difference between using different versions? I just use the top-most one and it seems to work fine, but I don't know the difference.  The one below that boots to text-only mode. I want to comment some out in my menu.lst if I'm not going to use them (It's very cluttered :D)  Also, what is different in recovery mode?  What is the memtest86+ option?
When the kernel is updated, the older kernel is usually kept as a backup, which is why you get more kernels with time.
If you don't need them, uninstall them in synaptic, that will also remove them from the boot menu (search for "linux-image" in synaptic. Just keep the one with the highest number).
The recovery mode option is for booting to a root command line mode, where you can fix things if something gets broken. It may be a pretty bad idea to remove this option.
The memtest option is for testing if there is something wrong with the memory.

---

### Post by EdSquareCat on 2009-02-22
Only one kernel version works properly...? 2.6.24-19 boots to text only. 2.6.24-14,  2.6.24-15, 2.6.24-16 never boot - the screen flickers and they stop at ```
/dev/sda:
   setting Advanced Power Management level to 0xfe(254)
                                                              [OK]

```

2.6.24-11 boots with no problems.

---

