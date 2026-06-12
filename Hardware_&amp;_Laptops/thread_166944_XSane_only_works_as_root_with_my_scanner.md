---
title: "XSane only works as root with my scanner"
date: 2006-04-27
forum: Hardware &amp; Laptops
---

### Post by tigr10 on 2006-04-27
I am using XSane with an HP 3970 scanner.  I followed the instructions to get it working at:
[http://ubuntuforums.org/showthread.php?t=152762&highlight=hp+3970](http://ubuntuforums.org/showthread.php?t=152762&highlight=hp+3970)

but I can only scan as the root user.

I contacted the author of the hp3900-series XSane plugin and he told me it is a permissions problem.  However, I'm new to Ubuntu so I don't know what to look for and what changes to make to get regular non-root users to access the scanner.

The error which currently appears is:
Failed to open device 'hp3900:libusb:005:003':
Access to resource has been denied

Please help and let me know what I need to do.

---

### Post by garretwp on 2006-06-03
I get the same issue! Have you figured out a way to get around this?

Garrett

---

### Post by garretwp on 2006-06-03
I have a fix for your problem. I had to go into /dev/bus/usb/005 and do a chmod a+w on 002 and all worked out well! Now for you, it looks like you will have to do chmod a+w 003 and you should be good to go! 

I hope this helps.

Garrett

---

### Post by cvmostert on 2006-10-05
hi there, i have the same problem, i did chmod a+w on my 002 in bus 001 and still i can not start xsane as normal user... just root.. i even tried chown!

looks like i must restart or reconnect the scanner?

thanks for trying to help.
Ciao.

---

### Post by DingDong on 2006-10-24
First of all you should find out which bus your usb scanner resides on, this is easily done with the lsusb command.

[HTML]
user@somelinuxbox:~$ lsusb
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 05d8:4002 Ultima Electronics Corp. Artec Ultima 2000 (GT6801 based)/Lifetec LT9385 Scanner
Bus 002 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 005 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
[/HTML]

as you can see the scanner resides on Bus 002 as the second (002) device in my case. The syntax for changing permissions of the scanner device is 

[HTML]
user@somelinuxbox:~$ sudo chmod a+w /dev/bus/usb/$BUS/$DEVICE
[/HTML]

remember to change the $BUS and $DEVICE variables according to the lsusb output as described above. to change permissions to my scanner device i would enter:

[HTML]
user@somelinuxbox:~$ sudo chmod a+w /dev/bus/usb/002/002
[/HTML]

---

### Post by shakma on 2006-12-11
DingDong, you rock!  :D Your post totally got me and my scanner up and running.  Ubuntuforums does it again!

P.S.  Anyone got a solution to the "three errors on exit" bug?

---

### Post by kidwithjedipowers on 2006-12-12
Thank you very much, you've solved my problem as well. We're all noobs at one point or another..

---

### Post by shakma on 2007-01-31
I had this same problem again after upgrading to Edgy.  Fortunately, I found your post (and my thanks) again.  And, of course, it worked again!

Peace.

---

### Post by gjohn2 on 2007-02-12
Thanks so much!!

---

### Post by Ekstreme on 2007-02-14
I have a parallel port scanner, which again, only works as root. How would I correct this? I'm assuming it's permissions on a similar thing, bust just not USB related :)

---

### Post by frnz on 2007-02-27
thank so much Ding Dong. your post was clear and professional. Solved the problem and helped me to know something more about linux tweaking.

ciao

---

### Post by Chilli Bob on 2007-03-10
Thanks Ding Dong, I did the chmod and now xsane is working. However, whwn I shut down it gives an error message as each window shuts - "Failed to create file - Permission Denied" and a close button. It doesn't seem to effect scanning though. Is this a problem , and if so does anyone know what I should do about it?
Thanks in advance.

---

### Post by bratliff on 2007-04-02
I I get another error message when trying to use Krusader in the root mode. "can't start root mode for krusader or kdesu is missing from the path. Please configure the dependencies in Krusader." What do I do?


I have done this command and got rid of the first error msg.  sudo chmod a+w /dev/bus/usb/002/002

ratliff

> **shakma said:**
> I had this same problem again after upgrading to Edgy.  Fortunately, I found your post (and my thanks) again.  And, of course, it worked again!

Peace.

---

### Post by sharke on 2007-04-05
Thanks Ding Dong, I did the chmod and now xsane is working. However, whwn I shut down it gives an error message as each window shuts - "Failed to create file - Permission Denied" and a close button. It doesn't seem to effect scanning though. Is this a problem , and if so does anyone know what I should do about it?
Thanks in advance.
This error is due to xsane being run as root on first run. It creates .sane folder in your home folder with root permission and when you run as user acess is denied delete .sane and rerun xsane and you are sweet.
Regards
Sharke

---

### Post by cotcot on 2007-04-28
> **DingDong said:**
> First of all you should find out which bus your usb scanner resides on, this is easily done with the lsusb command.



[HTML]
user@somelinuxbox:~$ sudo chmod a+w /dev/bus/usb/002/002
[/HTML]

Thanks, this worked for me also, except for an error when closing the program (3 x same error before closing) : 
> Failed to create file. Permission denied. 

---

### Post by sharke on 2007-04-28
Thanks, this worked for me also, except for an error when closing the program (3 x same error before closing) :
This is caused by running the first instance as root .In your home folder you will have a .sane folder delete this reboot run xsane and problem should be gone
Regards
Sharke

---

### Post by cotcot on 2007-04-29
The solution of Dingdong works as long as I do not reboot. After reboot the scanner is connected through another bus. So the command is to be given each time after stopping the PC or printer again.
Is there another way to hotplug usb devices with access rights to users ?

---

### Post by sharke on 2007-04-29
> **cotcot said:**
> The solution of Dingdong works as long as I do not reboot. After reboot the scanner is connected through another bus. So the command is to be given each time after stopping the PC or printer again.
Is there another way to hotplug usb devices with access rights to users ?

Open /etc/udev/rules.d/40-permission.rules as root and change usb device subsystem to mode=0666.
regards
Sharke

---

### Post by cotcot on 2007-04-29
Thanks Sharke. It is OK now.
There is a little typo in your file reference. ("s" missing in permission"s").

---

### Post by ruialexbarbosa on 2007-05-07
Thanks Sooooo Much Ding Dong!!!

---

### Post by Coolit on 2007-07-14
I had the same problem with permissions but this thread sorted it, thanks!

---

### Post by Ram Crammer on 2007-09-03
[HTML]
user@somelinuxbox:~$ sudo chmod a+w /dev/bus/usb/002/002
[/HTML][/QUOTE]

Every time I boot my computer I have to run thru this whole procedure all over again.  It seems the scanner ends up on a different USB device each session, and the permissions only last for the current session.  What a pain!!!  Isn't there some way to make this permanent so I don't have to struggle with this every time I boot?  Otherwise this fix seems like nothing more than a work-around for a system shortcoming or device driver bug, or whatever it turns out to be.  This is plug and play?  Hah!  Anyway, at least I can get by with it now.  Thanks for the help, Ding Dong

---

### Post by dmontalvao on 2007-10-13
Garretwp, i did as you told and now I hv xSane working without need to be root! Do u have any ideas on how I can do the same in Rhytmbox? I have to run it as root (gksudo rhytmbox), otherwise it will crash/freeze.

Cheers!

---

