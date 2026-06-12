---
title: "Install programs from old Ubuntu to new? (without internet)"
date: 2009-02-08
forum: Installation &amp; Upgrades
---

### Post by my window broke on 2009-02-08
I currently have my ubuntu 8.10 on an External Hard Drive and was looking into putting it onto my main laptop hard drive without having to do a complete new installation and downloading of programs. I am at a boarding school so bandwidth is tight, so downloading all over again is kinda out of the question. Can I copy my whole system to a new partition on my laptop or can I make a new installation and copy all of my programs and user settings and get it to work on my laptop side?

---

### Post by cariboo on 2009-02-08
Check out aptoncd, it will create an archive of the archived packages in /var/cache/apt/archives. IF you haven't cleaned out the archive since you installed, every update and everything you have installed from the prositories should still be there.

> This tool will allow you to create a media (CD or DVD) to use to install
software via APT in a non-connected machine, as well upgrade and install
the same set of softwares in several machines with no need to re-download
the packages again.

The above quote is from the description of aptoncd from synaptic.

Jim

---

### Post by girishsasikumar on 2009-02-08
I would suggest u use Remastersys ... it works great and u get all ur old software on a cd/DVD and install it anywhere u want to .

[http://www.remastersys.klikit-linux.com/]("http://www.remastersys.klikit-linux.com/")

---

### Post by my window broke on 2009-03-01
I just ended up copying my partition on my external and pasted it on my partition on my main hard drive. Everything worked perfectly, even grub!

---

