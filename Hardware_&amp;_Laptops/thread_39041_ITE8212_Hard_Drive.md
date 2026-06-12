---
title: "ITE8212 Hard Drive"
date: 2005-06-03
forum: Hardware &amp; Laptops
---

### Post by gibbylinks on 2005-06-03
Hi,
 I'm a newbie to Ubuntu having migrated from FD3. I'm having a problem with one of my hard drives, it's connected to my onboard ITE8212 raid. 

Ubuntu (Hoary Hedgehog) has correctly detected the ITE8212 but I can't see the drive, can anyone give me any pointers ?

Cheers

 :-)

---

### Post by jeremy on 2005-06-03
is the drive listed in /etc/fstab ?

---

### Post by gibbylinks on 2005-06-05
I'm not at my computer just now so can't check, but I can see the ITE8212 under device manager, but can't see any drives connected to it. With my SATA drives I can expand the contoller and see the drives.

I've made a directory in MNT to mount the drive, but I haven't added anything to FSTAB, should I ?

Thanks :roll:

---

### Post by jeremy on 2005-06-06
you should if it isn't already listed, so that is the first thing to check.

---

### Post by tofudrifter on 2005-06-07
I'm a noob and also having a bit of trouble
in Device manager the ite raid card is detected (i got a gigabyte 7n400-pro2)
i'm using the gigaraid as just ata controller and it is set to ata and not raid in bios
in device manager it looks as if nothing is connected to it but i have 4 hdds connected.  when i do a fdisk -l only my other hdds come up not the ones connected to the gigaraid.

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9541    76638051   83  Linux
/dev/hda2            9542        9729     1510110    5  Extended
/dev/hda5            9542        9729     1510078+  82  Linux swap / Solaris

Disk /dev/hdg: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdg1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/hdh: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdh1               1       30401   244196001    7  HPFS/NTFS

do i need to install another driver?
or are /dev/hdb through /dev/hdf hidden/lost somewhere

tried     sudo mount -t ntfs /dev/hdb1 /media/Disk1
but       mount: special device /dev/hdb1 does not exist

---

### Post by gibbylinks on 2005-06-07
tofudrifter, thats the problem I have.

In device manager I can see my CD-ROM / DVD drives connected to the onboard NFORCE IDE, and my SATA drives under the onboard SATA controller sil3112 when I expand it, and I can see the volumes on each drive. I can also see the onboard PATA/IDE controller IT8212, but it's not showing any drives attached or volumes ?? and there is a drive connected.

I can't put anything in my fstab, because I don't know what to put in there /dev/????

not at this stage yet, but liked the icon  ](*,)

---

### Post by tofudrifter on 2005-06-10
i've found some stuff about makeing the card work but i have no idea...

[http://www.linuxquestions.org/questions/history/154256](http://www.linuxquestions.org/questions/history/154256)
[http://www.g-tec.co.at/weblog/index.php?m=200408](http://www.g-tec.co.at/weblog/index.php?m=200408)

both have instructions on how to make the card work but i don't have a clue

---

### Post by tofudrifter on 2005-06-12
Compiling kernel as i type....

anyway
get ite driver from [www.ite.com.tw](www.ite.com.tw)

follow the instructions on bottom of this page to get an uptodate kernel
[http://kerneltrap.org/node/4543](http://kerneltrap.org/node/4543)

follow instructions from this page to add itedrivers from above to kernel source
[http://www.passys.nl/tips/ite_kernel_image_compile.txt](http://www.passys.nl/tips/ite_kernel_image_compile.txt)

then follow instructions from
[http://www.debianuniverse.com/readonline/chapter/21](http://www.debianuniverse.com/readonline/chapter/21)
to compile and install new kernel

i hope it works... fingers crossed

Didn't work

---

### Post by tofudrifter on 2005-06-13
ok i i got it!!!!!!!!

just get the 2.6.11 kernel
with the ac7 patch

there is an option to enable support for ite821x

don't bother trying to use the ite drivers from the site
compile the 2.6.11 with ac7 patch and it works

now that was a waste of my long weekend... if i had just done a little more reading from the start.

---

### Post by WarlockOmega on 2005-09-18
Any chance you can give instructions to a Noob??

---

### Post by gezzabob on 2006-02-11
[QUOTE=tofudrifter]ok i i got it!!!!!!!!

just get the 2.6.11 kernel
with the ac7 patch

there is an option to enable support for ite821x

don't bother trying to use the ite drivers from the site
compile the 2.6.11 with ac7 patch and it works

now that was a waste of my long weekend... if i had just done a little more reading from the start.[/QUOTE]

Whats the steps and files needed to recompile my kernel with ite821X support (or build a loadable module).  In other words I would really like to just run through a simple set of instructions and copy my current setting but just add support to the kernel everything else seems fine I have started to compile an new kerne but it is the next couple down from the one I have and all the options in the menuconfig well there is loads and not sure what to activate or deactivate I may end up screwing the rest of the system up because of not knowing every single peice of hardware etc to add not add.

I have the gigabyte board with the it8212 controller on and all I want to do at this stage is get it working so I can see my extra drivers all my extra stuff is on them drives.  Ironicly I think there is so linux docs on there that would actually help in this situation but thought not too sure lol  Will not find out until I can actually see them with out side stepping the problem and re-aranging my drives....

So please if anybody could just post me a simple how to get my drive working that will be great I have posted already here my spec 

[http://ubuntuforums.org/showthread.php?t=125524&highlight=GigaRAID](http://ubuntuforums.org/showthread.php?t=125524&highlight=GigaRAID)

---

### Post by gezzabob on 2006-02-11
just found this thread [http://ubuntuforums.org/showthread.php?t=85064&highlight=GigaRAID](http://ubuntuforums.org/showthread.php?t=85064&highlight=GigaRAID)

seems to explain about kernels I will give it a shot see what happens

---

### Post by gezzabob on 2006-02-11
Followed this thread AND NOW CAN SEE MY EXTRA DRIVES !!!! 

[http://ubuntuforums.org/showthread.php?t=106285&highlight=patch+kernel+2.6.12](http://ubuntuforums.org/showthread.php?t=106285&highlight=patch+kernel+2.6.12)

Thanks jimbosyn very much I had been trying to sort this out for weeks!!!

---

### Post by mhl978 on 2006-08-20
I am using a similar hardware setup as what has been described, and since installing Dapper the drives have appeared just fine and operated well for the part, but after manipulating (copying, opening, whatever) a small amount of files, Ubuntu can see what files exist, but can no longer manipulate them.  Any ideas?

---

