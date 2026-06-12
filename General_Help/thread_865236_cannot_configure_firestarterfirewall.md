---
title: "cannot configure firestarter/firewall"
date: 2008-07-20
forum: General Help
---

### Post by danny138 on 2008-07-20
It seems as if it should be simple but the firestarter shows no Active Connections.The error reads "the device eth0 is not ready".It then says " Please check your network device settings and make sure your internet connection is active". Of course the connection is active. Is there a edit or change to make? I don't use the Terminal much as a very new user, any help will be greatly appreciated. Thank You

---

### Post by mcduck on 2008-07-20
hwat kind of conenctiona re you using to connect to the internet? Wired or wireless? Do you have multiple network cards in your computer?

Check the Firestarter's settings, there's an option to select which network interface the firewall should protect. Based on the error message you are connected through some other interface than Firestarter's defaut, eth0.

---

### Post by jerome1232 on 2008-07-20
> **danny138 said:**
> It seems as if it should be simple but the firestarter shows no Active Connections.The error reads "the device eth0 is not ready".It then says " Please check your network device settings and make sure your internet connection is active". Of course the connection is active. Is there a edit or change to make? I don't use the Terminal much as a very new user, any help will be greatly appreciated. Thank You

I know you said you don't use terminal much but personally I perfer UFW, it's installed by defualt and it's very easy to use.

for example if you wanted ssh traffic only
```
ufw default deny
ufw allow ssh
ufw logging on
ufw enable
```

that example tels ufw to make rules in iptables (that's what firestarter does as well) that deny all traffic execpt ssh and log rejected connections, then you can turn it on (that's the enable part). Once you've done ufw enable the firewall automatically turns on on startup no need to worry about anymore.

to do a specific port you can just do

```
ufw allow 8567
ufw allow 8999/tcp
```

first one would let traffic in on port 8567 tcp and udp
second one would let traffic in on port 8999 tcp only.

```
man ufw
```
would give you more info about how to use ufw

---

