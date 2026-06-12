---
title: "Java plugin doesn't work in a Wubi installation"
date: 2008-07-21
forum: General Help
---

### Post by Nerdzrool on 2008-07-21
Hey, I am running into an unusual problem I was hoping you guys could help me with. I have been trying, with little success, to install the Java Firefox plugin. I was told on a website to just run this line:

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

I ran this on an up-to-date, non-Wubi Linux installation and, indeed, it worked without a single problem (I modified my sources.list file earlier).

Now I have two other computers, one a laptop and one a desktop which both run Wubi installs and, for some reason both of these computers don't seem to recognize the java plugin. When the above is ran on both of the Wubi systems, it responds:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

```

Going into aptitude, on both computers, I get a little more insight, with it saying "Sun Java 6.0 Plugin cannot be installed on your computer type (amd64). Either the application requires special hardware features or the vendor decided to not support your computer type."

Problem is that neither computer is amd64, or even amd-made at all. One is a Intel Pentium 4 with HT 32-bit (laptop) and the other is an Intel VIIV Quad Core.

Now, I may be running to conclusions here, but the only connection these two totally different computers have is that they are Wubi installations (which I would assume act and for the most part are exactly the same as regular installations). Anyone know of problems similar to this, or have recommendations on how to convince apt that these computers are not amd64? Is this problem tied to Wubi?

---

### Post by ago on 2008-07-22
Nothing to do with wubi, if a package only has a binary for i386 then it will not be possible to install on 64 bit Ubuntu installations, whether pure installations or Wubi ones. There are alternatives and workarounds, but I would encourage you to submit that in the general forum.

---

### Post by Nerdzrool on 2008-07-22
Thanks for answering, yet I still strongly believe it does have some relation to Wubi. As I said, neither computer are AMD64s, or 64-bit in general. They have 32-bit versions of Wubi installed. I recently gave up on the laptop's Wubi install and converted it into a full Linux install and, on the same laptop that it once insisted was a AMD64 under Wubi, not only didn't make that claim this time, but actually went through the install correctly and the Java plugin works.

The quad, also not a 64-bit to the best of my knowledge (If it were, I would be allowed to use greater than 3 GB of RAM) needs Windows and keeping Wubi is the best option for it. It still has the problem.

The error message comes from the fact apt thinks it is a 64-bit OS, correct? If that assumption is correct, then either apt, the way Wubi configured my computers, or I am somehow running 64-bit OSes on 32-bit hardware went wrong.

---

### Post by ago on 2008-07-23
> **Nerdzrool said:**
> Thanks for answering, yet I still strongly believe it does have some relation to Wubi. As I said, neither computer are AMD64s, or 64-bit in general. They have 32-bit versions of Wubi installed. I recently gave up on the laptop's Wubi install and converted it into a full Linux install and, on the same laptop that it once insisted was a AMD64 under Wubi, not only didn't make that claim this time, but actually went through the install correctly and the Java plugin works.


What happens is that you probably have a dual core processor, which is 64 bit and hence Wubi did (correctly) install the 64 bit version of Ubuntu. While you installed manually the 32 bit version of Ubuntu. Quite obviously 32-bit-only packages would only work in the manual installation, but only because you did not install the 64 bit version... Nothing to do with Wubi.

---

### Post by stormtrooprdave on 2008-07-23
I had the same problem and tried every thread on this forum to get java plugin to work with firefox on ubuntu 64 bit.  In the end I just went into Synaptic and searched java plugin and enabled everything that said web browser plugin.  I imagine it might cause me problems with conflicts but I have now have java working with firefox 3

---

