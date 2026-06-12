---
title: "No booth menu after install"
date: 2008-11-15
forum: General Help
---

### Post by Tangra on 2008-11-15
I installed Ubuntu with the Wubi installer and everything went fine, except for the fact that, there is no booth menu that appears after the reboot of windows.

I use windows Vista basic, 32 bit.

Is there a way to fix this, or is it something I had to do more?

Thanks in advance

---

### Post by Tangra on 2008-11-15
By reading on the threats on the forum I found out about EasyBCD. I checked it out, and to my surprise there was no traced of Ubuntu. I did tried to re-install it, but with no success.

---

### Post by Marcus Derekus on 2008-11-15
i'm glad you have easy bcd i will give you istructios on how to fix your problem

---

### Post by Marcus Derekus on 2008-11-15
Open easyBCD pres the **Add/remove entries** button.

 Click the linux selection.

 set the **type:** to GRUB.

Under **Drive:** select the partition (partition 1 is the primary harddrive.)
**Actually i don't think the partition matters because it is a Wubi installation but i'd do it anyway**

if it is on a secondary than select its partition) that your wubi install of ubuntu is installed on. 

Next select **add entry**. 

Now minimize easyBCD. 

enter into the drive that you wubi install of ubuntu is on.

enter the ubuntu folder.

Enter winboot folder and copy all files from that directory (i think you only need wubildr.mbr but copy them all just in case).

maximize Easy BCD click **view settings**

read entry #2 to find out the bootloader path.

Close easyBcd

Now enter the directory of the bootloader.

paste files that you copied earlier into this directory

delete nst_grub.mbr     

and rename **wubildr.mbr** to **nst_grub.mbr**

Now Reboot and Ubuntu option should be there.

Tell if you have problems (im confident you wont)

Please reply of succesful

---

### Post by Tangra on 2008-11-16
TX! Works perfectly.

---

### Post by Marcus Derekus on 2008-11-16
Your Welcome Tangra!

---

### Post by ellalan on 2008-11-18
Thank you Marcus for this excellent post,you saved me a lot of time.

---

