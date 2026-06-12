---
title: "Ubuntu not detecting all of my RAM"
date: 2007-04-13
forum: Hardware &amp; Laptops
---

### Post by dmroberson on 2007-04-13
I recently upgraded my system, to 8GB of RAM.  Whenever I look at the System Monitor, in Ubuntu 6.06, it only lists 3.2GB.  Why does it not see the rest of my RAM?  GDesklets only shows 3.2GB as well.

The system supports up to 16GB of RAM, and BIOS detects all 8GB, but why can't Ubuntu?  I've searched the forum, but haven't found anything that really addresses this.  Does 6.06 not support this much memory?

Thanks.

---

### Post by moixa on 2007-04-13
There is a lot of issues involed here
CPU being 32bit or 64bit
OS being 32bit or 64bit

I am guessing your machine is 64bit but running 32bit OS. Since 64bit CPUs don't have PAE anymore, along with a 32bit OS, it can only address (4gb - io space) ~ 3.2gb RAM
so using a 64bit OS solves the issue.

Again, I am just guessing your setting, you need to give more detail here

---

### Post by dmroberson on 2007-04-13
Sorry.  Yes, it's a 64bit system (IBM Intelistation A Pro), running a 32bit OS.  So then the other 4GB is useless, unless I switch to a 64bit OS?

---

### Post by moixa on 2007-04-13
That's correct. 64bit CPUs expect you to use 64bit OS, that's why they drop PAE (CPU extension allowing to use 64GB RAM). If you are using 32bit OS on a machine without PAE, it can only address 4GB memory including your IO space, so subtracting off the IO space, you get roughly 3GB physical RAM available for the OS.
The ONLY option for you is 64bit OS

---

### Post by dmroberson on 2007-04-13
Ok, thanks.  I guess I'll planon upgrading to 64bit this weekend.

---

