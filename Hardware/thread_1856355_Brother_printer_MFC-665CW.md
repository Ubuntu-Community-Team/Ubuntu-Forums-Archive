---
title: "Brother printer MFC-665CW"
date: 2011-10-08
forum: Hardware
---

### Post by M3GAPL3X on 2011-10-08
Hi guys,

I recently tried to install a MFC-665CW driver for Ubuntu. Followed the instructions on Brother's website.

However, my main problem now lies when I try to install packages via dpkg. I get the following error:
[b]
ms@ms-MS-7622:~/Downloads$ sudo apt-get install rpm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[color=red]E: The package mfc665cwlpr needs to be reinstalled, but I can't find an archive for it.[/color]

I looked this error up and found some documentation. Here are the commands I have tried to remove the mfc665cwlpr driver:
**sudo dpkg --remove --force-remove-reinstreq mfc665cwlpr** which gives me the output:
[b]
ms@ms-MS-7622:~/Downloads$ sudo dpkg --remove --force-remove-reinstreq mfc665cwlpr
dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 146250 files and directories currently installed.)
Removing mfc665cwlpr ...
start: Unknown job: lpd
dpkg: error processing mfc665cwlpr (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 mfc665cwlpr
[/b]

I'm new to linux and am really stuck. Any links to documentation or a way to solve this issue would be greatly appreciated.

---

### Post by cjazz on 2011-10-08
Are you trying to install a driver with the extension rpm? If so, you've got the wrong file.

Brother typically offers its drivers in two formats -- rpm and deb. Linux distributions like Red Hat, Fedora and PCLinuxOS, among others use rpms. Ubuntu, Mint and Debian are among those that use debs. Download the driver with the correct extension.

However, a method I find much easier is to simply install the packages from the Ubuntu repositories. If you still have Synaptic, you can simply type the model of your printer into the search box, and the drivers pop up.

Or just open a terminal and enter

```
sudo apt-get install brother-lpr-drivers-bh7 brother-cups-wrapper-bh7
```

---

### Post by M3GAPL3X on 2011-10-08
> **cjazz said:**
> Are you trying to install a driver with the extension rpm? If so, you've got the wrong file.

Brother typically offers its drivers in two formats -- rpm and deb. Linux distributions like Red Hat, Fedora and PCLinuxOS, among others use rpms. Ubuntu, Mint and Debian are among those that use debs. Download the driver with the correct extension.

However, a method I find much easier is to simply install the packages from the Ubuntu repositories. If you still have Synaptic, you can simply type the model of your printer into the search box, and the drivers pop up.

Or just open a terminal and enter

```
sudo apt-get install brother-lpr-drivers-bh7 brother-cups-wrapper-bh7
```

Nope they were .deb packages when I first tried to installl. Now I can't install anything via apt get because of that error. I just want to remove that error and worry about reinstalling the drivers later.

---

### Post by cjazz on 2011-10-09
I'm sorry, obviously I misread your problem. What happens when you try to reinstall? (I hope I didn't misread that too.)

---

