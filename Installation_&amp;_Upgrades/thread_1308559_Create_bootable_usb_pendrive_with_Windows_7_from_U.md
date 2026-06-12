---
title: "Create bootable usb pendrive with Windows 7 from Ubuntu 9.10?"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by leohimself on 2009-10-31
Help! I need to create a bootable pendrive with windows 7 x64 from ubuntu 9.10. I tried using UNetbootin, adding the iso file and specifying the pendrive(with ntfs), but it crashes everytime at 52% of progress. What are my alternatives? There are a lot of tutorials on web on how to create a bootable windows 7 pendrive from windows os, using cmd.exe, then adding bootsect to it etc. etc. but not one on how to create it from ubuntu.. Can anyone help me?:(

---

### Post by coolsam001 on 2011-11-14
Hii
 There are plenty of methods to make windows 7 bootable usb from linux. I will describe a much simpler method. 
Steps:
1. You need to install wine software from repository if you are connected to internet or download the .deb package and install. If you are doing manual installation then you also have to download libaudio2.deb. Install libaudio2.deb first and then wine.deb.(Wine enables Linux users to run Windows applications without a copy of Microsoft Windows and Libaudio2 is dependency for wine) 
2. Download Universal usb installer.exe and save it in your desktop.
3. Now right click on the universal usb installer and then click on the option-open with wine loader.
4. A window will appear. Simply check the windows 7 from the dropdown list.Provide the iso path of windows 7. Tick on the option show all drives. Select your usb. Tick the option format the drive.
5. Now click on the option-create
6. The creation of bootable usb will start.:)

---

### Post by oldos2er on 2011-11-14
Closed, necromancy.

---

