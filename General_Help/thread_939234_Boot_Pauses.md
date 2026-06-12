---
title: "Boot Pauses"
date: 2008-10-05
forum: General Help
---

### Post by Kaseas on 2008-10-05
When booting, it pauses once for 40 seconds during the "configuring network adapters" step, and when it hits the "Starting MTA" step it pauses for 15 more seconds.

Any idea what's causing this and why?

I am running Hardy on a HP Pavilion 2500 series laptop.

---

### Post by ghantoos on 2008-10-05
MTA stands for Mail Transfer Agent. It tries to get the IP of your hostname, if it can't find it, it hangs until it times-out.

You should edit /etc/hosts and make sure that your hostname is present there.

```

sudo gedit /etc/hosts

```then check if you see a line similar to:
```

127.0.0.1       localhost.localdomain localhost YOURHOSTNAME

```where "YOURHOSTNAME" is you actual box hostname.

If your hostname is not there, add it.

Hope this helps you out.

Cheers

---

### Post by Kaseas on 2008-10-06
Currently my /etc/hosts file is:
```

127.0.0.1 localhost
127.0.1.1 d-laptop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Do I need to do anything to it? (d-laptop is the name of my computer)

---

### Post by Kaseas on 2008-10-06
Anyone?

---

### Post by ghantoos on 2008-10-06
Try puting the following in your /etc/hosts file:

```

127.0.0.1 localhost d-laptop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```This is what I have.

Tell me if this does the job.

Cheers,

---

