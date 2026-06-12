---
title: "Parallels Workstation 2.2 - Module vm-main is not found"
date: 2008-10-31
forum: General Help
---

### Post by sprog on 2008-10-31
Parallels Workstation 2.2 used to work OK, but a week or so ago it stopped.  I'm on 8.04, and I'm not aware of making any changes since it last ran. Perhaps a security update broke it.

When run it says:  Module vm-main is not found! Parallels Workstation 2.2 is installed, but it has not been configured for your running kernel. To configure it please login as root and run parallels-config.

So as root: parallels-config  .....  Parallels Workstation has been successfully configured....  Now you can run Parallels Workstation 2.2....   Issue parallels command.

But the problem persists. Does anyone have any ideas.

Here is blurb when run from the command line:
Loading Parallels Workstation 2.2 hypervisor ... 
 Error: hypervisor module is not found in /lib/modules/2.6.24-21-generic/kernel/drivers/misc/parallels/
 Perhaps installation or/and configuration was done incorrectly.
 Run parallels-config again.
Fontconfig warning: "/etc/fonts/conf.d/53-monospace-lcd-filter.conf", line 17: invalid constant used : lcdfilterlegacy
QString::arg(): Argument missing: Module <b>vm-main</b> is not found! <b>Parallels Workstation 2.2</b> is installed, but it has not been configured for your running kernel. To configure it please login as root and run <b>parallels-config</b>., Parallels Workstation
QString::arg(): Argument missing: Module <b>vm-main</b> is not found! <b>Parallels Workstation 2.2</b> is installed, but it has not been configured for your running kernel. To configure it please login as root and run <b>parallels-config</b>., 2.2
QString::arg(): Argument missing: Module vm-main is not found! Parallels Workstation 2.2 is installed, but it has not been configured for your running kernel. To configure it please login as root and run parallels-config., Parallels Workstation
QString::arg(): Argument missing: Module vm-main is not found! Parallels Workstation 2.2 is installed, but it has not been configured for your running kernel. To configure it please login as root and run parallels-config., 2.2
Module vm-main is not found! Parallels Workstation 2.2 is installed, but it has not been configured for your running kernel. To configure it please login as root and run parallels-config.

---

### Post by Nicezia on 2008-11-04
> **sprog said:**
> Parallels Workstation 2.2 used to work OK, but a week or so ago it stopped.  I'm on 8.04, and I'm not aware of making any changes since it last ran. Perhaps a security update broke it.

When run it says:  Module vm-main is not found! Parallels Workstation 2.2 is installed, but it has not been configured for your running kernel. To configure it please login as root and run parallels-config.

So as root: parallels-config  .....  Parallels Workstation has been successfully configured....  Now you can run Parallels Workstation 2.2....   Issue parallels command.

But the problem persists. Does anyone have any ideas.

Here is blurb when run from the command line:
Loading Parallels Workstation 2.2 hypervisor ... 
 Error: hypervisor module is not found in /lib/modules/2.6.24-21-generic/kernel/drivers/misc/parallels/
 Perhaps installation or/and configuration was done incorrectly.
 Run parallels-config again.
Fontconfig warning: "/etc/fonts/conf.d/53-monospace-lcd-filter.conf", line 17: invalid constant used : lcdfilterlegacy
QString::arg(): Argument missing: Module <b>vm-main</b> is not found! <b>Parallels Workstation 2.2</b> is installed, but it has not been configured for your running kernel. To configure it please login as root and run <b>parallels-config</b>., Parallels Workstation
QString::arg(): Argument missing: Module <b>vm-main</b> is not found! <b>Parallels Workstation 2.2</b> is installed, but it has not been configured for your running kernel. To configure it please login as root and run <b>parallels-config</b>., 2.2
QString::arg(): Argument missing: Module vm-main is not found! Parallels Workstation 2.2 is installed, but it has not been configured for your running kernel. To configure it please login as root and run parallels-config., Parallels Workstation
QString::arg(): Argument missing: Module vm-main is not found! Parallels Workstation 2.2 is installed, but it has not been configured for your running kernel. To configure it please login as root and run parallels-config., 2.2
Module vm-main is not found! Parallels Workstation 2.2 is installed, but it has not been configured for your running kernel. To configure it please login as root and run parallels-config.

The kernel update is what broke your Parallels. The new kernel 2.6.24-21 doesn't have module in the repository, and no one seems to have updated parallels in the repository for the new kernel... 

I ran into this myself.
Had to build the modules myself for the newly installed kernel

---

### Post by MDee on 2008-11-17
I am an ubuntu newbie: How do I compile the module again?
Thanks in advance,
Michael

---

### Post by MDee on 2008-11-17
I mean: build the modules!

---

### Post by nossifer on 2008-11-30
hm... this didnt help either
[http://forum.parallels.com/showthread.php?t=10221](http://forum.parallels.com/showthread.php?t=10221)

parallels config seems to be working fine, but I cant launch the app without the error message.  I cant find vm-main on the internet for download/compile.

also, when I run "/usr/lib/parallels/autostart/drivers_start"
I get:
Loading Parallels Workstation 2.2 hypervisor ...
 Error: hypervisor module is not found in /lib/modules/2.6.24-22-generic/kernel/drivers/misc/parallels/
 Perhaps installation or/and configuration was done incorrectly.
 Run parallels-config again.

not too sure what to do next.

---

### Post by el_negro on 2009-02-14
> **Nicezia said:**
> The kernel update is what broke your Parallels. The new kernel 2.6.24-21 doesn't have module in the repository, and no one seems to have updated parallels in the repository for the new kernel... 

I ran into this myself.
Had to build the modules myself for the newly installed kernel

How do I have to do for build the modules for my kernel?
I have the 2.6.27-11-generic of Ubuntu 8.10 and the parallels-modules-2.6.24-19-generic of Parallels.

I need a solution :s
Thanks.

---

