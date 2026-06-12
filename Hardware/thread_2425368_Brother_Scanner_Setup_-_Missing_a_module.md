---
title: "Brother Scanner Setup - Missing a module"
date: 2019-08-24
forum: Hardware
---

### Post by sunrise718 on 2019-08-24
I am trying to set up my Brother MFC scanner software to work with Simple Scan.  I downloaded the Brother driver and installed it.  

When I tested a scan with Simple Scan, it identified the Brother printer as the scanner but failed to scan.  It changes from "Ready to Scan." to "Failed to scan.  Unable to connect to scanner."  

Yet my printer is hooked up properly and prints without any issues.

An error message that I received yesterday is:  

```
GTK-Message : Failed to load module "canberra-gtk-module"
```

I cannot locate the graphical software repository of dependencies to see if I can download it from that source.  So, I will try to install it with the Terminal.

Should I simply type:

```
Sudo Install Canberra-gtk-module
```

Will that work?  Any tips and advice for this novice (but getting savvier) Ubuntu user to connect the scanner to my computer?

---

### Post by SeijiSensei on 2019-08-25
[https://askubuntu.com/questions/342202/failed-to-load-module-canberra-gtk-module-but-already-installed](https://askubuntu.com/questions/342202/failed-to-load-module-canberra-gtk-module-but-already-installed)

```
sudo apt install libcanberra-gtk-module libcanberra-gtk3-module
```

seems to be the solution.

Linux is case sensitive.  There is no command "Sudo".  Nearly every command is in lower case.  Nor should "install" be capitalized.  Pay close attention to syntax if you're following online suggestions to save yourself a lot of pain.

---

### Post by sunrise718 on 2019-08-25
Thank you!  I successfully installed the module with your command.

Sadly, neither Simple Scan or XSane are still not recognizing the connection.

It could be an issue with the Brother scanner even though the printer in the machine is working.  

I need to try some troubleshooting with the machine.  If you have other ideas, let me know.

Also, on the topic of case-sensitive, do you think a problem could occur if I changed the name of my machine on the home page to upper case even though the other Unix code is lower case?  I have not detected any issues after changing that the other day.

---

### Post by SeijiSensei on 2019-08-27
I have an HP scanner for which there are no Linux drivers.  I purchased a copy of VueScan which works fine: [https://www.hamrick.com/](https://www.hamrick.com/)

---

### Post by slickymaster on 2019-08-27
*Thread moved to **Hardware**.*

---

### Post by him610 on 2019-08-27
I own a Brother MFC-7360N. Never experienced any issues for downloads, installation, and operation using Brother supplied installation installation routines or instruction through many installations of *buntu 14.04, 16.04, 18.04.
Which model Brother MFC? Maybe you have come to the right place for assistance.

---

