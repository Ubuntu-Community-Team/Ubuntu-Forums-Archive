---
title: "xp and ubuntu"
date: 2013-09-28
forum: Hardware
---

### Post by mrmgee on 2013-09-28
Hello I ran into a problem with having two hard drives. One had xp and the other unbuntu on the other.They worked fine with the gurub boot loader or whatever its callled .The xp drive started making unusual noises,so I removed the drive with xp and replaced the drive with a new seagate drive 250 gig drive. I installed xp onto the drive,but it will not boot into that drive. Is the gurub boot loader causing the problem? Can anyone give me a link to a website for anyhelpfull advice I'd sure appreaciate it.
thank you.

---

### Post by TheFu on 2013-09-28
Run **boot-repair**. See my sig for links.

---

### Post by mrmgee on 2013-09-29
I get dpkg was interrupted on my pendrive.

---

### Post by mrmgee on 2013-09-29
[http://paste.ubuntu.com/6169773/](http://paste.ubuntu.com/6169773/) I got it working on my pendrive now. I still cant boot on that drive.
Im not sure if the link is working either,sorry.

---

### Post by TheFu on 2013-09-29
Please fix the link. There's an extra 'n' to be removed. That will help others to help you.

Besides that, it looks like 1 drive (sdc) is 100% linux and the other is NTFS (sdb) drive. Which do you want to boot from? That is where grub needs to be installed.  There is probably a boot sector on sdb ...  installing grub there should work. 

I just made a new dual boot machine here and had to manually do this. Both the installer and boot-repair failed to do what I wanted.  It was putting grub on the first HDD in the list ... the flash drive in my case.  Of course, I had a 100% backup before starting and my Win7 machine is NOT UEFI.  Also, Windows needed to spend about an hour fixing the boot and I had some fear that it wouldn't work.

---

### Post by mrmgee on 2013-09-29
I wat to boot from both The sbd drive is the problem
 ,it looks like my fresh installation is on there for xp.
The drive does show up on my home folder.

---

### Post by mrmgee on 2013-09-29
I would like the option of botting from either one like i did before using gurub.
My sdb drive ,I cant get it to work at all.

---

### Post by TheFu on 2013-09-29
Sorry, don't have time to write out the instructions now ... [https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing) should help.
* boot from a CD or flash; be root
* mount the root partition of the linux install somewhere safe ... /mnt is usually a good place.
* chroot to that location ... making all your system programs available.  **chroot /mnt**
* run grub-install /dev/sdb - be certain to validate sdb is really the WinXP drive now (see below).

If that fails to boot, then run boot-repair - now that grub is in the correct HDD, hopefully it will add/setup all the other OSes (Win + Uubntu) to the grub menu.

After you boot, the HDD devices may have switched around, so don't blindly trust that sda, sdb and sdc are the same between boots. Check them with **sudo parted -l** to be positive.

Good luck.  That link should have more details about doing this stuff and my overview should be enough to let you follow along.

---

### Post by mrmgee on 2013-09-30
Sorry im abit lost on what to do here . I dont know how to do those commands

---

### Post by oldfred on 2013-09-30
Your sdb drive is not showing a MBR nor a partition like sdb1???

Did you just copy Windows from old drive onto an unformatted new drive? Windows needs to be installed as it uses the PBR or partition boot sector to boot from (as well as MBR).

---

### Post by mrmgee on 2013-09-30
Its a clean install from cd,and from devices there is a file boot ini and a windows folder and a couple of other files on sda. Is that what you mean? Im pretty sure it was formatted during install . I do remember it being formatted during the installation I think.

---

### Post by oldfred on 2013-09-30
It would show sdb1 not sdb if installed to a formatted NTFS primary partition. And Windows only works from primary partitions.

---

### Post by mrmgee on 2013-10-01
file:///home/clayton/Desktop/Screenshot%20from%202013-10-01%2011:40:41.png

---

### Post by oldfred on 2013-10-01
That is a .png on your /home. You can use Go Advanced and use paperclip icon to attach it here.

---

### Post by mrmgee on 2013-10-01
here is where my installation is[ATTACH=CONFIG]246657[/ATTACH]

---

### Post by mrmgee on 2013-10-01
[ATTACH=CONFIG]246664[/ATTACH]

---

### Post by oldfred on 2013-10-01
disk Utility is also saying it is not partitioned. Just sda, no sda1. You must have just copied files into the partitioned drive. Windows has to boot from a partition.

---

### Post by mrmgee on 2013-10-01
How can they go into this drive if its not ntfs[ATTACH=CONFIG]246665[/ATTACH]

---

### Post by mrmgee on 2013-10-01
Mayby ill just unplug my unbuntu drive and try again,I thought I diasabled that drive in bios when installed windows xp.

---

### Post by mrmgee on 2013-10-01
ok I unplugged my drive that I use for unbuntu and tried installing xp onto my new drive
The installation says that I have a windows operating system on that drive and that I can overwrite it.
If its on there why should I?

---

### Post by mrmgee on 2013-10-01
Obviously I don't understand what your saying.Do I have to partition the drive first before I can install windows.
I thought a clean install from cd would format and do all that stuff for me.

---

### Post by oldfred on 2013-10-01
I do not know how Windows is seeing a unpartitioned install? It normally partitions as part of the install and should have done that with your first install.
Windows has to have partitions to even boot.

       Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by mastablasta on 2013-10-02
yup osmehting is misisng. where are the autoexec.bat, command.com files. something obviously went wrong during windows install. i would also suggest to reformat that driver and reisntall. you can have ubuntu disk unplugged when you do it and then WindowsXP should boot.

as mentioned windows needs a tiny hidden disk sector for it to boot. it's all created automaticly upon install and reformat. it is also needs primary partition. and the frist primary partition in widnows is called C:\ if disk was unformatted when you put it into the PC then it will get propperly formatted for boto by default on windows xp install.

---

### Post by TheFu on 2013-10-02
> **mastablasta said:**
> yup osmehting is misisng. where are the autoexec.bat, command.com files. something obviously went wrong during windows install. i would also suggest to reformat that driver and reisntall. you can have ubuntu disk unplugged when you do it and then WindowsXP should boot.

as mentioned windows needs a tiny hidden disk sector for it to boot. it's all created automaticly upon install and reformat. it is also needs primary partition. and the frist primary partition in widnows is called C:\ if disk was unformatted when you put it into the PC then it will get propperly formatted for boto by default on windows xp install.

parted -l - shows a partition - assuming that I'm reading it correctly .... but it starts at sector zero ... highly unusual.  Seems the partition table is missing? Not good.

To reduce confusion, WinXP **DOES NOT** need a small partition to boot, but the "boot sector" at the beginning of a drive **is** required. That extra partition was added in Vista or win7 (can't recall) .  WinXP just needs a primary partition with the "boot" flag set.  All OSes use the first 512B of disk to figure out booting ... I don't recall the details - but wikipedia will explain how x86 systems boot.

To me, it seems that something has gone wrong somewhere and we can't exactly tell where.  Overwriting your Windows install is fine, if you don't want to use it ever again.  If you do want to use it, I'd highly recommend making the system boot into Windows, then making a 100% good backup of the entire HDD (clonezilla for Windows stuff), then trying again to install Linux.

It has been awhile since I read the original issue, but spelling out exactly where you want Windows AND where you want the Linux partitions AND where you'd like to boot from would be helpful.  You can "boot" off both drives, but changing will mean modifying the BIOS to select which drive is booted.  Most of us boot off the first drive we installed - usually SATA1 (sda), but it is easy to mix up the SATA cable plugs and change the order of the disks.  Add in that the Ubuntu installer seems to want to install the grub2 on the first disk in the list even if that is a flash drive - I was burned by this last week myself with a 12.04 Server install.

To make the install easy, things go well if
a) installation from a DVD/CD (not flash drive)
b) only 1 physical HDD is connected
Then the defaults should do the right thing almost always, provided there is free storage and available partitions for the ubuntu installation.

I haven't setup WinXP in about 4 yrs and I expect others here haven't either, so a reminder that XP is the OS being used would be helpful too.

Sorry if this is all confusing and I might not have helped. Feel free to ignore it.

---

### Post by mrmgee on 2013-10-02
I get the same thing.I installed xp again and it formatted and all that it does.
When It says to restart my computer to complete the installation nothing happens.It boots from cd to install again.
I will have to see if seagate will help me.I would install vista,but my cd must have a scratch. It wont read, and I have tried tooth paste to fix it. Since its its a version for builders they sold me, I have to see how I can get it replaced
I thankyou for your help.

---

