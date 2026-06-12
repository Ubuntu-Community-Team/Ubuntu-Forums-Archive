---
title: "[SOLVED] NVIDIA 7900GT and resolution problem"
date: 2008-09-23
forum: General Help
---

### Post by ProfKaramba on 2008-09-23
Hi

I just installed ubuntu 8.04 and I can't use a resolution over 800x600.

I already did all the tutorials that I found in internet with no success.

Any other ideas?

---

### Post by HittingSmoke on 2008-09-23
I have the same problem when I use the Restricted Drivers Manager to install my Nvidia 7600 GT drivers.

I can only get the drivers properly installed using EnvyNG to install them. After using EnvyNG my cards settings are fully supportive. It's in the repos.

Strangely enough, the driver Envy installs for my card is the same the Drivers Manager installs but Envy install a lot of other things with it that I imagine are needed for the drivers to correctly identify my card.

---

### Post by drs305 on 2008-09-23
I agree with HittingSmoke. I have a 7600GT card and after installing the drivers using EnvyNG everything works fine. 

To install EnvyNG (in the universe repository): 
```
sudo apt-get install envyng-gtk
```

To run it:
System Tools, EnvyNG

---

### Post by ProfKaramba on 2008-09-23
I don't know how this can be possible but I already tried that without success. I did it again, and now it's working

sorry to take your time!

thanks

---

### Post by HittingSmoke on 2008-09-23
> **ProfKaramba said:**
> I don't know how this can be possible but I already tried that without success. I did it again, and now it's working

sorry to take your time!

thanks

You'd be surprised how often that actually happens (lol)

Glad you're up and running :)

---

