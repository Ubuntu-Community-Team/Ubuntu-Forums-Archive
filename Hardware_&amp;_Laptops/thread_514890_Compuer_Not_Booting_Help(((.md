---
title: "Compuer Not Booting Help:((("
date: 2007-08-01
forum: Hardware &amp; Laptops
---

### Post by ExXxTaZi on 2007-08-01
I NEED FAST HELP PLEASE HELP ME IM SORRY ON ALL MY QUESTIONS BUT THETS A CRITICAL PROBLEM:
I INSTALLED WITH envy MY ATI DRIVER,BUT MY DESKTOP EFFECTS STILL WONT WORKING.SO I UNINSTALLED THE ATI DRIVER&#1474;(RADEON X300 
AND NOW MY COMPUER IS NOT WORKING!!!!!IM CHOOSING LINUX KERNEL AND HE IS BOOTING.THEN WHEN THE LOGON NEED TO START ITS WRITING SOME THINGS AND GIVING BLUE SCREEN WITH WITH MESEEGE;
FAILD TO START THE X SERVER YOUR COMPUTER INTERFACE
IT IS LIKELY THET HE IS NOT SET UP CORRECTLY
WOULD YOU LIKE TO VIEW THE X SERVER OUTPUT TO CORRECT THE PROBLEM?
HELPPPPPPPPPP UNTILL NOW I HAD LITTLE PROBLEMS BUT THET...I AM NEW IN LINUX SO I DONT KNOW WHET TO DO
IM SORRY ON MY TYPING BUT ITS REALLY REALLY SCARY:(:(

---

### Post by hessiess on 2007-08-01
you just need to reconfigure the x config file, unfortunatly i cannot rember the command to do this:(, il try to find it.;)

x config is trying to load a driver witch no longer exists, fails, then you should get a command line.

if you can ditch the ati and get nvidia, you will alwase get bad proformance with ati cards.

---

### Post by dannyboy79 on 2007-08-01
> **ExXxTaZi said:**
> I NEED FAST HELP PLEASE HELP ME IM SORRY ON ALL MY QUESTIONS BUT THETS A CRITICAL PROBLEM:
I INSTALLED WITH envy MY ATI DRIVER,BUT MY DESKTOP EFFECTS STILL WONT WORKING.SO I UNINSTALLED THE ATI DRIVER&#1474;(RADEON X300 
AND NOW MY COMPUER IS NOT WORKING!!!!!IM CHOOSING LINUX KERNEL AND HE IS BOOTING.THEN WHEN THE LOGON NEED TO START ITS WRITING SOME THINGS AND GIVING BLUE SCREEN WITH WITH MESEEGE;
FAILD TO START THE X SERVER YOUR COMPUTER INTERFACE
IT IS LIKELY THET HE IS NOT SET UP CORRECTLY
WOULD YOU LIKE TO VIEW THE X SERVER OUTPUT TO CORRECT THE PROBLEM?
HELPPPPPPPPPP UNTILL NOW I HAD LITTLE PROBLEMS BUT THET...I AM NEW IN LINUX SO I DONT KNOW WHET TO DO
IM SORRY ON MY TYPING BUT ITS REALLY REALLY SCARY:(:(


first of all, never ever use captial letters when typing anything especially when requesting help except for maybe when you need to respond to your ex-wife when she requests more alamony payments.

second, the command that you need to issue after you login to your system thru the command line is

```
sudo dpkg-reconfigure xserver-xorg
```

then choose vesa for the driver and then just accept all the defaults. then after that, issue these commands

```
sudo /etc/init.d/gdm stop
```
```
sudo /etc/init.d/gdm start
```
then if that doesn't bring up your GUI login screen, hold ctrl-alt and hit the F7 or F8 keys. if that still doesn't bring you to a login window then do this
```
sudo shutdown -rH now
```
that'll restart your machine after it halts itself and you should then be up and running again.

---

### Post by dannyboy79 on 2007-08-01
> **hessiess said:**
> if you can ditch the ati and get nvidia, you will alwase get bad proformance with ati cards.

just not true. It's merely more difficult to setup but performance is comparable with the correct ATI card and correct driver.

---

