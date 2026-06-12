---
title: "SCP Error"
date: 2008-09-09
forum: General Help
---

### Post by ahounsome on 2008-09-09
Hi, every time I try and scp data over to my proxy box I get an error "host key verification failed. Lost connection". How can I fix this?

---

### Post by Jere_ on 2008-09-09
Hi

Has the connection worked earlier? One possible reason for this is that if you are running Debian or Ubuntu on your proxy box the SSL key has probably changed because of an update some time ago. The solution is to remove the host from known_hosts file. You can do that by entering ssh-keygen -R hostname as normal user.

---

### Post by ahounsome on 2008-09-09
I've reset the key on my local laptop and on the target PC. I'm still getting errors - permission denied, please try again - publickey,password.

---

### Post by Jere_ on 2008-09-09
The new error means that you either type your username or password incorrectly. Note that there's a difference between lower case letters and capitals! Also, if root login is disabled in sshd's config you will get that error.

---

### Post by ahounsome on 2008-09-09
what is really strange is that when the authenticity challenge comes up it lists the host name ok but the wrong IP address. It states the IP as 127.0.1.1, when in fact ifconfig states the IP as 192.168.0.3

---

