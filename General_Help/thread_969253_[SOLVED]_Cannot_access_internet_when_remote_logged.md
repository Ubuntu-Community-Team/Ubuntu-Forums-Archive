---
title: "[SOLVED] Cannot access internet when remote logged on via ssh"
date: 2008-11-03
forum: General Help
---

### Post by LunaEqualsLuna on 2008-11-03
I have a machine running ubuntu that uses a proxy to access the internet.

When i am physically on the machine itself it can access the internet, install packages and down load things normally from the commandline.

When I remote log on to the machine however from another machine, none of these things work...attempts to download anything just get stuck as if it cannot access the internet. (commands like wget don't work when remotely logged in but they work when i input them on physically at the machine)

I don't really understand why his is happening. An ideas how to fix this.

---

### Post by Portmanteaufu on 2008-11-03
This is a total shot in the dark, but it might be worth trying: 

Type:
```
env
```
while you're at the computer and again while you're SSH'ed in. See if the SSH login is missing an environment variable or two related to proxy configuration. (e.g. I think there's supposed to be a $http_proxy variable to direct http traffic, an $ftp_proxy variable for ftp traffic, etc.)

If it turns out you *are* missing them, you probably just have to add those environment variables to your .bashrc to get it going over SSH.

---

### Post by LunaEqualsLuna on 2008-11-10
Thanks this was indeed the problem once i set the http_proxy enviroment variable appropriately in .bashrc everything worked out fine.

Thanks a lot!:guitar:

---

