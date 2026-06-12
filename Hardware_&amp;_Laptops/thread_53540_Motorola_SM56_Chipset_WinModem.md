---
title: "Motorola SM56 Chipset WinModem"
date: 2005-08-01
forum: Hardware &amp; Laptops
---

### Post by elgalad525 on 2005-08-01
Hi All,

I know that lots of posts are already here on this topic, but being really new to linux (two days) none of them make sense to me.

I have an internal pci modem based on the Motorola SM56 chipset, which was not detected automatically by ubuntu (5.04) when I installed.  I located the linux drivers on the motorola website, available both for SuSE and Mandrake, and tried installing these, but I'm unsure as to exactly how to complete setup.  It doesn't seem as though the drivers have installed properly, as none of the available modem ports in connection setup work.

Being in non-debian formats,I used the cmd line:

       alien -i [filename]

to install the drivers

Could someone please give me a simple, step-by-step set of instructions as to how to get around this problem, I'm about ready to throw in the towel and return to XP where my modem is automatically detected with no trouble.

Thanks in advance.

---

### Post by eivind on 2005-08-09
Modem setup can be a pain, yes indeed. I have been there, and it's no fun.

Just one small thought about your alien usage: Are you sure that alien -i filename does the trick? Why not try first

alien filename

and then

dpkg -i filename?


I know, the command you've tried may work just as well, but do try. 

Trick two: It would be wise to read up on which device is created when you install the Motorola driver. Sometimes, such drivers create their own devices, such as /dev/something. Try

man filename,

where filename is the name of the driver you installed, or you may try to read the documentation in /usr/share/doc/filename/ to see what the modem device is called. Then, you might be able to type that device name in the ppp setup, and that *might* do the trick.

Tell us of any failure or success.

Cheers,


Eivind

---

### Post by az on 2005-08-09
Motorola does not beleive that linux is profitable so they do not have drivers for current linux distributions.  You are out of luck.  Those drivers are for the 2.2 or 2.4 kernel.

---

