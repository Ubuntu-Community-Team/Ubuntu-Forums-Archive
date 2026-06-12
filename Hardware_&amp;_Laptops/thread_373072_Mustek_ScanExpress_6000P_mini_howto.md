---
title: "Mustek ScanExpress 6000P mini howto"
date: 2007-02-28
forum: Hardware &amp; Laptops
---

### Post by art2003 on 2007-02-28
I got my old Mustek ScanExpress 6000P working under ubuntu 6.10 and would like to share my experience so that others can benefit from it
Incidentally this scanner doesn't work in Windows XP at all once you have SP2 installed

a) make sure your PC's bios has parallel port set to 'bidirectional'
Any other setting wouldn't work in my case

b) Make sure  you are running a recent sane version
go to the terminal and type 

scanimage -V

```
scanimage (sane-backends) 1.0.18; backend version 1.0.18
```

c) Lets edit some config files!


```
sudo gedit /etc/sane.d/dll.conf

and remove the # 
from
#mustek_pp
```

```
sudo gedit /etc/sane.d/mustek_pp.conf 
remove the #
from:

#  option no_epp

and add these 2 lines:

    scanner mustek-ccd300 * ccd300
    option top 56
```

```
sudo gedit /etc/modules

add this line:
ppdev
```

```
Finally click on System, Administration, Users & Groups, Manage groups,
Add group
enter group name:   lp
and tick the users you want to have access to the scanner
```

At this point reboot (not sure why this had to be done but in my case it would only work as root previous to rebooting) and it should be working fine now

troubleshooting:

If XSane image scanner reports no scanner found, open a terminal and try from there:
sudo xsane

If it works this way then the user you are logged on as is not part of the lp group

For further info and troubleshooting options I recommend this page:
[http://penguin-breeder.org/sane/mustek_pp/](http://penguin-breeder.org/sane/mustek_pp/)

---

