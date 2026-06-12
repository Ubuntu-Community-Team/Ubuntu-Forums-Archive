---
title: "How to install video drivers for Intel(R) Extreme Graphics"
date: 2012-10-16
forum: Hardware
---

### Post by Larstpoint on 2012-10-16
Hi everyone,

I have a quick question.  How do i install my video drivers for Intel(R) Extreme Graphics.  I don't know if its needed but I have a Compaq Presario v2000.

---

### Post by Axxon95 on 2012-10-19
> **Larstpoint said:**
> Hi everyone,

I have a quick question.  How do i install my video drivers for Intel(R) Extreme Graphics.  I don't know if its needed but I have a Compaq Presario v2000.

If by Intel Extreme Graphics, you mean Intel HD Graphics, they are installed by default.

You can check and see if they are installed and working by:
[ sudo apt-get install mesa-utils ]
then
[ glxinfo | grep render ]
and to test it
[ glxgears ]

---

