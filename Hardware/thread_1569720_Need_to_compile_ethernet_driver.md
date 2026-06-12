---
title: "Need to compile ethernet driver"
date: 2010-09-07
forum: Hardware
---

### Post by HanDuo on 2010-09-07
Hi there,

I've just installed ubuntu server 10.04 on a via C3 board to learn about server computing. The installation from a usb-flash went well with the only exception that my ethernet controller isn't recognized by the system. 

Now I've downloaded a driver from Via, which has to be compiled. Well, I don't know much about compiling. 

What I did was the following: I made a directory called 'temp' and copied the package (rhinefet.tgz) in there. I extracted it and got the directory 'Rhine_5.20'.

I cd to 'Rhine_5.20'. In there are several files. One called 'Makefile'. I wrote 
./Makefile and got several messages:

./Makefile: 1: DEBUG: not found
./Makefile: 9: shell: not found
.
.
.
./Makefile: 15: Syntak error: word unexpected (expecting ")")

I never compiled anything before and since it's the ethernet not working I can't access the Internet to download anything like e.g. kernel source or any other packages/updates I need. 

I have another computer and could use that one for download and then copy the stuff to a usbflash. But there are to manny question at the same time. 
Do I need the kernel source and the linux-kernel-devel package? And if so: Where can I download them not using apt-get but to store them on the pen-drive?

Sorry folks, for some of you this might sound a bit long-winded. 
I can't help it. 

I upload the 'rhinefet.tgz' as 'rhinefet.zip' since it is not possible to upload .tgz-files here. I guess it makes it much easier to understand what I am talking about. I also attach the instruction 'linux.txt' from via seperatly.

Thanks to everybody who at least is reading this post.

Best wishes
HanDuo****

---

