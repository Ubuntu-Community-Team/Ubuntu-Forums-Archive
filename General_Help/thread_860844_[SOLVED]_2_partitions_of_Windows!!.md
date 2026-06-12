---
title: "[SOLVED] 2 partitions of Windows?!?!?"
date: 2008-07-16
forum: General Help
---

### Post by Bbman90 on 2008-07-16
I use Linux for almost everything now. However, my father and the rest of my family insist on using Windows. Recently there was a problem on Windows. It said that some system files had been changed. It was going crazy, so my dad asked me to reinstall it. After I did, the boot loader screen refused to come up. Windows was the only option. Thinking that it had ate Linux, I put in the Live CD and began to reinstall it. However, at the partition stage of the installation, all of my old partitions for Linux are there. Some parts of them are used, indicating to me that my files are still there. Additionally, there is a new Fat32 partition about 4,000 MB. When I looked at it, it turned out to be Windows! A still have a 70 GB partition of Windows as well. I don;t know what's going on anymore. Do I still have Linux, do I have Windows twice, can I delete the small Windows, what happened?

---

### Post by oldos2er on 2008-07-16
When you reinstalled Windows, it overwrote grub with its own bootloader. You still have Linux. If you have an Ubuntu live cd, I think you can run update-grub from there. Or download Super Grub Disk and use that.

---

### Post by p_quarles on 2008-07-16
> **Bbman90 said:**
> I use Linux for almost everything now. However, my father and the rest of my family insist on using Windows. Recently there was a problem on Windows. It said that some system files had been changed. It was going crazy, so my dad asked me to reinstall it. After I did, the boot loader screen refused to come up. Windows was the only option. Thinking that it had ate Linux, I put in the Live CD and began to reinstall it. However, at the partition stage of the installation, all of my old partitions for Linux are there. Some parts of them are used, indicating to me that my files are still there. Additionally, there is a new Fat32 partition about 4,000 MB. When I looked at it, it turned out to be Windows! A still have a 70 GB partition of Windows as well. I don;t know what's going on anymore. Do I still have Linux, do I have Windows twice, can I delete the small Windows, what happened?
The "new" partition may be a hidden Windows recovery partition. This would just be an image of the OEM Windows installation disk. Many Windows boxes ship with these partitions rather than actual reinstallation media. 

Ultimately, the only way you'll know what's in there is to look, though.

---

### Post by Sef on 2008-07-16
> download Super Grub Disk and use that

[Super GRUB Disk]("http://www.supergrubdisk.org/")

That disk makes it real easy to reinstall GRUB.

---

### Post by Bbman90 on 2008-07-16
Thank you for the excellent replies. However, I do not have access to the internet on Windows. I'm currently using an Ubuntu Live CD. Trying to get that worked out... I have about 4 GB of unallocated space left on my drive now. Could I reinstall Linux there, download the disk, use, then delete the new Linux? Could Linux be on the same system with itself? Dual Booting Linux, something nobody should ever have to do...

---

### Post by p_quarles on 2008-07-16
No need to download another disk:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Bbman90 on 2008-07-16
Thank You!!! I have restored Ubuntu. I shall mark this thread as solved.

---

