---
title: "fglrx-control"
date: 2004-10-26
forum: Hardware &amp; Laptops
---

### Post by Vulc on 2004-10-26
what is the command to run fglrx-control?

just fglrx-control doesn't work

---

### Post by Vulc on 2004-10-26
need to change my resolution but it can't find the default program when I use fglrx instead of "ati"

---

### Post by wallijonn on 2004-10-31
fglrxconfig

---

### Post by artnay on 2004-12-23
GUI for control panel can be found from directory called /usr/X11R6/bin. Just execute fireglcontrol. There's only DualScreen and Adjustment options available so you can't change resolution over there at the moment. Try changing the resolution using X's config file: /etc/X11/XF86Config-4.

EDIT: Yeah, you should install it first...

---

### Post by HiddenWolf on 2004-12-25
[QUOTE=artnay]EDIT: Yeah, you should install it first...[/QUOTE]

LOL

---

### Post by HughR on 2007-02-02
This reply is very late, but I got here via google and maybe others will too.  Here are some answers for Edgy.

1. you need to install the package fglrx-control

2. you can find out what files were in this package using the command "dpkg -L fglrx-control"

3. the one you want is /usr/bin/fireglcontrol

---

### Post by hotrod6657 on 2008-01-12
when i try and do this i get the following message:

Driver does not provide the FireGL X11 extensions! 
Panel components will operate only partially.

if i click okay it launches something, but it's just a screen that says what driver i have.  I think it's the right application, it just only has the information tab at the top, nothing else, and nothing to let me do.  Do i still need something?


I found this and a driver at the ATI website, but i'm not so good with navigating in the terminal so i'm having some trouble following their instructions...

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat712-inst.html]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat712-inst.html")

---

### Post by DouglasAWh on 2008-05-07
bump.  This would be useful to me too.  See [http://ubuntuforums.org/showthread.php?p=4903411](http://ubuntuforums.org/showthread.php?p=4903411)

---

### Post by tipp98 on 2008-07-07
Update, the executable has changed to amdcccle (AMD Catalyst Control Center Linux Edition)

/usr/bin/amdcccle

---

