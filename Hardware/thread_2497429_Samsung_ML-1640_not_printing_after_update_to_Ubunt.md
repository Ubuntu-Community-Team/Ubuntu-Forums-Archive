---
title: "Samsung ML-1640 not printing after update to Ubuntu 22.04"
date: 2024-05-04
forum: Hardware
---

### Post by RobotOfBarr on 2024-05-04
The printer prints its test page using the on-board button, works fine on a Windows machine, worked fine on Ubuntu 20.04. A Canon Pixma IP3000 works fine on Ubuntu 22.04.
The printer appears to accept the job but fails to pick up the paper and print, the pop-up shows "Printing..." and then the print status shows "Stopped".
The driver is the only download available from HP: V1.00.39_01:17 (14.7 MB) Sep 1, 2017  and using CUPS.

Output from lpstat -t (with one stopped job (74) in the queue)[INDENT]scheduler is running[/INDENT]
[INDENT]system default destination: ML-1640-Series[/INDENT]
[INDENT]device for iP3000: usb://Canon/iP3000?serial=90F410[/INDENT]
[INDENT]device for ML-1640-Series: usb://Samsung/ML-1640%20Series?serial=4R37BKCQB00391L.[/INDENT]
[INDENT]iP3000 accepting requests since Sat 04 May 2024 12:35:56 BST[/INDENT]
[INDENT]ML-1640-Series accepting requests since Sat 04 May 2024 13:42:00 BST[/INDENT]
[INDENT]printer iP3000 is idle.  enabled since Sat 04 May 2024 12:35:56 BST[/INDENT]
[INDENT]printer ML-1640-Series is idle.  enabled since Sat 04 May 2024 13:42:00 BST[/INDENT]
[INDENT]    Rendering completed[/INDENT]
[INDENT]ML-1640-Series-74       r              2912256   Sat 04 May 2024 13:41:52 BST[/INDENT]


Is there anyone who knows of an alternative driver or a work-around? 

TIA.

[Edit]
It turns out that Ghostscript was necessary to provide the PCL Interface.

---

