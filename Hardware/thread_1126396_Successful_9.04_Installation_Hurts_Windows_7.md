---
title: "Successful 9.04 Installation Hurts Windows 7"
date: 2009-04-15
forum: Hardware
---

### Post by CrunchyDoodle on 2009-04-15
I run Windows 7 and ubuntu on my MSI Wind U100 netbook. I have Windows 7 (build 7077) installed on the internal SSD, and ubuntu is installed on an external USB HDD. With ubuntu 8.10, I had to manually install GRUB onto the external HDD and perform a repair on Windows to keep them totally separate. That way this netbook is a Windows 7 machine or an ubuntu machine, depending on whether the USB HDD is plugged in or not.

Mostly because I was not able to get a kernel past version 10 to run right on this machine, I decided to try the beta of 9.04. I used the special netbook image with a 1GB thumb drive. The creation of the image on the thumb drive went well. After booting into 9.04 and seeing that all my hardware was properly supported and worked, I started the 9.04 installation. When the option came up of where to install it, I chose the external USB HDD and said to over-write the 8.10 installation. I checked the Advanced setting and it appeared that GRUB would be put on the external HDD and the Windows C: drive would be untouched. I let it proceed. The installation went well and ubuntu 9.04 appeared to worked properly.

I then shut down and unplugged the external HDD. When I powered it up, it appeared to be starting Windows 7 as it should. However, Windows did not properly start, and crashed instead. This caused a boot - Windows start - crash cycle, and I shut it down. I then plugged in my external USB DVD drive and reinstalled Windows. Now Windows works properly.

I don't know what happened for sure. It could have been some weird coincidence, or the ubuntu installer did something to Windows 7.

Bye.    :cool:

---

