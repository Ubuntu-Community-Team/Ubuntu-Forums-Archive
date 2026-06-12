---
title: "NVIDIA Geforce Go 7600 on Asus A8JM"
date: 2007-05-17
forum: Hardware &amp; Laptops
---

### Post by Hatchy on 2007-05-17
Well, i'm new to linux, but now run Feisty on my Laptop and simplyMEPIS on my PC. 

I had a huge amount of trouble loading the nvidia drivers! I tried and tried and tried and failed and failed and failed. 

So here's how I eventually got it loaded for my Laptop (PC ran fine for Geforce fx 5700)

Go into Synaptic and get the following
Kernel Headers
Kernel source
binutils
linux-kernel-devel
linux-libc-dev

Then follow this guide fully. 
[http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html](http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html)


Where the guide says
sudo vi /etc/default/linux-restricted-modules*
- replace the * with -common


Good Luck!

---

### Post by Kobalt on 2007-05-17
The 7600 Go are working pretty fine when you install the drivers from the Restricted Drivers Manager. Your experience, using the legacy drivers for such a recent card, is pretty weird...

---

### Post by Hatchy on 2007-05-18
I didn't use the legacy drivers - this is a post as to how to get the GO 7600 to work on an Asus A8JM - it doesn't work from standard install and the drivers from the synaptic stuffed things up.
- This is for using the latest nvidia 9755 (I belive) release. 

Regards

---

