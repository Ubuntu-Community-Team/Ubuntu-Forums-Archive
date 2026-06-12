---
title: "USB Mouse Stops Working"
date: 2009-12-08
forum: Hardware
---

### Post by er0k02 on 2009-12-08
Hello, 

My USB keyboard works fine throughout the session, but my USB mouse (laser) stops working completely. I have tried the > acpi=force irqpoll seems to work...
to add it to all of your kernel entry, open /boot/grub/menu.lst

scroll until you find defoptions=
and append

acpi=force irqpoll

save, quit and the run

sudo update-grub

as well as reinstalled the entire operating system twice, my question is, what could be causing my mouse to stop working? I've been using linux for ten years and have never had this problem. Could it be my BIOS? 

Thanks

---

### Post by er0k02 on 2009-12-08
BTW - the computer is a Dell Dimension E521 Desktop (AMD64 Athlon)

Ok, 

I reset the bios completely. It did not recognize the previous ubuntu installation, saying it failed to find the filesystem. 

So, I burned a copy of ubuntu9.10-amd64.iso and booted from cd to reinstall. The installation works until I get to the keyboard layout section, in which it returns the error: 

> 
ubi-console-setup failed with exit code 135. Further information may be found in /var/log/syslog. Do you want to try running this step again before continuing? If you do not, your installation may fail entirely or may be broken.

I click continue anyway. It goes to the partition setup page. Nothing is on the screen that I can select or click or highlight, and the setup freezes (as in, I can't go forward or do anything but go back). 

I have googled this problem and the error ubi-console-setup with exit code 135 in quotes does not return anything. 

I have not had much luck on this forum in the past, maybe I am not providing the adequate amount of information or people don't know the answer. Either way, someone please let me know how to better help myself with this issue and to help you help me. 

Thanks.

---

### Post by er0k02 on 2009-12-08
update: After erasing the BIOS settings, and the failed install, I have managed to install the operating system successfully. However, the mouse problem reoccurs (this is in different USB ports, with different mice and they all do the same). 

Thanks again if anyone can help.

---

