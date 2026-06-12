---
title: "New user help"
date: 2008-11-23
forum: General Help
---

### Post by jakari on 2008-11-23
Hey

Im a long time windows user first time ubuntu user...

im thinking about making ubuntu my preferred O/S and iv just downloaded my Nvidia graphics driver and ran it but it says it needs to be run in /root

so when i try and copy the file over to the root folder it says i don't have permission... 

can some one please tell me how to get control of the folder?

Thanks

---

### Post by drs305 on 2008-11-23
To make any changes/additions/subtractions from system files, you need to have administrative powers (root). When running a terminal command, preceed it with "sudo" (e.g. sudo cp myfile /etc ). When running a graphical app like nautilus or gedit, start with "gksudo". 

You will have to enter your password when asked. Type it and hit ENTER when done. You won't see anything as you type.

This will explain Sudo:
[RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by fooman on 2008-11-23
its a little trickier to install the nvidia driver from nvidia in linux then it is in windows.

normally the easiest method is to go to system > administration > hardware drivers

and see if there is a driver listed for your card.  if it is there...enable it.

---

### Post by sisco311 on 2008-11-23
go to System > Administration > Hardware Drivers and enable the driver.

---

### Post by jimmy the saint on 2008-11-23
Don't try to do that manually if you are a newbie.  just go to system>administration>hardware drivers and activat the restricted Nvidia driver there.  No fuss no muss and no need to worry about fragging your system because you are creating a learning curve that looks more like a brick wall!  Also, do not choose the 177 driver, choose the older one.  WAY to many bugs with 177.

---

