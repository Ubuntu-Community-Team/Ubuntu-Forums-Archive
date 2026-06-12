---
title: "using initramfs corrupted the kernel"
date: 2008-07-27
forum: Hardware
---

### Post by ohme on 2008-07-27
hello,

I have a lg p1 laptop, and after updating to 8.04 I had a shut-down due to high temperatures, during some (heavy) numerical work. after some experimenting I saw that the fan never turns on even when I get to extremely high temps.

I saw this page : [https://bugs.launchpad.net/ubuntu/+bug/211980](https://bugs.launchpad.net/ubuntu/+bug/211980) , which seemed relevant. I did what they suggest : 
1. load from their site dsdt.aml
2. running from shell : update-initramfs -u 
3. include in the kernel line on menu.lst the following : acpi_no_auto_ssdt .
4. restart. 

afterwards I could not load (!!!!) because it's stuck on boot after saying "starting up". so now I use the next kernel in the raw 2.6.22-15, and still don't have fan working, so I only run one process at the time.

does someone know what's wrong?

---

