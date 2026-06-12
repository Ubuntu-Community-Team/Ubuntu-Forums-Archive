---
title: "how to upgrade linux headers"
date: 2006-01-15
forum: Installation &amp; Upgrades
---

### Post by kasemodz on 2006-01-15
Hi, right now I have kernel 2.6.12-9 and I want to upgrade to 2.6.12-10. I used synaptic to install 2.6.9.12-10 linux headers. It created another folder in /lib/modules. However, whenever I boot i still run 2.6.12-9. How do I run the 2.6.12-10 header?

---

### Post by Sutekh on 2006-01-17
What is kernel do you use now? 386, k7, AMD64, SMP?

Use
```

uname -r

```
to determine what you are currently using, if unsure.  

If you get 2.6.12-9-**386**, then use Synaptic to find the linux-**386** package.  Change the bold where necessary. 

It will install linux-image-386, which is the actual kernel and linux-restricted-modules-386.

Then you should be able to choose the new kernel in your bootloader.

---

