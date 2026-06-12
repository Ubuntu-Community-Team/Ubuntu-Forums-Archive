---
title: "Kopete Crash and Reboot Hardy"
date: 2008-08-18
forum: General Help
---

### Post by sangprabv on 2008-08-18
I dont know if Im alone with this issue or not. I have Kopete on Hardy which is installed on Dell D620. Kopete launched well, but after sometimes when a new message popup it crashed and reboot Hardy. Is there any solution? TIA

---

### Post by satir.satir on 2008-08-18
just use QIP:  [http://forum.qip.ru/showthread.php?t=4876](http://forum.qip.ru/showthread.php?t=4876)
or this:
1 install wine
2. install QIP_8070.exe or later
3. create new file  
```
sudo gedit QIP
```
 in new file: full path to QIP.exe :  ```
 d /home/satir/.wine/drive_c/Program\ Files/QIP
wine C:\\Program\ Files\\QIP\\qip.exe /oldgif
```
```
chown -x QIP
```
create new starter with full path to QIP
enjoy...:guitar:

Kopete!? first full uninstall and then reinstal.....

---

