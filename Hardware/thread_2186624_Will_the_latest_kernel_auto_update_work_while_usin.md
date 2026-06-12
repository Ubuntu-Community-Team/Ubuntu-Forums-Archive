---
title: "Will the latest kernel auto update work while using the latest AMD beta drivers?"
date: 2013-11-08
forum: Hardware
---

### Post by DanglingPointer on 2013-11-08
Hi All,

The Ubuntu Update Manager has Kernel updates.  I am currently using the latest Catalyst Beta drivers from AMD (3.11).
So the question is...
1) Do I need to uninstall the non-repo driver first; then update via Update Manager; then reinstall the latest and greatest from AMD?
Or
2) Can I just update without worrying about the AMD driver?

---

### Post by gordintoronto on 2013-11-08
2.

---

### Post by QIII on 2013-11-08
Personally, I'd recommend the first.

If you installed outside the package management system, the package management system will not know to reinstall the driver.  This can lead to sorts of excitement, including being dropped to the shell with no GUI.  I'd uninstall the driver, rename Xorg.conf as a backup, run the kernel upgrades and reinstall the driver when you get done.

If you install the driver from the repo, you don't need to do all that horsing around.

---

### Post by kostkon on 2013-11-08
> **QIII said:**
> Personally, I'd recommend the first.

If you installed outside the package management system, the package management system will not know to reinstall the driver.  This can lead to sorts of excitement, including being dropped to the shell with no GUI.  I'd uninstall the driver, rename Xorg.conf as a backup, run the kernel upgrades and reinstall the driver when you get done.

If you install the driver from the repo, you don't need to do all that horsing around.
Most drivers nowadays support DKMS (for example, I'm pretty sure the Nvidia driver is DKMS aware), plus Xorg.conf is not used anymore by X, at least not by default.

---

### Post by QIII on 2013-11-08
If you make a .deb of it and install it that way, dkms will work.  That's using the package management system.  Using the .run can cause problems.

No, xorg.conf is not used by default.  But one is created by initializing the AMD driver.

---

### Post by DanglingPointer on 2013-11-09
Thanks everyone for your input but unfortunately I only got Gorditoronto's response on my email notification so as soon as I got home I just updated!  LoL
I just read all your views now.

So far it looks like it is working.  Should I reinstall the driver anyway to play safe?

Hmmm... I'll run Unigine Heaven and Valley tests to confirm...

---

### Post by QIII on 2013-11-09
If you followed instructions that had you create a .deb file, you are probably good.

To be sure, would you please post the results of 

```
fglrxinfo
```

---

### Post by DanglingPointer on 2013-11-09
> **QIII said:**
> If you followed instructions that had you create a .deb file, you are probably good.

To be sure, would you please post the results of 

```
fglrxinfo
```

Its a Radeon HD 5870

```
:~$ fglrxinfodisplay: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Radeon HD 5800 Series
OpenGL version string: 4.3.12614 Compatibility Profile Context 13.25.18



```

---

