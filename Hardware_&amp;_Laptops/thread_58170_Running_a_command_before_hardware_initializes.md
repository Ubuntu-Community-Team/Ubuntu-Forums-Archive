---
title: "Running a command before hardware initializes"
date: 2005-08-19
forum: Hardware &amp; Laptops
---

### Post by fmpuk on 2005-08-19
I need to run this command: setpci -s 0:14.4 subordinate_bus=03
Before the hardware initializes as to get my wireless network to work on boot. I use to use Fedora and I placed this in the /etc/rc.sysinit file, and it worked great - what is an equivalent file on Ubuntu where I can achieve this? 
I did try using the /etc/default/pcmcia and putting the command at the top, it works but it initializes too late so it isn't all properly configured on boot.
Thanks a lot

---

### Post by heimo on 2005-08-19
You can make your own init script just for this (if you can't find other place). Those files are under /etc/init.d/ and I believe somewhere there's also "skeleton" or template file for a new one (or you can take any existing one, copy and modify). Then you need to add symbolic links (there's also command line tool to do this, but I can't get the name to my head right now), you can do something like 
 ```
ln -s /etc/init.d/mynewscriptfile /etc/rc2.d/S10mynewscriptfile
``` 
where 10 is the sequence number from 01-99 when in the boot process this script is executed, and S means to start it, K would mean to "kill" it. Make your script executable (chmor u+x [scriptname]). If any questions, please don't hesitate to ask - I'm sorry to be light on details here.

---

### Post by fmpuk on 2005-08-19
[QUOTE=heimo]You can make your own init script just for this (if you can't find other place). Those files are under /etc/init.d/ and I believe somewhere there's also "skeleton" or template file for a new one (or you can take any existing one, copy and modify). Then you need to add symbolic links (there's also command line tool to do this, but I can't get the name to my head right now), you can do something like 
 ```
ln -s /etc/init.d/mynewscriptfile /etc/rc2.d/S10mynewscriptfile
``` 
where 10 is the sequence number from 01-99 when in the boot process this script is executed, and S means to start it, K would mean to "kill" it. Make your script executable (chmor u+x [scriptname]). If any questions, please don't hesitate to ask - I'm sorry to be light on details here.[/QUOTE]
 Thanks for the quick reply. I did as you said but nothing happened. Would it be worth trying a number lower than 10? Or could I be using a different run level?

---

### Post by heimo on 2005-08-19
/etc/inittab tells you the default initlevel, and in Ubuntu default install, it's 2. 10 is very early, you may need to experiment.

---

### Post by fmpuk on 2005-08-20
[QUOTE=heimo]/etc/inittab tells you the default initlevel, and in Ubuntu default install, it's 2. 10 is very early, you may need to experiment.[/QUOTE]
 Thanks for the help - In the end I added the line to "/etc/init.d/module-init-tools" and it worked fine.
Thanks a lot :) Hope that helps others too

---

