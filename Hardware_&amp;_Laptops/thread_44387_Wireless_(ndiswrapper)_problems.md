---
title: "Wireless (ndiswrapper) problems"
date: 2005-06-25
forum: Hardware &amp; Laptops
---

### Post by colphorbin on 2005-06-25
I am using a Compaq Presario 2195us. I have just started using Ubuntu about 2 weeks ago. I am using a Broadcom wireless modem, and (of course) having problems installing it.

This might sound a little ridiculous (because it is). I cannot delete an invalid driver from NDISWRAPPERS database. I have entered every variation of  ndiswrapper -e /home/zach/Desktop/My Stuff/System files/b57win32.inf that i can possibly think of.

Its getting to the point down right aggravation. I am two seconds from formating my hard drive. and this is coming from a newly addicted linux user.

I am thankful for any help.
-colphorbin

---

### Post by ssck on 2005-06-25
[QUOTE=colphorbin]I am using a Compaq Presario 2195us. I have just started using Ubuntu about 2 weeks ago. I am using a Broadcom wireless modem, and (of course) having problems installing it.

This might sound a little ridiculous (because it is). I cannot delete an invalid driver from NDISWRAPPERS database. I have entered every variation of  ndiswrapper -e /home/zach/Desktop/My Stuff/System files/b57win32.inf that i can possibly think of.

Its getting to the point down right aggravation. I am two seconds from formating my hard drive. and this is coming from a newly addicted linux user.

I am thankful for any help.
-colphorbin[/QUOTE]

maybe you could paste the error message here so that we can help .... more details would help

---

### Post by byen on 2005-06-27
Hey colphorbin, I have a presario with the same chip that you have. Please go to this link to see the detailed walkthrough. It works! good luck!

 link: [http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)

---

### Post by az on 2005-06-27
ndiswrapper -e (driver _name_ *** Not file name ***)

do ndiswrapper -l and it will tell you the name of the drivers it has installed.  Use that name to delete it.

Example NETPRISM.inf = netprism driver

I would do

sudo dniswrapper -e netprism

and *not*
sudo ndiswrapper -e /home/sally/WinXP/Driver/NETPRISM.inf.......

Hope this is what you are looking for!

---

