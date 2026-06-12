---
title: "ATI Radeon 9600 proprietary drivers : what's the point? (or am I missing something?)"
date: 2007-05-23
forum: Hardware &amp; Laptops
---

### Post by aks44 on 2007-05-23
First, as a disclaimer, I have to say that I'm not a native english speaker, so I may have misunderstood the (tons of) documentation I have read about ATI drivers (both free and non free).

However, I am under the impression that most people advise installing ATI's proprietary "fglrx" drivers. Being a Linux newb, I did that.
Oh well, it worked. But anything using openGL was soooooooo slow...

Then I installed the free "radeon" drivers (my video card is a Radeon 9600). Now openGL stuff is quite performant, I got AIGLX working fine and Beryl runs like a charm.

So, the question is : is there a good reason that people advise installing proprietary, slow drivers when the free ones are far more performant (at least when it comes to Radeon 9600)? Am I missing something important?

Thanks for your insights...

---

### Post by codesplice on 2007-05-23
Supposedly the open-source ati/radeon drivers are unstable.... though I haven't really seen that.  I've found the fglrx driver to be a lot less stable.  I'm running the ati driver with AIGLX and Beryl just fine after spending about three hours yesterday trying to make fglrx/XGL work reliably.

I too am kind of stumped on this issue.

---

### Post by aks44 on 2007-05-23
Hmm so this *may* be why my Xorg *sometimes* freezes when I just turned my machine on, after I login into KDE.

Now that I think of it, it didn't happen with fglrx drivers.

But well, I found that on this occasion an X reset (Ctrl+Alt+Backspace) solves the problem : I login again and then all goes fine...

The strange thing is that this kind of error only happens on warm up (when/if it happens), if I reboot the machine or do an X reset it doesn't happen...

---

