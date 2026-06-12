---
title: "Linux fails to detect or use my wired connection"
date: 2008-10-27
forum: General Help
---

### Post by InlineSkate on 2008-10-27
Im using a wired connection through a netgear WGR614 router

---

### Post by InlineSkate on 2008-10-27
bump

---

### Post by InlineSkate on 2008-10-28
bump

---

### Post by plucky on 2008-10-28
Have you done any research on your problem? Alot of answers can be found by searching these forums.

Open a terminal **Applications > Accessories > Terminal** and copy and paste the output of these commands ```
lspci
sudo lshw -C network
ifconfig
```

To find out what those commands do,again in the terminal ```
man lspci
man lshw
man ifconfig
```

Also give as much of your system specifications and what version of software you are using.

Left click on the network icon and select **manual configration** Select Unlock and input logon password.
Can you see a wired connection card? If so click on properties and disable roaming mode and enable dhcp.

See if you can connect to the internet.

I am sure someone will then be able to help.

Good Luck

---

