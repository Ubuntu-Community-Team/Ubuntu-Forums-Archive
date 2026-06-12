---
title: "Reflecta Digitdia 5000 support?"
date: 2010-12-02
forum: Hardware
---

### Post by olof_ on 2010-12-02
Hello out there.
I am wondering if it is possible to get the scanner [Reflecta Digitdia 5000]("https://reflecta-shop.de/en/products/detail/~id.19~pcat.2/reflecta-DigitDia-5000.html") to work on Ubuntu. I am posting this as it seems that I am the first one having this problem.

[IMG]https://reflecta-shop.de/uploads/pictures/resized/20090810053624_65630_digitdia_800x600.jpg[/IMG]

Looking at the [sane supported device list]("http://www.sane-project.org/sane-mfgs.html") there is nothing about it at all.

I tried both simplescan (version 2.32.0) and xsane (version 0.997-2), and neither detects it. Tried both with and without sudo.

Edit: now also even tried with Skanlite (version 0.4-kde4.4.0-1), but still without any success.

using sane versions:
scanimage (sane-backends) 1.0.21; backend version 1.0.21

and, I am using ubuntu 10.10 x86 just to have all the details.

The driver which came with the scanner is called "Cyberview X Multiple-Slides Scanner v1.18a", and it is for both windows and macintosh edit: found that the latest driver was version 1.20, but that did not work either.

My output from lsusb looks like this:
```
nord-eliasson@nord-eliasson:~$ lsusb
Bus 005 Device 002: ID 1267:0103 Logic3 / SpectraVideo plc G-720 Keyboard
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0461:4d03 Primax Electronics, Ltd Kensington Mouse-in-a-box
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 14cd:121c Super Top 
*Bus 001 Device 004: ID 05e3:0142 Genesys Logic, Inc. Multiple Slides Scanner-3600*
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Is there any alternative programs avalabile, or at all any other solution than rebooting into windows? Also I read somewhere that wine couldn't handle usb peripherals, is that correct?

trying virtualbox atm, will post results later.

---

### Post by olof_ on 2010-12-02
seems like there is no option to share usb devices in virtualbox...
How should I be able to use virtualbox and my scanner then, if they cant discover eachother?
using virtualbox 3.2.8_OSE r64453

seems like this is not a problem that can be solved with virtualbox.

---

### Post by olof_ on 2010-12-02
tried with wine, but it does not work. (edit: using wine 1.2.1), edit2: also tried with wine 1.3.8, but still not working.

console output in wine 1.2.1:
```
nord-eliasson@nord-eliasson:/media/CyberView X-MS/Install/DiskImages/Disk1$ wine setup.exe 
nord-eliasson@nord-eliasson:/media/CyberView X-MS/Install/DiskImages/Disk1$ fixme:storage:create_storagefile Storage share mode not implemented.
fixme:shell:IShellLinkA_fnGetPath (0x150f210): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x150f210): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1517a90): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1517a90): WIN32_FIND_DATA is not yet filled.
fixme:setupapi:SetupSetNonInteractiveMode 1
fixme:propsheet:PROPSHEET_UnImplementedFlags PSH_STRETCHWATERMARK 
```

console output in wine 1.3.8:
```
nord-eliasson@nord-eliasson:~/Hämtningar$ wine 20101105021012_CyberView-X-MS-1.20-English.exe 
fixme:storage:create_storagefile Storage share mode not implemented.
fixme:shell:IShellLinkA_fnGetPath (0x126d3f8): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x126d3f8): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1273cd0): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1273cd0): WIN32_FIND_DATA is not yet filled.
fixme:setupapi:SetupSetNonInteractiveMode 1
fixme:propsheet:PROPSHEET_UnImplementedFlags PSH_STRETCHWATERMARK 
```

edit3: found that it was possible to run wine with debugmode on, so I [ran it again]("http://ubuntuone.com/p/S5o/") see linked log.

I get an error saying "Cannot Complete the Device Driver Wizard" when the installer tries to install "Windows Driver package - Multiple Slides Scanner Vendor (scsiscan) Image 10/22/2002 1.1.1"

---

### Post by olof_ on 2010-12-04
I filed a bug in the SANE bug tracker [here]("https://alioth.debian.org/tracker/index.php?func=detail&aid=312873&group_id=30186&atid=410366"), and also submitted it to wine appdatabase, [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=22162").

This is really the first issue i have had with ubuntu/linux that I really cant solve, it feels so bad...

---

### Post by olof_ on 2010-12-04
Just discovered that the program even managed to place two shortcuts in the C:\Users\Public\Startmenu\Program that wine finds. (they do not work)
they are called:
[LIST]
[*]CyberView X.lnk
[*]Help.lnk
[/LIST]
It also creates a folder, C:\Program\InstallShield Installation Information\{B455DA2A-531A-4456-BA1C-3534DD327EFE}\
with the following files:

[LIST]
[*]data1.cab
[*]data1.hdr
[*]entries
[*]ISSetup.dll
[*]layout.bin
[*]_setup.dll
[*]setup.exe
[*]setup.ilg
[*]setup.ini
[*]setup.inx
[*]setup.isn
[/LIST]

---

