---
title: "Kernel panic? on X60s"
date: 2012-05-22
forum: Hardware
---

### Post by rogerdean on 2012-05-22
Hello all
I keep getting a system freeze (kernel panic?) on my Thinkpad X60s running Xubuntu Precise, as per the screenshot attached. It happens once every few days, seemingly randomly. I'm a bit of a distro hopper at the moment and this doesn't happen with Mint Debian or Wheezy.
Can anyone diagnose from the screenshot? Many thanks in advance
Roger

---

### Post by Redblade20XX on 2012-05-22
I think that each linux distribution takes the official linux kernel source, modifies it for the distribution and package them so that the end user just has to install it and not compile. In saying that, there could be a kernel problem for the said distribution. Try reinstalling the kernel source. From looking at the attachment, it seems as if the process scheduler is having trouble accessing certain memory addresses, which could be due to a random hiccup.

-Red

---

### Post by rogerdean on 2012-05-22
Thanks very much. This error has persisted over a couple of Xubuntu installs, so reinstalling the source won't be the answer I think. Does your analysis imply that there might be a problem with the physical memory in my laptop?
Cheers
Roger

---

### Post by Redblade20XX on 2012-05-23
> **rogerdean said:**
> Thanks very much. This error has persisted over a couple of Xubuntu installs, so reinstalling the source won't be the answer I think. Does your analysis imply that there might be a problem with the physical memory in my laptop?
Cheers
Roger

Most likely not since you've tried other distributions and never had the problem. If you want to check out your memory, try doing a memtest. Also did you do updates or clean installs because maybe some residual configuration files got carried over?

-Red

---

### Post by rogerdean on 2012-05-23
Clean installs Red. I guess it's going to be 'just one of those things' then...
Thanks for the advice
Roger

---

