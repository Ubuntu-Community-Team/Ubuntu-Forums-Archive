---
title: "Battery Recall Checker in Wine?"
date: 2008-11-12
forum: Hardware
---

### Post by williamHH on 2008-11-12
My Toshiba M35X's battery just got recalled, and their website won't accept the battery serial number. Customer service told me to download and run batterycheck.exe, a windows program that's supposed to automate the process. I get this:
```
william@comp:~/Desktop/battcheck$ wine BatteryCheck.exe
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\william\\Desktop\\battcheck\\EBLib.dll") not found
err:module:import_dll Library EBLib.dll (which is needed by L"Z:\\home\\william\\Desktop\\battcheck\\BatteryCheck.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\william\\Desktop\\battcheck\\BatteryCheck.exe" failed, status c0000135
```
I also have no way of running windows as the CD drive is broken.

---

