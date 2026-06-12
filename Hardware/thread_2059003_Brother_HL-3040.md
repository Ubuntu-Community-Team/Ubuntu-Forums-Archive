---
title: "Brother HL-3040"
date: 2012-09-17
forum: Hardware
---

### Post by messerve on 2012-09-17
I've installed ubuntu a few times now but am not up on the terminal commands.  I am trying to install a driver for a Brother HL-3040 and am having no luck.  
"hl3040cnlpr-1.1.2-1i386.rpm"  Any help with the install would be great.

Thanks,
Peter

---

### Post by GeForce 9500GT on 2012-09-17
First of all, .rpm files won't mwork under Ubuntu or any Debian-based Linux distro. 
To get the correct drivers, [check this site]("https://sites.google.com/site/tipsandtricksforubuntu/printer-info/brother"). It provides you with links for Brother printer drivers.

---

### Post by pdc on 2012-09-19
Brother supply an installer

[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/linux-brprinter-installer-1.0.0-1.gz&lang=English_lpr](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/linux-brprinter-installer-1.0.0-1.gz&lang=English_lpr)

I have seen others say that it works well.it automates the process

can I suggest you try that, and tell us how it goes ...

____________________________________________

......if you want to do it yourself..

.....go here........

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

you need [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-3040CN](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-3040CN)

for your HL-3040CN ?

you need **TWO** .deb packages: **lpr.deb** and [B]cupswrapper.deb
[/B]
you need to download and install the **lpr.deb** package first ...

........*likely gdebi installer will jump to offer to install..I suggest you let it*.............

and then download and install the **cupswrapper.deb** package afterwards

Brother do provide detailed instructions to work through if you wish

........for the lpr driver first............

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html)

......and then the cupswrapper driver

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)

.........so you may find the installer that Brother offers..is good !

if you subscribe to a thread, ..top-right..thread tools..easier to keep in touch

---

### Post by messerve on 2012-09-26
Thanks GeForce and pdc.....the driver is installed but am still not able to communicate with the printer...any suggestions?

---

### Post by messerve on 2012-09-26
Tried re-installing the driver but that did not work as far as an automated process goes.
How do I install it from terminal? (I know its a silly question)

---

### Post by messerve on 2012-09-26
This is the message I get when trying to re-install.

Unpacking replacement hl3040cnlpr ...
Setting up hl3040cnlpr (1.1.2-1) ...
mkdir: cannot create directory `/var/spool/lpd/hl3040cn': No such file or directory
chown: cannot access `/var/spool/lpd/hl3040cn': No such file or directory
chgrp: cannot access `/var/spool/lpd/hl3040cn': No such file or directory
chmod: cannot access `/var/spool/lpd/hl3040cn': No such file or directory

---

### Post by messerve on 2012-09-26
This is what I get when installing cups


(Reading database ... 219144 files and directories currently installed.)
Preparing to replace hl3040cncupswrapper 1.1.2-1 (using .../hl3040cncupswrapper-1.1.2-1.i386.deb) ...
cups stop/waiting
cups start/running, process 8905
Unpacking replacement hl3040cncupswrapper ...
Setting up hl3040cncupswrapper (1.1.2-1) ...
cups stop/waiting
cups start/running, process 9002

---

### Post by pdc on 2012-09-27
if you COPY and PASTE this command into a terminal

> sudo dpkg -l | grep Brother and hit the enter key

and if you COPY and PASTE back what you get please;

______________________________________________________________

> This is what I get when installing cups


why would you do that? cups is normally a core part of any installation..

......help us understand............

---

