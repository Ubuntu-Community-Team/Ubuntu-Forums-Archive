---
title: "Missing Half of RAM"
date: 2010-08-27
forum: Hardware
---

### Post by nuehara on 2010-08-27
I've just installed 9.04 on my first build machine. It is only recognizing 3GB of RAM in linux, even though the bios recognizes my full 6GB. Any Ideas?

---

### Post by sikander3786 on 2010-08-27
You might have installed the 32-bit version. For fully utilising RAM more than 3GB, you neet to install the 64-bit version.

---

### Post by dapperdanny77 on 2010-08-27
hmm - is this a 32 bit installation ? - as fas as I know you can overcome the 4gb boundary with a pae kernel image

> apt-cache search linux-image |grep pae

first guess ...

---

