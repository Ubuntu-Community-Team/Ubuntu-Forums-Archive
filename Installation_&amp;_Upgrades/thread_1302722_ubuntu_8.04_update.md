---
title: "ubuntu 8.04 update"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by mosaic2s on 2009-10-27
About a week, Ubuntu 8.04 LTS updated to 
Ubuntu 8.04.3 LTS, kernel 2.6.24-**25**-generic

However, I did not update the grub menu list at that time. So my machine runs 
Ubuntu 8.04.3 LTS, kernel 2.6.24-**24**-generic

Can I now edit  the existing grub menu so that latest kernel is used?

---

### Post by BigG123 on 2009-10-27
If you updated Ubuntu with ```
sudo do-release-upgrade -d 
``` you don't have to touch grub.

---

### Post by slakkie on 2009-10-27
When that kernel was installed, grub has added it already. You need to reboot to run that kernel..

---

### Post by slakkie on 2009-10-27
> **BigG123 said:**
> If you updated Ubuntu with ```
sudo do-release-upgrade -d 
``` you don't have to touch grub.

-d is only to upgrade to development releases. Normal upgrades can do without the -d...

---

### Post by mosaic2s on 2009-10-27
I am using LTS version and sticking to it. So updates are done to LTS version without upgrading to the 8.10 or 9.04.

However, the kernal gets updated about once in 4 months or so.

I had made some changes in the grub menu file hence I did not accept the updation to grub menu while the updation was on. Now, I wish to edit the grub menu file so that latest kernel installed in my system can be used. But I have no idea where the kernel versions may be saved.

Is there a way to access the new but not applied grub menu file?

---

### Post by slakkie on 2009-10-27
update-grub regenerates the file, which is located at /boot/grub/menu.lst

---

### Post by mosaic2s on 2009-11-13
slakkie 	 		**Re: ubuntu 8.04 update**
 		update-grub regenerates the file, which is located at /boot/grub/menu.lst


yes. that did the job.
THANKS.

---

