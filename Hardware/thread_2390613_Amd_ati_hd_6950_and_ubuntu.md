---
title: "Amd ati hd 6950 and ubuntu"
date: 2018-04-30
forum: Hardware
---

### Post by engenier on 2018-04-30
Hi, i'm new to the forum.
My problem is:
I have an HD6950(Ubuntu 16 OS) but i want to use proprietary drivers, as i can see Ubuntu 16 and 18 don't support them, my question is which linux distro should i install to make them work? i googled it a lot, and i found arch linux should, so i probably switch to antergos, could you please be friendly with me and tell me some different distro or a possible fix to this?
Thank you a lot for reading my bad english.

---

### Post by deadflowr on 2018-04-30
The AMD drivers are only supported for any version below linux kernel 3.19 (or 3.18 I forget which).
So on Ubuntu that would be 14.04.1 which uses the 3.13 linux kernel.
This kernel version drawback applies to all distros.

You can get 14.04.1 from here:
[http://old-releases.ubuntu.com/releases/14.04.1/]("http://old-releases.ubuntu.com/releases/14.04.1/")
(Ignore the top banner as the version it holds is 14.04.1 and not 14.04.2)

---

### Post by engenier on 2018-04-30
Thank you a lot, so it depends only for the kernel?
for this reason could i use an ubuntu 16 with a different kernel?

---

### Post by deadflowr on 2018-04-30
> **engenier said:**
> Thank you a lot, so it depends only for the kernel?
for this reason could i use an ubuntu 16 with a different kernel?

I believe Xserver factors into it as well.
Can't remember what version, though.
But below 1.18 at least.

---

### Post by Yellow Pasque on 2018-05-02
> but i want to use proprietary drivers
Why?

---

