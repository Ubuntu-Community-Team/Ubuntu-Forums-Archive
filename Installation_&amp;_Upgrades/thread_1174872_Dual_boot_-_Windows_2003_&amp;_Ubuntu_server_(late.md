---
title: "Dual boot - Windows 2003 &amp; Ubuntu server (latest version)"
date: 2009-05-31
forum: Installation &amp; Upgrades
---

### Post by philtrim on 2009-05-31
I have dual-booted Vista with the Ubuntu Desktop version ok, but what about dual booting Ubuntu server with W2K3 Server.  Can it be done (with Win2K3 already installed?)

Thanks.

---

### Post by VastOne on 2009-05-31
> **philtrim said:**
> I have dual-booted Vista with the Ubuntu Desktop version ok, but what about dual booting Ubuntu server with W2K3 Server.  Can it be done (with Win2K3 already installed?)

Thanks.

It would be no different in the setup process, but you would have not have an ubuntu desktop in the new server setup. You can get the desktop by running 

```
sudo apt-get install ubuntu-desktop 
```

---

### Post by philtrim on 2009-05-31
I just did not want to screw up my existing Win2K3 server.

I was afraid to go past the initial Ubuntu Server menu thinking I would not get an option (like with my other Win XP/Ubuntu Desktop install) to select a free area on the primary disk to install Ubuntu Server.

So GRUB will take over after the install and allow me to choose which OS to use?

---

### Post by theozzlives on 2009-05-31
You get the option, its just text based. Yes, GRUB will load like your Vista box.

---

### Post by philtrim on 2009-05-31
Thanks,

I will give it a try this week!

Thanks again for your prompt reply!

---

