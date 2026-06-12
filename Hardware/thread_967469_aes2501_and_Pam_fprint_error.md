---
title: "aes2501 and Pam fprint error"
date: 2008-11-02
forum: Hardware
---

### Post by gnom on 2008-11-02
Hi,
I installed 8.10 few days ago, now I'm setting it up - the last thing to go is my finger print reader. My laptop is HP dv6750ew with AES2501. I followed [http://blog.irwan.name/?p=471]("http://blog.irwan.name/?p=471"). To install aes2501-wy, libfprint0, libpam-fprint and fprint-demo I used Synaptic - everything went smooth.
But the problem starts when I'm trying to complete "E.g 1: Integration with su utility" step of that tutorial - I modified */etc/pam.d/su* but when I try *su -* I get: ***Could not locate any suitable fingerprints matched with available hardware.***

Everything works great from print-demo - my fingerprint is displayed and recognized.

Thanks in advance for help!

---

