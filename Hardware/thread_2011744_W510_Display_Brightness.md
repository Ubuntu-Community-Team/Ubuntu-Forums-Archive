---
title: "W510 Display Brightness"
date: 2012-06-27
forum: Hardware
---

### Post by fbicknel on 2012-06-27
This is in several places on the web, here's a very concise one:

[http://www.ryanlothian.com/projects/linux/thinkpad_w510_ubuntu_12_04](http://www.ryanlothian.com/projects/linux/thinkpad_w510_ubuntu_12_04)


The upshot of which is to add this to your xorg.conf file:

```
Option "RegistryDwords" "EnableBrightnessControl=1"
```This goes in the Device section thereof.

Now for my contribution: I figured that logging out/in or restarting lightdm:

>  $ sudo service lightdm restartWould do the trick.  But for my situation, this didn't work.

It might have been in some funky mode: it had not had an extensive xorg.conf (a small, non-specific file with only a device section).  It had been suspended many times... the last one left the display dim.  

Anyway, a reboot did it and things are working now.

My situation:
> DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"

---

