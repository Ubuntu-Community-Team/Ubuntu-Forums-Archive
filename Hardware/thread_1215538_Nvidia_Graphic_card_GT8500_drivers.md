---
title: "Nvidia Graphic card GT8500 drivers"
date: 2009-07-17
forum: Hardware
---

### Post by rbahati on 2009-07-17
Hello everybody,

I'm actually having a problem with my Nvidia graphic card GT8500 series. I'd like to use enhanced graphical features in Ubuntu but i unfortunately can't do it.
I'd already been to the hardware compatibility dialogue to download the driver from there, but after a little while it fails. 
PLEASE CAN ANYONE OUT THERE HELP ME :sad: AS THAT WILL BE VERY MUCH APPRECIATED.

THANKS IN ADVANCE.

---

### Post by DownTown22 on 2009-07-17
I have also have an 8500GT card.

To get the "enhanced graphical features in Ubuntu" I had to use the drivers available via the restricted drivers - the actual driver wasn't available to me after initial installation, but after running all updates available and after a reboot it was.

Actually, a notification appeared in the top panel letting me know that restricted drivers were available.  After clicking on the icon or the message window (don't remember which) I was able to choose which driver I wanted, it installed and after a reboot, my resolution was what it should be and all "enhanced graphical features" worked.

---

### Post by khelben1979 on 2009-07-17
[URL="http://www.nvidia.com/object/linux_display_ia32_185.18.14.html"]Linux Display Driver - x86

Version: 185.18.14
Operating System: Linux x86
Release Date: June 05, 2009[/URL]

or

[URL="http://www.nvidia.com/object/linux_display_amd64_185.18.14.html"]Linux x64 (AMD64/EM64T)

Version: 185.18.14
Operating System: Linux x64 (AMD64/EM64T)
Release Date: June 05, 2009[/URL] 

Try the driver from above if all else fails and don't forget to kill off the x server before proceeding and running the script with root permissions using the sudo command.

```
man top
``` and ```
man kill
```
will give you information on how to use these commands and you're going to need to find the process number for the x server and if you have some GDM processes in there too.

---

