---
title: "apache user"
date: 2005-11-08
forum: General Help
---

### Post by odin on 2005-11-08
Hi all!!

I'm doing a set of scripts to configure an access point.It has an interface running on apache so you can conect and configure it from any computer in the LAN.

The thing is that the user apache is using to execute everything has no permissions to execute some of the commands I need.I dont wanna give root permissions to that user due to security reasons but the user has to execute commands like ifconfig iwconfig and iptables.

Any idea?

I know this might be confusing so if you need more explanations I'll post it

Thank's :)

---

### Post by cbkm on 2005-11-08
```

$ man sudo

```

Maybe something like,  /etc/sudoers:
```

apache          LOCAL = NOPASSWD: /sbin/ifconfig, /sbin/iwconfig

```

Edit: Oh, and then have apache/PHP/CGI whatever run
```

$ sudo /sbin/ifconfig ....

```

---

### Post by odin on 2005-11-08
Thank's for the fast reply.I'll try that when I get home

---

### Post by odin on 2005-11-17
[QUOTE=cbkm]```

$ man sudo

```

Maybe something like,  /etc/sudoers:
```

apache          LOCAL = NOPASSWD: /sbin/ifconfig, /sbin/iwconfig

```

Edit: Oh, and then have apache/PHP/CGI whatever run
```

$ sudo /sbin/ifconfig ....

```[/QUOTE]


But how do I edit /etc/sudoers so I can modify it??

---

