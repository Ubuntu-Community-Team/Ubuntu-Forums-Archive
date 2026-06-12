---
title: "Installing a pkg via windows"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by MikeJRamsey on 2009-08-20
I have a new Ubuntu build on a new machine. I don't want to connect it to the internet until I am confident that I have the security setup properly. Next to the ubunto machine is an old windows Xp machine with a fast internet connection.
 
I tried to download an ubunto package (denyhosts.deb) to the windows box, burning it to a CD (error messages about unable to copy some data), reading that CD on the ubunto machine and then executing
dpkg -i *package*
 
No joy. What do I have to do to download an ubuntu package on windows and burn it to a cd that can be used on ubuntu to install?
 
Thank you,
Mike

---

### Post by presence1960 on 2009-08-20
Ubuntu has no open ports by default. if you are worried activate the firewall by doing this in terminal ```
sudo ufw status
``` if inactive do this in terminal ```
sudo ufw enable
```

If you don't want to configure iptables there are a few frontends for them which are easy to install. one is gufw and the other is firestarter. These are not the actual firewall but are a graphical frontend to use in configuring the actual firewall.

[A must read]("http://ubuntuforums.org/showthread.php?t=510812")

Now go ahead and enjoy Ubuntu ! Forget that windows mindset.

---

