---
title: "Ubuntu install from freeBSD?"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by barnacles on 2009-02-17
So I haven't been able to find the answer on the freeBSD forums so I thought I would give these a shot. I installed ubuntu on my laptop and love it. So I decided to install it on my desktop as well. The desktop currently has been completely formatted and just has freeBSD on it. I want to install unbuntu on it now though. I have an installer DVD, and have enabled boot from CD in the bios, but when i put in the cd and restart nothing happens. It just boots the freebsd loader. When the CD is in and i start it, it hangs for a while with a blinking cursor while the cd drive light blinks. But after waiting like i said it just boots freeBSD. Any help would be greatly appreciated.

---

### Post by avtolle on 2009-02-17
You are booting from a DVD, correct? Is the drive on the desktop a CD-ROM only, or is it a DVD-ROM?

---

### Post by barnacles on 2009-02-17
it is a samsung dvd rom. when freebsd is loading it acknowledges there is a disc in the drive.

---

### Post by avtolle on 2009-02-17
Next question, now that a potential hardware problem has been eliminated; the DVD you are using; did you download the iso and burn it yourself, or did you obtain the DVD from a third party source? If you downloaded the iso and burned it yourself, before burning, did you check the md5sum of the iso to be sure it passes? The reason for the question; it sounds like a bad DVD. Another thought: have you tried cleaning your DVD drive?

---

### Post by barnacles on 2009-02-17
I actually acquired the disc in a magazine. It is the same disc I used on my laptop, so I know the disc works. Its scratch free which eliminates the possibility of the disc being unreadable. 

If the drive itself needed cleaned, wouldn't it not notice the disc at all?

---

### Post by ebooa on 2009-03-10
probably a stupid question but how did u processed the disc boot option??

did u just changed the booting order and switched dvd-rom to primary boot or did u use the boot console?

another thing, have u tried to download some sort of ubuntu iso burned it with boot and tried to install even if the current installation dvd u have is perfectly ok?

---

### Post by Mr-Biscuit on 2009-03-14
Is the BIOS set to boot from the cdrom?

Have someone burn a CD for you and verify the hash then install.

---

