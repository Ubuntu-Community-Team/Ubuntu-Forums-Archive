---
title: "How to install AMD R5 M230 drivers on Ubuntu 16/18 + LTS version?"
date: 2018-08-22
forum: Hardware
---

### Post by Hemantkshirsagar on 2018-08-22
Can anyone tell how to install amd R5 m230 drivers on ubuntu 18 version?

There are no drivers for r5 m230 on amd webiste for 16/18 versions only 14 lts

And someone in their infinite wisdom has removed fglrx-core and fglrx from their repos..

Please help...

---

### Post by Mark Phelps on 2018-08-22
If you're referring to the older fglrx drivers, they have not been supported by AMD for years, now.  

But, others have said here that the newer Ryzen drivers are working -- I just don't have any details on those.

---

### Post by QIII on 2018-08-22
Before casting aspersions about "infinite wisdom", take heed of a bit of background:

For many years, AMD and Canonical have been carrying on a romance so close that many a tech writer has cried "Foul!"

As indicated, fglrx is no longer supported by AMD and it will not work on ANY modern distro.  While it was being developed, each new version was first made available to Canonical -- much to the chagrin of many in the Linux community.

With the advent of AMD's new technology, AMDGPU was developed primarily using Ubuntu as the platform.  It was first released in its experimental version targeted at ... wait for it ... Ubuntu.  Take a wild guess who got first crack at the final release.  Now take a guess which distro installs it by default on supported hardware.

If you were watching the AMD download site during development, you would have seen that the releases all targeted Ubuntu.

If your hardware is supported by AMDGPU, it is already installed.  If it's not, installing AMDGPU won't work.

Just so you know.

While Canonical is not above criticism, the absence of the fglrx driver is due to neither oversight nor poor judgement nor ineptitude.  Keeping a dead package in your repo is recommended no more highly than keeping a dead badger in your pantry.

---

### Post by Yellow Pasque on 2018-08-22
The open-source drivers should work out of the box. Most users don't need the proprietary drivers nowadays.

Do you actually have an issue with your graphics or are you just operating under the assumption that you have to use/install a different driver?

---

