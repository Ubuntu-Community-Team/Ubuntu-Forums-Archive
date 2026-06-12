---
title: "Kernel Upgrade=broken system. Please help"
date: 2005-08-05
forum: Hardware &amp; Laptops
---

### Post by frustrate on 2005-08-05
Last night I went ahead and tried to install the 2.6.11-1 kernel package. dpkg -i the headers and kernel image. restarted. Couldn't log into X. 
Figured it had to do with the nvidia module needing a reinstall so I went started up the nvidia installer script. Got error, nvidia.ko unable to load something about kernel not matching my headers, which I know to be wrong, I downloaded the appropriate headers for the kernel image (sorry I can't post logs, I am on a windows machine). 

Frustrated, I decided to just scrap it go back to my original kernel 2.6.10-5,  the default with Hoary 5.04. I get back into X and try to run some of my 3d programs (wings, and Maya6.5, which I used HEAVILY), and got segmentation faults for both programs, as well as glxgears and glxinfo. I  went on and reran the nvidia installer script,  started X, everything worked again (hardware accel was back), !!!UNTIL i restart. !!!

---->Problem<-----
Everytime I restart my comp, x fails to load. the only way I can get x to load is by rerunning the nvidia installer script and then starting x. This is wrong. The only thing I notice out of place is a message about Nvidia TLS links while my system is booting, which I should mention  NEVER appeared  before now.  PLEASE help me get my system back.  I NEED to get back to my 3d work ASAP :(

btw..
this TLS, from as far as I can tell resides in /etc/rc0.d nvidia-glx (sorry if this is innaccurate i am away from my machine) and there is a file /etc/default/nvidia-glx with options to force use or unuse of these TLS links, which I know nothing about. On or off, i still fail to get into KDE on startup. Just a black screen and I have to ctrl+alt 2 to get a console. This sux. i need my machine back :(

---

