---
title: "Seagate expansion 320 gb drive cannot be mounted"
date: 2011-08-25
forum: Hardware
---

### Post by paul98 on 2011-08-25
I bought a Seagate Expansion 320 gb drive about two months ago, but I use it quite rarely. However, it worked in the past, and I was able to transfer a lot of files from my hard disk. I tried to do the same thing today, and it mounted. However, in the middle of transferring files, it suddenly stopped, and then I saw this message: 
[INDENT]Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

[/INDENT]I tried restarting the computer and reconnecting the device twice. It still would not mount. I attached a picture so you can get a better idea of the problem. Please help me, as I am no computer expert. Thanks. [ATTACH]200799[/ATTACH]

---

### Post by jerrrys on 2011-08-26
i have no answer for you, but you may have luck finding one here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=exit+code+13&sa=Search&cof=FORID:9#791](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=exit+code+13&sa=Search&cof=FORID:9#791)

---

### Post by coffeecat on 2011-08-26
The answer is in the error message.

> **paul98 said:**
> NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important!

Since you've been able to use it before, then we can assume it's not a fakeraid, which leaves a hardware fault or a NTFS filesystem inconsistency. I'd put my money on the latter. NTFS is a Microsoft filesystem so you need a use a Microsoft utility to repair it - chkdsk. There is no Linux utility that can do what chkdsk can do - the terminal command ntfsfix will not solve this.

Do you have access to a Windows system? You need to attach the Seagate drive to a Windows system and run chkdsk from a command prompt or whatever graphical utility Windows uses.

Ubuntu will not mount a damaged filesystem as a failsafe in order to prevent further damage.

---

### Post by paul98 on 2011-08-27
Thanks for the help, guys! Will try to get access to a Windows computer. I haven't had a lot of time just yet to read the Googlubuntu sites, but thanks for that resource as well. :)

---

