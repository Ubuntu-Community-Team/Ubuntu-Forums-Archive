---
title: "need help soon or reinstalling window$"
date: 2005-06-23
forum: Hardware &amp; Laptops
---

### Post by mondo on 2005-06-23
I've been trying to get ubuntu up and runnig for two weeks now.  I've checked out the forums and other documentation,and I've posted my probem before (no response) and am ready to give up.  I don't have any wierd hardware, and if Linux is this hard for a newb to get going it is, disapointingly, not mature enough to take on microsoft.

Anyway here (again) is my problem:,

When I try to install ubuntu on my amd64 3400 and all the file copying goes fine, but when it reboots and, I'm assuming, tries to start x,. all I get is a lovely pattern of colorful vertical lines. I tried rebooting into recovery mode and typing "sudo dpkg-reconfigure xserver-xfree86" like it said on another thread and "sudo dpkg-reconfigure xserver-xorg" but both came back with an error message to the effect of xserver not installed. I'm using a radeon 9200se, and don't realy need 3D, so the vesa driver should do it, but I can't figure out what to try next. Any help would be apretiated!
me

---

### Post by bunced on 2005-06-23
If you can wait until Sunday, I can help you then. Please be patient until then, as I am up to my ears in Web design work.

Until we meet again
David

---

### Post by mondo on 2005-06-23
thank you very much for your quick reply!

---

### Post by bunced on 2005-06-23
If I get distracted, feel free to PM me and send a curt reminder :D!

---

### Post by bunced on 2005-06-26
OK, as promised, I will help you!

I think that the problem is the fact you are using the Vesa driver and it is not detecting your graphics card correctly. I suggest you install the ati driver. 

1) Issue 'sudo apt-get install xorg-driver-fglrx' at command line 

2) When it has finished installing, do 'sudo depmod -a ; sudo modprobe fglrx'

3) Hopefully the above command won't produce errors :D. If it doesn't, you can re-run 'sudo dpkg-reconfigure xserver-xorg' and select the driver as being "fglrx" instead of "ati".

I hope this solves you problem. If not, feel free to ask for more help.

Regards
David

---

