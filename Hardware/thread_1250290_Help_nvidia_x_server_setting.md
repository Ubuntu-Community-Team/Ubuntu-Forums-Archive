---
title: "Help: nvidia x server setting"
date: 2009-08-26
forum: Hardware
---

### Post by aljoriz on 2009-08-26
I am using a nvdia ge6100 and updated the driver.  

When I try to save display resolution (800x600 to 1024x768) using the 'save to x configuration file' button.  I would get this error:

Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

Can someone help?

---

### Post by distorteddork on 2009-09-02
go to system>preferences>display  click no, then set the settings you want. this is what worked for me.

---

### Post by gradinaruvasile on 2009-09-02
> **aljoriz said:**
> I am using a nvdia ge6100 and updated the driver.  

When I try to save display resolution (800x600 to 1024x768) using the 'save to x configuration file' button.  I would get this error:

Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

Can someone help?

It doesnt work because you dont have the permission to write to xorg.conf file. U have to launch nvidia settings with sudo privileges.

Hit Alt+F2 and type:

```
gksudo /usr/bin/nvidia-settings
```

This way u can save ur settings to xorg.conf. 

I would recommend using nvidia-settings to adjust ur configuration over the systems resolution switcher.

---

