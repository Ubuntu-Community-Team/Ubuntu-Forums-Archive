---
title: "Changing from CRT monitor to LCD monitor"
date: 2005-10-10
forum: Hardware &amp; Laptops
---

### Post by chettyk on 2005-10-10
I have an old Pentium III computer that I use principally to retain backups of all my files and this computer runs on Hoary. I am planning to change the computer's monitor from a power-hogging CRT to a LCD monitor. Would Hoary automatically recognise and configure the new LCD monitor on bootup or do I tweak somewhere or the other, perhaps the xorg.conf file or by running "dpkg-reconfigure xserver-xorg"? Or (shudder) do I reinstall Ubuntu if all else fails?

Any advice and warnings would be most welcome. Thanks.

---

### Post by landotter on 2005-10-10
Here's what I did:

turned off computer
installed monitor
turn computer on

and it all just automagically worked.

LCDs are pretty standard compared to CRTs, you shouldn't have any problems.

---

### Post by chettyk on 2005-10-10
Thanks a bunch, landotter. I was hoping that was the case, i.e. Ubuntu would automatically recognise the new LCD monitor and configure it suitably. What made me a little nervous was that Ubuntu doesn't seem to have system admin options, like those in Fedora and Suse, that help one configure the monitor.

---

### Post by DJ_Max on 2005-10-10
[QUOTE=chettyk]I have an old Pentium III computer that I use principally to retain backups of all my files and this computer runs on Hoary. I am planning to change the computer's monitor from a power-hogging CRT to a LCD monitor. Would Hoary automatically recognise and configure the new LCD monitor on bootup or do I tweak somewhere or the other, perhaps the xorg.conf file or by running "dpkg-reconfigure xserver-xorg"? Or (shudder) do I reinstall Ubuntu if all else fails?

Any advice and warnings would be most welcome. Thanks.[/QUOTE]
No reinstalling, this is not Windows. Ubuntu will try it's best to hotplug the new LCD, but if it doesn't, than just reconfigure it, as you posted.

---

### Post by chettyk on 2005-10-10
[QUOTE=DJ_Max]No reinstalling, this is not Windows. Ubuntu will try it's best to hotplug the new LCD, but if it doesn't, than just reconfigure it, as you posted.[/QUOTE]

Will do. Thanks DJ_Max.

---

