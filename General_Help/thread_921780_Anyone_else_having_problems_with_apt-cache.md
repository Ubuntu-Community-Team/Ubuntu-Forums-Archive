---
title: "Anyone else having problems with apt-cache?"
date: 2008-09-16
forum: General Help
---

### Post by jakev383 on 2008-09-16
EDIT: Sorry, meant to say apt-proxy, not apt-cache!

I have apt-proxy set up and running on a Debian 4 machine I use for email, and tried to point my laptop at it, but it keeps erroring out.  Here's what my sources.list looks like:
```

deb http://192.168.76.4:9999/ubuntu/ hardy main restricted
deb-src http://192.168.76.4:9999/ubuntu/ hardy main restricted

deb http://192.168.76.4:9999/ubuntu/ hardy-updates main restricted
deb-src http://192.168.76.4:9999/ubuntu/ hardy-updates main restricted

deb http://192.168.76.4:9999/ubuntu/ hardy universe
deb-src http://192.168.76.4:9999/ubuntu/ hardy universe
deb http://192.168.76.4:9999/ubuntu/ hardy-updates universe
deb-src http://192.168.76.4:9999/ubuntu/ hardy-updates universe

deb http://192.168.76.4:9999/ubuntu/ hardy multiverse
deb-src http://192.168.76.4:9999/ubuntu/ hardy multiverse
deb http://192.168.76.4:9999/ubuntu/ hardy-updates multiverse
deb-src http://192.168.76.4:9999/ubuntu/ hardy-updates multiverse

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

```

Here are the entries for apt-proxy on the other machine:
```

[ubuntu]
;; Ubuntu archive
backends = http://us.archive.ubuntu.com/ubuntu

[ubuntu-security]
;; Ubuntu security updates
backends = http://security.ubuntu.com/ubuntu

```

But it always seems to time out.  Can anyone see what is wrong or offer any suggestions?

---

### Post by Pro-reason on 2008-09-16
If the title is wrong, you can edit that too.

---

### Post by jakev383 on 2008-09-16
Thanks! Did not know that, to be honest.
Anyway, I think I found my issue - seems I had the medibuntu repo installed, and it was hanging on their GPG key.
Seems to be good now though!

---

### Post by Pro-reason on 2008-09-16
> **jakev383 said:**
> I had the medibuntu repo installed, and it was hanging on their GPG key.

Did you remove Medibuntu or just add the key?  I recommend the latter.

---

### Post by jakev383 on 2008-09-17
I added the key.

---

