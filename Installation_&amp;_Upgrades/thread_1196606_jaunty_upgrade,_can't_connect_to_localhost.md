---
title: "jaunty upgrade, can't connect to localhost"
date: 2009-06-25
forum: Installation &amp; Upgrades
---

### Post by gleble on 2009-06-25
Hi
  Yesterday I upgraded to Jaunty from Hardy. Since then I cannot connect localhost. I can ping 127.0.0.1 I have apache running.Please help, I'm lost here.

---

### Post by Divider on 2009-06-25
```
cat /etc/hosts
```

Look for this line in the output.

```
127.0.0.1   localhost ip4-localhost ip4-loopback

```

If its not there. Add it.

---

### Post by gleble on 2009-06-25
No luck /etc/hosts now says
```
127.0.0.1	localhost
127.0.1.1	neil-laptop
127.0.0.1   localhost ip4-localhost ip4-loopback
hotwayd: 127.0.0.1
hotsmtpd: 127.0.0.1
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by Divider on 2009-06-25
Look at your spacing, its not aligned. You might have to bring the adapter down and back up.

```
sudo ifconfig eth* down
```

```
sudo ifconfig eth* up
```

*= obviously your adapter. But judging how quickly you assesed the response i assume you know this routine.

---

### Post by gleble on 2009-06-25
No luck

---

### Post by Divider on 2009-06-25
```
127.0.0.1 localhost localhost.localdomain
```

try addin that one.

---

### Post by gleble on 2009-06-25
Still no luck

---

### Post by Divider on 2009-06-25
wow this one is tricky, i'm fresh out of ideas. Might be a stupid question did you try rebooting?

---

### Post by gleble on 2009-06-25
Yes.  Could it be a ufw problem?

neil@neil-laptop:~$ sudo ufw status
Status: active

To                         Action  From
--                         ------  ----
139                        ALLOW   Anywhere
22                         ALLOW   Anywhere
23                         ALLOW   127.0.0.1
Anywhere                   ALLOW   127.0.0.1
Anywhere                   ALLOW   192.168.1.1
25                         ALLOW   127.0.0.1

---

### Post by Divider on 2009-06-25
if your behind a good firewall other than ufw or want to risk it for 30 seconds try taking ufw down and see it that works, then we know were the problem lies.

---

### Post by gleble on 2009-06-25
Turned ufw off. Didn't make any difference. Halfway through the upgrade it asks you to choose ufw settings i.e existing or new. I chose existing. Was that wrong?

---

### Post by gleble on 2009-06-25
Reinstalled XAMPP and alls OK Hooray

---

