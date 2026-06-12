---
title: "Afraid to upgrade. Unsupported video driver warning."
date: 2009-10-02
forum: Installation &amp; Upgrades
---

### Post by sptrsn on 2009-10-02
I'm running Ubuntu 8.10 on a couple year old HP Pavillion a1644x. 
I attempted an upgrade to 9.04, but got a warning saying the AMD fglrx drivers were not available. (See attached screenshot)
I stopped.

I'm afraid to do anything. When I first installed Ubuntu on this machine, I seem to recall getting a scrambled screen when fussing with video drivers and resolution and had to do a complete re-install. Unfortunately I don't recall what happened exactly, and I really am not interested in a re-install right now.


I'm desperately trying to move 100% to Ubuntu. I appreciate any help. 
The forum support for Ubuntu is the best I have ever seen for any computer related item I have ever worked with. 

Thanks in advance.
steve

---

### Post by markbuntu on 2009-10-02
That gpu is not supported by fglrx in Jaunty. You should remove fglrx before upgrading. The open source ati driver supports that gpu now.

---

### Post by tgalati4 on 2009-10-02
AMD/ATI thinks your 2-year-old graphics card is too old to support.  They are only supporting newer (HD-series) with the proprietary fglrx driver in Jaunty.  There is a new xorg that only supports the newer fglrx driver.  You can't mix and match.

Your choice is to stay where you are, or upgrade and enjoy OK 2D performance with Jaunty or Karmic.  The open drivers are improving, but experience is varied depending on your card and what you are trying to do.

---

### Post by sptrsn on 2009-10-06
sorry for the extended absence, but thank you very much for your responses. I'm thinking I'll stay where I am for the moment. I'm pretty close to being completely moved to Ubuntu. 

Once I figure out how to run a virtual xp, I'll wipe the drive on my primary machine and install the latest and greatest, and probably use this machine as a back up file server.

---

