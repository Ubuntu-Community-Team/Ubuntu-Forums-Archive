---
title: "su: Authentication failure"
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by msohn88 on 2009-04-08
[http://www.linuxjournal.com/video/get-your-webcam-working-gspca](http://www.linuxjournal.com/video/get-your-webcam-working-gspca)

I followed this HOWTO to fix my Webcam for GSPCA, but at 1:55.

He typed "su" command, and it shows with 

> 
su: Authentication failure


HELP!

---

### Post by taurus on 2009-04-08
If you've assigned a password for root, then you would run that; otherwise, use sudo.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by msohn88 on 2009-04-08
> **taurus said:**
> If you've assigned a password for root, then you would run that; otherwise, use sudo.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I get:

> 
FATAL you need to install the Kernel Source for your running kernel


ARUGH

---

### Post by taurus on 2009-04-08
Go into synaptic and Search for linux-image.  Then, install the headers for the kernel version that you are running.

---

### Post by benj1 on 2009-04-08
> **taurus said:**
> Go into synaptic and Search for linux-image.  Then, install the headers for the kernel version that you are running.

would that work? you need your password to use synaptic.

---

### Post by taurus on 2009-04-08
> **benj1 said:**
> would that work? you need your password to use synaptic.

You would use the same password that you log in with, assuming you belong to group admin.

```
id
```

---

### Post by benj1 on 2009-04-08
> **taurus said:**
> You would use the same password that you log in with, assuming you belong to group admin.

```
id
```

good point.
hmm will have to read up on passwords and sudo, i thought they were both essentially the same

---

