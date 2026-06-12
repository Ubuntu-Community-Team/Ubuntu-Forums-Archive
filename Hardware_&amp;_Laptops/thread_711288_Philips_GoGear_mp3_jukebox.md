---
title: "Philips GoGear mp3 jukebox"
date: 2008-02-29
forum: Hardware &amp; Laptops
---

### Post by Kreuger on 2008-02-29
I know of PyGoGear and OpenGoGear for managing files on my mp3 player but I decided to try using the software that came with it for Windows through Wine. However, Whenever I try to run the program, it says "This application cannot be started" The terminal output shows:

> kreuger@kreuger-desktop:~/.wine/drive_c/Program Files/Philips/PCDMM$ wine PCDmm.exe
err:winedevice:ServiceMain driver L"AFS2K" failed to load
fixme:spoolsv:serv_main (0 (nil))
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 8000000a
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\PROG~FBU\\Philips\\PHIL~HPK\\Modules\\PPDM~VAS.DLL"
err:ole:create_server class {5010a245-e2f7-4d72-bff2-cf0f74760393} not registered
err:ole:CoGetClassObject no class object {5010a245-e2f7-4d72-bff2-cf0f74760393} could be created for context 0x5
[email]kreuger@kreuger-desktop:~/.wine[/email]/drive_c/Program Files/Philips/PCDMM$

Before it was giving me problems about permissions on a drive that I wasn't even aware I had. /dev/sdf or something. When I checked fdisk it showed the mp3 player as /dev/sdb1 so I was confused. Now this is what comes up and I have no idea what to do.

---

