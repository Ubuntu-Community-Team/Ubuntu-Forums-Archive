---
title: "Fan Problems! (9.04, toshiba)"
date: 2009-04-20
forum: Hardware
---

### Post by vidus on 2009-04-20
Hello! Just tossed windows on my new lappy and install 9.04. 

My fan is not being controlled properly. It will turn on full blast at 80c, which is quite warm, and then never turn off for as long as I leave the laptop on. Is this a problem with 8.10 as well? Should I downgrade?

I've read a couple other threads and this seems to be a widespread problem. Some have had success by adding acpi_osi="Linux" to the grub boot kernal options or something. (menu.lst). I have tried to add it as well but it has had no effect, perhaps I am not adding it in the right spot, but there has not been any detailed instructions on how to do this.

If anyone else has this problem please please help me, the noise is crazy!

---

### Post by dlm4849 on 2009-04-20
Im having the same problem in a Lenovo R61. Luckily my fan is quiet so I dont hear it, but it has pretty much stayed on since installing 9.04.

---

### Post by porksome on 2009-04-20
I have a toshiba l350-171. The acpi_osi="Linux" seems to make a difference for me. To change it:
open /boot/grub/menu.lst with a text editor as root eg sudo nano /boot/grub/menu.lst
You will be prompted for you password.

Scroll down the file until you see the following:

"
## ## End Default Options ##

title           Ubuntu 9.04, kernel 2.6.28-11-generic
uuid            55b3c634-36c5-4a06-b8ec-8d51a8cb97d4
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=55b3c634-36c5-4a06-b8ec-8d51a8cb97d4 ro quiet splash acpi_osi="Linux"
initrd          /boot/initrd.img-2.6.28-11-generic
"

add the acpi_osi="Linux" to the end of the line starting "kernel" as shown above. Save your changes and reboot.

Hope this works for you
:D

---

### Post by vidus on 2009-04-20
[SOLVED]

Well, mostly... :)

I did two things, I added the acpi_osi="Linux" to the grub thing.. I also noticed a few people mentioning it may be related to disabling the sleep function, which I had done.

After rebooting there was no change, until I did a suspend, and logged back in and the fan is then controlled normally and keeps the temp normal.

So if nothing if working for anyone, suspend your system then log back in and see what happens. I have to do this every time I boot up my laptop now which kind of sucks. I hope Ubuntu devs notice this prob! In any case im happy I dont have to deal with vita anymore.

---

### Post by InternetDominus on 2010-03-09
Any ideas for ubuntu 9.10, my menu.lst is empty, and as I far as I know it is empty for all of us on version 9.10.  

Any ideas on how to start fan on version 9.10?

Thanks!

---

