---
title: "Network Scanner"
date: 2006-09-11
forum: Hardware &amp; Laptops
---

### Post by 192.168.1.10 on 2006-09-11
Hi,

  I've got a small home network with a few Mac's which have sane and and Ubuntu laptop all connected to an old PC with Ubuntu server.
I'm trying to share my scanner using saned on the server. The Scanner is an Epson Stylus Photo RX520 Multifunction Printer/Scanner which is connected to the server via USB. The software used is sane with the epkowa backend and works fine through scanimage run on the server as a normal user. I've setup saned, checked that saned is working through telneting the port, even remotely through one of the Mac's but I can't scan from either the Mac's or the Ubuntu laptop.

The command I think I've got to use to connect is scanimage -d net:192.168.1.10:epkowa:libusb:001:003 is this the right command?

Any ideas?

Thanks for any help.:)

---

### Post by computx on 2006-09-13
Yeah I just did this and wrote up a little how-to since I didn't find it to be very straitforward.
Check it out at [http://computx.us/blog/index.php?/archives/8-Using-a-photo-scanner-on-the-network-in-Ubuntu.html](http://computx.us/blog/index.php?/archives/8-Using-a-photo-scanner-on-the-network-in-Ubuntu.html)

---

### Post by 192.168.1.10 on 2006-09-13
Thanks for your response.
I've done most of that but, I don't have a /etc/udev/libsane-extras.rules file, I assume it comes with the libsane-extras package which I can't install as it would break my iscan package and the epkowa backend provided with libsane-extras won't work with my scanner. I can't seem to change the permissions trhough the hotplug script. I also can't find saned through ps -C but I know the port os open, should I be able to see saned trough ps -C?. I allso tryed changing the permissions on /proc/bus/usb/001 and 003 which is the correct file and made the group saned. I then restarted xinetd and still I couldn't list saned.
I've tryed to connect on both the Mac with sane and the Ubuntu laptop with iscan including the epkowa backend and still no luck.

Any ideas, thanks.

---

### Post by computx on 2006-09-13
I wasn't quite sure which package created the file it may be libsane-extras or it may be sane-utils. I was able to just *chgrp saned /dev/sg0* and *chmod g+rw /dev/sg0* to use the scanner but those changes get lost at reboot. You can run the saned demon in debug mode and that may be helpful. First stop xinet.d with */etc/init.d/xinetd stop* then run
*saned -d* to run saned in debug mode.
My ps never lists the saned process even though It is listening and I can scan.
The saned man page suggests telneting into the saned port to test if it is listening. *man saned *for more info.
By the way /proc/bus/usb/001 or 003 are not the right files to be modding the priveleges on. You need to be changing the privileges/ownership of the correct/dev entry. For my scanner it was /dev/sg0 for yours it may be different. do an *ls /dev/sg** 
one of the /dev entries listed should be the scanner and that is the file you need to give proper priveleges too.

---

### Post by 192.168.1.10 on 2006-09-13
Thanks, I've done saned -d and got this.

[saned] main: starting debug mode (level 2)
[saned] main: [1] bind failed: Address already in use

I'm using libusb for the devices, I tryed changing permisions of /dev/sg0 which is the only sg device I've got listed and still no luck. My scaner has always worked as a user on the server, I just can't connect but at least now I know I've got a problem with saned, the question now is how to get it working.

Cheers.

---

### Post by computx on 2006-09-14
I know nothing about iscan So maybe the libsane extras will break it but it seems to me that since sane is what is on the macs you will need to implement the complete saned install. What makes you think libsane-extras will break iscan? Seems to me that extra backends should not wipe out the backends already installed.

---

### Post by 192.168.1.10 on 2006-09-14
libsane-extras contains the epkowa backend but this doesn't work with my scanner, epkowa is also provided by the iscan package and if I try to install one with the other I get errors installing packages.
The iscan package is a backend and a graphical frontend but the backend provided works fine with scanimage on the server. The documentation provided with the iscan package has instructions simmilar to your howto showing what needs to be done to share the scanner through saned, but I can't seem to get anywhere.
To make things easyer I'll try connecting wih the Ubuntu laptop before worying about the macs.
It seems I've got to figure out how to get saned to start without errors in debug mode, If I could get that to work I think I'd be sorted.

---

### Post by 192.168.1.10 on 2006-09-16
I'm sorted now.

I've got all my clients working, the Mac's and the Ubuntu laptop. I had to add the scanner group to the user saned, that seemed to do the trick. I'm not using xinetd as it all seems to work fine with inetd and the Ubuntu laptop can either Xsane or iscan to the server and the Mac's can scan through The GIMP, OpenOffice.org and the one with Mac OS Tiger can even use the Image Capture programme which is installed with OS X.

Thankyou Computx.:D

---

### Post by computx on 2006-09-17
Your Welcome, Glad you got it all going.

---

### Post by Fenix-TX on 2006-11-23
Can you explain your steps to get working scanner on network?

---

### Post by cyb3rj on 2007-07-21
> **Fenix-TX said:**
> Can you explain your steps to get working scanner on network?

Many months later, but... 
[https://help.ubuntu.com/community/HpAllInOne](https://help.ubuntu.com/community/HpAllInOne)


I just went through this and got my HP 7210 working.  This is one of the many reasons why I am becoming an unashamed rabid fanatic about Ubuntu.  Some things do require some fiddling to get them to work from time to time, but the huge amount of support, and links like the one above just make the use and configuration experience so much better.

---

