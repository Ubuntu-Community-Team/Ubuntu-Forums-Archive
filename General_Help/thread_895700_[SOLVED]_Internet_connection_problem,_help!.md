---
title: "[SOLVED] Internet connection problem, help!"
date: 2008-08-20
forum: General Help
---

### Post by gsongpvamu on 2008-08-20
Hi, I just installed ubuntu hardy 8.04 on my new laptop. I have been using ubuntu on my old dell laptop, never run into any internet connection problem before. But for my new laptop, the connection is unstable. I set the ethernet to roaming mode. When I first start my laptop, usually no connection, and no dynamic assigned ip (use ifconfig to check). But after I restart the system, the connection will come back with 90% chance. Feel wired, anyone know what's the problem? Thanks a lot

The hardware information:

Detecting your network controller(s):

Broadcom Corporation BCM4312 802.11b/g (rev 01)
Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

---

### Post by prince_niceguy on 2008-08-20
do you have the ethernet cable plugged in when you start your computer? realtek should not be a problem. broadcom had some issues but that was in feisty days, i have not used a laptop with broadcom wireless for a long time now.

try starting your computer with ethernet cable in. If it is coming up then no issues.

Else you can try modifying the /etc/network/interfaces file to include your eth0 (ethernet) interface there. You will still be able to use network manager for configuring the wireless. Your ehternet would get configured automatically or just restarting networking services would do the trick.

---

### Post by prince_niceguy on 2008-08-20
To configure your ethernet in the interfaces do the following.

Open a terminal and type the following commands

```
sudo gedit /etc/network/interfaces
```

Now paste the following in the file which is opened

> 
auto eth0
iface eth0 inet dhcp


Save the file and close it. Now restart your networking service.

```

cd /etc/init.d
sudo ./networking restart

```

You will see some print outs regarding getting new ip etc. It should resolve the issue.

If it does then please do mark the thread as solved.

---

### Post by gsongpvamu on 2008-08-20
> **prince_niceguy said:**
> To configure your ethernet in the interfaces do the following.

Open a terminal and type the following commands

```
sudo gedit /etc/network/interfaces
```

Now paste the following in the file which is opened



Save the file and close it. Now restart your networking service.

```

cd /etc/init.d
sudo ./networking restart

```

You will see some print outs regarding getting new ip etc. It should resolve the issue.

If it does then please do mark the thread as solved.



Solved my problem, thanks a lot for your help, already marked this thread.

---

