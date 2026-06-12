---
title: "NVIDIA Geforce GT310M driver x86_64"
date: 2011-03-22
forum: Hardware
---

### Post by madallig on 2011-03-22
Laptop - Dell Vostro 3500 i3

Tried to install from Nvidia's site: 

[http://www.nvidia.com/object/linux-display-amd64-260.19.44-driver.html](http://www.nvidia.com/object/linux-display-amd64-260.19.44-driver.html)
It does not exactly list my driver as my driver is Geforce GT310M and the Nvidia site says: 310M - not sure if its spelling error or it's not same driver ....

All the instructions are here:

[http://us.download.nvidia.com/XFree86/Linux-x86_64/260.19.44/README/index.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/260.19.44/README/index.html)

What I did:
1.Reboot and enter into recovery mode
2. Scroll down and find root shell or similar
3. enter this script:
./NVIDIA-Linux-x86_64-260.19.44.run
It should unpack and install ... there will be some error messages but you can ignore and continue at your own risk!
4. Do not set Nvidia as default display - there is one button there - 
5. After reboot you are still on Intel display - 
6. To get into Nvidia display you can either use terminal following scripts found somewhere in the above link - or reboot into recovery mode and choose alternative display and restart xserver there ...
7. The Nvidia display does not seem to work correctly, and there are no easy settings to adjust, and if you do get into Nvidia display - the mouse cursor becomes an "X" and it seems that Nvidia display is actually just in recovery graphic mode - 
8. What is the terminal script to check what display is being used - 
9. If i have more time i will investigate further - or maybe someone has already modified the driver to work correctly??

Cheers!
madallig

 Dell Vostro 3500 i3 is an excellent laptop so far except for terrible speakers - such a disappointment!

---

