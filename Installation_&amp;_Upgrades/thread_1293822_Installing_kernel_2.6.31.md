---
title: "Installing kernel 2.6.31"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by sibel1919 on 2009-10-17
Hi, i'm an absolute beginner on Ubuntu and have so far enjoyed my experience and because of this I don't want to revert back to windows again, but I'm having some trouble lately..

I've been trying to upgrade my kernel version _2.6.27_
to  the more recent version kernel 2.6.31 here.. [http://people.canonical.com/~apw/lp386468-karmic/]("http://people.canonical.com/%7Eapw/lp386468-karmic/")

the first deb installs fine, but the second header gives me an error: Dependency is not satisfiable :lbc6
 
I'm trying to install a new kernel to fix a problem with my wireless intel 5100 hmc
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418933](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418933)

I also tried to install an older kernel version 2.6.29 but I got another error when trying to install the image..Dependency is not satisfiable: wireless-crda

But I think the 2.6.31 would be better to fix my wireless problem..I just need to get all the debs installed..please someone help me out I've been scratching my head for ages now..

---

### Post by sibel1919 on 2009-10-17
I got it working, I had to find the wireless package missing and install it via synaptic..

---

