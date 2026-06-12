---
title: "Canon IP4200 problems after install 12.04"
date: 2012-05-05
forum: Hardware
---

### Post by old_dog on 2012-05-05
Can someone point me in the right direction. Upgaded to 12.04  from previous release. 
Printer no longer wants to work correctly. Not a printer problem, it works ok in windows, removed "CUPS" and re-installed. 
Currently prints the doc say 5 lines and stops with power light flashing can't eject the printed doc or anything? 
Previous Ubuntu release spot on.

---

### Post by dserebren on 2012-05-07
Same problem here. Doesn't even start printing for me. Just sits there with blinking power light. The only way to wake the printer up after this seems to be to pull the power cord.

I'm on amd64 version, desktop. First time trying this, so maybe that's why. Also I tried to install driver according to this [http://www.iheartubuntu.com/2012/02/install-canon-printer-for-ubuntu-linux.html](http://www.iheartubuntu.com/2012/02/install-canon-printer-for-ubuntu-linux.html) but got errors during apt-get update.

---

### Post by mörgæs on 2012-05-07
Moved to the hardware forum.

---

### Post by isanaud on 2012-06-20
I have the same probleme 
No problem with previous version of ubuntu

---

### Post by kimberley on 2012-06-22
I have exactly same problem, ie will not print and will not switch off until plug removed.:KS

---

### Post by Tom64 on 2012-06-27
Same problem on 12.04 64bit.  I have a file "to be printed" on my dual boot Win 7 but this is time consuming.

---

### Post by ggschorsch on 2012-08-04
Same problem here.

I'm running ubuntu 12.04 64bit on a thinkpad.
Kernel is 3.2.0-27-generic-tp #43~tp15-Ubuntu SMP x86_64

With gutenprint, my iP4200 starts making noise, preparing the printhead and than stops with powerlight blinking.

With recent turboprint 2.26-2 the printer is working.

---

### Post by lashbam on 2012-12-16
Same problem here.  amd64 and my Canon Pixma iP4200 isn't working.  I'm reading there is a 32bit driver but not a 64bit driver.  Then I read at 
[https://wiki.ubuntu.com/HardwareSupportComponentsPrintersCanon]("https://wiki.ubuntu.com/HardwareSupportComponentsPrintersCanon")

that the Gimp-Print Canon BJC 8200 drivers will work but only at low resolution.  if it works, I'll post my success.  If not, count me in the same printless boat.

---

### Post by pdc on 2012-12-16
it has often needed a symbolic link as the 32bit driver points to lib and with a 64bit system, there is only a lib64

[http://ubuntuforums.org/showthread.php?p=12385174#post12385174](http://ubuntuforums.org/showthread.php?p=12385174#post12385174)

as in post #7 in this thread ............try ........

> [COLOR="Red"]sudo ln -s /usr/lib /usr/lib64[/COLOR]

and 

> [COLOR="Red"]sudo ln -s /usr/local/lib /usr/local/lib64[/COLOR]

---

