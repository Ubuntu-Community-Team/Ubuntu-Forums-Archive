---
title: "Nvidia tainting kernel?"
date: 2017-08-20
forum: Hardware
---

### Post by tmccaffery on 2017-08-20
I am getting following message in syslog:

nvidia: module verification failed: signature and/or  required key missing - tainting kernel

I am using NVidia Driver 375.66 instead of Xorg driver..

---

### Post by vocx on 2017-08-20
> **tmccaffery said:**
> I am getting following message in syslog:

nvidia: module verification failed: signature and/or  required key missing - tainting kernel

I am using NVidia Driver 375.66 instead of Xorg driver..
So? What is the problem?

This is just a message, but it does not indicate a problem.

My gut feeling is that "tainting the kernel" is just kernel-speak indicating that you are using a proprietary kernel driver (the Nvidia driver), so it is just like an asterisk, a mark indicating something to the kernel.

---

### Post by jeremy31 on 2017-08-20
Is Secure Boot enabled?  If Secure Boot is not an option/disabled the message won't affect anything

---

### Post by Yellow Pasque on 2017-08-20
[https://unix.stackexchange.com/a/118117](https://unix.stackexchange.com/a/118117)

---

