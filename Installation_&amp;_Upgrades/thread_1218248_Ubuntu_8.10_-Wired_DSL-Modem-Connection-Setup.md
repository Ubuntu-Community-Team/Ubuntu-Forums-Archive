---
title: "Ubuntu 8.10 -Wired DSL-Modem-Connection-Setup"
date: 2009-07-20
forum: Installation &amp; Upgrades
---

### Post by cb2410 on 2009-07-20
Hello,

it is easy to get online with Ubuntu 9.04 but I have trouble to get online with Ubuntu 8.10 after a new installation. 


I am missing the "DSL-Tab" inside the Network Configuration window. Why is it not there?  Pls help - thx

-----

Normal installation routine would be:

**How to configure PPPoE in Ubuntu:**
**1**) Go to System > Preferences > **Network Configuration**.
**2**) Go to **DSL tab** (inside the Network Configuration window)
**3**) Press the **Add** button.
**4**) At Connection Name enter a name for your connection (you can enter everything you like).
**5**) If you want to connect automatically you can check **Connect Automatically**
**6**) At **Username** and **Password** enter the username and password your ISP provided.
**7**) Press OK.
**8**) To connect to the Internet using PPPoE select your connection from the Network choser at the top panel (somewhere near Volume and Date).



*******+  EDIT *****

I fixed the problem with the login

Use the Terminal:

```

sudo pppoeconf

```

- Follow the step-by-step instructions 
- Enter username and password (delete the word "username" in text field first)
- make sure you connect via boot (option should be selected)

Connect to Internet ISP
```

pon dsl-provider

```

Start Firefox and check if you can connect to the Web

Connectivity check
```

ifconfig pppo
plog

```

---

### Post by ZhuaSD on 2009-07-22
The network manager has been upgraded.  so there is not dsl tab on 8.10

I wish there was a dsl tab at my local bar.

Check out this thread for a fix:

[http://ubuntuforums.org/showthread.php?t=1176117](http://ubuntuforums.org/showthread.php?t=1176117)

---

