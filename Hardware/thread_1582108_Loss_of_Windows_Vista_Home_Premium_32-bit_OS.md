---
title: "Loss of Windows Vista Home Premium 32-bit OS"
date: 2010-09-26
forum: Hardware
---

### Post by Jim Liiner on 2010-09-26
I was running Vista Home Premium 32-bit when I tried to install Ubuntu 10. When asked if I wanted to partition the main drive, I said yes and was told it "could not be undone". OK. When I found I had very little of my main partition left (on C:\drive) I tried to uninstall Ubuntu and recover the new partition. After the uninstall and reboot, I got the following screen:

error: unknown filesystem.
grub rescue>

I was unable to restore my OS using the eRecovery system on my notebook, an Acer 4730Z, and since the notebook did not come with discreet recovery discs, I went to Acer's support pages and ordered a set of discs made for my computer, based on the serial number. I received the discs today - a System Disc and two Recovery discs. When I followed the instructions, a message box appeared saying the 'destination was partition 2', and not really understanding that or why I couldn't use the main partition that stored the OS files, I proceeded and it appeared that all went well... until the reboot - and I got the same error message as above. I have absolutely no clue how to get my system running again, using the Windows Vista OS that belongs on the system. 
How do I recover my full partitions and ability to get my notebook back to the factory defaults?
Here's what I have:
ACER 4730Z, Intel Dual-core processors @ 2.16 GHZ, 2GB ram, 250 GB hard drive in two equal partitions, C:\ACER and D:\Data, each at 111.4 GB
Windows Vista Home Premium, 32-bit.

Can anyone help me resolve getting my original factory set up back? 

Thank you all for the opportunity to present this and any and all input will be greatly appreciated.

Jim Liner

---

### Post by sanderd17 on 2010-09-26
Sorry to say, but if you want to get your computer back to the original state and it doesn't work with the CD's delivered by Acer, you have to complain to Acer, not here. One thing you can try, maybe it works:

Run ubuntu from the live CD, open Gparted (normally it's already installed, if not, install it from synaptic), unmount the swap partition (if any), delete all partitions you have and create a new partition which takes all the space and which you format as ntfs. Maybe windows is able to read the hard drive that way.

I do would like if you stayed with ubuntu, why do you want to get back to windows? I don't have any windows anymore on my pc. Sorry that's a lie. I have a virtual win7 but I only installed it to check out what win7 looked like. It has been some months since I ran it the last time.

If you have problems with ubuntu, just post your messages here and if you don't get an answer, PM me and I'll try to answer it.

---

### Post by P4man on 2010-09-26
The fact you get a grub prompt after running the recovery cd suggests its doing a poor job. Grub is the linux bootloader, it should have been replaced with the windows bootloader.

I dont know how acer cd's work, but any original windows cd (vista or 7) can boot from the cd and then have options to repair the "MBR" (= master boot record, thats where the bootloader sits). And if you just install windows it will automatically write the MBR so I have no idea why Acer CD's arent doing that.

Anway, the above poster had the right idea. If there is nothing on the laptop thats worth saving, and if Acer boot cd isnt up to the job, then boot an Ubuntu CD again, run gparted from 

system > administration > gparted

select the harddrive, right click the swap partition (if any) and select "swapoff". Now go ahead and delete or create partitions as you see fit. Id try deleting them all and let the acer cd recreate them. Im assuming it can do that.

---

### Post by Megaptera on 2010-09-26
Is the following any help?


[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

Scroll down to Vista.

---

### Post by 0N3 on 2010-09-26
Load your Vista installation disk do all as usual name location ect.... and then selct repair my PC go to the cmd (command prompt) and type bootrec.exe/fixmbr

---

