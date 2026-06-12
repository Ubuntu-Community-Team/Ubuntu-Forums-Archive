---
title: "Successful iBook G3 sleep/wake!!!"
date: 2005-10-19
forum: Hardware &amp; Laptops
---

### Post by Rinnan on 2005-10-19
Good people of Ubuntu...

I finally got my iBook G3 700 to sleep and wake correctly.  Here's how.

Originally, I had problems with my iBook waking up after sleep.  Sleeping was never a problem.  I had been bitten by this bug:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=1940]("https://bugzilla.ubuntu.com/show_bug.cgi?id=1940")

If you read the bug and comments, you will see that a patch has been submitted to fix it.  I applied this patch and it worked.  

The patch is here:
[https://bugzilla.ubuntu.com/attachment.cgi?id=4375]("https://bugzilla.ubuntu.com/attachment.cgi?id=4375")

To apply it, you need to follow the instructions from the wiki for compiling your own kernel.  The instructions are here:
[https://wiki.ubuntu.com/KernelHowto]("https://wiki.ubuntu.com/KernelHowto")

There is one small deviation from the standard instructions however. You must apply the patch to the kernel source before you compile it. At some point the instructions have you run a line looking like this one:
```
fakeroot make-kpkg --append-to-version=.181004 kernel_image --initrd binary
``` 
BEFORE you run that line, which will compile the kernel and create the new kernel .deb package, you must apply the ide fix patch. This is done like this:

```
bash:/usr/src/linux $ patch -p1 < /whereyouputit/ide-wakeup-fix.diff
``` 
Then proceed as normal with the instructions.

Note that the build takes a LONG time in a G3, about 3 hours or so for me.

Then, I installed the new kernel, according to the instructions in the HowTo.  Afterwards, however I did this:
```
sudo /usr/sbin/ybin
``` 
I'm not sure if this is necessary. Can someone more clueful on the PPC platform fill me in? In any case, it all works. YAY! For once all the hardware on my iBook works under Linux.

It is a day to remember.

Erik

---

### Post by SushiChef on 2005-12-26
Great Guide. even the complete noob to linux and ubuntu was able to understand it. It worked great on my ibook 800mhz duel usb! 

One error though, you linked us to the wrong patch, instead of downloading:
[https://bugzilla.ubuntu.com/attachment.cgi?id=4375](https://bugzilla.ubuntu.com/attachment.cgi?id=4375) ,
You should of directed us to download this one, it seems like this is the one you used:
[https://bugzilla.ubuntu.com/attachment.cgi?id=4376](https://bugzilla.ubuntu.com/attachment.cgi?id=4376)

excellent work though :D, I too have a fully working ibook, other than the fact that the volume keys on the keyboard dont work, but there's no reason they should :D

---

### Post by x2l2 on 2006-02-15
> excellent work though , I too have a fully working ibook, other than the fact that the volume keys on the keyboard dont work, but there's no reason they should 

volume keys (fn+f4 and fn+f5) works for me and  i didn't change nothing :P

---

### Post by Churusaa on 2006-05-10
We have liftoff!!!

Recompiled with that patch (and a really cool kernel hack that lets me use the sleep light as a Disk activity light =D) and it sleeps and wakes without any problems!!! I still (I think) have the issue with my sound card (headphone switch has to be tripped before I get any sound) but I can worry about that later!

Thanks man!
---Churusaa

---

### Post by Ptero-4 on 2006-08-28
Hi. Can you PM me the patch. The bugzilla link asks me a username and password (which I don't know).

---

