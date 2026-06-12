---
title: "Kernel update not listed in Grub"
date: 2008-11-28
forum: General Help
---

### Post by hissyfut on 2008-11-28
After an update to 2.6.27-9 in Intrepid ibex, it is not shown on boot, and uname -a shows still previous -7. Synaptic show both as installed.

---

### Post by adult swim on 2008-11-28
an easy fix for this is to edit your grub menu. to do this from a terminal run ```
gksudo gedit /boot/grub/menu.lst
```  scroll down to near the bottom where you will see your current grub entries.  highlight one block from title to boot.  here is an example of what you would want to highlight, note its going to be different from yours.  ```
title		Ubuntu 8.10, kernel 2.6.27-8-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-8-generic root=UUID=e68b2bb7-17f9-445b-b1b7-10d07ed8099a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-8-generic
savedefault
boot

```  copy and paste that above the top entry in your menu.lst file and then change the  2.6.27-7 to 2.6.27-9 in the title, kernel, and initrd line.  save and close the file and you should be all set.

---

### Post by hissyfut on 2008-11-28
> **adult swim said:**
> an easy fix for this is to edit your grub menu. to do this from a terminal run ```
gksudo gedit /boot/grub/menu.lst
```  scroll down to near the bottom where you will see your current grub entries.  highlight one block from title to boot.  here is an example of what you would want to highlight, note its going to be different from yours.  ```
title		Ubuntu 8.10, kernel 2.6.27-8-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-8-generic root=UUID=e68b2bb7-17f9-445b-b1b7-10d07ed8099a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-8-generic
savedefault
boot

```  copy and paste that above the top entry in your menu.lst file and then change the  2.6.27-7 to 2.6.27-9 in the title, kernel, and initrd line.  save and close the file and you should be all set.

Thanks for your help, grub seems to work a lot like lilo. Couple of questions.
Would not the uuid change? (Not on topic, but for some reason a fresh install from cd did not find all partitions, give them a uuid, and list them in grub as with previous ubuntu. :(  )
Is iniitrd necessary?

And the more important question is why did the kernel update not update grub in the first place?

---

### Post by drs305 on 2008-11-28
> **hissyfut said:**
> And the more important question is why did the kernel update not update grub in the first place?

There are settings in menu.lst that determine whether or not grub will automatically update to a newer kernel. The line is:
```

# updatedefaultentry=true

```
*Note:* In menu.lst a single # symbol is not a 'comment' symbol within the 'Automagic Kernel' section. Any line within this area with a single # symbol is acted upon.

You can change the default action by manually editing menu.lst or by making the change in the gui-based app *startupmanager*. StartUp-Manager can safely tweak a lot of grub's options. Refer to the link in my signature line for a tutorial on this app (StartUp-Manager).

---

### Post by spiderbatdad on 2008-11-28
The above is not a method of updating grub I have seen. When the update ran, you should have been asked to use the installed grub...there is a drop down menu to select the package maintainer's version. Ok missed it?
```
sudo update-initramfs -c -k 2.6.27-9-generic
sudo update-grub
```I believe is the correct way.

---

### Post by ferronica on 2008-11-29
spiderbatdad,

i missed that options and used local system settings of menu.lst. I tried your command but no luck :( any other way to insert new kernel 2.6.27-9 in menu.lst

---

### Post by drs305 on 2008-11-29
> **ferronica said:**
> i missed that options and used local system settings of menu.lst. I tried your command but no luck :( any other way to insert new kernel 2.6.27-9 in menu.lst


I used the commands as well but it still didn't update my menu.lst nor use kernel 9.

I then manually edited grub, copied the existing menu.lst entry for the -7 kernel and the -7 kernel recovery modes, and pasted them above the current first entry and changed all references to -7 to -9. After rebooting, the -9 kernel was being used. 

@ spiderbatdad,

I may not have been clear enough on my previous post. StartUp-Manager searches for available kernels when it starts and allows the user to select which one to make the default. It then makes the applicable edit to the grub menu. Whether or not the grub menu file is replaced is determined during the upgrade.

---

### Post by hissyfut on 2008-12-01
In the process of manually updating menu.lst, just happened to look in /boot and noticed no 2.6.27-9 images! Synaptic description of new linux-image-x advises using linux-generic meta package.
Selecting linux-generic in turn might need more packages.

This worked and it updated menu.lst with the new kernel entrries without editing it manually first.
The entry # updatedefaultentry=false is unchanged.

Now it appears to be correct, though only diligence in this case found the problem. Only someone with previous knowlege of installed or installing kernels would have noticed. Otherwise the system had the kernel source and headers with no image and possibly no modules. A bit quirky.

All this update needed was a simple if then script that could detect what was needed and pop up a notice to the user.
Hope this helps.

---

