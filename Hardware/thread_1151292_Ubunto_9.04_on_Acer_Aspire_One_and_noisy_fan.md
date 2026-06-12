---
title: "Ubunto 9.04 on Acer Aspire One and noisy fan"
date: 2009-05-06
forum: Hardware
---

### Post by ckuter on 2009-05-06
I installed Ubuntu 9.04 on my AA1 (a0a 150) via a Wubi installation.  The fan will not stop running even though the laptop is cool to the touch.  

I tried this fix:

Some Acer Aspire One netbooks out there suffer from a noisy fan. Mine too and it was really starting to drive me crazy. I really wouldn’t want to be caught using it in a quiet place like a library for example. Luckily there’s a couple of scripts you can use to control the fan. The aspireone.net Wiki has all the details, but here’s a quick rundown of what you need to do to get rid of the noise: 

download the acerfand daemon script 
download the acer_ec.pl script (direct download) 
Copy both files to /usr/local/bin 
make acerfand executable using chmod 755 /usr/local/bin/acerfand 
open /etc/rc.local as root (or use sudo) and add /usr/local/bin/acerfand at the end of the file 

This did not change a thing.  Does the Wubi installation prevent Ubuntu from controlling the fan?

---

### Post by 1roxtar on 2009-05-07
That's a unique problem.  I installed Ubuntu 9.04 on my Aspire One with Wubi, too.  I haven't experienced any problems with the fan or any other thing to be honest.  Maybe you might have a faulty fan. Does it do the same thing with Windows???

---

### Post by ckuter on 2009-05-07
No problem with XP.  I used one of the Windows fan control problem and it works flawlesssly.

---

### Post by Aearenda on 2009-05-07
It's better to use acerhdf - the 8.04 instructions at [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne) still work for 9.04. I don't know whether wubi interferes with this, but it's easy to try.

---

### Post by ckuter on 2009-05-07
No go.  When I do the make, it says something about not finding a lib/modules/2.6.28-11-server/build:  No such file or directory.   In the lib/modules/ on my pc, I and 2.6.28-11-generic and 2.6.28-11-server. The is no build in the server module.

---

### Post by Aearenda on 2009-05-07
I suspect your fan will behave with the generic kernel! Why do you run the server kernel on a netbook?

---

### Post by ckuter on 2009-05-07
That is what the fix you suggested selected.

---

### Post by Aearenda on 2009-05-07
I'm confused - the setup for acerhdf works with whatever kernel you are running. It doesn't install a kernel, or select a kernel, itself. 

To verify what kernel you are running, do this is a terminal:```
uname -r
```

---

### Post by bajunganut on 2009-05-08
> **ckuter said:**
> I installed Ubuntu 9.04 on my AA1 (a0a 150) via a Wubi installation. The fan will not stop running even though the laptop is cool to the touch. 
 
I tried this fix:
 
Some Acer Aspire One netbooks out there suffer from a noisy fan. Mine too and it was really starting to drive me crazy. I really wouldn’t want to be caught using it in a quiet place like a library for example. Luckily there’s a couple of scripts you can use to control the fan. The aspireone.net Wiki has all the details, but here’s a quick rundown of what you need to do to get rid of the noise: 
 
download the acerfand daemon script 
download the acer_ec.pl script (direct download) 
Copy both files to /usr/local/bin 
make acerfand executable using chmod 755 /usr/local/bin/acerfand 
open /etc/rc.local as root (or use sudo) and add /usr/local/bin/acerfand at the end of the file 
 
This did not change a thing. Does the Wubi installation prevent Ubuntu from controlling the fan?
 
 
This didn't work for me either, or at least I thought.  
 
Try running:  **sudo acerfand**
 
Doing so forced the script to run and it made my fan stop right away and will auto start if temp is greater than 70 degrees.
 
If your fan still doesn't turn off then check the log to see if the script is running:
 
**sudo tail -f /var/log/syslog**
 
------------------------------------------------------
 
Maybe there is a setting that we are forgetting to make the script run when we first turn on our computer.  It seems like placing **/usr/local/bin/acerfand** in the **rc.local** doesn't execute at startup?  And yes... the line is above the exit 0  :)

---

### Post by ckuter on 2009-05-08
> **bajunganut said:**
> This didn't work for me either, or at least I thought.  
 
Try running:  **sudo acerfand**
 
Doing so forced the script to run and it made my fan stop right away and will auto start if temp is greater than 70 degrees.
 
If your fan still doesn't turn off then check the log to see if the script is running:
 
**sudo tail -f /var/log/syslog**
 
------------------------------------------------------
 
Maybe there is a setting that we are forgetting to make the script run when we first turn on our computer.  It seems like placing **/usr/local/bin/acerfand** in the **rc.local** doesn't execute at startup?  And yes... the line is above the exit 0  :)

Thanks  The syslog says my bios, v0.3116 is unsupported.  Now to find a supported bios and install it.  I did put the line abovre the exit 0 line.

---

