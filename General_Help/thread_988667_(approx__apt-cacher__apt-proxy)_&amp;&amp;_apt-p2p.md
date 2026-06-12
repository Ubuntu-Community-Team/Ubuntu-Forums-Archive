---
title: "(approx || apt-cacher || apt-proxy) &amp;&amp; apt-p2p ??"
date: 2008-11-20
forum: General Help
---

### Post by dutler on 2008-11-20
Hello, I am working on helping with some bandwidth issues both on my end on Canonical's - lots of US mirrors though but still, every bit helps.

**Goal:**
[LIST]
[*]Intelligently store packages that my network downloads in on a centralized server. 
[*]Look to this store first for packages.
[*]Serve my own repo for packages not in Ubuntu repos.
[*]Share the store via apt-p2p and download via apt-p2p.
[/LIST]

**Solution:**
I could have a nfs of my debs and run apt-p2p on every device on the local net- that would prob help a lot, but we have machines on multiple subnets and it sounds like trouble doing lots of config each machine and net.

I think having one server that has exposure to the Internet and to my nets would be better. This server would do the apt-p2p stuff and would need approx, apt-cacher, or apt-proxy.

**The Needed Help**
Searching for the three in the forums returns four results with out much of a comparison (and are dated). Looking for thoughts and wisdom about which of the three would be better for me and other's experiences solving the same problem.

thank you and regards, tom

---

### Post by dutler on 2008-11-22
not sure how to use launchpad answers and the forums - seams like having the questions tied right there with the package is a good idea. any way, asked a question about how apt-p2p works with apt-cacher-ng:
[https://answers.launchpad.net/ubuntu/+source/apt-cacher-ng/+question/52177](https://answers.launchpad.net/ubuntu/+source/apt-cacher-ng/+question/52177)

I have read how to import existing debs in to apt-cacher-ng, but what about using it with apt-p2p as well? Surely apt and apt-cacher can be configured to use the same debs?

Ahhh, but wait, maybe no extra config is needed. apt-p2p is a helper, so when apt-cacher-ng needs to download a package, by default, it ask apt which in turn uses apt-p2p all ready?

How does the caching server get its packages? If it is configured to use the proxy, one would get a loop? Yet if not, than the server does not use its own proxy service?

---

