---
title: "FGLRX-control and atp-get conflicts"
date: 2006-04-07
forum: Hardware &amp; Laptops
---

### Post by pizmal on 2006-04-07
I just installed a ATI radeon card in my computer. The driver is working fine and started looking up a way to dual monitor.  I came accross a HOWTO ATI driver that said if I install FGLRX-CONTROL i could span my display.  So I apt-get installed and now I have a conflict i am unable to get rid off.  I tried to remove the fglrx-control and it still prompts me to reinstall a libstd... file.  Here is the error msg i am getting:

E: /var/cache/apt/archives/libstdc++5_1%3a3.3.6-8ubuntu1_i386.deb: trying to overwrite `/usr/lib/libstdc++.so.5.0.7', which is also in package compat-libstdc++-33

Any Thoughts:  At this point I would be happy to have the error go away and just mannually configure xorg.conf

--Piz

---

### Post by pizmal on 2006-04-07
FIXED:

sorry must have jumped the gun on the post. the FGLRX-control panel isnt the only thing to uninstall I need to remove the driver too.  I dont need them since i installed the ATI driver off ati.com.  I guess I cant use the old control panel.  But at least apt-get is working and I can manually edit xorg now.  FUN :)

--Piz

---

