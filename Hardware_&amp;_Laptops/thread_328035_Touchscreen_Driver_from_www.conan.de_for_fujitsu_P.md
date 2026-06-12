---
title: "Touchscreen Driver from www.conan.de for fujitsu P1510"
date: 2006-12-30
forum: Hardware &amp; Laptops
---

### Post by JoeNewb on 2006-12-30
I'm having trouble with installing the driver from [www.conan.de](www.conan.de). 

It says "Copy the file "fujitsu_drv.o" to the appropriate location ("/usr/X11R6/lib/modules/input"). Insert the lines below to the file "/etc/X11/XF86Config-4" or "/etc/X11/xorg.conf". "

The location ("/usr/X11R6/lib/modules/input") does not exist, I have /usr/X11R6/lib but I can't create folders there as the option is greyed out. Should the file be copied somwhere else?

I think i will be ok following the other instructions.

Thanks in advance for any help.

---

### Post by orengolan on 2007-06-26
I have the same issue. I can't find this folder!

I also found this solution:
[http://samengstrom.com/nxl/6968/linux_p1510_page.en.html](http://samengstrom.com/nxl/6968/linux_p1510_page.en.html)
But I don't understand his instructions:

"There's now also a real X driver available here, but so far the button click actions have not been very intuitive.
If you don't have the X11::GUITest module, you can install it from the CPAN shell:
# perl -e shell -MCPAN
cpan> install X11::GUITest"
What is X11::GUITest module and how do i verify that I have it?
What is Cspan shell?

"At every boot you should run the following commands (as root):
# setserial /dev/ttyS0 irq 4 port 0x220 autoconfig
# chmod a+rwx /dev/ttyS0"
how do i run those commands at every boot?

"After that run one of these scripts in X:"
What is X and how do i run scripts inside it


anyone can help us with our touchscreen?

---

