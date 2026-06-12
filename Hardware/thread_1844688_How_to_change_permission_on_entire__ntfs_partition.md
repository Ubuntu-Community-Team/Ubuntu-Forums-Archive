---
title: "How to change permission on entire  ntfs partition"
date: 2011-09-15
forum: Hardware
---

### Post by Waidas on 2011-09-15
Hi,

On me laptop I have tree partitions: two ntfs and one ext4. In one of ntfs partition I'm keeping all windows applications. On linux I have installed wine, but then I'm trying to load one or other windows application it shows me error that execute bit is not set. So I tried set it, but I can't. When application is in ext4 partition, I easily can set that bit and wine is working. So, how I can change ntfs permission, that allow me to set exetuce bit?

Thanks for your help :)

---

### Post by oldfred on 2011-09-15
NTFS  does not support Linux permissions & ownership so there is no bit to set. Not sure if you set everything to executable, which is not recommended anyway, if it would work. If you set everything to executable you open up to virus' and other issues. Big part of why Linux is more secure than NTFS.

I just copied Windows version of Saving Bond Wizard into Wine programs and installed it there. Then it worked and I was able to load my data files from my shared NTFS partition without issue.

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by Morbius1 on 2011-09-15
> On linux I have installed wine, but then I'm trying to load one or other  windows application it shows me error that execute bit is not set.The irony of it all is that there is no way Wine can determine or even cares if a given *.exe file has a Linux executable bit set. The problem is something called "cautious launcher".

Here's three ways to fix it:
> **[1] Run it from the terminal:**
```
wine "/path/to/exe/file" 
```**[2] Fix the file association:**
Right click an *.exe file and select Properties  -> Open With -> Add -> Use a custom command > type in:  wine

In the "Open With" tab mark the "wine"[COLOR=Black] [COLOR=Blue]**you added**[/COLOR] [/COLOR]as   the default ( from the Wine that's already selected) and every time  you run an exe it should select the wine without the cautious  launcher  script.

**[3] Fix it at it's source:**
Open up as root "Properties" on /usr/share/applications/wine. 

What you will see is this:
[QUOTE]cautious-launcher %f wine start /unix                                 Change it to this:
```
wine start /unix 
```I would go with option [2] myself. I don't like messing with system files unless I really have to.[/QUOTE]

---

### Post by Waidas on 2011-09-15
Nice :) I have tried this
 
> [2] Fix the file association:
Right click an *.exe file and select Properties -> Open With -> Add -> Use a custom command > type in: wine

In the "Open With" tab mark the "wine" you added as the default ( from the Wine that's already selected) and every time you run an exe it should select the wine without the cautious launcher script.

 and it works for me :)

Thanks :)

---

