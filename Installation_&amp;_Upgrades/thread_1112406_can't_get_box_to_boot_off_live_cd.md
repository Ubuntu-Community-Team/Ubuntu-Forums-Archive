---
title: "can't get box to boot off live cd"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by psanf on 2009-03-31
i have an old 500mhz box that i'm trying to install ubuntu from with a live cd. the problem is that the box can't boot from the cd-rom drive, and i need a floppy that i can use to get it to do so. does anyone know how i go about making this floppy with winXP? i've tried a couple of the rawwrite utilities around, but none of them seem to work. any help would be much appreciated.

---

### Post by kestrel1 on 2009-03-31
To be honest you would be lucky to get Ubuntu running on a 500mhz CPU. I would be looking at a linux version that would work better on that hardware. Puppy is good as is DSL.

---

### Post by Pumalite on 2009-03-31
If you have 256 MB of RAM or less; try the Alternate CD. You also can try:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
If not; try Puppy or DSL

---

### Post by kestrel1 on 2009-03-31
Also have a look at this for floppy help: [http://www.linuxmigration.com/quickref/install/media.html](http://www.linuxmigration.com/quickref/install/media.html)

---

### Post by psanf on 2009-03-31
that would be great, except that i need a floppy disk in to boot off of first.

---

### Post by Coreigh on 2009-03-31
Kestrel1~ baloney! Ubuntu will run fine (NOT fast) on that computer if it has 256MB ram or more.

To get older computers to boot off the liveCD I have had to use safe or VGA mode with --noapic and ACPI=OFF in the boot arguments. This will get a lot of them going, but there will still be some that will not. The alternate CD is also a good idea. And finally there are CD-less install options available.
check this info:
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

It is true that the full Ubuntu Desktop will slow this older machine down. You may want to try Xubuntu or a bare install with only the base system and a simple xorg and window manager like Fluxbox

After a base install or use Ubuntu Server
```
sudo apt-get install fluxbox xdm numlockx xterm xserver-xorg-core xfonts-base

```

get familiar with the terminal and command line

---

### Post by lisati on 2009-03-31
> **psanf said:**
> i have an old 500mhz box that i'm trying to install ubuntu from with a live cd. the problem is that the box can't boot from the cd-rom drive, and i need a floppy that i can use to get it to do so. does anyone know how i go about making this floppy with winXP? i've tried a couple of the rawwrite utilities around, but none of them seem to work. any help would be much appreciated.
[Smart Boot Manager]("http://sourceforge.net/projects/btmgr/") might be of some help. One of the downloads is a Windoes exe file that will write the necessary info to a floppy

---

### Post by psanf on 2009-03-31
i've tried all of those various programs, but i'm not sure which img file i need to put onto the floppy with it. i tried the /install/smb.bin file on the cd, but it didn't work.

---

### Post by lisati on 2009-03-31
> **psanf said:**
> i've tried all of those various programs, but i'm not sure which img file i need to put onto the floppy with it. i tried the /install/smb.bin file on the cd, but it didn't work.

If you want to create a boot floppy from Windows, download sbminst.exe from [http://sourceforge.net/project/showfiles.php?group_id=4185&package_id=4201&release_id=25481](http://sourceforge.net/project/showfiles.php?group_id=4185&package_id=4201&release_id=25481) and run it.

---

### Post by kestrel1 on 2009-04-01
> Coreigh: Kestrel1~ baloney! Ubuntu will run fine (NOT fast) on that computer if it has 256MB ram or more.
I have Ubuntu running on a 1300mhz CPU with 512mb ram & it still runs a bit slow.
For older equipment, you are better off getting the most out of it or you would soon get fed up with Linux, so running an OS that would run a lot faster is a far better idea than trying to get something running that would be like a tortoise on ice.

---

