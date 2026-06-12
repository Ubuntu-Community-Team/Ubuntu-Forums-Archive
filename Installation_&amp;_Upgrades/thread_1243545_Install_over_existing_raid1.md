---
title: "Install over existing raid1"
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by froggy on 2009-08-18
Hi,

I'm trying to do some testing.

I have an existing CentOS Raid1 box used for testing purposes. It has Raid1 already configured as md0 software raid. I'd like to keep this. I'm willing to reformat md0 to wipe everything on it.

How can I do the install and keep my md0? I've searched around and ...

Any suggestion?

Thanks

---

### Post by ronparent on 2009-08-20
I think what you are trying to do is install to a reformated fresh md0? If so, try to install using the alternate cd. It has raid support built in and should recognize your raid drive when you start the install and support install to it.

---

