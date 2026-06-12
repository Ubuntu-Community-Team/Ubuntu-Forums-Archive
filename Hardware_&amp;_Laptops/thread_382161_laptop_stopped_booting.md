---
title: "laptop stopped booting"
date: 2007-03-11
forum: Hardware &amp; Laptops
---

### Post by shoofy on 2007-03-11
Recently, my laptop has stopped being able to boot successfully into Ubuntu using the 2.6.17-11-generic kernel. For a while I could keep trying and it would boot on the 3rd or 4th try, but now it seems to have stopped working altogether. I tried booting in recovery mode and I always get the following error:

```
[17179600.96400] Bug: soft system lockup detected on CPU#0!
```

After that it would stop doing anything and I'd have to hard reboot. I can boot fine into the 2.6.17-10-generic kernel. Can anyone tell me how to fix this?

---

### Post by bernied on 2007-03-11
It's like that old joke,
Patient: Doctor it hurts when I do this
Doctor: Well don't do that

It sounds like there is an issue with that kernel and your laptop. You could have a look in the log files, particularly /var/log/messages
```
cat /var/log/messages
```though if it is crashing early perhaps there will be nothing there. 

You can try to get a bit more info by removing the 'quiet' and 'splash' options from the kernel line in /boot/grub/menu.lst - then you will at least see what the kernel is saying while it boots. You can also try things like 'noacpi' as kernel options, but have a look at the output first.

---

### Post by bernied on 2007-03-11
If it were mine and the previous kernel was working fine, then I'd use the old one.

---

