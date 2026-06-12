---
title: "DVDROM tray won't open with media inside. Have to use software Eject"
date: 2005-08-26
forum: Hardware &amp; Laptops
---

### Post by linuxa on 2005-08-26
Hi there

I run a freshly installed Ubuntu on a Toshiba laptop. To my dismay I recently learnt that with a cd/dvd inside, my DVDROM tray won't open when pressing the eject button on the side.

I would have to right click on the CDROM icon my desktop and choose Eject to get the media out of the tray.

I know that the button itself isn't broken, as it was working fine on WinXP, and when I was installing Ubuntu.

Does anyone know what the problem is or how I could go about fixing it please?

I'd be really grateful to fix this little annoying problem.

Thanks.

---

### Post by Buffalo Soldier on 2005-08-26
ubuntu wouldn't let you eject any drive that is still *mounted*. that's why you have to "right-click eject", what that method exactly does is cleanly unmount your cd-rom and then ejects it.

---

### Post by s_p_a_r_k_y on 2005-08-26
There are also good reasons for not letting users eject CDs. If i'm an administrator and want to keep a CDrom in a server or desktop, bc I need to use it or run software from it, no one can eject it unless they mounted it themselves. If I mount it then they must gain root or my user priveleges before being able to unmount the cdrom...It may seem silly in a desktop situation, but in a secure network administrators should be able to allow or disallow certain activities.

---

### Post by linuxa on 2005-08-27
Thanks for the info guys.

These are indeed very valid reasons. Having come from a Window background, I simply wasn't accustomed to the fact that I had lost (some) control over my hardward :D

Cheers

---

### Post by doclivingston on 2005-08-28
As another example of why you need to unmount things before removing them, consider a floppy disk, or usb stick. Until you unmount it, the computer may not have written everything out to the disk/stick yet - so if you remove it without unmounting it first, you may loose data.

Windows deals with disks by writing everything out as soon as possible, which means that you can remove them at any time (assuming that it's not in the middle of writing), but makes it slower. I think Windows deals with usb sticks in the same way as Linux does - if you remove them without telling it first, you may lose data or have a currupted file system.

---

### Post by linuxfanatic1024 on 2005-08-28
[QUOTE=doclivingston]As another example of why you need to unmount things before removing them, consider a floppy disk, or usb stick. Until you unmount it, the computer may not have written everything out to the disk/stick yet - so if you remove it without unmounting it first, you may loose data.

Windows deals with disks by writing everything out as soon as possible, which means that you can remove them at any time (assuming that it's not in the middle of writing), but makes it slower. I think Windows deals with usb sticks in the same way as Linux does - if you remove them without telling it first, you may lose data or have a currupted file system.[/QUOTE]

This was so annoying on Win98 because there was no way to tell it I removed the disk. I quit after Win98 and went pure Linux.  :grin:

---

### Post by linuxa on 2005-09-01
Yeah, who would've thought that one extra step (unmounting) would make so much difference  :razz: 

Cheers guys

---

### Post by Lord Illidan on 2005-09-01
This is better than Microsoft's way of saying "It's not bug, it's a feature!"

---

