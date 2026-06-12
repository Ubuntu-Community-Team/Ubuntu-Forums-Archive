---
title: "loading md and raid0 during initramfs? how?"
date: 2006-10-24
forum: Hardware &amp; Laptops
---

### Post by peller on 2006-10-24
Hello everyone. I'm new to Ubuntu, decided to give it shot (coming from Gentoo). I already have a linux raid0 partition setup, and when md and raid0 are built into the kernel, it automatically works. However, I want to try and stick with the default Ubuntu kernel. I've tried modprobing md and raid0 once the system is booted; this doesn't work. How can I replicate the behavior of having the modules built directly into the kernel? (I'm assuming this means loading them during initramfs). 
Thanks!
peller

---

### Post by Aberrix on 2006-10-24
I don't know if this helps or not, but I struggled with getting my (Fake)RAID setup for a couple days, especially while trying to use dmraid. I finally got it up and running with absolutely no problems simply by using the alternate-install CD. I was up and running in minutes.

---

