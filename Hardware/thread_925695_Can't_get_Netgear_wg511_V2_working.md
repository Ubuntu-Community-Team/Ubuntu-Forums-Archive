---
title: "Can't get Netgear wg511 V2 working"
date: 2008-09-20
forum: Hardware
---

### Post by tito475 on 2008-09-20
Hi, 
I am new at ubuntu. I just installed it on my laptop and I can't get the external wireless card to work. 
I checked out various forums, where people told me to use the NDISwrapper. While I was following the instructions, it said to type in the folowing code to find the driver chipset. ```
sudo lspci -n
``` 
I got 11ab:1faa as the result. 
Then it told me to go and find the driver files for that card, unfortunately, Netgear wg511 V2 driver file is available only in .exe format, so I could not find the .inf file for the driver. 

Does anyone know what I could do to get the wireless card working in my laptop? 

Thank you

---

### Post by steve.t on 2008-09-27
I don't know which version of Ubuntu you're running.  I used this post for instructions to get WG511v2 working on Gutsy Gibbon (Ubuntu 7.10):

[http://ubuntuforums.org/showthread.php?t=756260&highlight=activate+wg311v3](http://ubuntuforums.org/showthread.php?t=756260&highlight=activate+wg311v3)

Attached is a tarball of all the files contained in the WG511v2 folder on the Win XP partition.  

Good Luck,
Steve

---

