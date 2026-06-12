---
title: "dns goes south on upgrade to 5.10?"
date: 2006-02-10
forum: Installation &amp; Upgrades
---

### Post by bodhidharma on 2006-02-10
Has anyone had problems with DNS going all flaky when upgrading?
I used a pretty generic sources.list and followed the BreezyUpgrade
directions, which sort of worked....
Then I thought I'd do an apt-get update ... and two weird things:
(a) it wants to upgrade something like 400meg of software... is this
     reasonable after a new install (upgrade 5.04->5.10)?
(b) it balks at many (most) of the connections to machines cited in
     sources.list... and when I manually ping them, it says it is trying
     1.0.0.0 -- which seems like name resolution failure.

in fact, I'm trying Automatix right now in the background, and it keeps
having this problem (the 1.0.0.0 thing)

But it is not consistent!  Firefox can find many sites, sometimes I *can*
ping sites (gmail.com, nytimes.com, ubuntu.com, etc.)

Any ideas?  Thanks!

---

### Post by lenzpa on 2006-02-12
I am going through a very similar problem as yours - e.g. apt-get update not downloading, wget resulting in the (1.0.0.0) thing, etc.  Originally, I couldn't even use Firefox.  This was solved by disabling ipv6.  I have now reached a stage where wget is no longer doing the (1.0.0.0) thing and this was achieved by changing /etc/modprobe.d:

Was:           alias net-pf-10 ipv6 
Changed to: alias net-pf-10 off #ipv6

It therefore looks like my problems could somehow be linked to ipv6(?).

I am sorry that the above won't solve your problem, but perhaps there are people out there who might give us some indications as to 1. whether ipv6 is the problem and 2. how to solve it?

All the best

---

### Post by toorima on 2006-02-12
[https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4](https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4)
That did it for me but I only had problem while wired, worked perfekt with wireless and network manager
After the fix both wired and wireless works like a dream :)

---

