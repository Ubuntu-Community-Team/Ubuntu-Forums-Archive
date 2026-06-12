---
title: "Issues installing XP after failed attempt to use ubuntu"
date: 2008-09-01
forum: General Help
---

### Post by rjameskettere on 2008-09-01
I am working with a Compaq Presario C700 laptop.  I installed ubuntu on it only to discover an extreme incompatibility with my broadcom chipset.  I am not looking to resolve that issue.  I am attempting to install windows XP onto the machine.  I boot the disk and setup runs through its initial blue screen steps.  After the "setup is starting windows" message, I am returned this error:

Setup did not find any hard disk drives installed in your computer.  Make sure any hard disk drives are powered on and properly connected to your computer, and that any disk-related hardware configuration is correct.  This may involve running a manufacturer-supplied diagnostic or setup program.

Setup cannot continue.  To quit setup, press F3.

I am able to boot into the Ubuntu installation just fine, indicating that there certainly is a hard drive powered and connected properly.  I am assuming this has to do with the way Ubuntu formatted my hard drive.  How can I resolve this and get Windows XP running on my machine?  Any help would be greatly appreciated.

---

### Post by overdrank on 2008-09-01
> **rjameskettere said:**
> I am working with a Compaq Presario C700 laptop.  I installed ubuntu on it only to discover an extreme incompatibility with my broadcom chipset.  I am not looking to resolve that issue.  I am attempting to install windows XP onto the machine.  I boot the disk and setup runs through its initial blue screen steps.  After the "setup is starting windows" message, I am returned this error:

Setup did not find any hard disk drives installed in your computer.  Make sure any hard disk drives are powered on and properly connected to your computer, and that any disk-related hardware configuration is correct.  This may involve running a manufacturer-supplied diagnostic or setup program.

Setup cannot continue.  To quit setup, press F3.

I am able to boot into the Ubuntu installation just fine, indicating that there certainly is a hard drive powered and connected properly.  I am assuming this has to do with the way Ubuntu formatted my hard drive.  How can I resolve this and get Windows XP running on my machine?  Any help would be greatly appreciated.
Hi and welcome, you can use the live cd and createa fat partition for windows install. Use the partition editor on the live cd located under system administration, resize the ubuntu partition and then create the one for windows. Then after the windows installation you may look here to recover ubuntu.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by prshah on 2008-09-01
> **rjameskettere said:**
> 
Setup did not find any hard disk drives installed in your computer.

I am assuming this has to do with the way Ubuntu formatted my hard drive.  How can I resolve this and get Windows XP running on my machine?

Wrong assumption. 

Your hard disk drive is probably SATA, for which Windows XP does not have drivers:

Workarounds/Solutions:

1) check if there is an option in the BIOS similar to "SATA/IDE compatible mode" / "SATA: Legacy" / "SATA: Native" / "IDE: Legacy" etc; something that makes the SATA show up as IDE.

==OR==

2) slipstream the SP3 into your Windows XP installation files.

==OR==

3) Get a SATA driver disk and use that by pressing F6 when the Windows install is beginning.

This post should be in a Windows forum.

---

### Post by masmina on 2008-09-01
I don’t have so much idea regarding this subject. Just I suggest you to take steps accordingly.

---

### Post by rjameskettere on 2008-09-01
> **prshah said:**
> Wrong assumption. 

Your hard disk drive is probably SATA, for which Windows XP does not have drivers:

Workarounds/Solutions:

1) check if there is an option in the BIOS similar to "SATA/IDE compatible mode" / "SATA: Legacy" / "SATA: Native" / "IDE: Legacy" etc; something that makes the SATA show up as IDE.

==OR==

2) slipstream the SP3 into your Windows XP installation files.

==OR==

3) Get a SATA driver disk and use that by pressing F6 when the Windows install is beginning.

This post should be in a Windows forum.

Hhm...extremely helpful...with a hint of cheeky prick...delicious!  Thanks!

:lolflag::lolflag::lolflag::lolflag::tongue::-({|=:-({|=[-X

---

### Post by prshah on 2008-09-01
> **prshah said:**
> Wrong assumption. 
This post should be in a Windows forum.

> **rjameskettere said:**
> with a hint of cheeky prick

Err.. let me rephrase; I meant this post showed be moved to the sub-forum related to windows.

No offense intended, and glad to see none taken.

---

### Post by matdombrock on 2008-09-02
Hey sorry to hear that ubuntu didn't work out for you. The people on these forums somtimes dont like to admit it but linux has prety crappy device support. 

Anyway you should make sure that you delete the ubuntu partition while in the windows installer then format your hard drive to NTFS. That may be WAY off from your issue but it's worth a try.

---

