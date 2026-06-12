---
title: "I'm done with ubuntu, i want it gone."
date: 2008-07-19
forum: General Help
---

### Post by Chaoskeeper56 on 2008-07-19
hello,
I have been using ubuntu for the last several months now, and even though i think it is a great OS, i would be much better off using windows, But heres my problem. whenever i try to install windows XP via CD, it says it cannot find the Hard Disks, and won't let me install. 

Does ubuntu have to be removed or something? If you know how to help me, than please stop reading and tell me! lol.

BTW: i am not trying to do one of those things where i can duel boot or somthing. i just want ubuntu gone and windows back on my laptop. thanks.

(Please try to explain this in a way that anyone with basic knowledge of ubuntu can understand, cause i have some trouble with technical terms and things like that.

thanks.

---

### Post by bubba_169 on 2008-07-19
What is the exact error message you get regarding the drive? It could just be you have an unknown partition filesystem (ext2) that windows cant recognise... just use windows setup to delete your partitions and start afresh

Make sure you back up any important information :)

---

### Post by bollix47 on 2008-07-19
Get [gparted live]("http://gparted.sourceforge.net/livecd.php"), burn it to a cd(right click on the downloaded iso file and select write to ...), boot your laptop from the cd, delete the existing partitions and format the disk with ntfs or fat32.

Rerun your windows setup disk.

---

### Post by Chaoskeeper56 on 2008-07-19
> **bubba_169 said:**
> What is the exact error message you get regarding the drive? 

Hold on a little bit, it will take a bit of loading to get back to that page, and i have nothing on ubuntu that i need backuped.

---

### Post by damis648 on 2008-07-19
Boot up with the Windows CD in the drive. If it says "Press any key to boot from CD", do so. When you get to the first dialog, press enter like the prompt states. When you get to the "Install to Partition" menu, press "d" on everything on your main drive. Now press "c" on the "Unpartitioned Space" and then press enter. Press enter one more time,  then let the installer do its thing.

---

### Post by jerome1232 on 2008-07-19
It sounds like you have a SATA hard drive controller and windows doesn't recognize it, Windows XP doesn't recognize a few (like mine is a ULi on board controller) IF that is the case you have to press F6 during the first part of installation (it prompts you) and insert a floppy disket with the driver on it.

Windows xp pro will lable filesystems it doesn't recognize is unknown file system but you can still delete and manipulate partitions.

I don't know about home edition on that matter.

---

### Post by Vorian Grey on 2008-07-19
You can also use the ubuntu LiveCD and use the Partition Manager found under System > Admin. Change your disk to NTFS and let it do it's think and then reboot into your Windows disk and it should work. Windows uses only NT file systems while Ubuntu usually uses ext3, which Windows can't read.

---

### Post by damis648 on 2008-07-19
> **jerome1232 said:**
> It sounds like you have a SATA hard drive controller and windows doesn't recognize it, Windows XP doesn't recognize a few (like mine is a ULi on board controller) IF that is the case you have to press F6 during the first part of installation (it prompts you) and insert a floppy disket with the driver on it.

Windows xp pro will lable filesystems it doesn't recognize is unknown file system but you can still delete and manipulate partitions.

I don't know about home edition on that matter.

That would be a good point. SATA was implemented into modern computers after Windows XP. Do you have a SATA drive? If you do not know, could you post the model of your computer?

---

### Post by damis648 on 2008-07-19
> **Vorian Grey said:**
> You can also use the ubuntu LiveCD and use the Partition Manager found under System > Admin. Change your disk to NTFS and let it do it's think and then reboot into your Windows disk and it should work. Windows uses only NT file systems while Ubuntu usually uses ext3, which Windows can't read.

Actually, windows will use FAT32 if prompted to, but is not defualt. And, for the OP, if you do this, make sure to delete the two existing ones and add a new, single partition and format as NTFS.

---

### Post by Chaoskeeper56 on 2008-07-19
heres the message i'm getting when trying to boot from the windows xp disk. 

"Setup did not find any hard disk drives installed in your computer. Make sure any hard disk drives are powered on and properly connected to your computer, and that any disk-related hardware configuration is correct. This may involve running a manufactured-supplied diagnostic or setup program."

---

### Post by jerome1232 on 2008-07-19
> **Chaoskeeper56 said:**
> heres the message i'm getting when trying to boot from the windows xp disk. 

"Setup did not find any hard disk drives installed in your computer. Make sure any hard disk drives are powered on and properly connected to your computer, and that any disk-related hardware configuration is correct. This may involve running a manufactured-supplied diagnostic or setup program."

Yeah that says unrecognized SATA controller all over it, can you post your make and model of computer, you have two options depending:

1: Some BIOS lets you put the SATA controller into an IDE compatibility mode, so if your's allows that it's easiest

2: Download the driver off your manufacturers website, copy it to floppy and tell windows where the driver is during setup

---

### Post by flytripper on 2008-07-19
if this is a parallel ata drive (pata) sounds like a mbr problem.. perhaps. try the "repair from recovery console" option on the xp bootdisk and if it picks up the drive type fix mbr or fixmbr (cant remember).if this doesnt work i have found that the windows 98 boot disk and the fdisk command will enable you delete the partitions and rebuild some semblance of a readable partition for your xp install. alternatively you could run a program call activekilldisk (normally from a floppy or ahem.... hirens bootcd ....ahem.)to wipe the drive completely and restart the installation from there.. hope this helps

---

### Post by Chaoskeeper56 on 2008-07-19
I tried the f6 thing once, but i got the same result.

---

### Post by jonian_g on 2008-07-19
> It sounds like you have a SATA hard drive controller and windows doesn't recognize it, Windows XP doesn't recognize a few (like mine is a ULi on board controller) IF that is the case you have to press F6 during the first part of installation (it prompts you) and insert a floppy disket with the driver on it.

I also think that this is your problem. A friend of mine got a new laptop with vista on it. When he tried to install winxp he got the same error (no hdd). He downloaded the driver and put it in a floppy. F6 when install started and his problem was solved.

---

### Post by want2bdifferent on 2008-07-19
were you originally on windows Vista?
if you were it is a bios setting, i can not remember the exact setting. i know my brother had the same problem when downgrading from vista to XP.

---

### Post by Chaoskeeper56 on 2008-07-19
> **want2bdifferent said:**
> were you originally on windows Vista?


Yes i was using vista. But don't worry about it. my sisters boyfriend had to do the same thing, so he's gonna just do it for me. thanks for your help guys.

---

### Post by Spaceman9 on 2008-07-19
If I had this problem I'd just fire up the Ubuntu live cd and use Gparted to delete any unwanted partitions and reformat the hard drive with NTFS. 

I have PCLOS Gnome 2008.1 on my second hard drive as my backup OS. If your windows fails you, you'd still have a great OS to keep working with until you get windows working again. At the end of the day it's up to you of course.

---

