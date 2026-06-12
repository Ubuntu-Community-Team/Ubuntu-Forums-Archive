---
title: "xbmc iso files not working properly"
date: 2008-11-09
forum: General Help
---

### Post by Periswell on 2008-11-09
hello

i copied the iso off of a dvd (harry potter and the order of the phoenix) using k3b but when i went into xbmc, it would get half way through the warner brothers logo then crash (xbmc would close and the mouse won't work untill i go back into xbmc and close it properly). i tried ripping it with k9copy and the same thing happened. i ran xbmc in the terminal and this is what it said:
> xbjoshua@MediaBox:~$ xbmc
xbmc.bin: vm.c:1493: process_command: Assertion `0' failed.
Aborted (core dumped)

 any ideas?
im running ubuntu 8.04 and the new xbmc (cant remember the name)

-joshua

---

### Post by TryMe on 2009-04-14
I know this is an old post but I was having the same issue. I fix it by increasing the "Video/Audio/DVD - HardDisk" cache setting to 2048kb from 256kb. Setting is found in menu  Settings->Cache->Video/Audio/DVD - HardDisk 

I believe the cause (at least for me) is that I had the ISO located in mounted network smb shares and linux sees mounted shares as local disk. After changing this setting I haven't had an issue. Only been a week so we'll see.

---

