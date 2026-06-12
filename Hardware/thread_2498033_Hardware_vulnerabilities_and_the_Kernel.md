---
title: "Hardware vulnerabilities and the Kernel"
date: 2024-05-27
forum: Hardware
---

### Post by henk982 on 2024-05-27
Hi Guys,

A simple question but maybe not easy to answer. I could not find it. 

I have some old computers. Hardware updates are not supported anymore. 
I was thinking, are hardware vulnerabilities fixed by the Kernel? The Kernel does support drivers and hardware right? Or am I wrong?

And if I am wrong? How to fix hardware vulnerabilities on Linux/Ubuntu? The way I see it is that Fwupd does not nearly gives the same hardware updates that Windows does.

Thanks for your help!

Greetz,

Bas

---

### Post by currentshaft on 2024-05-27
The kernel is updated with the operating system. As long as you're on a supported release of Linux, your kernel is likely patched and secure. There are additional parameters and tools to audit and harden kernels, such as [https://github.com/a13xp0p0v/kernel-hardening-checker](https://github.com/a13xp0p0v/kernel-hardening-checker) - use them at your own risk, however.

Fwupd manages the firmware of your devices and depends on the manufacturer of them to publish updates.

Finally there are CPU vulnerabilities (such as meltdown and spectre), some of which can be patched or mitigated in software, but others which are architectural flaws or affect hardware which will never get updates. Here's another tool (again, use at your own risk) to assess some of those vulnerabilities - [https://github.com/speed47/spectre-meltdown-checker](https://github.com/speed47/spectre-meltdown-checker)

The bottom line is to stay secure online you need a modern operating system with recent hardware and as many vulnerability mitigations enabled as can be tolerated.

---

### Post by henk982 on 2024-05-28
Thank you for your clear answer.

A small follow up question.

How much of a concern are hardware vulnerabilities? Do I have to worry if I only use my computers for the basic stuff. Browsing, some libreoffice things, a bit of Netflix? 
Too me it seems a lot of money to buy a new PC every couple of years because of hardware concerns. And Linux is doing so well on older PC's, it would be a shame. 

Thanks again!

Henk

---

### Post by currentshaft on 2024-05-28
asd

---

### Post by henk982 on 2024-06-02
Thanks again for your reply Currentshaft. This really helps. Thank you!

---

