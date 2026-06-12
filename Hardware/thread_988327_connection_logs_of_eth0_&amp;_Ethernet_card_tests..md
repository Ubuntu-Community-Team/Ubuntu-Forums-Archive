---
title: "connection logs of eth0 &amp; Ethernet card tests."
date: 2008-11-20
forum: Hardware
---

### Post by Bruce M. on 2008-11-20
Hi Folks,

First and foremost I know ***nothing*** about networks. I know I plug my cable modem into my Ethernet card connection on the back of my desktop and it works. My cable modem can also be hooked up by a USB port. I haven't tried that but may have to at some point. So here's my questions, of which there are 3:

**1. Connection logs** - Is there a program I can run at boot-up that will create a log file of net (Internet) connections via the eth0 card? Something like:
```

20 Nov 2008 15:26 connected
20 Nov 2008 15:29 dis-connected
20 Nov 2008 15:29 connected
20 Nov 2008 15:42 dis-connected
20 Nov 2008 15:43 connected
```
**2. Test Ethernet Card** - Is there a utility, in the repos, that can test an Ethernet card? Mine is built into the motherboard.

I'm having "micro-cuts" quite frequently. I'll be on the net and network manager with tell me "no connection" seconds later I'm back. We've had the techies from my ISP here quite frequently for the past couple of months. Some of them have told us it's a "zone" thing and they are looking into it, but it's hard to find as it goes out and comes right back. Nobody thinks it's my machine, but they simply can't find what is causing it.

**3. Utility to test a Motorola Cable Modem** - does such a beast exist in the repos?

Thanks for your time.
Bruce

---

### Post by cariboo on 2008-11-20
Has anybody tried another network card to see if the problem goes away? I have a builtin nic on the motherboard of my server that did the same thing, replacing it with with a new one and disabling the onboard adapter solved the problem.

Jim

---

### Post by Bruce M. on 2008-11-20
> **cariboo907 said:**
> Has anybody tried another network card to see if the problem goes away? I have a builtin nic on the motherboard of my server that did the same thing, replacing it with with a new one and disabling the onboard adapter solved the problem.

Jim

No, no one tried that. But it has been something I've been thinking about on my own over the past few days.

Would like to see if there is a way to test this sucker first though.

Thanks for the reply.
Bruce

---

