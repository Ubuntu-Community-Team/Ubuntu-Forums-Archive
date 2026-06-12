---
title: "Help please- unable to install/uninstall/launch apps"
date: 2008-12-14
forum: Installation &amp; Upgrades
---

### Post by michaelk60 on 2008-12-14
Hi,

I am pretty lost here, recently migrated to uBuntu 8.04 from years with MS.
After a smooth start (of about a month) I got to a point where I can no longer install / uninstall/ or launch most of the apps from the application menu like VirtualBox, Skype and lots others.

I did have problems with the synaptic but thought i got that fixed.

well to the point....
No matter what I do I keep getting :
---------------------------------
Setting up unetbootin (partitionmanagerrev146) ...
expr: syntax error
cat: /boot/ubnkern: No such file or directory
Installation failed, kernel was not downloaded or extracted properly, make sure your internet connection is working and that there is free space in /boot and try again
dpkg: error processing unetbootin (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 unetbootin
--------------------------------------------

I have tried all :
 dpkg --configure -a
 apt-get upgrade
apt-get install -f
 dpkg --configure -a
etc....
I keep getting the same result.


Help please ](*,)

Thanks.

Michael

---

### Post by michaelk60 on 2008-12-14
Quick update ok I got that cleared by reinstalling unetbootin from sorceforge and I do not get this error message any longer,  however I am still in a situation where applications like Skype, VirtualBox will do nothing after clicking the their menu icon (obviously I have done complete uninstall and install)...nor can I launch them from the terminal

Michael

---

### Post by michaelk60 on 2008-12-14
Just thought I'd mention it....skype, VirtualBox etc all worked fine until I installed aladdin's eToken minimal client to recognize their usb eToken. Not sure this has anything to do with my current situation, just thought id mention it.

Michael

---

