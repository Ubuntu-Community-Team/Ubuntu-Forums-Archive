---
title: "USB sticks/camera fail to mount after upgrade"
date: 2008-05-07
forum: Hardware
---

### Post by keirlawson on 2008-05-07
They show up in the "Places" menu, but don't appear on the desktop, and when I click on them, no window appears.  I think it might be a problem with HAL as when i click on "Removable Drives and Media" in Preferences, i get: ```
The "hald" service is required but not currently running. Enable the service and rerun this application, or contact your system administrator.
```

However, ps -A | grep hal yields:

```
keir@squall:~$ ps -A | grep hal
 5292 ?        00:00:00 hald
 5357 ?        00:00:00 hald-runner
 5370 ?        00:00:00 hald-addon-inpu
 5380 ?        00:00:00 hald-addon-cpuf
 5381 ?        00:00:00 hald-addon-acpi
 5403 ?        00:00:00 hald-addon-stor
 5407 ?        00:00:00 hald-addon-stor
```

Any idea what the problem could be?

---

### Post by demercel on 2008-05-07
try 
```
sudo apt-get install --reinstall hal
sudo dpkg-reconfigure hal
sudo reboot

```
Solution taken from and more info here: [http://ubuntuforums.org/showthread.php?t=692817](http://ubuntuforums.org/showthread.php?t=692817)

---

### Post by keirlawson on 2008-05-07
Unfortunately that doesn't seem to work, the problem persists.

---

