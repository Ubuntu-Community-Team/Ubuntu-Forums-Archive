---
title: "help to install poser 7"
date: 2008-07-21
forum: General Help
---

### Post by bambanx on 2008-07-21
Hi i tray install poser 7 on wine 1.1.1 and my hardy heron 64 bits , the installation is fine , when i run it ., the screen is deform only can restart but i have a impr paint [http://img147.imageshack.us/img147/2600/pantallazo2cb1.png](http://img147.imageshack.us/img147/2600/pantallazo2cb1.png) , why deform my screen and the impr paint it's fine ? , well
apply gatito@gatito:~$ WINEDEBUG=warn+all wine poser.exe for debug and this is my lines :
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
warn:file:wine_nt_to_unix_file_name L"poser.exe" not found in /home/gatito/.wine/dosdevices/h:
warn:ntdll:NtQueryFullAttributesFile L"\\??\\H:\\poser.exe" not found (c0000034)
warn:file:wine_nt_to_unix_file_name L"poser.exe" not found in /home/gatito/.wine/dosdevices/c:/Archivos de programa/Archivos comunes/Adobe/AGL
warn:ntdll:NtQueryFullAttributesFile L"\\??\\C:\\Archivos de programa\\Archivos comunes\\Adobe\\AGL\\poser.exe" not found (c0000034)
warn:file:wine_nt_to_unix_file_name L"wineboot.exe" not found in /home/gatito/.wine/dosdevices/c:/windows/system32
warn:ntdll:NtQueryFullAttributesFile L"\\??\\C:\\windows\\system32\\wineboot.exe" not found (c0000034)
warn:file:wine_nt_to_unix_file_name L"wineboot.exe" not found in /home/gatito/.wine/dosdevices/c:/windows/system32
warn:ntdll:NtCreateFile L"\\??\\C:\\windows\\system32\\wineboot.exe" not found (c0000034)
warn:file:CreateFileW Unable to create file L"C:\\windows\\system32\\wineboot.exe" (status c0000034)
warn:ntdll:NtCreateFile L"\\??\\C:\\windows" not found (c0000035)
warn:ntdll:NtCreateFile L"\\??\\C:\\windows\\system32" not found (c0000035)
warn:file:wine_nt_to_unix_file_name L"wineboot.exe" not found in /home/gatito/.wine/dosdevices/c:/windows/system32
warn:ntdll:NtCreateFile L"\\??\\C:\\windows\\system32\\wineboot.exe" not found (c0000034)
warn:file:wine_nt_to_unix_file_name L"wineboot.exe.manifest" not found in /home/gatito/.wine/dosdevices/c:/windows/system32
warn:ntdll:NtCreateFile L"\\??\\C:\\windows\\system32\\wineboot.exe.manifest" not found (c0000034)
warn:file:wine_nt_to_unix_file_name L"wininit.ini" not found in /home/gatito/.wine/dosdevices/c:/windows
warn:ntdll:NtCreateFile L"\\??\\C:\\windows\\wininit.ini" not found (c0000034)
warn:file:CreateFileW Unable to create file L"C:\\windows\\wininit.ini" (status c0000034)
warn:profile:PROFILE_Open profile file L"C:\\windows\\wininit.ini" not found
warn:file:wine_nt_to_unix_file_name L"dllcache\\" not found in /home/gatito/.wine/dosdevices/c:/windows/system32
warn:ntdll:NtCreateFile L"\\??\\C:\\windows\\system32\\dllcache\\" not found (c0000034)
warn:file:wine_nt_to_unix_file_name L"services.exe" not found in /home/gatito/.wine/dosdevices/c:/windows/system32
warn:ntdll:NtCreateFile L"\\??\\C:\\windows\\system32\\services.exe" not found (c0000034)
warn:file:CreateFileW Unable to create file L"C:\\windows\\system32\\services.exe" (status c0000034)
warn:ntdll:NtCreateFile L"\\??\\C:\\windows" not found (c0000035)
warn:ntdll:NtCreateFile L"\\??\\C:\\windows\\system32" not found (c0000035)
warn:file:wine_nt_to_unix_file_name L"services.exe" not found in /home/gatito/.wine/dosdevices/c:/windows/system32
warn:ntdll:NtCreateFile L"\\??\\C:\\windows\\system32\\services.exe" not found (c0000034)
warn:file:wine_nt_to_unix_file_name L"services.exe.manifest" not found in /home/gatito/.wine/dosdevices/c:/windows/system32
warn:ntdll:NtCreateFile L"\\??\\C:\\windows\\system32\\services.exe.manifest" not found (c0000034)
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\windows\\system32\\iphlpapi.dll": /home/gatito/.wine/dosdevices/c:/windows/system32/iphlpapi.dll: cabecera ELF inválida
warn:file:wine_nt_to_unix_file_name L"winedevice.exe" not found in /home/gatito/.wine/dosdevices/c:/windows/system32
warn:ntdll:NtQueryFullAttributesFile L"\\??\\C:\\windows\\system32\\winedevice.exe" not found (c0000034)
warn:file:wine_nt_to_unix_file_name L"winedevice.exe" not found in /home/gatito/.wine/dosdevices/c:/windows/system32
warn:ntdll:NtCreateFile L"\\??\\C:\\windows\\system32\\winedevice.exe" not found (c0000034)
warn:file:CreateFileW Unable to create file L"C:\\windows\\system32\\winedevice.exe" (status c0000034)
warn:ntdll:NtCreateFile L"\\??\\C:\\windows" not found (c0000035)
warn:ntdll:NtCreateFile L"\\??\\C:\\windows\\system32" not found (c0000035)
warn:file:wine_nt_to_unix_file_name L"winedevice.exe" not found in /home/gatito/.wine/dosdevices/c:/windows/system32
warn:ntdll:NtCreateFile L"\\??\\C:\\windows\\system32\\winedevice.exe" not found (c0000034)
warn:file:wine_nt_to_unix_file_name L"winedevice.exe.manifest" not found in /home/gatito/.wine/dosdevices/c:/windows/system32
warn:ntdll:NtCreateFile L"\\??\\C:\\windows\\system32\\winedevice.exe.manifest" not found (c0000034)
warn:file:wine_nt_to_unix_file_name L"ntoskrnl.exe" not found in /home/gatito/.wine/dosdevices/c:/windows/system32
warn:ntdll:NtQueryFullAttributesFile L"\\??\\C:\\windows\\system32\\ntoskrnl.exe" not found (c0000034)
warn:file:wine_nt_to_unix_file_name L"ntoskrnl.exe" not found in /home/gatito/.wine/dosdevices/c:/windows
warn:ntdll:NtQueryFullAttributesFile L"\\??\\C:\\windows\\ntoskrnl.exe" not found (c0000034)
warn:file:wine_nt_to_unix_file_name L"ntoskrnl.exe" not found in /home/gatito/.wine/dosdevices/c:/windows/system32
warn:ntdll:NtQueryFullAttributesFile L"\\??\\C:\\windows\\system32\\ntoskrnl.exe" not found (c0000034)
warn:file:wine_nt_to_unix_file_name L"ntoskrnl.exe" not found in /home/gatito/.wine/dosdevices/c:/windows/system
warn:ntdll:NtQueryFullAttributesFile L"\\??\\C:\\windows\\system\\ntoskrnl.exe" not found (c0000034)
warn:file:wine_nt_to_unix_file_name L"ntoskrnl.exe" not found in /home/gatito/.wine/dosdevices/c:/windows
warn:ntdll:NtQueryFullAttributesFile L"\\??\\C:\\windows\\ntoskrnl.exe" not found (c0000034)
warn:file:wine_nt_to_unix_file_name L"ntoskrnl.exe" not found in /home/gatito/.wine/dosdevices/c:/windows/system32
warn:ntdll:NtQueryFullAttributesFile L"\\??\\C:\\windows\\system32\\ntoskrnl.exe" not found (c0000034)
warn:file:wine_nt_to_unix_file_name L"ntoskrnl.exe" not found in /home/gatito/.wine/dosdevices/c:/windows
warn:ntdll:NtQueryFullAttributesFile L"\\??\\C:\\windows\\ntoskrnl.exe" not found (c0000034)
warn:file:wine_nt_to_unix_file_name L"ntoskrnl.exe" not found in /home/gatito/.wine/dosdevices/c:/windows
warn:ntdll:NtQueryFullAttributesFile L"\\??\\C:\\windows\\ntoskrnl.exe" not found (c0000034)
warn:file:wine_nt_to_unix_file_name L"ntoskrnl.exe" not found in /home/gatito/.wine/dosdevices/c:/Archivos de programa/Archivos comunes/Adobe/AGL
warn:ntdll:NtQueryFullAttributesFile L"\\??\\C:\\Archivos de programa\\Archivos comunes\\Adobe\\AGL\\ntoskrnl.exe" not found (c0000034)
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\windows\\system32\\iphlpapi.dll": /home/gatito/.wine/dosdevices/c:/windows/system32/iphlpapi.dll: cabecera ELF inválida
warn:sync:SetNamedPipeHandleState stub: 0x24 0x7edc95b8/2 (nil) (nil)
warn:module:load_builtin_dll failed to load .so lib for builtin L"C:\\windows\\system32\\msvcrt.dll": /home/gatito/.wine/dosdevices/c:/windows/system32/msvcrt.dll: cabecera ELF inválida
warn:msvcrt:msvcrt_init_console :Console handle Initialisation FAILED!
warn:file:wine_nt_to_unix_file_name L"poser.exe" not found in /home/gatito/.wine/dosdevices/c:/windows/system32
warn:ntdll:NtCreateFile L"\\??\\C:\\windows\\system32\\poser.exe" not found (c0000034)
warn:module:load_builtin_dll cannot open .so lib for builtin L"poser.exe": /usr/bin/../lib32/wine/poser.exe.so: no se puede abrír el archivo de objeto compartido: No existe el fichero ó directorio
warn:module:load_dll Failed to load module L"C:\\windows\\system32\\poser.exe"; status=c0000135
wine: could not load L"C:\\windows\\system32\\poser.exe": Module not found
gatito@gatito:~$ warn:profile:PROFILE_FlushFile No current profile!
warn:rpc:RPCRT4_SendWithAuth rpcrt4_conn_write failed (auth)
warn:profile:PROFILE_FlushFile No current profile!


what i need install for run poser 7 ?

for any help thanks very much

PD: sorry my english is bad

---

### Post by Uchiha_madara on 2008-07-21
hi,
with My Expierence in wine , i have to tell you two 
Probablities :

1 - Update your Wine version to wine 1.1.1.
    Because this version has got good ability to install heavy   Application's such as Adobe photoshop cs3.


2 - Or Poser is very heavy that wine cannot install it for you

---

### Post by bambanx on 2008-07-21
men , you don't read my post , i install in wine 1.1.1  . XD

---

