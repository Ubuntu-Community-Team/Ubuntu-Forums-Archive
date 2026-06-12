---
title: "cant see ubuntu 8.10 due to xp installation prob"
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by vpnm_87 on 2009-05-24
I had win 2000 and ubuntu 8.10...thought of migrating to XP professional..
used XP cd and formattin,copyin done successfully..then comes the nightmare...after resarting my XP installation completely hangs in logo screen itself...

1) now is that possible to OS selection screen again to boot into ubuntu..any shortcut keys to go into boot option screen..

2) i can view all partitions using puppy..so is there any way i can bring back my grub to boot into ubuntu

BTW..am using puppy linux from USB now to troubleshoot that installation prob..plz provide some suggestion for logo screen hangin durin installation...

3) also am lookin for BIOS update procedure in puppy..coz i think xp hangs coz of ACPI issue(jus a guess)..but no idea how to do that in puppy..

---

### Post by raymondh on 2009-05-24
> **vpnm_87 said:**
> I had win 2000 and ubuntu 8.10...thought of migrating to XP professional..
used XP cd and formattin,copyin done successfully..then comes the nightmare...after resarting my XP installation completely hangs in logo screen itself...

1) now is that possible to OS selection screen again to boot into ubuntu..any shortcut keys to go into boot option screen..

2) i can view all partitions using puppy..so is there any way i can bring back my grub to boot into ubuntu

BTW..am using puppy linux from USB now to troubleshoot that installation prob..plz provide some suggestion for logo screen hangin durin installation...

3) also am lookin for BIOS update procedure in puppy..coz i think xp hangs coz of ACPI issue(jus a guess)..but no idea how to do that in puppy..

Hello vpnm_87,

Try this link (albeit using a ubuntu liveCD)

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Regards,

---

### Post by vpnm_87 on 2009-05-24
thanks for the immediate reply raymond..
got a small issue with my live cd..
when i choose to try ubuntu as a live cd..it goes to a black screen just before comin to home desktop screen..issue with my video card i guess..
but i installed ubuntu using the same cd but after installin i removed compiz components due to login problems..
some video card prob i guess..checked the cd for detects..it didnt report any error...
so any idea now?live cd option s not possible now..thats y am using puppy in my USB

---

### Post by raymondh on 2009-05-24
> **vpnm_87 said:**
> thanks for the immediate reply raymond..
got a small issue with my live cd..
when i choose to try ubuntu as a live cd..it goes to a black screen just before comin to home desktop screen..issue with my video card i guess..
but i installed ubuntu using the same cd but after installin i removed compiz components due to login problems..
some video card prob i guess..checked the cd for detects..it didnt report any error...
so any idea now?live cd option s not possible now..thats y am using puppy in my USB

I have never used puppy but would you like to try (??????)...

-Try to boot puppy and get into a live session.
-Navigate to a terminal
-Type

```
grub
```  (you may have to use sudo grub)

If you get to the GRUB menu, type

```
find /boot/grub/stage1
```

If you get an error, try

```
find /grub/stage1
```

Hopefully, it'll spit out info where it is. Copy it on a piece of paper, then..

```
root (hd_,_)
```   Fill in the blanks with the info you have copied

```
setup (hd0)
```

```
quit
```


take out/unmount the puppy usb and reboot.  Let's go from there.

Good luck,

---

### Post by vpnm_87 on 2009-05-24
both find option returned file not found error..
there s a GUI GRUB installation option in Puppy,,tryin that now..ll update the status soon

---

### Post by vpnm_87 on 2009-05-24
it asked to specify the place to put grub files..
gave /dev/hda8(my ubuntu root file system drive)
then asked me to whether to install in MBR or any linux superblock partition..
first time gave MBR..status showed GRUB installed successfully..but agian it booted to XP and hanged in logo screen
now tryin superblock partition..donno wats gonna happen..

---

### Post by vpnm_87 on 2009-05-25
nothing heped to boot into my Ubuntu 8.10 again..
am getting only xp logo screen that hangs:-(

---

### Post by zeroseven0183 on 2009-05-25
Have you tried pressing F8 several times before the Windows XP boot screen appears? I believe it will post some boot options there.

---

### Post by raymondh on 2009-05-25
> **vpnm_87 said:**
> nothing heped to boot into my Ubuntu 8.10 again..
am getting only xp logo screen that hangs:-(

Using the puppy liveUSB, can you do the following

1.  can you access and open gparted.  It is a partitioning tool.  Are you able to take a screenshot and post it here?  Are you sure ubuntu is at hda,8 (as you mentioned)???  If no gparted, can you post the output of

```
fdisk -l
```  (that's a small letter L)

what happens if you try in terminal

```
grub
```
```
root (hd0,8)
```
```
setup (hd0)
```
```
quit
```

and reboot

2.  Do you have access to the internet?  can you download a boot info script from [https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/) to your desktop.  From there, open a terminal and type (or copy/paste this code)

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will generate a RESULTS.txt file. Copy/paste back here that output.

---

### Post by vpnm_87 on 2009-05-25
first of all bunch of thanks for ur kind help Raymond:-)
since i didnt even sleep sterday night i got frustrated n used ubuntu cd n formatted my root file system alone in manual partition option..

now am in ubuntu..i dont want to waste d efforts u took for me..got small prob now..

previously i used /home partition with 12 GB and / with 12 GB...now i formatted only /...so my /home is separate like my windows partition now..got to mount it separately before accessing...

1) do u think thats a prob since my broadband connection became slow now..does that separate /home partition affects my internet speed?

If u say that its gonna affect my internet speed and some applic installation then i hav to install my ubuntu again as i previously did..

if i have to reinstall ubuntu then before that i ll surely try the puppy suggestion u gave me in the previous post:-)

---

### Post by raymondh on 2009-05-25
> **vpnm_87 said:**
> 
1) do u think thats a prob since my broadband connection became slow now..does that separate /home partition affects my internet speed?


I do not think so.  I think the slow internet connection is another problem which is not due to having a separate /home partition.  BTW, congratulations on having the foresight of installing a separate /home partition.  :KS  

Regarding your comment about "got to mount it separately before accessing"..

Can you share the steps you took to re-install? During re-intsall, did you format /home?  Can you post output of

```
cat /etc/fstab
```

Am glad you got your ubuntu back.  

Regards,

---

### Post by vpnm_87 on 2009-05-25
steps i did for re-install..
inserted live CD..gave Install Ubuntu
selected manual partition
chose "edit partition" in root file syst partition
selected Format option for tat partition alone..
didnt touch any other option...
then pressed next options as usual..

u can also go thro this link
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=0e2edd13-d719-4cd0-bd2b-c0b14418ca0d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=6be7ca9c-42d0-42bb-acf3-3b1a750aeeca none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by raymondh on 2009-05-25
ok .. I may be reading too much into this.;) 

If you are able to access your old /home partition, then you're fine.

If not, have a look at this thread and the tutorial of the poster LURKO (about 3rd post). Note that noatime is automatically done by Ubuntu.  Psychocats also has a good tutorial which I have used successfully.

[http://www.linuxquestions.org/questions/ubuntu-63/can-i-delete-and-reinstall-ubuntu-8.04-and-keep-a-home-partition-697267/](http://www.linuxquestions.org/questions/ubuntu-63/can-i-delete-and-reinstall-ubuntu-8.04-and-keep-a-home-partition-697267/)

As for the slow internet, I think it's a different issue.  Why not start a new thread if your searching and tweaking could not find a solution?

Regards,

---

