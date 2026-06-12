---
title: "Multi-touch scrolling"
date: 2011-04-06
forum: Hardware
---

### Post by Sidrabs on 2011-04-06
Hello,

I was excited to learn that Ubuntu now has pretty well-integrated multi-touch trackpad scrolling: [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

I installed the DKMS package, downloadable from here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/308191/comments/116](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/308191/comments/116)

Now my System -> Preferences -> Mouse -> Touchpad  shows nice options on this (see attachment).

It's not yet a full-blown multi-touch trackpad guesture configuration utility, but it's nice to see some movement in this area.

However, this scrolling is still pretty unstable, either the scroll step is too big, or the content jumps down or up uncontrollably. I fully understand this feature is currently very fresh and might still receive multiple bugfixes, etc. I just wanted to hear what is other user experience, and learn if there is perhaps a way how I could fix this myself.

---

### Post by belltown on 2011-04-06
> **Sidrabs said:**
> Hello,

I was excited to learn that Ubuntu now has pretty well-integrated multi-touch trackpad scrolling: [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

I installed the DKMS package, downloadable from here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/308191/comments/116](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/308191/comments/116)

Now my System -> Preferences -> Mouse -> Touchpad  shows nice options on this (see attachment).

It's not yet a full-blown multi-touch trackpad guesture configuration utility, but it's nice to see some movement in this area.

However, this scrolling is still pretty unstable, either the scroll step is too big, or the content jumps down or up uncontrollably. I fully understand this feature is currently very fresh and might still receive multiple bugfixes, etc. I just wanted to hear what is other user experience, and learn if there is perhaps a way how I could fix this myself.

I notice in [Bug #308191]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/308191") there are two other DKMS packages listed (in the "Bug Attachments" section towards the bottom of the right-hand column) for versions 1.1.0 and 1.1.1. Have you tried either of these? The one you linked to seems to be an earlier version (1.0.0).

---

### Post by Sidrabs on 2011-04-07
Damn, you're totally right, I should have been more careful. Installed the 1.1.1, the scrolling seems smoother now, I hope that is not placebo effect in action here :)

---

