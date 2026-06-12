---
title: "Installer not detecting my HD"
date: 2006-05-05
forum: Hardware &amp; Laptops
---

### Post by jjftails on 2006-05-05
Hello, I'm new a here, and I'm a newbie with linux. I tried to install ubuntu, and once I get to the partitioner, it says there is nothing TO partition because no hard drives were found. I have a Dell XPS 400 with a 3.2 GHz pentium 4 processer, 1 gig of ram, and 80 gigs of HD space. I have about 60 gigs of unpartitioned free space currently for the installation. I had also tried to install it on an external Hard Drive, it detected it, and I was able to get about half way through the installation when it tells me I need to reboot because it is going to install more packages. After rebooting and trying to boot off the external, right after it decompresses the kernel, it says something like dev/console not found, and it says it can't continue on with the boot, so it just stops. I would appreciate if anyone could reply with solutions to my problems. 
Thanks, 
Josh.

---

### Post by encompass on 2006-05-05
Boot from external harddrive howto is what you want first off...
[http://ubuntuforums.org/showthread.php?t=80811&highlight=boot+external+usb](http://ubuntuforums.org/showthread.php?t=80811&highlight=boot+external+usb)
That will get you drive from the outside working...
But to your first question...  It may be that you have an undetected sata drive... is that what you have?

---

### Post by jjftails on 2006-05-06
Yes, I have a serial ATA hard drive. Can you tell me how I can get it to detect it? Oh and by the way thanks for your help, I will try out what it says on the external usb HD topic and tell you how it goes.

EDIT: I have tried the external hard drive method, but no luck, because there is no directory in my DEV called "mkinitramfs" that they want me to edit the modules file inside of it with vim..

---

### Post by encompass on 2006-05-12
Just to tell everyone... it has been fixed by using breezy instead of hoary.  He personaly chatted with me and we fixed the problem together.
:)

---

