---
title: "unable to see/mount DVDRW on my laptop"
date: 2007-07-28
forum: Hardware &amp; Laptops
---

### Post by abadfish on 2007-07-28
My computer is a Dell Latitude D830 dual-boot w/ Vista and Ubuntu 7.04.

I'm unable to mount my DVDRW drive.

Here is  etc/fstab:

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=9b7fd845-b9e3-45a1-ad53-3c8c679b9265 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=07D7-0714  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=6E8074A980747A03 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=929AF7E19AF7BFB1 /media/sda3     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=7A56B32C588DA4C1 /media/sda7     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=fb130f6c-fc15-49d3-baaa-9a2887d949df none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0


when I try to mount, it says:

mount: special device /dev/hda does not exist


From advice in other threads, I've done:

% dmesg | grep CD

That produces nothing.

I've also done lshw, and it doesn't show the drive.

Obviously the drive works because I was able to install Ubuntu from it (plus, it works in Windows Vista no problem).

Any thoughts?  I need to get the drive working because when I try to install a package (build-essential), its asking me to insert the install disk in the drive.

---

### Post by vwaj on 2007-07-28
i'm having the exact same issue and would very much like to see this solved.  i too have a latitude d830 dual boot with vista/ubuntu 7.04.  the last line of my fstab is identical to yours, and dmesg | grep CD produces nothing for me.

if you want to install build-essential, though, you can get it from the online repositories.  just go to synaptic, settings -> repositories and then deselect the cdrom options.

don't abandon this thread though...you'll eventually need your cd working!  and i need mine working!

---

### Post by abadfish on 2007-07-29
> **vwaj said:**
> 
if you want to install build-essential, though, you can get it from the online repositories.  just go to synaptic, settings -> repositories and then deselect the cdrom options.


Thank you for that tip.  You don't know how many hours of frustration I've spent all day today trying to load packages just so that I can get gcc to work.  I was very close to giving up on this distro and going with another.  Now I'm finally building GTK.  whew!!


Since we have the same computer, were you able to get the wireless card to work??  I have the Intel 4965 card on mine.  Its not recognized with the 2.6.20 kernel.  There is a fix posted that requires you to use the 2.6.22 kernel.  It works but then I lose my sound card.  I think I may wait for a more stable kernel to come out rather than compromise something else on my system.  Hopefully, they'll get that problem squared away soon.  In the meantime, I'll either go with a wired internet connection or just use Vista for a wireless connection.

---

### Post by Syke on 2007-07-29
The D830 is a Santa Rosa-based system. Sometimes you need to add "piix" to /etc/modules.

```
sudo gedit /etc/modules
```

and add

```
piix
```

to the end of the file. Save, exit, and reboot. Hopefully that will re-enable your drive.

---

### Post by vwaj on 2007-07-29
> The D830 is a Santa Rosa-based system. Sometimes you need to add "piix" to /etc/modules.
Thanks a lot Syke -- that did the trick.

> Since we have the same computer, were you able to get the wireless card to work?? I have the Intel 4965 card on mine. Its not recognized with the 2.6.20 kernel.
That's weird.  I managed to get my wireless working, and I'm using the 2.6.20 kernel.  I too have the 4965 card.  If I remember correctly, I roughly followed the instructions at [https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty](https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty) (that uses the Windows drivers and ndiswrapper).  I believe Intel has created Linux drivers for this card too -- you could look into that for a more elegant solution.

---

### Post by abadfish on 2007-07-29
Skye, thanks.... you just saved my laptop's life :)

> **vwaj said:**
> That's weird.  I managed to get my wireless working, and I'm using the 2.6.20 kernel.  I too have the 4965 card.  If I remember correctly, I roughly followed the instructions at [https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty](https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty) (that uses the Windows drivers and ndiswrapper).  
I'll give this a try.

> 
I believe Intel has created Linux drivers for this card too -- you could look into that for a more elegant solution.
This was the solution I mentioned earlier.  The linux driver requires the use of 2.6.22 and when I migrate to that kernel, I lose my sound card.

---

### Post by mikko_i on 2007-07-31
Thanks! 
I had exactly the same problem with my cdrom.

---

### Post by ThanhBT on 2007-10-21
I has same problem.
```
# dmesg | grep CD
[    0.000000] ACPI: SSDT 3F69CD6A, 0692 (r1 SataRe  SataSec     1000 INTL 20030224)
[    4.708000] scsi 1:0:1:0: CD-ROM            PIONEER  DVD-RW  DVR-K16D 1.00 PQ: 0 ANSI: 5
[    4.908000] Uniform CD-ROM driver Revision: 3.20
[    4.908000] sr 1:0:1:0: Attached scsi CD-ROM sr0
```

Someone help me to mount my dvd plz.

---

