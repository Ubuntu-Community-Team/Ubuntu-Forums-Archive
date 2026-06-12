---
title: "Name resolution broken after upgrade to 9.10"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by awacs on 2009-11-04
The main symptom is that Postfix cannot deliver mail:
[...] (Host or domain name not found. Name service error for name=egg-mail.egps.com type=A: Host not found, try again)

but dig works:
# dig egg-mail.egps.com
[...]
;; ANSWER SECTION:
egg-mail.egps.com.      86400   IN      A       10.1.1.84

unless I try trace:
# dig +trace egps.com
[root server stuff snipped]
dig: isc_socket_create: address family not supported

and ssh fails:
# ssh [email]root@salami.egps.com[/email]
ssh: Could not resolve hostname salami.egps.com: 
Temporary failure in name resolution

Eh?

---

### Post by awacs on 2009-11-04
Bump.](*,)

---

### Post by jjcv on 2009-11-04
Have you got a namserver entry in /etc/resolv.conf that is appropriate:

You should see a line:

namserver 10.1.1.1   

Needs to be a valid namserver that you have access to.

---

### Post by awacs on 2009-11-04
> **jjcv said:**
> Have you got a namserver entry in /etc/resolv.conf that is appropriate:

You should see a line:

namserver 10.1.1.1   

Needs to be a valid namserver that you have access to.

No, I go to the roots.

---

### Post by awacs on 2010-04-28
> **awacs said:**
> No, I go to the roots.

This just happened again after apt-get update on karmic.

---

