---
title: "A Beginner Needs Help"
date: 2005-05-14
forum: Hardware &amp; Laptops
---

### Post by Mutant Human on 2005-05-14
Hi 

I have installed ubuntu linux but I have 2 problems:

1.My modem,i.e, Conexant HSF 56k internal modem is not detected.It is shown in the  device manager but it says that device type is unknown.

2.How can i access my hard drives.Normally,they are present in the mnt folder but instead they are present in /dev/evms folder.When i click on them an error is shown'the location is not a folder'.

Please help me so that i can use internet plus i m able to access my hard drives.

Thanks

---

### Post by jobezone on 2005-05-14
[QUOTE=Mutant Human]Hi 
1.My modem,i.e, Conexant HSF 56k internal modem is not detected.It is shown in the  device manager but it says that device type is unknown.
[/QUOTE]
Where does it say that the device type is unknown?

Check some of these guides:
[list]
[*][http://www.ubuntulinux.org/wiki/DialupModemHowto](http://www.ubuntulinux.org/wiki/DialupModemHowto)
[*][http://www.ubuntulinux.org/wiki/WinModemLucent](http://www.ubuntulinux.org/wiki/WinModemLucent)
[*][http://www.ubuntulinux.org/wiki/FrontPage/searchwiki?expr=howto&submit=Search](http://www.ubuntulinux.org/wiki/FrontPage/searchwiki?expr=howto&submit=Search)
[*][http://www.ubuntuforums.org/showthread.php?t=31094](http://www.ubuntuforums.org/showthread.php?t=31094)
[*][http://www.ubuntuforums.org/search.php?searchid=736420](http://www.ubuntuforums.org/search.php?searchid=736420)
[/list] 

Also, the general places to get documentation and help on ubuntu are:
[list]
[*][http://www.ubuntulinux.org/wiki/](http://www.ubuntulinux.org/wiki/)
[*][http://www.ubuntuguide.org](http://www.ubuntuguide.org)
[*][http://www.ubuntuforums.org](http://www.ubuntuforums.org) (using the search button)
[/list]

---

### Post by ludi on 2005-05-14
[QUOTE=Mutant Human]Hi 

I have installed ubuntu linux but I have 2 problems:

1.My modem,i.e, Conexant HSF 56k internal modem is not detected.It is shown in the  device manager but it says that device type is unknown.
[/QUOTE]

This is from another thread:
ttp://www.linuxant.com/drivers/
[http://www.linuxvoodoo.com/howto/HO...-HOWTO/hsf.html](http://www.linuxvoodoo.com/howto/HO...-HOWTO/hsf.html)
[http://www.linuxant.com/drivers/hsf...s-installer.php](http://www.linuxant.com/drivers/hsf...s-installer.php)
The linuxant site should solve your problem.

> 
2.How can i access my hard drives.Normally,they are present in the mnt folder but instead they are present in /dev/evms folder.When i click on them an error is shown'the location is not a folder'.


How many hds do you have? Didn't you setup them in installation (formated and selected a mount folder)?
If they are unmount,  mount each one (test purpose) on a specific folder (like /home/xxx/hd2).

---

### Post by az on 2005-05-14
The conexant modem is not supported in linux unless you buy a driver for it.  The linux driver costs 15USD which is probably more than what a new intel chipset or lucent chipset modem would set you back.  Those have linux support.

The linuxant driver gets you updates for a year, after which you have to pay again.

---

