---
title: "ATI Instalation"
date: 2006-11-14
forum: Hardware &amp; Laptops
---

### Post by robotux on 2006-11-14
Hi. I'm using Ubuntu 6.06 and recently changed my graphics card from a nVidia to an ATI.
I've uninstalled the nVidia driver and followed this tutorial:
[http://http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.29.6_drivers_in_Ubuntu_Dapper_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.29.6_drivers_in_Ubuntu_Dapper_Manually") 
to install the new drivers.
It all went ok but when i reach the part of testing the new drivers I only get the results shown on the tutorial if i run the commands as root. I mean instead of:

```
$ fglrxinfo
$ glxinfo | grep render
```

I do:

```
$ sudo fglrxinfo
$ sudo glxinfo | grep render
```

So can please anyone tell me if the drivers are installed for the normal user? I don't think so because if I try to watch a movie using xine i get a huge amount of frame drop. But if i launch xine by the console as root the movie plays fine.

Can anyone help me on this please?

---

