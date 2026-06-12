---
title: "problems in wine , poser  7 don't find my system"
date: 2008-07-25
forum: General Help
---

### Post by bambanx on 2008-07-25
I re install all poser 7 and wine , give this error in :
gatito@gatito:~$ WINEDEBUG=warn+all wine poser.exe
warn:ntdll:NtCreateFile L"\\??\\C:\\windows" not found (c0000035)
warn:ntdll:NtCreateFile L"\\??\\C:\\windows\\system32" not found (c0000035)
warn:file:wine_nt_to_unix_file_name L"poser.exe" not found in /home/gatito/.wine/dosdevices/h:
warn:ntdll:NtQueryFullAttributesFile L"\\??\\H:\\poser.exe" not found (c0000034)
warn:file:wine_nt_to_unix_file_name L"poser.exe" not found in /home/gatito/.wine/dosdevices/c:/windows/system32
warn:ntdll:NtQueryFullAttributesFile L"\\??\\C:\\windows\\system32\\poser.exe" not found (c0000034)
warn:file:wine_nt_to_unix_file_name L"poser.exe" not found in /home/gatito/.wine/dosdevices/c:/windows/system
warn:ntdll:NtQueryFullAttributesFile L"\\??\\C:\\windows\\system\\poser.exe" not found (c0000034)
warn:file:wine_nt_to_unix_file_name L"poser.exe" not found in /home/gatito/.wine/dosdevices/c:/windows
warn:ntdll:NtQueryFullAttributesFile L"\\??\\C:\\windows\\poser.exe" not found (c0000034)
warn:file:wine_nt_to_unix_file_name L"poser.exe" not found in /home/gatito/.wine/dosdevices/c:/windows/system32
warn:ntdll:NtQueryFullAttributesFile L"\\??\\C:\\windows\\system32\\poser.exe" not found (c0000034)
warn:file:wine_nt_to_unix_file_name L"poser.exe" not found in /home/gatito/.wine/dosdevices/c:/windows
warn:ntdll:NtQueryFullAttributesFile L"\\??\\C:\\windows\\poser.exe" not found (c0000034)
warn:file:wine_nt_to_unix_file_name L"poser.exe" not found in /home/gatito/.wine/dosdevices/c:/windows/system32
warn:ntdll:NtCreateFile L"\\??\\C:\\windows\\system32\\poser.exe" not found (c0000034)
warn:module:load_builtin_dll cannot open .so lib for builtin L"poser.exe": /usr/bin/../lib32/wine/poser.exe.so: no se puede abrír el archivo de objeto compartido: No existe el fichero ó directorio
warn:module:load_dll Failed to load module L"C:\\windows\\system32\\poser.exe"; status=c0000135
wine: could not load L"C:\\windows\\system32\\poser.exe": Module not found
gatito@gatito:~$ 
any body help pls

---

### Post by nikgare on 2008-07-25
This might help:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7598&iTestingId=12592](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7598&iTestingId=12592)

---

