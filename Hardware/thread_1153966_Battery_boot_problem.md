---
title: "Battery boot problem"
date: 2009-05-09
forum: Hardware
---

### Post by john28857 on 2009-05-09
Battery power-- wont start or shutdown without assistance

Fresh install Jaunty (64bit)
HP9925NR laptop
AMD 64 Turion x2 proc.
4gb ram
Under AC power starts and shuts down normally. Battery power  you see normal startup then the grub screen, then the screen goes blank and nothing happens. I waited 3 minutes and still nothing. Then I pressed &  held the shift key and it booted as normal. Same problem with shutting down  screen goes blank and nothing happens no disc activity until shift key is pressed and held.Once again only under battery power. Any help greatly appreciated.
John

---

### Post by sergiom99 on 2009-05-23
wow!
same thing here.
I upgraded to Kubuntu JJ 32bits (fresh install) and same thing happens.
I then realized that pressing any key does the trick.
If I got it plugged to AC, it boots just fine.

sergio@kubuntu:~$ uname -a
Linux kubuntu 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

---

### Post by Chrisk7fender on 2009-05-24
same problem here...I'm running 9.04 on my HP DV6604NR...looking for a fix...

---

### Post by sergiom99 on 2009-05-24
I tried adding *acpi_osi="Linux"* to the boot line in GRUB as suggested somewhere, but nothing. Upgraded to the latest BIOS version provided by HP, but nothing again.

---

### Post by sergiom99 on 2009-05-26
*bump*

---

### Post by sergiom99 on 2009-05-28
Here are my dmesg and syslog when I booted on battery to see if they help someone.
Thanks!

---

### Post by cusa on 2009-05-31
Hi,
I have the same problem :) ... I am running Kubuntu 9.04. The moment I plug in the power it starts normally ...

---

### Post by qlinux on 2009-06-13
I too am encountering this issue...in fact since upgrading from 8.04 to 9.04 I've encountered a few issues (note to self: maybe staying with the LTS is a good idea)

Unfortunately I don't have a solution but.. here's what I know...

Non-recovery mode Grub options are:
boot with 9.04 Kernel 2.6.28-11-generic (Automagic)
boot with 9.04 Kernel 2.6.24-24-generic (Automagic)


use battery to boot with 9.04 Kernel 2.6.28-11-generic (Automagic)
	- does not startup properly on battery
	- have to press keys (esc, arrows, spacebar... whatever)
	- Noticed that during this process if I plug in the power then "voom" the startup continues no problem. (ok it doesn't really go "voom" but you know know what I mean)

use battery boot with 9.04 Kernel 2.6.24-24-generic (Automagic)
	- starts up fine

I hope this provides somebody with an idea for a solution.

In the meantime I'm going to keep digging..

---

### Post by sergiom99 on 2009-06-18
Today I upgraded to
```
$ uname -a
Linux kubuntu 2.6.28-13-generic #44-Ubuntu SMP Tue Jun 2 07:57:31 UTC 2009 i686 GNU/Linux
```

But it's still not solved.

---

### Post by sergiom99 on 2009-06-25
I got it fixed by fixing my DSDT with this awesome howto [1] and thanks to 67GTA's kind help.
Take a look and help yourselves, its not difficult at all!
Good luck! 
-Sergio

[1] [http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051)

---

### Post by qlinux on 2009-07-18
Like I said.. I'd keep digging....

I too found the DSDT solution posted above by Sergiom99.  
----------------------------
I also found this posted by Ripose in another forum entry ([http://ubuntuforums.org/showthread.php?t=1059545]("http://ubuntuforums.org/showthread.php?t=1059545"))

"FIX: Having to repeatedly hit or hold down ANY key to continue boot and/or shutdown.

Add the following parameters to the kernel line in /boot/grub/menu.lst somewhere between the "resume=/dev/sda*" and "splash=silent" parameters:

notsc pci=assign-busses apicmaintimer idle=poll reboot=cold,hard

I found the solution on the SuSE forum."
----------------------------------------
This was suggested here: ([http://forums.opensuse.org/install-boot-login/407628-laptop-does-not-boot-battery.html]("http://forums.opensuse.org/install-boot-login/407628-laptop-does-not-boot-battery.html"))

"Try adding:

acpi_osi="Linux"

...to the end of the boot line at the grub screen.

I have a HP dv6000 series and that helps with thermal limits and stuff, plus a few other interesting things that I've forgotten now .

Type it exactly as seen with the quotes.

It's a HP specific thing I think"
---------------------------------------
So which is it?  Edit grub or do the DSDT fix.  
I'm guessing both is probably best.. but if you are stuck for time or are technically wary (I don't blame you really).  You might want to try the grub change first.  At least to get your laptop booting from the battery.

Good luck..  I'd like to know if anyone has encountered any other fixes or knows of any updates from Ubuntu that correct this without having to execute feats of technology.

Q

---

### Post by sergiom99 on 2009-07-18
> **qlinux said:**
> 

"Try adding:

acpi_osi="Linux"

...to the end of the boot line at the grub screen.

I have a HP dv6000 series and that helps with thermal limits and stuff, plus a few other interesting things that I've forgotten now .

Type it exactly as seen with the quotes.


Thats supposed to work with a custom DSDT file.
I tried it before the new DSDT and didn't work by itself.

---

