---
title: "Running WINE and Microsoft Project"
date: 2005-11-10
forum: General Help
---

### Post by laiyf on 2005-11-10
I have Microsoft Project installed on NTFS drive. The drive is mounted as 'read-only'.

I used winecfg to add a library "d:\windows\system32" (native) to the Library tab. After running the following command:

wine WINPROJ.EXE

The following error messages appear:

err:module:import_dll Library COMMTB32.dll (which is needed by L"E:\\Program Files\\Microsoft Office\\Office\\WINPROJ.EXE") not found
err:module:LdrInitializeThunk Main exe initialization for L"E:\\Program Files\\Microsoft Office\\Office\\WINPROJ.EXE" failed, status c0000135

Is it that my setting is incorrect? The COMMTB32.dll is in d:\windows\system32\ directory.

---

### Post by darknuala on 2005-11-16
what version of Project are you trying?

---

### Post by laiyf on 2005-11-17
Microsoft Project 98

---

