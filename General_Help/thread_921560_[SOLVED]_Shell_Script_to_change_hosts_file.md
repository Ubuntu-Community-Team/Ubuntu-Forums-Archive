---
title: "[SOLVED] Shell Script to change hosts file"
date: 2008-09-16
forum: General Help
---

### Post by ashkev on 2008-09-16
Can someone help me write a script to switch back and forth between two hosts files?  I move my laptop between work and home, and when I am at work I need to point towards the private ip's for our servers, where as from home, I just need to point to th regular DNS addresses.

I have written a script to easily edit the hosts file:

```
#! /bin/bash
cd /etc
sudo gedit hosts
```

I would like to have a shell script that actually switches between two hosts files.

Thanks

---

### Post by Too Late on 2008-09-16
Umm... This is quite experimental, but you could do two separate config files and copy them to your /etc/hosts file.
```

#! /bin/bash
sudo cp -f /etc/hosts-config1 /etc/hosts

```
and
```

#! /bin/bash
sudo cp -f /etc/hosts-config2 /etc/hosts

```
where /etc/hosts-config1 and /etc/hosts-config2 are static files having the settings you need. I'm not sure what options the cp command would need.

---

### Post by ashkev on 2008-09-16
Thanks, works like a charm!

---

