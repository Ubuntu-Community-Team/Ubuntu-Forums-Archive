---
title: "LVPM. Now what?"
date: 2008-11-22
forum: General Help
---

### Post by DonQuichote on 2008-11-22
LVPM copied my Wubi Xubuntu install to a dedicated hard drive. Nice.

But to boot the new "dedicated" install, I now have to boot through 3 boot layers. Is there any way to see the new install in the Windows boot menu, alongside with the wubi install? I now have to boot through Windows boot loader, through the Wubi grub to see that I can yet again boot the new dedicated install. So there is no way yet to remove the wubi install as that takes away my possibility to even see the new dedicated install.

---

### Post by notyou on 2008-12-21
Bump.

Same issue here following a WUBI to Dedicated Partition switch. 

Power on --> Windows Boot Loader Menu (Win2k; Ubuntu (which is actually Wubi); UBNetwhatever) --> Ubuntu --> Ubuntu Boot Loader Menu (Several varieties of the Kernel; dedicated Ubuntu) --> Dedicated Ubuntu ... and we're off.

It's a little much. I assume there's a more elegant solution. Any suggestions?

---

### Post by magmon on 2008-12-21
Unfortunately, thats about good as its gonna get.. You can change the amount of time untill it auto starts tho. Someone gave me the terminal code a while ago, Ill see if I can find it.

Edit-
gksudo gedit /boot/grub/menu.lst

Run that command, then change the timeout setting to 3, or whatever you want. You could make it 1, but I dont think 0 would work. And if it did, then rescue mode would be unreachable.

---

### Post by azmo35 on 2008-12-22
well I am not sure if I understand your thread but when you boot should start with the real install and display the error 17 because you still have installed wubi I suggest uninstall wubi first and then boot again.

---

### Post by DonQuichote on 2008-12-22
> **azmo35 said:**
> well I am not sure if I understand your thread but when you boot should start with the real install and display the error 17 because you still have installed wubi I suggest uninstall wubi first and then boot again.

I don't understand this. When I boot, I have two options: Windows and the Wubi Ubuntu install. When I uninstall Wubi, I lose the link to Ubuntu altogether. If I want to boot the real installation, I have to choose the wubi install at power-on, then in the **second** boot level (GRUB in Wubi) choose Ubuntu on the separate harddisk. I then get a third boot level (GRUB of the real install). So I always have to go through Wubi to go to the real install. What I want is the real install to show up in the first boot screen (next to Windows) so I can remove wubi and still be able to boot the real Ubuntu install from the dedicated hard disk. In other words: I want to keep the third boot layer but delete the second without deleting the third.

---

### Post by azmo35 on 2008-12-22
Hi,again can you post your menu.lst?

---

### Post by DonQuichote on 2008-12-23
> **azmo35 said:**
> Hi,again can you post your menu.1st?

I have to reboot to do that, so let me put things in order. First layer is Windows. That is where I want things changed. Wubi has created a .mbr file which is a binary. The problem is that I need to edit it and have no clue to what the file structure is and see no link to documentation whatsoever.
Also, wubi has also adapted boot.ini, which may also be a starting point for putting the other harddisk in.

As an alternative, I could install grub to boot windows. However, I downloaded and burned the "Super GRUB Disk" and do not see an option that even comes close. So my first attach is boot.ini and wubi.mbr.

---

### Post by notyou on 2008-12-29
An update:

I was experiencing the same problem (Wubi install transferred to a new partition on a new drive resulting in a hinky boot process (Windows Bootloader --> Wubi Grub --> New Ubuntu install)). 

I downloaded and burned Super Grub Disk and let it automatically detect Ubuntu's partition and then install Grub. Seems to have worked just fine.

---

### Post by Jammanuser on 2008-12-30
> **DonQuichote said:**
> LVPM copied my Wubi Xubuntu install to a dedicated hard drive. Nice.

But to boot the new "dedicated" install, I now have to boot through 3 boot layers. [COLOR="Red"]Is there any way to see the new install in the Windows boot menu, alongside with the wubi install?[/COLOR] I now have to boot through Windows boot loader, through the Wubi grub to see that I can yet again boot the new dedicated install. So there is no way yet to remove the wubi install as that takes away my possibility to even see the new dedicated install.

Yes, there is a way! :) Download, install, and use [EasyBCD]("http://neosmart.net/dl.php?id=1") to add Xubuntu to your Vista bootloader. The program is very easy to figure out, and requires little technical know-how in order to see Xubuntu added to the Vista bootloader...provided you use [NeoGrub]("http://neosmart.net/wiki/display/EBCD/NeoGrub"), that is, as its a bit harder to get the normal entry working! :P

Cheers! :popcorn:

-Jam man

:guitar:

---

