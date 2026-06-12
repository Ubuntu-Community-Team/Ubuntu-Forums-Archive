---
title: "[SOLVED] No USB in VirtualBox"
date: 2008-12-28
forum: Installation &amp; Upgrades
---

### Post by ancient_ee on 2008-12-28
Installed VirtualBox 2.1 (closed source) on Intrepid Ibex. No USB in WinXP_SP3 virtual box. Whever I pop in a USB drive, it opens a window in Ubuntu, ignoring the open WinXP virtual box. I followed the fix-it directions at [http://www.virtualbox.org/wiki/User_FAQ](http://www.virtualbox.org/wiki/User_FAQ), still no USB in box.

In a possibly related issue, the mouse remains captured even when I depress the right CTL key, The only way I can move the mouse back into Ubuntu is to shut down the WinXP box.

---

### Post by scorp123 on 2008-12-29
[http://ubuntuforums.org/showthread.php?p=6450868#post6450868](http://ubuntuforums.org/showthread.php?p=6450868#post6450868)

---

### Post by ancient_ee on 2008-12-29
Hi Scorp123,
I did check the users and groups, and found I am a member of vboxusers, group 123. So I edited the fstab statement to read gid=123. Still, when I start WinXP in the virtual box, I get a "new hardware found" message, a USB controller, for which the driver cannot be found. I also cannot access the CD drive from within the virtual box.

BTW, after re-installing Ubuntu (yes, I am that desperate) I can liberate the mouse by pressing right CTL key.

---

### Post by howefield on 2008-12-29
After you created the virtual machine, did you go back into the VirtualBox settings and check the boxes against Enable USB Controller and Mount CD.DVD Drive ?

Sorry for the basic question, but just to be sure.

---

### Post by ancient_ee on 2008-12-29
No problem with basic suggestions for a noob like me. I did screw up on the CD/DVD-ROM. It is now enabled. Before it was enabled, the icon showed up in "My computer" but did not work. Now, with CD/DVD-ROM enabled, the CDROM icon does not even show up.

The USB controller is enabled, along with the USB 2.0 EHCI controller. I created a filter (I just thought it was the thing to do) which is simply named New Filter 1. But still no USB, still showing a hardware driver error.

---

### Post by howefield on 2008-12-29
> **ancient_ee said:**
> The USB controller is enabled, along with the USB 2.0 EHCI controller. I created a filter (I just thought it was the thing to do) which is simply named New Filter 1. But still no USB, still showing a hardware driver error.

Err... all mine are labelled with the actual name of the device, eg  EPSON USB2.0 MFP(Hi-Speed) [0100] ect ect, you need to press the second top icon on the right, the one with the plus sign on it and add the usb peripheral you want (it obviously needs to be plugged in)

If you take the top icon, it will create an empty filter named Filter 1.

---

### Post by ancient_ee on 2008-12-29
Thanks, Howefield. Clicking on the second icon down, naming the external storage device, did the trick.:P Still no CDROM, but that maybe should be another thread. How do you mark a thread solved?

---

### Post by howefield on 2008-12-29
> **ancient_ee said:**
> Thanks, Howefield. Clicking on the second icon down, naming the external storage device, did the trick.:P Still no CDROM, but that maybe should be another thread. How do you mark a thread solved?

Should be a thread tools option, you'll find it in there.

Have you installed guest additions ? That may have your cd tied up, having mounted the iso for guest additions, go back into settings and ensure your physical drive has selected.

---

### Post by ancient_ee on 2008-12-29
I have not installed guest additions, though I probably will now that I have researched it. In any case, that does not seem to be the issue regarding lack of CDROM in WinXP virtual box.

---

### Post by howefield on 2008-12-29
> **ancient_ee said:**
> I have not installed guest additions, though I probably will now that I have researched it. In any case, that does not seem to be the issue regarding lack of CDROM in WinXP virtual box.

Well worth installing, for the mouse doesn't get captured in the vm, better video drivers, resolutions and a host of other goodies.

Hope you get the cd sorted, I'm off for the night. Have a good one.

---

