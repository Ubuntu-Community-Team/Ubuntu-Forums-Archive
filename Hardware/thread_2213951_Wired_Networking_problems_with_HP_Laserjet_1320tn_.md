---
title: "Wired Networking problems with HP Laserjet 1320tn printer installation"
date: 2014-03-29
forum: Hardware
---

### Post by dkdias on 2014-03-29
I am replacing the windows xp os computers at our local youth center with Ubuntu 12.04 os, but I am having problems getting the wired networked printer to work. I can see the printer as a wired networked printer (HP laserjet 1320tn) on the list of networked printers, but it will hang up when I try to send a printjob to it? I can "install" the HP printer, but it will not print anything. I have tried using Samba, but it wants a password every time there is a print job sent to the printer, so that won't work for the youth center. Please help!

---

### Post by ajgreeny on 2014-03-29
It should be fully supported by the version of hplip in all versions of ubuntu available, so all I can suggest is that you make sure hplip is installed, and I also suggest you install hplip which will give you an HP-toolbox which you can use to configure and if necessary troubleshoot your printing problem.

You may also find that if you open a web-browser (it doesn't matter which) and go to [http://localhost:631/admin](http://localhost:631/admin) for a webmin printer page which may help you.

---

### Post by dkdias on 2014-04-05
> **ajgreeny said:**
> It should be fully supported by the version of hplip in all versions of ubuntu available, so all I can suggest is that you make sure hplip is installed, and I also suggest you install hplip which will give you an HP-toolbox which you can use to configure and if necessary troubleshoot your printing problem.

You may also find that if you open a web-browser (it doesn't matter which) and go to [http://localhost:631/admin](http://localhost:631/admin) for a webmin printer page which may help you.

I installed hplip, all of the files and tried the URL given and it still does not see the Hp printer?  When  I ran lpstat -p -d in a terminal window, this is what i got.
I found that this command should show me the printer?  it did not........

guest@dan-OptiPlex-320 ~ $ lpstat -p -d
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-b5tPAa/pkcs11: No such file or directory
no system default destination
guest@dan-OptiPlex-320 ~ $

I also got the printer stats. They are as follows?  Please help!  Thanks!
[ATTACH=CONFIG]251752[/ATTACH]

---

### Post by dkdias on 2014-04-06
How can I move this thread to the printer/hardware forum?

---

### Post by dkdias on 2014-04-13
I am going to move this tread to hardware and see if I can get help there........... thanks

---

### Post by Iowan on 2014-04-13
> **dkdias said:**
> I am going to move this tread to hardware and see if I can get help there........... thanksDone!

---

### Post by dkdias on 2014-04-13
I am replacing the windows xp os computers at our local youth center with Ubuntu 12.04 os, but I am having problems getting the wired networked printer to work. The printer is connected to the network through a switch via a cat5e cable then to the router. I can see the printer as a wired networked printer (HP laserjet 1320tn) on the list of networked printers, but it will hang up when I try to send a printjob to it? I can "install" the HP printer, but it will not print anything. I have tried using Samba, but it wants a password every time there is a print job sent to the printer, so that won't work for the youth center. Please help!

I installed hplip, all of the files and tried the URL [http://localhost:631/admin](http://localhost:631/admin) it still does not see the Hp printer? When I ran lpstat -p -d in a terminal window, this is what i got. I found that this command should show me the printer? it did not........

guest@dan-OptiPlex-320 ~ $ lpstat -p -d
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-b5tPAa/pkcs11: No such file or directory
no system default destination
guest@dan-OptiPlex-320 ~ $

I also got the printer stats. They are as follows? Please help! Thanks!

---

