---
title: "How to I avoid this: In battery mode HD is turning on and off and on and off..."
date: 2009-08-23
forum: Hardware
---

### Post by MikeMay on 2009-08-23
I am using Ubuntu Netbook Remix on a EEE Pc. In battery mode the HD is turning on and off and on and off...
When it is turned off its spinning up after ~20 sec.
Then its turning off after around 2 minutes.

I heared that this is damaging the Harddisk...
Is there a way to configute this behavior?

Thanks,
Philip

---

### Post by binbash on 2009-08-23
You can enable laptop-mode if it is not enabled and edit the configuration files (i guess it is under main configuration file laptop-mode.conf or whatever its name). There is an option for that and the configuration file is well commented.

The config files are under /etc/laptop-mode/conf.d/

---

