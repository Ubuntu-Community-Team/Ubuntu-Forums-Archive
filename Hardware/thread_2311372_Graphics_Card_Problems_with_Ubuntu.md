---
title: "Graphics Card Problems with Ubuntu"
date: 2016-01-26
forum: Hardware
---

### Post by gabrielbouzard10 on 2016-01-26
I recently purchased an R9 380X OCE (ASUS brand) and installed it in my desktop. It works great for gaming, but when I use it with Ubuntu 15.10 my screen will not uncommonly do the following: freeze for 3 seconds completely, go black, and finally go back to the desktop where the only thing not frozen is my mouse. If I am lucky I can log out of my session (even though the screen is frozen) by pressing Ctrl-Alt-Delete and then Enter. Then I just log back in. Most of the time, though, I have to restart my computer. In either case, I loose all of my current work and have to recover from backup files. If, when the screen is frozen, I switch to one of the other (non-gui) user sessions by pressing, for example, alt-f2, I cannot type anything because there is a constant stream of the following on the console:

```
[COLOR=#000000][FONT=arial]drm:amdgpu_gem_va_ioctl [amdgpu]] *ERROR* Couldn't update B0_VA (-22)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]amdgpu 0000:01:00.0: couldn't schedule ib[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]drm:amdgpu_gem_va_ioctl [amdgpu]] *ERROR* Couldn't update B0_VA (-22)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]amdgpu 0000:01:00.0: couldn't schedule ib[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]drm:amdgpu_gem_va_ioctl [amdgpu]] *ERROR* Couldn't update B0_VA (-22)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]amdgpu 0000:01:00.0: couldn't schedule ib[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]drm:amdgpu_gem_va_ioctl [amdgpu]] *ERROR* Couldn't update B0_VA (-22)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]amdgpu 0000:01:00.0: couldn't schedule ib[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]drm:amdgpu_gem_va_ioctl [amdgpu]] *ERROR* Couldn't update B0_VA (-22)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]amdgpu 0000:01:00.0: couldn't schedule ib[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]drm:amdgpu_gem_va_ioctl [amdgpu]] *ERROR* Couldn't update B0_VA (-22)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]amdgpu 0000:01:00.0: couldn't schedule ib[/FONT][/COLOR]

```

I cannot tell if this is a problem with Ubuntu 15.10 or my graphics card. I tried contacting AMD support and they have not gotten back to me. Here are some of my questions about how I should proceed. 

[LIST]
[*]Asus has a driver specifically for Ubuntu 14.*. If I install this, will it work with Ubuntu 15.10?
[*]If I install an Ubuntu driver, will I still be able to game on Windows?
[*]Should I downgrade to Ubuntu 14.*? I know this is very tricky.
[*]In general if I dual boot, what set of drivers should I use for the graphics card?  (Windows or Linux).
[*]If there is no workaround for this, is it possible to use two graphics cards and have one boot with Ubuntu and the other with Windows (I don't need a good graphics card for what I do on Ubuntu, and previously I had a 35 dollar graphics card in the box which worked great with Ubuntu).
[/LIST]

---

### Post by QIII on 2016-01-26
If you are dual booting, each OS will use its own driver.  They will not conflict.  Use the Windows driver when Windows is running and the Linux driver when Linux is running.

These are new adapters, so the open source driver may not have caught up to them yet.  Install fglrx-updates from the repository.

Don't install the Asus driver, which is probably a Windows installer.

---

### Post by gabrielbouzard10 on 2016-01-26
Thank you. That is what I needed to know. I will try this out and let you know how it goes.

---

### Post by Yellow Pasque on 2016-01-26
> **gabrielbouzard10 said:**
> I cannot tell if this is a problem with Ubuntu 15.10 or my graphics card.
Probably with Ubuntu since the "amdgpu" kernel module/driver is very new. Are you running the open-source radeon 3D driver on top of amdgpu or are you using a Catalalyst/fglrx blob? I agree with QIII that the blob will probably give you the best support at the moment. Some background reference:
[http://www.phoronix.com/scan.php?page=article&item=amd-tonga-linux42&num=1](http://www.phoronix.com/scan.php?page=article&item=amd-tonga-linux42&num=1)
[https://www.phoronix.com/scan.php?page=news_item&px=Linux-4.5-rc1-AMDGPU-Kernel](https://www.phoronix.com/scan.php?page=news_item&px=Linux-4.5-rc1-AMDGPU-Kernel)

> I tried contacting AMD support
LOL.

> Asus has a driver specifically for Ubuntu 14.*. If I install this, will it work with Ubuntu 15.10?
Probably not, but give a link to be sure. I'm guessing it's an older version of Catalyst that won't support your card and/or newer kernels.

> ]If I install an Ubuntu driver, will I still be able to game on Windows?
Installing a driver on one OS will not affect the other.

> Should I downgrade to Ubuntu 14.*? I know this is very tricky.
No. If you're looking for better driver support for such a new card, it would more likely for 16.04 to help you out even though it's in pre-release. 

> In general if I dual boot, what set of drivers should I use for the graphics card?  (Windows or Linux).
If you don't want to do intensive 3D on Ubuntu/Linux, it's generally better to stick with the open source drivers. Your card's an exception because it's new and AMD is shifting to a new driver strategy.

> Is it possible to use two graphics cards and have one boot with Ubuntu and the other with Windows
Yes. It will be easier to configure in Linux/Ubuntu if the cards use different drivers.

---

### Post by gabrielbouzard10 on 2016-01-27
Installing the  fglrx-updates fixed the problem; I have been using my computer for several hours with no problem. And Temujin you clarified some things for me. I was clueless about drivers. For some reason I thought of them more as firmware that sits on the card.

---

