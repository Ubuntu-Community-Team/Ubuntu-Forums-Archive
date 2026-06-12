---
title: "Connecting hp 3055A deskjet to Ubuntu"
date: 2013-10-01
forum: Hardware
---

### Post by sam27 on 2013-10-01
Hi there

I hope somebody can help!  

I've been trying without any success to scan a document using hp 3055a deskjet, however, even after upgrading my software to version 12.04 the deskjet keeps stating `computer not found'.  If anybody knows how I would be very grateful!  Please note I'm not very technical so in simple terms please, thank you!!:)

---

### Post by decrepit on 2013-10-02
I have a HP 3520, and I also get "no computer found" when I try to scan from the desktop to the computer. It says something about some software not installed. I suspect this is a windows function not available with ubuntu, (but I could be wrong).
There's a few ways you can initiate a scan from the computer. If you go to "graphics" there's 3 programs there that will do it.
With the Gimp image editor, go to new, create, select xsane.
or you can select "xsane" directly, then there's the "simple scan"

I had problems with my computer not finding the scanner, reinstalling HPLIP fixed that.

---

### Post by Bucky Ball on 2013-10-02
*Thread moved to **Hardware**.*

Welcome. You need to have hplip installed (in the repos) and the drivers for your printer from the HP site.

---

### Post by oldfred on 2013-10-02
The HPLIP in the repository is fairly old. 
You can get a much newer version directly from HP.



I have an HP Deskjet 3520 and this worked for me.
[http://ubuntuforums.org/showthread.php?t=2109050](http://ubuntuforums.org/showthread.php?t=2109050)
HP's newest On this website you can download the HPLIP software which supports 2,211 HP printers on nearly any Linux distribution available today.
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)
Ubuntu's older version
sudo apt-get install hplip-gui
gksudo hp-setup
# new version
hp-upgrade

No system tray error:
open up the "startup applications" editor from the admin menu.
add a new program, for the command put:
sleep 10;/usr/bin/hp-systray

---

