---
title: "DESPERATION! Unable to install HPDeskjet930c"
date: 2006-12-30
forum: Hardware &amp; Laptops
---

### Post by parigigi on 2006-12-30
Hi to all!

I'm a Kubuntu 6.10 user and I tried to install my HP Deskjet 930c printer with the graphical utility installed, but It doesn't work: the program hangs!!!

So I decided to install the printer manually first of all with the hplip specific program "hp-setup", but I receive this error:

```


stranger@alvaro:~$ sudo hp-setup

HP Linux Imaging and Printing System (ver. 1.6.9)
Printer/Fax Setup Utility ver. 2.2

Copyright (c) 2003-6 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: Unable to connect to hpiod.

```

So i tried the cups utility "lpadmin", but I receive this error:

```

stranger@alvaro:~$ sudo /usr/sbin/lpadmin -p DeskJet -E -v usb:/dev/lp1 -m stp-hp-dj_930c.5.0.ppd
lpadmin: Unable to copy PPD file!

```


I tried to uninstall/reinstall with several sequences cups and hplip, but nothing changed!

Please help me! It's 14 hours that I'm trying to make this printer working!

:( 

thanks

---

### Post by dasunst3r on 2006-12-30
For my HP PSC-xxxx devices, I plug it in, turn it on, and set it up through my desktop environment (GNOME).  Before starting, you should make sure your packages are updated:
```
sudo apt-get update
sudo apt-get upgrade
``` Since you are using Kubuntu, you should go to Control Center -> Peripherals -> Printer and add the printer that way.  I do not know the specific steps from here, but I am confident that others can fill you in.  Best of luck!

Note: Control Center is the place that you change all your preferences and stuff.

---

### Post by tajreed on 2006-12-30
check the CUPs website to see if this printer is supported in Linux. I had a 920 series that was extremely difficult to set up. Ubuntu may not support it.

---

### Post by parigigi on 2006-12-31
I've checked that my printer is fully supported (through the HPLIP project) before installing kubuntu. 

Before attempting to install the printer in command line I tried KDE Control Center, but the program freezes...


:(

---

### Post by 11hjpphty76lkjj on 2007-01-12
What happens if you run

sudo /etc/init.d/hplip restart

and then 

sudo hp-setup

A

---

### Post by parigigi on 2007-01-14
I get this error...

```

stranger@alvaro:~$ sudo /etc/init.d/hplip restart
 * Stopping HP Linux Printing and Imaging System                                [ ok ]
 * Starting HP Linux Printing and Imaging System                                [ ok ]
stranger@alvaro:~$ sudo hp-setup

HP Linux Imaging and Printing System (ver. 1.6.9)
Printer/Fax Setup Utility ver. 2.2

Copyright (c) 2003-6 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: Unable to connect to hpiod.

```


I have also a problem with cups: i tried to configure my printer without hplip and so I tried to open cups's web interface ([http://localhost:631](http://localhost:631)) but the browser says that it can not reach localhost. This is really strange!

---

### Post by 11hjpphty76lkjj on 2007-01-14
Run:

cat /etc/hosts

and post the output. as well run

sudo /etc/init.d/cupsys restart

and post the output.

A

---

### Post by parigigi on 2007-01-15
I get this output:

```

stranger@alvaro:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 alvaro

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
stranger@alvaro:~$ sudo /etc/init.d/cupsys restart
Password:
 * Restarting Common Unix Printing System: cupsd                                [ ok ]
stranger@alvaro:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 alvaro

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
stranger@alvaro:~$


```

---

### Post by 11hjpphty76lkjj on 2007-01-19
Are you still getting the unable to connect to hpiod when you run hp-setup?

If so run then run 

ps ax | grep hp

and post that.

---

### Post by parigigi on 2007-01-21
No, unfortunately I can not still connect to hpiod...

```

stranger@alvaro:~$ sudo /etc/init.d/cupsys restart
Password:
 * Restarting Common Unix Printing System: cupsd                                [ ok ]
stranger@alvaro:~$ ps ax | grep hp
 2758 ?        S<     0:00 [shpchpd]
 4603 pts/1    R+     0:00 grep hp
stranger@alvaro:~$

```

---

### Post by 11hjpphty76lkjj on 2007-01-24
What happens if you run 

sudo /etc/init.d/hplip restart

---

