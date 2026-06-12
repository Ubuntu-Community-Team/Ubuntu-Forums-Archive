---
title: "nvidia driver + Xubuntu Gutsy"
date: 2008-01-25
forum: Hardware &amp; Laptops
---

### Post by smacd on 2008-01-25
Hey guys,

I am trying to install the nVidia 169.09 driver on my fresh install of Xubuntu 7.10. However, when I run the program, I get an error that says:

> ERROR: You appear to be running an X server; please exit X before installing. 
       For further details, please see the section INSTALLING THE NVIDIA DRIVER
       in the README available on the Linux driver download page at
       [www.nvidia.com](www.nvidia.com).
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).


I'm not sure how to "exit X" before installing. it gave a process ID for X, but killing it just brings me out to the log-in screen.

My system:
Xubuntu 7.10 Gutsy / WinXP
AMD Athlon64 4000+
nVidia 7800gtx (evga)

Any tips or help?

---

### Post by Daez on 2008-01-25
try this:
```
ctrl+alt+F1
```

then login and type:
```
sudo /etc/init.d/gdm stop
```

next; cd to the directory with nvidia installer eg:
```
cd ~/Desktop
```

type:
```
ls
```

to see name of installer file and then excute installer with:
```
sudo sh NameOfInstaller
```

when it's complete type:
```
sudo /etc/init.d/gdm start
```

you may need to press:
```
ctrl+alt+F7
```

when thats done

---

