---
title: "Two Ubuntu8.10 Kernels"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by huruixd on 2009-02-10
Hi friends,

I have a question and I would like to have your suggestions.

I installed Ubuntu8.10 last week on my brand new laptop. When I logged in the  Ubuntu, there was a update icon showing up on the desktop asking for software update. So I clicked it and did the update successfully.

Then I restarted my laptop, in the grub menu, there are two kernel options, asking for a choice. They are:
> Ubuntu 8.10. kernel 2.6.27-11-generic
Ubuntu 8.10. kernel 2.6.27-11-generic (recovery mode)
Ubuntu 8.10. kernel 2.6.27-7-generic
Ubuntu 8.10. kernel 2.6.27-7-generic (recovery mode)
Ubuntu 8.10. memotest86+
Other operating systems:
Windows Vista/Longhorn (loader)

My question is:
1. What is the difference between *Ubuntu 8.10. kernel 2.6.27-11-generic* and *Ubuntu 8.10. kernel 2.6.27-7-generic*?

2. Do I need to keep two kernels at the same time? I'd like to have your suggestions. Remove it or leave it like this? 

Thank you.

---

### Post by huruixd on 2009-02-10
Please don't let it done.

---

### Post by ibutho on 2009-02-10
Kernel-2.6.27-11-generic is newer than kernel-2.6.27-7-generic. If the new kernel works fine, then its ok to uninstall the older one using Synaptic (search for linux-image) although there is no harm in having two kernels installed.

---

