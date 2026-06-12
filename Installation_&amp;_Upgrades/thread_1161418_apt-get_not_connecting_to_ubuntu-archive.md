---
title: "apt-get not connecting to ubuntu-archive"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by hkgangwar on 2009-05-16
Hi all
somehow I lost my gnome-panel, so I decided to installed gnome panel by using
sudo apt-get install gnome-panel(I can't use synaptic as no taskbar is there, however it works properly when by gnome panel was working ).
Now I am getting message while doing apt-get install gnome-panel
"connection -timeout". 
When I read about this problem in archive,I tried apt-get--fix-missing etc,but nothing is working
Plz help me in getting gnome -panel some how by removing this connection problem

---

### Post by zeex on 2009-05-16
> **hkgangwar said:**
> Hi all
somehow I lost my gnome-panel, so I decided to installed gnome panel by using
sudo apt-get install gnome-panel(I can't use synaptic as no taskbar is there, however it works properly when by gnome panel was working ).
Now I am getting message while doing apt-get install gnome-panel
"connection -timeout". 
When I read about this problem in archive,I tried apt-get--fix-missing etc,but nothing is working
Plz help me in getting gnome -panel some how by removing this connection problem

hi, 

Is your network working, means can you access internet? Do you use any kind of proxy for accessing net?

If you do you need to specify proxy for apt in configuration file.

Add 

```
Acquire {
 http {
  Proxy "http://*user_name:passwd*@proxy.server:port";
 }
}
```

to file 
```

/etc/apt/apt.conf.d/70debconf
```

---

