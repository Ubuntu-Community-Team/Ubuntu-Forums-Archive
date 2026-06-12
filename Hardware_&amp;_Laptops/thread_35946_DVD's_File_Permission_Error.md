---
title: "DVD's File Permission Error"
date: 2005-05-21
forum: Hardware &amp; Laptops
---

### Post by Kemotaha on 2005-05-21
I am getting this realy strange error.  I just got a Pioneer 120S DVDROM Drive.  I installed and it works great except that it gives this error when trying to access a Data DVD (ie. FARCRY) :

You do not have the permissions necessary to view the contents of "cdrom0".

The funny part is that it works fine if it is a Data CD.  It mounts and reads the file just fine.  Any Ideas?

---

### Post by Gangus on 2007-11-09
I'm having the same problem, upon going to a terminal and performing a sudo su can browse to the contents of the drive, seems that the files belong to user 401, who doesn't exist...  

Here's an output from a directory listing as root:
root@Valgur:/home/gangus# ls -lrt /media/cdrom/
total 16809
-rwx------ 1 400 401 1708856 2002-03-12 03:45 instmsia.exe
-rwx------ 1 400 401 1822520 2002-03-12 04:06 instmsiw.exe
-rwx------ 1 400 401  126976 2002-10-01 07:33 Launch_ITA.exe
-rwx------ 1 400 401  126976 2002-10-01 07:33 Launch_FRA.exe
-rwx------ 1 400 401  126976 2002-10-01 07:33 Launch_ESP.exe
-rwx------ 1 400 401  126976 2002-10-01 07:33 Launch_ENU.exe
-rwx------ 1 400 401  126976 2002-10-01 07:33 Launch_ENG.exe
-rwx------ 1 400 401  824320 2003-11-12 04:32 ISScript9.Msi
-rwx------ 1 400 401    5463 2004-08-31 03:26 0x040c.ini
-rwx------ 1 400 401    5169 2004-08-31 03:28 0x0410.ini
-rwx------ 1 400 401    5308 2004-08-31 03:30 0x040a.ini
-rwx------ 1 400 401    4581 2005-07-16 03:20 0x0409.ini
-rwx------ 1 400 401    4581 2005-07-16 03:21 0x0809.ini
-rwx------ 1 400 401    4581 2005-09-08 10:48 0x0411.ini
-rwx------ 1 400 401  276276 2005-10-20 09:50 Splash.bmp
-rwx------ 1 400 401     380 2006-02-25 13:39 Launch_ENG.ini
-rwx------ 1 400 401     380 2006-02-25 13:39 Launch_ENU.ini
-rwx------ 1 400 401     380 2006-02-25 13:40 Launch_ESP.ini
-rwx------ 1 400 401     380 2006-02-25 13:41 Launch_FRA.ini
-rwx------ 1 400 401     380 2006-02-25 13:41 Launch_ITA.ini
-rwx------ 1 400 401     139 2006-02-25 13:43 autorun.inf
-rwx------ 1 400 401     292 2006-03-31 13:24 version.inf
drwx------ 7 400 401    2048 2006-03-31 13:24 Docs
drwx------ 2 400 401    2048 2006-03-31 13:24 DirectX
-rwx------ 1 400 401  229376 2006-03-31 13:25 setup.exe
drwx------ 4 400 401    2048 2006-03-31 13:25 Setup
-rwx------ 1 400 401  606208 2006-03-31 13:29 2057.mst
-rwx------ 1 400 401  607232 2006-03-31 13:29 1041.mst
-rwx------ 1 400 401  945152 2006-03-31 13:29 1040.mst
-rwx------ 1 400 401  952832 2006-03-31 13:29 1036.mst
-rwx------ 1 400 401  947200 2006-03-31 13:29 1034.mst
-rwx------ 1 400 401  606208 2006-03-31 13:29 1033.mst
-rwx------ 1 400 401    1287 2006-03-31 13:29 Setup.ini
-rwx------ 1 400 401 7007868 2006-03-31 13:29 Doom 3.msi

(Yes it's Doom3 :P)
Any help would be greatly appreciated
Gangus

---

