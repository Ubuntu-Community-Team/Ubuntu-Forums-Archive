---
title: "How to install GUI in Ubuntu server 9.10 edition without internet connection?"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by eswarmandepu on 2009-11-02
[COLOR=black][FONT=Verdana][SIZE=2]Hi,[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=2]I had installed Ubuntu 9.10 Server edition in VMWare machine. I want to add GUI(GNOME) for this server. Found in forums, using apt-update, apt-get install ubuntu-desktop utilities will install GUI from internet connectivity. This one working fine, but I want to install same GUI with offline (without internet) from CD or .iso image. [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=2] [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=2]Can you please some one suggest which cd(iso)I need to download and what are steps need to follow to complete this GUI install?[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=2][/SIZE][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana][SIZE=2]Thanks & Regards,[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=2]Eswar[/SIZE][/FONT][/COLOR]

---

### Post by wojox on 2009-11-02
Try AptonCD: [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by ajgreeny on 2009-11-02
> **wojox said:**
> Try AptonCD: [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)
That assumes that the OP has installed all those packages in another computer which started as a server.  It will not work from an install from CD which is already including the GUI.

So using another web-connected machine, download the iso of the Alternate install CD which you can then use to install what you want by choosing the CD as your repository.

---

