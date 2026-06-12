---
title: "Slow, unstable network with Edimax EW-7811Un"
date: 2014-08-14
forum: Hardware
---

### Post by henrik79 on 2014-08-14
Hello,

I'm having some trouble with my Edimax wireless network dongle. It's much slower than in Windows and frequently disconnects.

Anyone else have trouble with this?

What can I do?

Attaching some network/system info. Running Lubuntu 64 bit.

Best Regards

Henrik

---

### Post by varunendra on 2014-08-15
Not the same card, but the same driver, apparently same problem, and thus the same advice as in this thread (suggestion in post #4) : [http://ubuntuforums.org/showthread.php?t=2238888](http://ubuntuforums.org/showthread.php?t=2238888)

---

### Post by henrik79 on 2014-08-25
Sorry for late reply.

I tried the patched driver, but I can't see that it helped. Thanks for the suggestion though.

I think I will try another network card instead of trying to make this work.

/Henrik

---

### Post by varunendra on 2014-08-25
> **henrik79 said:**
> I think I will try another network card instead of trying to make this work.

Not a bad idea. You may take a look at thinkpenguin.com who claim to supply 100% Linux compatible hardware. Or purchase one from anywhere that you can be sure about that it works well on Linux.

We could try to make the current one work, but it seems time has more value for you than the money a new dongle will cost. :)

---

### Post by kurt18947 on 2014-08-26
> **henrik79 said:**
> Sorry for late reply.

I tried the patched driver, but I can't see that it helped. Thanks for the suggestion though.

I think I will try another network card instead of trying to make this work.

/Henrik

The patched driver should work.  I have an EW-7811Un and it works.  I wonder if the broken driver is still in use?  The script should blacklist the broken driver but ........
If you run the command "lsmod" in a terminal, do you see "rtl8192cu" listed, or "8192cu"?  rtl8192cu is the broken driver, 8192cu should work.

```

ThinkPad:~$ lsmod
Module                  Size  Used by
8192cu                632715  0 
ctr                    13049  0 
ccm                    17773  0 

```

---

