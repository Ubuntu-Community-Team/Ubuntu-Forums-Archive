---
title: "Ejecting USB drive like in WinXP"
date: 2008-10-18
forum: Hardware
---

### Post by qbektrix on 2008-10-18
I am newbie to Linux all together. So sorry if my question is rather silly.
In WinXP i had an option of ejecting the USB drive and USB Extrenal Hard drive by just clicking an icon in the system tray. I could not find an alternative to that in Ubuntu. I tried using Unmount but it did not eject the usb drive.
Pls help me out. Thanks.

---

### Post by Wanyal on 2008-10-18
Hi, i'm also a newbie, and i don't think you have to eject using Ubuntu. And if you do, i have seen no harm in not ejecting it so far.

---

### Post by fballem on 2008-10-18
> **qbektrix said:**
> I am newbie to Linux all together. So sorry if my question is rather silly.
In WinXP i had an option of ejecting the USB drive and USB Extrenal Hard drive by just clicking an icon in the system tray. I could not find an alternative to that in Ubuntu. I tried using Unmount but it did not eject the usb drive.
Pls help me out. Thanks.

An icon for the drive probably appears on your desktop. Right click the icon and from the menu select 'Unmount Volume'. When the icon disappears, it is safe to remove the drive.

If the icon doesn't appear on your desktop, then check Places from the top panel (assuming that you're using Gnome). It should be listed there. If you right click on the listing for the USB drive and have a look at the menu. If there is an option to 'Mount Volume', then you don't have to do anything - just remove it. If there is an option to 'Unmount Volume', then select that option and wait a few seconds.

Hope this helps,

---

### Post by KuriKai on 2008-10-18
If you are browsing the root folder of your usb device then you can click on white space in it and select "Unmount volume"

---

### Post by Sef on 2008-10-18
> I am newbie to Linux all together. So sorry if my question is rather silly.

Your question is not silly.   Asking how to do something is a sign of intelligence and willingness to learn.

---

### Post by qbektrix on 2008-10-18
Thanks a lot for the feedback. But from what i observed unmounting does not exactly do what eject in winxp. When i checked for my thumb drive, if i eject in WinXP, the led flashing would stop. But when i unmounted, the led light was still on.

While googling around i came across an app called Ejecter([https://launchpad.net/ejecter/](https://launchpad.net/ejecter/)). I having trouble installing it. So could not check it. If anyone managed to install it, pls do tell me how. I am kinda lost. So far all my installation has been via synaptic package manager & apt-get.

---

### Post by Rhubarb on 2008-10-18
> **qbektrix said:**
> Thanks a lot for the feedback. But from what i observed unmounting does not exactly do what eject in winxp. When i checked for my thumb drive, if i eject in WinXP, the led flashing would stop. But when i unmounted, the led light was still on.

Yes, if it's unmounted (even if the light is still on on the drive), you can usually disconnect the USB device safely.
Don't disconnect the drive if you are using programs that operate on unmounted drives (like testdisk, photorec, gparted), as this is very uncommon, don't worry about it.
Generally, if it's unmounted, you can safely disconnect it.

---

### Post by rinishak on 2008-10-18
Yes, it's true what the others have said. All you have to do is right-click the icon of the USB device and click unmount. Once the icon disappears, it is safe to remove the USB device even if the light on the USB device itself is still blinking. And normally if your drive is still working on something, Ubuntu would notify you.

---

### Post by peakshysteria on 2008-10-18
You should wait until the light of the pen is not blinking any more. If it's blinking it's working. Then somehting can get lost or messed up. If the light have stopped flickering after you have unmounted it (or ejected it) it is safe to remove it. But you have to unmount (or eject it) by right clicking the icone (or likewise). It is not safe to skip this as someone above have suggested. Other machines and OS's are also dependent on the drive being removed correctly from the last place you used it.

---

### Post by fballem on 2008-10-19
On my drive (a LaCie external hard drive), the light is steady when it's plugged in. It only blinks when it is actually doing work.

I suspect that the steady light indicates that there is power to the device. Windows turns off the power as part of the unmount process, ubuntu does not. The light blinks when it is working, and that is the important bit!

As long as you unmount the drive, which you must do each time, you should be fine. If you try to unmount while the drive is actually doing something, then ubuntu will warn you that it is working, and tell you when it is done.

---

