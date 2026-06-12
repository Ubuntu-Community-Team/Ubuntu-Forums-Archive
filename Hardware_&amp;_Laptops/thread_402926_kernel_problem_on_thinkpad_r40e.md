---
title: "kernel problem on thinkpad r40e"
date: 2007-04-06
forum: Hardware &amp; Laptops
---

### Post by bharath.bhushan on 2007-04-06
I am using feisty on a thinkpad r40e. 2.6.20-2-generic kernel works fine. But any kernel after that has a strange problem. If I hold a key pressed, the key repeats for one second, then it does not repeat for one second. Then again it starts repeating for one second and so on. The same thing happens for the mouse. It stops moving every second (roughly).

I would appreciate any kind of help. Also please ask if any more info is required. (The fun starts when I want to type the password at the console -- I don't know which characters got typed and which ones did not :) )

---

### Post by ozstriker78 on 2007-04-10
I am having the same issue with my r40e.  The keyboard is very unstable.  It's very inconsistent and unusable.  I get see flapping between character repeats in spurts of about 5, keys not functioning, to delayed reactions.  The mouse buttons and pointer act very unstable.  The mouse is jumpy and sometimes the mouse buttons don't work, but other times it works fine.

If you need more info, I'm glad to give it to you.

---

### Post by Morbid Angel on 2007-04-11
same here... it takes a long time to load acpi modules and start hald... after that same problems with keyboard/mouse... any sollutions? (I have tried it with knoppix and there I didnt had any problems)

cu

---

### Post by Msakaji on 2007-04-19
Yes, please help! I have this exact problem on my own ThinkPad R40e.

I installed Feisty freshly from an ISO onto a clean disk today and I am experiencing the exact same symptoms: the inputs are frustratingly locking up at intervals of approx every second, after about 10 seconds there's a short 20 or so second period of normal operation, after which the behaviour        repeats :/

On booting, the system takes quite a while loading hald, too. :(

Edit: adding the line 'acpi=off' to GRUB before booting didn't help, so it doesn't appear to be ACPI to me..

---

### Post by Msakaji on 2007-04-19
I reported this as a bug here:

[https://bugs.launchpad.net/ubuntu/+bug/107859](https://bugs.launchpad.net/ubuntu/+bug/107859)

If you want to see it fixed or wish to add any more information on your experience of this bug, please add a comment.

---

### Post by smithsmg on 2007-04-23
Same problems on my r40e. On old 6.10 all worked fine.

---

### Post by smithsmg on 2007-04-26
Quick and dirty solution - kill both acpid and hald daemons. In my case killing hald help, looks like problem with them.

---

### Post by smithsmg on 2007-05-05
Keyboard and mouse after downgrade of kernel to version 2.6.17-10-generic start works fine.

---

### Post by threespacemen on 2007-06-04
I know "me too's" aren't particularly helpful, but.... me too.

Experiencing the same with my R40e, and I've been sticking with the 2.6.17-10-386 kernel because of this problem (are there any security implications with this kernel?).

Question for the other R40e users - have you experienced similar, although nowhere near as pronounced, keyboard problems even on this older kernel? I sometimes find that not every letter typed shows up, especially when typing over, say, around 50-60 wpm (as an example, I've probably had to go back and reinsert about 3 or 4 letters just typing this). It's only mildly annoying, especially in contrast to the issues with later kernels, but it can become frustrating, especially when coding. Thought for a while that it may have been hardware error, but I'm fairly sure it's the kernel (and not my typing!).

Might play around with hald and see if that changes things...

---

### Post by threespacemen on 2007-08-22
Bump....?

Didn't seem to have any luck with hald, and the keyboard still seems to be exhibiting the same behaviour. I've been wanting to use this old "beast" for some audio editing, and thought I'd try the realtime kernel from texware.it. Unfortunately the same problem exists with this kernel, and the patches at [http://people.redhat.com/mingo/realtime-preempt/older/](http://people.redhat.com/mingo/realtime-preempt/older/) don't go back as far as 2.6.17.

Hopefully this can be resolved in a future kernel, because I'd love to be able to use that realtime kernel and squeeze the most out of my faithful thinkpad.

How are other R40e users getting on...?

---

### Post by threespacemen on 2007-08-22
Hmm.. should've checked all the links first to avoid three posts in a row...

For those, like me, who haven't, the most recent post on the bug thread above gives a solution that, so far, seems to be working perfectly.

Using: 

Linux tardis 2.6.20-16-realtime #2 SMP PREEMPT Fri Jun 15 04:43:25 CEST 2007 i686 GNU/Linux

...no keyboard or mouse problems whatsoever. From the above link: add "ec_intr=0" to your boot line to fix this. I can't help thinking, though, that messing with the embedded controller will break something in ACPI somewhere...

Still, very happy indeed to have this fixed.

---

### Post by browneye253 on 2008-03-30
I tried pulling up the bug tracker link but it didn't seem to be active anymore.   Can someone elaborate a little more or repost the instructions for fixing this issue?

---

### Post by manytinyanimals on 2008-04-07
I have had luck adding "ec_intr=0" to GRUB boot entry.

(Open  "/boot/grub/menu.lst" with your favorite text editor and append "ec_intr=0" to the end of the line. You will have to do this everything your upgrade your kernel.)

This allows me to use the keyboard and everything else, although I don't think suspend works.

---

