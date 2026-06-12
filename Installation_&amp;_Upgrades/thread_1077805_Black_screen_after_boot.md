---
title: "Black screen after boot"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by maclinux on 2009-02-22
I've completed the 8.10 upgrade and after restarting it loads up and goes into a black screen with no prompt at all. When restarting I find in grup the kernel upgrades and if I choose the 8.04 kernel it loads up perfectly and with the new upgrade to 8.10. The going into the blackbox after loading also happens while trying to install from de 8.10 cd. Live cd or straight to install it goes straight into a black screen. with 8.04 everything is always fine.

What is happening? How can I go around it?

---

### Post by Dj TweeX on 2009-02-23
it could be a conflict with your video card. are you using restricted drivers for video?
what video card is it?

---

### Post by maclinux on 2009-02-23
> **Dj TweeX said:**
> it could be a conflict with your video card. are you using restricted drivers for video?
what video card is it?

I'm sorry I was not more specific.  It's an onboard video card.  Old hardware in perfect conditions. HP Vectra, Pentium III, 512k Ram.  I don't know which video card.  How do I check it under linux.  Do I have to reboot in windows?

Thanks.

---

### Post by Dj TweeX on 2009-02-24
> **maclinux said:**
> I'm sorry I was not more specific.  It's an onboard video card.  Old hardware in perfect conditions. HP Vectra, Pentium III, 512k Ram.  I don't know which video card.  How do I check it under linux.  Do I have to reboot in windows?

Thanks.

you need to find the chipset.
im not sure how to do this in linux but you can check in windows with a program called CPUZ

---

### Post by maclinux on 2009-02-24
This is the info on the chipset:

Video Adapter Intel(R) 82815 Graphics Controller (Microsoft Corporation)  (32 MB)
3D Accelerator  Intel i752

---

### Post by maclinux on 2009-02-24
> **Dj TweeX said:**
> you need to find the chipset.
im not sure how to do this in linux but you can check in windows with a program called CPUZ

This is the info on the chipset:

Video Adapter Intel(R) 82815 Graphics Controller (Microsoft Corporation) (32 MB)
3D Accelerator Intel i752

Will this help to find the problem?
Thanks

---

### Post by avtolle on 2009-02-24
This might be applicable: [http://www.ubuntu.com/getubuntu/releasenotes/810#Hangs%20with%20desktop%20effects%20on%20Intel%20830MG%20and%20845G%20video%20cards](http://www.ubuntu.com/getubuntu/releasenotes/810#Hangs%20with%20desktop%20effects%20on%20Intel%20830MG%20and%20845G%20video%20cards)
if you had visual effects enabled under 8.04 when you did the upgrade. Once installed, it would seem to me that you would need to disable the effects to get past the black screen problem by perhaps removing compiz at the command line. First, though, can you boot into the updated kernel in recovery mode to get to a command line? If you can, type ```
xfix
```and see if that helps.

---

### Post by maclinux on 2009-03-11
> **avtolle said:**
> This might be applicable: [http://www.ubuntu.com/getubuntu/releasenotes/810#Hangs%20with%20desktop%20effects%20on%20Intel%20830MG%20and%20845G%20video%20cards](http://www.ubuntu.com/getubuntu/releasenotes/810#Hangs%20with%20desktop%20effects%20on%20Intel%20830MG%20and%20845G%20video%20cards)
if you had visual effects enabled under 8.04 when you did the upgrade. Once installed, it would seem to me that you would need to disable the effects to get past the black screen problem by perhaps removing compiz at the command line. First, though, can you boot into the updated kernel in recovery mode to get to a command line? If you can, type ```
xfix
```and see if that helps.


Thanks a lot.  it's fixed.

---

