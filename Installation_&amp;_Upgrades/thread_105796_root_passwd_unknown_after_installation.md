---
title: "root passwd unknown after installation"
date: 2005-12-19
forum: Installation &amp; Upgrades
---

### Post by metaljacket on 2005-12-19
Hi! Merry christmas! an early one.

I just installed a ubuntu on a winxp machine.

After new installation i found that i do not have access to root. 

The password i was asked to input during the installation process was given to my user name, i.e. i can enter my useraccount using the passwd i inputted in.  BUT I CANNOT LOGIN TO ROOT USING THIS PASSWD, AND THIS IS THE ONLY I HAVE EVER INPUT IN DURING INSTALLATION. I tried other possibilities, like 'root', ' return' etc, and nothing worked.

I did not input any other passwd during installation, i wonder where can the problem lie in? I have already tried reinstallation and the problem remains.

Thanks for your attention, wish you could gimme a clue.

---

### Post by frodon on 2005-12-19
Ubuntu don't use root account : [https://wiki.ubuntu.com/RootSudo?](https://wiki.ubuntu.com/RootSudo?)
The password for sudo is your user password by default.
If you want to become root in a terminal use this command : ```
sudo su
```

---

### Post by metaljacket on 2005-12-19
frodon:

thank you very much. I found a page using the key word provide by you.
Ubuntu looks different from other distributions, Might take some time to learn it. Ha ha

thanks

---

