---
title: "Olympus C-740 Ultra Zoom"
date: 2010-11-30
forum: Hardware
---

### Post by Giancarlo.Rinaldo on 2010-11-30
Codice:[COLOR=#000000][FONT=Times New Roman][FONT=verdana]Hi.
I have a photocamera as in the title  that has always  been recognized by Ubuntu. Surely til the previous LTS Hardy. In this moment Lucid unfortunately does not recognize it!
The problem is Lucid since I have the same problem with 4 different PC: Hp Notebook, Compaq Presario PII 400, EEEBox and my workstation.
If I execute "lsusb", I obtain

[COLOR=#000000][FONT=courier new]Bus 002 Device 002: ID 07b4:0105 Olympus Optical Co., Ltd Camedia C-310Z/C-700/C-750UZ/C-755/C-765UZ/C-3040/C-4000/C-5050Z/D-560/C-3020Z Zoom Camera Un  grazie anticipato.[/FONT][/COLOR]
But unfortunately it does not make automount and if I executesudo fdisk -l I do not get anything related to the camera. 

Do you have some hints?

By Googling I didn't find any solution.

Thank you in advance.
[/FONT][/FONT][/COLOR]

---

### Post by shosto on 2011-07-10
My wife has a similar problem. Her camera is sometimes automounted and others times it isn't. Did some research and came up with a small shell script to use with nautilus to mount it, when automount fails. Instructions are contained in the script itself.

---

