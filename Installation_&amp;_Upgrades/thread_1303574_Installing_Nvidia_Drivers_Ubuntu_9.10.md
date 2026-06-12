---
title: "Installing Nvidia Drivers Ubuntu 9.10"
date: 2009-10-28
forum: Installation &amp; Upgrades
---

### Post by Flatuance on 2009-10-28
How do you install the NVIDIA drivers in Ubuntu 9.10?  I don't know the command to stop the X Server.  When I type in:  sudo /etc/init.d/gdm stop, it doesn't work.  Must have been changed in the new version  Any suggestions?  ;)

---

### Post by albandy on 2009-10-28
enter a tty: ctrl+alt+F1
enter your login and password

then stop gdm:
sudo /etc/init.d/gdm stop
wait some seconds
now start gdm:
sudo /etc/init.d/gdm start

you can return to the X environment by pressing ctrl+alt+f7

---

### Post by Flatuance on 2009-10-28
That was really weird...I did a restart, ran that command, and it worked!  I was able to stop the X Server and install the newest NVIDIA driver.  Thank you very much for your fast response.  :)  I really appreciate it!  :D

---

### Post by Norwal on 2009-12-30
The Stop comd still does not work for me.  At one point it even said it had stopped, but when I go to run drivers, I get a message that says X is running.

---

### Post by kpsg25690 on 2010-02-05
try this
> sudo init 3
it should work..
it did for me..

---

### Post by audiomick on 2010-02-05
> **kpsg25690 said:**
> try this

it should work..
it did for me..
I thought that is not supposed to work on Ubuntu
from here
[http://en.wikipedia.org/wiki/Run_level#Ubuntu](http://en.wikipedia.org/wiki/Run_level#Ubuntu)

> **Debian Linux**

 [Debian]("http://en.wikipedia.org/wiki/Debian"), as well as most of the distributions based on it, like early Ubuntu, does not make any distinction between runlevels 2 to 5.
  [SIZE=1]Debian Linux runlevels[/SIZE]  [SIZE=1]ID[/SIZE] [SIZE=1]Description[/SIZE]   [SIZE=1]**0**[/SIZE] [SIZE=1]Halt[/SIZE]   [SIZE=1]**1**[/SIZE] [SIZE=1]Single-User mode[/SIZE]   [SIZE=1]**2**-**5**[/SIZE] [SIZE=1]Full Multi-User with console logins and display manager if installed[/SIZE]   [SIZE=1]**6**[/SIZE] [SIZE=1]Reboot[/SIZE]   **[[edit]("http://en.wikipedia.org/w/index.php?title=Runlevel&action=edit&section=5")] Ubuntu**

 [Ubuntu]("http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29") 6.10 (Edgy Eft) and later contain [Upstart]("http://en.wikipedia.org/wiki/Upstart") as a replacement for the traditional init-process, but they still use the traditional init scripts and Upstart's SysV-rc compatibility tools to start most services and emulate runlevels.


---

### Post by kelvin spratt on 2010-02-05
why don't you just use restricted drivers to install the correct driver.
There are vids on youtube that show you how do do it if you are not sure.

---

