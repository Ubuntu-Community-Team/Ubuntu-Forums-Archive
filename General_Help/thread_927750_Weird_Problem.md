---
title: "Weird Problem"
date: 2008-09-23
forum: General Help
---

### Post by joeyknuccione on 2008-09-23
My Symantic as quit opening from Sys>Admin>Synaptic. It works from the command line though. I think tied into this problem, when using the command line to do modprobe, I'm getting:

unable to resolve host joe-laptop

This appears to have happened after trying to get my wifi/wired network configured correctly. In doing this, but after the Synaptic problem, I've installed Wicd, which appears to function normally.

Also, I think some of the lag I've gotten lately is a result of all this.

'Preciate any help.

---

### Post by joeyknuccione on 2008-09-23
bump

---

### Post by joeyknuccione on 2008-09-23
bump

---

### Post by joeyknuccione on 2008-09-23
bump

---

### Post by joeyknuccione on 2008-09-23
bump

---

### Post by -Zeus- on 2008-09-23
can you post the file /etc/hosts?

---

### Post by joeyknuccione on 2008-09-23
Thanks!
etc/hosts:

127.0.0.1 localhost
127.0.1.1 joe-laptop.joenet

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by joeyknuccione on 2008-09-23
bump

---

### Post by lisati on 2008-09-23
> **joeyknuccione said:**
> bump

> **joeyknuccione said:**
> bump

> **joeyknuccione said:**
> bump

> **joeyknuccione said:**
> bump

> **joeyknuccione said:**
> bump

Please be patient while other forum users contemplate a reply.....

---

### Post by kokkus on 2008-09-23
Hi. You have to wait 24 hours before you bump.
And you shouldn't bump in the first place. 
To many people it means the same as ignore the post.
If people are able to help you, they will.
A tip could be to post the tread when you see there are many people on the forum.

---

### Post by lintoon on 2008-09-23
Sounds like Synaptic is corrupt.  You could try reinstalling synaptic from the command line using apt-get.  Or check out the troublshooting section at the bottom of this page:

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

### Post by nikgare on 2008-09-24
What happens when you run this from a terminal:

gksu /usr/sbin/synaptic

---

### Post by joeyknuccione on 2008-09-24
Synaptic will run from the command line as nikgare suggested. From the Synaptic Troubleshooter that Lintoon suggested, it seems maybe my automatic DNS is messed up.

I will look for how to change this, but I'd appreciate if someone could explain this in the official language of noob.

---

