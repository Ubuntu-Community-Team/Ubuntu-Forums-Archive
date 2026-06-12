---
title: "Wacom tools not working!"
date: 2008-03-21
forum: Hardware &amp; Laptops
---

### Post by haplo_09 on 2008-03-21
Hi everyboy., I encounter strange problem, for some reason wacom tools did not work.  after reinstalling ubuntu7.10. In particular  xsetwacom stopped working. I was getting the following message after I typed xsetwacom into the terminal. 

xsetwacom: error while loading shared libraries: libxcb-xlib.so.0: cannot open shared object file: No such file or directory

note that this happens after I configured and get sylus working.  tried to find some possible solutions on google but unfortunately there is not information reagring xsetwacom libxcb-xlib.so.0.  and . The strange thing is that when I installed 7.10 for the first time I did not see this problem. I could easily configure my table.  So I thought that I should make another clean reinstall  but it did not change things. The problem persits.  I am getting the same message. So, if anybody has any idea where to look for a solution or how to fix it share it,please.

---

### Post by perixx on 2008-03-25
I have no Wacom tablet by now, but have you had a look at this link here?
[http://ubuntuforums.org/showthread.php?t=25151&highlight=wacom]("http://ubuntuforums.org/showthread.php?t=25151&highlight=wacom")

Maybe you need to remove everything completely first, with: ```
sudo apt-get remove wacom-tools --purge
```
I'm not sure, but maybe there's the kernel driver missing for the Wacom tablet? You could check by running 'sudo modconf' and look for it there...

Another possibility that comes to my mind is that you're lacking the 'restricted drivers' - have you switched to Synaptic, enabled the 'restricted' repositories, made an update and tried to re-install the Wacom drivers again?

perixx

---

