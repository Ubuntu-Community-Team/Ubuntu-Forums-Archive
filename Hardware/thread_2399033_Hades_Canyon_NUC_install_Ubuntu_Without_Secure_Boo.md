---
title: "Hades Canyon NUC install Ubuntu Without Secure Boot"
date: 2018-08-21
forum: Hardware
---

### Post by garret-picchioni on 2018-08-21
Hello,
I'm cross posting from the intel support forums per their advice: In short, I have a Hades Canyon NUC (NUC8i7HVK) that will be running Ubuntu Server (I've tried 16.04 and 18.04 LTS releases so far) with VirtualBox on it. I'm installing VirtualBox straight from their repo instead of using Ubuntu's DKMS packages, so I need to disable Secure Boot. However when I disable Secure Boot via the checkbox in the following menu: Advanced->Boot->Secure Boot->Uncheck Secure Boot, Ubuntu completely stops booting. This is whether I'm attempting to boot Ubuntu from the local disk, or an Ubuntu Flash Drive installer. Grub displays, I can select a boot option (either Ubuntu or Install Ubuntu Server depending on if I'm attempting to boot from local disk or Flash Drive), the screen goes black (using HDMI) and all of the USB ports stop functioning (Keyboard, Mouse, etc...). As soon as I reenable Secure Boot, Ubuntu boots just from from the local installed copy or from USB installer...rinse wash and repeat. I've tried everything I can think of and can't find a resolution. I've tried updating the bios, clearing secure boot data, booting with nomodeset, and a few other things, none of which has worked. Does anyone have any ideas on what the issue could be? I can confirm UEFI booting is still enabled and my flash drive is setup with UEFI and not legacy bios. It seems to be specifically surrounding disabling secure boot. If anyone has any tips/tricks I'd truly appreciate it!

Thanks

---

### Post by dankegel on 2018-09-05
I just ran into this, too.  I'm installing on the slower variant of Hades Canyon, NUC8i7HNB,
and it just wouldn't do anything after the grub prompt unless I enabled secure boot.

---

### Post by dankegel on 2018-11-12
As of today, I was able to disable secure boot after installing 18.04 and updating.  In fact, I had to in order to silence the new grub warnings...

---

