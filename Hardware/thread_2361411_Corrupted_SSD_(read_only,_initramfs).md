---
title: "Corrupted SSD (read only, initramfs)?"
date: 2017-05-16
forum: Hardware
---

### Post by sif00x on 2017-05-16
Hi

I installed Kubuntu 16.10 on Intel 600p M.2 512GB SSD NVMe drive. Everything was fine for two or three months but about one week ago errors started to occur. I'm not aware that I'd done anything that may lead to errors. Extremely irregularly the SSD was going to read-only state during any kind of activity (text writing, web browser, movie playing, ...). The only possibility was to reboot the computer, the system didn't start and instead of that "(initramfs)" error appeared. I had to run "fsck /dev/kubuntu-vg/root" which removed some errors and than the system started normally. Sometimes everything was fine for a whole day, sometimes the error occurred several times per hour.

I tried to run fsck when the system was fine and it gave me no error. SMART also does not report any problem and according to online discussion I understood that it may be also cause by a corrupted OS. Therefore, I decided to reinstall Kubuntu (SSD format, new installation of 17.04) but the problems persist! I rewrote everything with dd if=/dev/urandom and it gave me no error (does it mean that the SSD is fine?).

Do you have any idea what causes the errors? Is is a hardware problem or a bug in Kubuntu? How should I test it?

---

### Post by LastDino on 2017-05-16
Hi!
Kind of shooting in the dark, but had a similar problem with friends SSD where SMART would not report any error but would have read/write problems and slowness issues. It was resolved after "firmware update" for the SSD and BIOS updates for motherboard.

It is highly unlikely that Kubuntu has problem in general with SSD, or there would've been bug-reports of same. But you never know for sure.

---

### Post by sif00x on 2017-05-16
> **LastDino said:**
> Hi!
It was resolved after "firmware update" for the SSD and BIOS updates for motherboard.
Thank you. Do you have any idea how to find out if this is really causing the problem?

---

### Post by LastDino on 2017-05-16
> **sif00x said:**
> Thank you. Do you have any idea how to find out if this is really causing the problem?


No, this is where we got to when trying out everything we could and this one finally worked. 

You can find firmware by intel for your model, it should be in ISO format and you can install it through CD/DVD/Live usb system

/There might be some way to check if this is actually the problem, but we were not able to find it back then.

---

### Post by sif00x on 2017-05-29
I updated the firmware of my SSD and I haven't experienced the problem since that time. Thanks!

---

