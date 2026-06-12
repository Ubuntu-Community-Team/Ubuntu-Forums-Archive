---
title: "server configuration"
date: 2008-08-12
forum: General Help
---

### Post by dapim on 2008-08-12
i wuold like to configurate server 

Public Ip :123.15.117.112 forward to 110.45.4.4 on port 22 ssh

in witch file should i put this?

/etc/network/interfaces ????

---

### Post by ggaaron on 2008-08-12
For ip yes. What do you mean by forward?

---

### Post by dapim on 2008-08-12
when i connect to this server i want to forward ip

---

### Post by WRDN on 2008-08-12
> **dapim said:**
> when i connect to this server i want to forward ip

If you want the client to know the IP of the SSH host machine, then they will when they connect. To connect, you need to type the IP anyway. The command used is:

```
ssh [IP_Address]
```

I would recommend you change to a different port than the default port 22. To do this, type:

```
sudo gedit /etc/ssh/sshd_config
```

Now, change the the line "Port 22" to a different port. I use port 1025 personally.

Note that, if you know try to use the SSH command shown above, it will no longer connect, as it will use port 22 when attempting to connect. You will now need to use the command:

```
ssh [IP_Address] -p 1025
```

---

### Post by dapim on 2008-08-12
how i can do ipforward, where can i configurate this?

---

### Post by ggaaron on 2008-08-12
I'm still not sure what you want to do, but for ip forwarding I would check iptables.

---

### Post by dapim on 2008-08-12
i want to configura the server to allow  forward ip , public to internal ip

---

### Post by ggaaron on 2008-08-12
You mean:
world -> server -> other computers
And routing on server to allow this setup?

---

### Post by dapim on 2008-08-12
yes

---

### Post by cariboo on 2008-08-12
Do you have a router? or are you building the server to be a router?

If you have a router you do the port forwarding in the router. It is best that you set a static ip address on your server, so that ip address does not change when the dhcp lease runs out.

Jim

---

### Post by ggaaron on 2008-08-13
[http://www.gentoo.org/doc/en/home-router-howto.xml](http://www.gentoo.org/doc/en/home-router-howto.xml)

I've used this guide when making my router.

---

