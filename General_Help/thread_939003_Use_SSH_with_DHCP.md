---
title: "Use SSH with DHCP?"
date: 2008-10-05
forum: General Help
---

### Post by Absinthe Minded on 2008-10-05
Hi all,

I'm starting up a new business and I'm going to try and run the whole thing on Ubuntu but I've come across a bit of a problem.

I want to access the PC remotely from home but the remote machine will be using DHCP, so I need to connect via the hostname, and that needs to be sent to the router. It looks like I can use SSH (openssh-server), so I've installed that via synaptic and all seemed to go well.

Now, I've tried editing the /etc/dhcp3/dhclient.conf file, as suggested [here]("http://ubuntuforums.org/showthread.php?t=177832") - but the attached device still shows up as unknown in my router config page.

Any idea what I'm doing wrong?

I use:

```
sudo gedit /etc/dhcp3/dhclient.conf file
```

to get to the config and edit the send host-name bit.

I'm a complete newbie to all this, so please bear that in mind!

Cheers,
Nick.

---

