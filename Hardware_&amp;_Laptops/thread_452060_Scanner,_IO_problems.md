---
title: "Scanner, I/O problems"
date: 2007-05-22
forum: Hardware &amp; Laptops
---

### Post by lemoniceblock on 2007-05-22
Hi all,

I have a Brother MFC 4420C printer/scanner/fax, but I only use it for scanning.  It doesn't seem to be supported by Sane (the device wasn't recognised and Sane incompatibility was later confirmed [here,]("http://www3.sane-project.org/lists/sane-backends-external.html") so I downloaded the Brother driver for Linux [here,]("http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html") following the instructions [here]("http://solutions.brother.com/linux/sol/printer/linux/sane_install.html") (I am on Feisty so I followed the instructions for Kernel 2.6* versions).  The instructions seemed to be straightforward enough, except that I had to use root to run ```
$ echo 'none /proc/bus/usb usbfs auto,devmode=0666 0 0' >> /etc/fstab 
``` and the umount didn't work, although I did skip that and went onto the following steps alright...could this have contributed to the problem?  If so, is there a way to undo this whole process so I can try installing the drivers anew?

Now my scanner is recognised (or at least I think so!) since the error message has changed to
[COLOR="Blue"]
Failed to open device 'brother:bus5;dev2': Error during device I/O.[/COLOR]

Thanks!

---

### Post by magicfab on 2007-05-23
Have you contacted Brother about this ? It seems they support Debian explicitly, but there may be differences between any Debian packages/instructions and Feisty. Please let Brother know that you are using Ubuntu Feisty and voice your wish to have Ubuntu added in their instructions. 

I'd rather see them publish their drivers as free code and submit them to the [Linux Foundation]("http://www.linux-foundation.org/en/OpenPrinting") but at least letting them know you are using Ubuntu is a start.

---

### Post by lemoniceblock on 2007-05-24
Thanks for the reply; I will give them a call within these 2 days and will update asap.  Meanwhile I am suspecting that the driver's working fine but it's the I/O that's causing the trouble...not that I know what that means one bit xD  How are I/O errors handled in general?
Thanks again ^___^

---

### Post by lemoniceblock on 2007-05-25
Fixed it! :

After going to the links in Post #1 to follow the instructions provided by Brother and to d/l the Linux driver,

Following this thread [here]("http://ubuntuforums.org/showthread.php?t=104772"), I edited the fstab line:
> 
1.Change the line "none /proc/bus/usb usbfs auto,devmode=0666 0 0"
to "usbfs /proc/bus/usb usbfs auto,devmode=0666 0 0"
in the file "/etc/fstab".

2.Next, run the command "#mount /proc/bus/usb" and
see what will happen.
If you got some error message, please let us know it.
And if you didn't get any error message, please try scanning.

Then I found a [FAQ]("http://solutions.brother.com/linux/sol/printer/linux/linux_faq.html") on Brother's site (don't know why I didn't see it the first time I attempted to get the scanner working >.<"" ), followed the instructions written explicitly for Ubuntu 6.06&+ users, restarted the computer and it's working like magic now =)

I have to say that while I haven't been very impressed with Brother's products before, their attention to Linux users has really improved my liking of them ^___^

---

