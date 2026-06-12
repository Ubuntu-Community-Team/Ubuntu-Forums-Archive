---
title: "Installing gentoo from a live cd"
date: 2008-12-02
forum: Gentoo and derivatives
---

### Post by canistra on 2008-12-02
well, I always wondered : is it possible to install gentoo from a linux live cd or directly from windows ? I just hate spending a couple of hours in front of a CLI ...

---

### Post by Ayuthia on 2008-12-02
You can do it from a liveCD  All you to do is chroot into the partition where you are going to install Gentoo.

I multi-boot so I am usually in Arch/Kubuntu when I install Gentoo.  The instructions are still the same based on the Gentoo Handbook:
[http://www.gentoo.org/doc/en/handbook/index.xml](http://www.gentoo.org/doc/en/handbook/index.xml)

---

### Post by imog on 2008-12-02
I used part 3 of this guide with an Ubuntu 8.10 livecd to install Gentoo.  You do mostly use the regular handbook, with only a slight difference:

[http://www.gentoo.org/doc/en/altinstall.xml](http://www.gentoo.org/doc/en/altinstall.xml)

---

### Post by canistra on 2008-12-03
Thanks for the answers ! I've got one more question: is it worth installing gentoo from pentium4 (*assuming I have a pentium4 cpu*) stage3 tarball provided by funtoo.org ? maybe it could affect my computer performance, because it is not officially supported by gentoo dev team ?

---

### Post by canistra on 2008-12-03
+ one more question :) !  I have chosen the Systemrescuecd (although i don't know if it has X up and a wm/de [so please answer to this question as well :)]) Ah yeah ! the question: how I will install gentoo from it like ordinary ? on gentoo docs pages there is only knoppix livecd installation example ...

---

### Post by djhyland on 2008-12-05
> **canistra said:**
> + one more question :) !  I have chosen the Systemrescuecd (although i don't know if it has X up and a wm/de [so please answer to this question as well :)]) Ah yeah ! the question: how I will install gentoo from it like ordinary ? on gentoo docs pages there is only knoppix livecd installation example ...

As stated before by Imog, it shouldn't matter which livecd you use to install from.  As long as your livecd has the required tools (read: stuff that ANY linux distro requires to run), you'll be fine.  Although I'm unfamiliar with the Knoppix instructions, I imagine that they'll work equally well, without alteration, for any other livecd as well.

---

