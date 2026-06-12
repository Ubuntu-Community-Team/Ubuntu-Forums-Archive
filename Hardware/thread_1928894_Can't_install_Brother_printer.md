---
title: "Can't install Brother printer"
date: 2012-02-20
forum: Hardware
---

### Post by Capt'n on 2012-02-20
I own a MFC-9450CDN printer manufactured by Brother. However, when I plug it into my computer, it refuses to recognize it. This is a problem localized to my computer as the printer hums happily along when plugged into my roommate's computer. Any ideas as to what's wrong with it?

---

### Post by plucky on 2012-02-21
> **Capt'n said:**
> I own a MFC-9450CDN printer manufactured by Brother. However, when I plug it into my computer, it refuses to recognize it. This is a problem localized to my computer as the printer hums happily along when plugged into my roommate's computer. Any ideas as to what's wrong with it?

You need to download and install the driver from [Brother Solution Centre](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html) for your printer.Use the .deb files and follow the instructions given on the website.


Good Luck

---

### Post by Capt'n on 2012-02-21
Okay then. Thank you for your help.

---

### Post by Capt'n on 2012-02-21
I tried to install the drivers, and it spat a lot of things at me while still not installing the driver.

> (Reading database ... 215941 files and directories currently installed.)
Preparing to replace mfc9450cdnlpr 1.0.3-1 (using .../mfc9450cdnlpr-1.0.3-1.i386.deb) ...
Unpacking replacement mfc9450cdnlpr ...
Setting up mfc9450cdnlpr (1.0.3-1) ...
mkdir: cannot create directory `/var/spool/lpd/mfc9450cdn': No such file or directory
chown: cannot access `/var/spool/lpd/mfc9450cdn': No such file or directory
chgrp: cannot access `/var/spool/lpd/mfc9450cdn': No such file or directory
chmod: cannot access `/var/spool/lpd/mfc9450cdn': No such file or directory

I don't understand what went wrong :sad:

---

### Post by ratazana80 on 2012-02-21
Same problem here, but with a MFC-235c on Ubuntu 11.10.

If i use the tool listed here: 

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104)

the printer is installed and works, but if i do a
 #apt-get update 

It shows a "distribution upgrade" and everything is uninstalled automaticaly :( I can't get it to work..the same goes for the scanner.

---

### Post by plucky on 2012-02-22
> **Capt'n said:**
> I tried to install the drivers, and it spat a lot of things at me while still not installing the driver.



I don't understand what went wrong :sad:

Nothing went wrong,it was just unable to create the directory.

You could run from a terminal ```
sudo mkdir /var/spool/lpd
sudo mkdir /var/spool/lpd/mfc9450cdn
``` and then run the install command again and those error messages won't appear.

Just install the cupswrapper .deb and then run ```
dpkg -l | grep -i brother
``` to see if it is installed.

The driver should now be installed,so if you connect your printer and go to **System Settings > Printers** and add a new printer,you should be able to select the correct printer driver.

Good Luck

---

### Post by Capt'n on 2012-02-22
Okay, I tried that and it told me this

> dpkg: error: operation requires read/write access to dpkg status area


How do I give it the proper permissions?

---

### Post by plucky on 2012-02-23
> **Capt'n said:**
> Okay, I tried that and it told me this



How do I give it the proper permissions?

Tried what?

If the mkdir command,you have to use "sudo" in front of all commands so you have the privilege to write to the system area.

Good Luck

---

