---
title: "Upgrade from desktop to server?"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by auquicu on 2009-01-23
Elsewhere I have an Ubuntu server, and it is working nicely.
I have just installed Intrepid Desktop which has a very messy networking setup - I still have not gotten it to work correctly.
(There are many gripes, but one that I consider a serious security bug: the only way I have discovered so far of getting a network going only functions while I am logged in. That means that if I want to have the possibility to ssh into my machine from elsewhere, I must leave an unattended login. Very bad. Maybe "Desktop" is meant for laptops only?)

Anyway, my question: is it possible to upgrade desktop to server without reinstalling?

---

### Post by boof1988 on 2009-01-23
> **auquicu said:**
> There are many gripes, but one that I consider a serious security bug: the only way I have discovered so far of getting a network going only functions while I am logged in. That means that if I want to have the possibility to ssh into my machine from elsewhere, I must leave an unattended login.

I can't help with the "upgrade" to server.  Wouldn't it just be removing the ubuntu-desktop package and any (un)necessary dependencies?

Is there something wrong with the way the system is configured?  There is an Ubuntu-Desktop-8.10 machine on my home network that I can ssh into.  The machine (on my network) doesn't require an unattended login.  Just turn it on and leave it at the login screen.

Is the main difference between your setup and mine, you have to access the machine over the WWW rather than just over a home network?  If that is the case, I don't have any advice.

---

### Post by auquicu on 2009-01-23
Yes, no doubt something is wrong. But this is just a freshly installed 8.10 without any changes, up-to-date, on a new computer. The network was not set up by the installation, and under system/adm there is no network, and under system/preferences there is a menu item network configuration, but it looks like the configuration done there is personal preferences only, and the network connection given there disappears as soon as I log out. Somehow the authors of the scripts that handle this were not thinking of the old basic static network setup with IP, netmask, gateway, nameserver.

---

### Post by boof1988 on 2009-01-23
You might want (if you haven't yet) to check out the Networking & Wireless Forum(s).  I just did a little reading there and there may some useful info there. *dunno*

---

### Post by auquicu on 2009-01-23
Yes, thank you. I also did so and concluded that many people have rather similar problems. Setting of static network configuration seems to be broken in Intrepid. People advise to edit configuration files by hand, and I did, and that works, but leaves me unhappy.
Such handwork, although successful in the short run, tends to lead to unstable systems. I would prefer to switch to a version of Ubuntu where I can avoid this handwork. That is why I asked the above question.

Now concerning your reply: I learned from you that there exists a meta-package ubuntu-desktop. But adding or removing it does not seem to make any difference.

---

### Post by boof1988 on 2009-01-23
From what you are saying, it sounds like there is a bug(?) in the core of the Ubuntu 8.10 build regarding static ip addressing?

Oh... And it seems you're using static ip.  I'm using dhcp, so that must be why it's working for me.

I hope someone else can help some...

EDIT:

I wonder if installing the server kernel and then using it instead of the default Ubuntu-8.10-Desktop kernel would solve your problem.

---

