---
title: "CAT S41 Android phone partly recognized by Kubuntu, but won't open"
date: 2019-02-08
forum: Hardware
---

### Post by raphaell2 on 2019-02-08
Hi, 

I'm running Kubuntu 18.04 (on a pc that doesn't really have a brand name because it was put together from individual parts by the small independent computer store where I bought it). My current cellphone is a CAT S41 running Android 8.0.0 (sold by Bullitt under license from Caterpillar). When I plug in the phone, at first I get a regular pop up message telling me that the phone has been plugged in, and giving the correct model name. The phone is one of those phones that, after you plug them in, requires you to set it to file transfer before you can transfer files - AFAICT you can't do that before you plug it it. So the next thing I do is set the phone to file transfer. Then, I click on the pop up on my KDE screen in order to open the phone. 

Then I get an error message telling me that the file or directory 

>   udi=/org/kde/solid/udev/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/



doesn't exist. And the phone doesn't show up, neither in Dolphin nor when I check /media/myusername/ on the command line. I often get similar messages for my thumb drives, but they usually show up under /media/myusername/ anyway. Running mtp-detect gets me a very long output in which the phone is recognized - correct manufacturer, model, serial number etc.

Any ideas?

---

### Post by raphaell2 on 2019-02-09
Update: I've now "solved", if that's the right word, the issue by switching to Ubuntu Mate, which, after I installed some mtp-related packages, handles my cellphone just fine. Since that's not really a solution for the underlying problem, though, I'm not going to mark the thread as solved.

---

