---
title: "Need help wiping usb drive"
date: 2009-09-10
forum: Hardware
---

### Post by Kisame on 2009-09-10
So, I have this flash drive that i partitioned for installing a netbook OS, then I needed to use it for something else so i stuck it into my windows pc right clicked and chose format, i put fat32 on it (yeah I know, fat32 sucks for usb stuff) but I only had a little time and I only needed it for moving one film between windows pcs so i figured whatever. But then when I tried to move the film it said the drive was full... strange since its a 32gb drive and I just formatted it.. but I guess i did something wrong, so here i am. Looking for a hand hold to be honest Im terrible with ubuntu if someone could really walk me through this id be very greatful.

---

### Post by Fafler on 2009-09-10
Applications -> Add/Remove. Find and install gparted
Start it from System -> Administration -> Partition Editor
Select your flash drive from the drop down list. Delete any existing pertitions. Create a new. Format exit.

---

### Post by ottosykora on 2009-09-10
This can have different reasons. Very likely it is simply hardware problem on the controller inside the usb drive. Firmware crash on that is sometimes not recoverable if all done simple and cheap.
I have number of such drives which are simply non recoverable any more. 
Sometimes it also depends on what does the controller communicate to the driver. Does it still say it is 32gb? Or does it say different figure? Are you sure this was 32gb drive and not 8gb saying it is 32gb? I have collection of those cheap and give away goodies saying they are 16gb, but the chip inside is only 4gb size. One can write *anything* into the controller and sell it so for higher price.

Next what you could try is to reformat it with some other tool as gparted for example.
But delete the partition first.
Sometimes this is tricky, I had two sticks which even gparted refused to format saying the file system is virtual. Sometimes even there after some trying the partitioning can be removed, sometimes two attempts are needed.
Thereafter try to format again with gparted for example and see if the formating reminds consistent.
The formating is anyway virtual only, so it also depends how well the controller is converting flash file system to the fat32, which is not so bad thing for usb flash after all, or better then any of the journaling file systems at least.

---

