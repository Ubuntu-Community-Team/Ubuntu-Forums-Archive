---
title: "Set screen brightness from terminal?"
date: 2008-08-16
forum: General Help
---

### Post by Jack the R on 2008-08-16
Well I thought I had this figured out, but - 

> jeremy@r1e:/proc/acpi/video/VGA/LCDD$ dir
brightness  EDID  info	state
jeremy@r1e:/proc/acpi/video/VGA/LCDD$ ./brightness
bash: ./brightness: Permission denied
jeremy@r1e:/proc/acpi/video/VGA/LCDD$ sudo ./brightness
sudo: ./brightness: command not found


What gives?

---

### Post by Sycron on 2008-08-16
before typing **./brightness** make the file executable with
```
$ sudo chmod +x brightness
```

Then run it with ./brightness. Next time you won't have to chmod again.

---

### Post by Jack the R on 2008-08-16
That sounds like it would work, but - 

> jeremy@r1e:/proc/acpi/video/VGA/LCDD$ sudo chmod +x brightness
jeremy@r1e:/proc/acpi/video/VGA/LCDD$ ./brightness
bash: ./brightness: Permission denied
jeremy@r1e:/proc/acpi/video/VGA/LCDD$ sudo ./brightness
sudo: unable to execute ./brightness: Permission denied


edit - chmod 777 worked.  Problem solved!

---

### Post by Jack the R on 2008-08-16
Great - problem not solved after all!  Brightness reverts back to its original permissions on reboot.  WTF.

O.K., how can I set permissions on brightness so that it stays 777 PERMANENTLY?  Or at least until I decide to change it back.

---

### Post by Sycron on 2008-08-17
Go to System->Preferences->Sessions->Startup Programs->Add

And add the **chmod 777** and the **./brightness**. Hope it works.

---

### Post by Jack the R on 2008-08-17
Chmod has to be run as super user.  I've tried running chmod from a script and entering the command straight into the startup program command line, with and without sudo, it gets ignored either way.  

I found this - 

> Retaining Manual Brightness Edits

The default level of brightness that Ubuntu uses whenever it boots up is stored in brightness_default. No matter what you change the brightness file entry to, the next time you start your computer, it's going to use the default brightness again. To change this default brightness to the level you want, issue the following command, replacing the # with any number between 1 and 8:

# sudo echo "#" > /proc/acpi/sony/brightness_default

[Link](https://help.ubuntu.com/community/SonyVaioBrightness)

But there is no brightness_default in my /proc/acpi/video/VGA/LCDD/ (where brightness lives on my machine).  I ran "find brightness_default" and also got nothing. 

Thanks for your help.

---

