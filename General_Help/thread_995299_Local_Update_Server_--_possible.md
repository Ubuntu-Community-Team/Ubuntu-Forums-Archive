---
title: "Local Update Server -- possible?"
date: 2008-11-27
forum: General Help
---

### Post by r0b0h0b0 on 2008-11-27
Sorry for the cross-post, I suffered a slip of the mouse...

We've recently replaced a bunch of windows machines here at work with Ubuntu 8.10 and so far, so good. The frequent updates are nice, but here in South Africa, bandwidth is really expensive.

Is there a way to set up one machine on the network as a kind of an "update server" where IT downloads all the latest updates, and then the other machines update from IT? Once each machine has downloaded the necessary stuff from this local update server, it then searches the repositories for updates specific to the software installed on it.

It breaks my heart (and my bank) to watch four machines download the exact same xxxMB of updates, individually.

---

### Post by Elfy on 2008-11-27
Maybe something along the lines of [https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

Also there's nothing to stop you copying the contents of an apt-cache to other machines and updating that way.

---

### Post by r0b0h0b0 on 2008-11-27
> **forestpixie said:**
> Maybe something along the lines of [https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

Also there's nothing to stop you copying the contents of an apt-cache to other machines and updating that way.

Thanks for the prompt reply. Two issues:

1) I'm going to need some hand-holding as my foray into the world of linux has just begun recently (in earnest).

2) One of the machines on the network is 8.04, the others are all 8.10. Is this going to be a problem?

---

### Post by adaptr on 2008-11-27
> **r0b0h0b0 said:**
> Thanks for the prompt reply. Two issues:

1) I'm going to need some hand-holding as my foray into the world of linux has just begun recently (in earnest).
You will be best served by an update **proxy**, which will download everything for the others, but never download the same package twice.
In essence, it offers its own package cache to the others as their repository.
I am quite certain there is an actual package that does this, as it's an unbelievably obvious idea.

> 2) One of the machines on the network is 8.04, the others are all 8.10. Is this going to be a problem?
Not at all, as a repository will contain, and a proxy will retrieve, all needed packages.

---

### Post by r0b0h0b0 on 2008-11-28
As my original was a cross-post, I got this reply from cariboo907 in the other thread:

> **cariboo907 said:**
> This:

[http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher](http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher)

may bw what you are looking for.

Jim

It looks like that is *exactly* what I am looking for. This is incredibly useful and I hope that a lot of people in a similar situation will find this thread.

---

