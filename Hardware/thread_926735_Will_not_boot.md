---
title: "Will not boot"
date: 2008-09-22
forum: Hardware
---

### Post by profexcon on 2008-09-22
Hello, I recently switched from vista to Ubuntu two days ago. Since the switch, i have had to reinstall the OS twice, and now maybe a third time. After I install Ubuntu, my machine works very good. But once I restart, the desktop will not boot. After the Ubuntu logo & preloader displays, a black screen follows. This is the second time this has happened. Below are my machine specs:

Manufacturer: Toshiba
Model: Satellite A135-S2346
Processor: Intel (Celeron M)
Graphics (ATI)
OS Machine was distributed with: Windows Vista (Home Basic)

Any assistance with this is very much appreciated.

---

### Post by IntuitiveNipple on 2008-09-22
This sounds as if the display driver configuration is somehow incorrect.

Can you be more specific about when the black-screen occurs. You see the 'splash' screen with the Ubuntu logo and animated progress bar... does it display a log-in screen asking for user-name before the blackness occurs, or do you never see that?

---

### Post by profexcon on 2008-09-22
> **IntuitiveNipple said:**
> This sounds as if the display driver configuration is somehow incorrect.

Can you be more specific about when the black-screen occurs. You see the 'splash' screen with the Ubuntu logo and animated progress bar... does it display a log-in screen asking for user-name before the blackness occurs, or do you never see that?

First of all, thanks for helping me. To answer your question, No - the login screen never shows. It goes from the animated progress bar, straight to a completely black screen. However, immediately following the fresh install of Ubuntu, I had no problems. Everything worked great, until after I tried to restart, which was approximately 15hrs after I installed.

---

### Post by IntuitiveNipple on 2008-09-22
> **profexcon said:**
> However, immediately following the fresh install of Ubuntu, I had no problems. Everything worked great, until after I tried to restart, which was approximately 15hrs after I installed.
That statement is slightly confusing so let me try to clarify.

How did you install Ubuntu? If it was using the Live CD then, after the installer has completed, the system is still using the Live CD configuration.

The fresh installation won't be used until the system is restarted (without the CD in the drive) and boots from the new files installed to the hard disk.

When the system starts, as soon as the BIOS messages are done, press **Esc**ape to access the GrUB boot menu. From there, try using the Recovery option to boot and report back on what happens.

---

### Post by profexcon on 2008-09-22
> **IntuitiveNipple said:**
> 
When the system starts, as soon as the BIOS messages are done, press **Esc**ape to access the GrUB boot menu. From there, try using the Recovery option to boot and report back on what happens.

I followed your instructions and am still unable to boot from the hard drive. My version of Ubuntu is ([Ubuntu 8.04 LTS Desktop Edition - Supported to 2011]("http://www.ubuntu.com/getubuntu/download"), I installed it after downloading the image, and burning it to a disk. I have restarted since the installation, twice without needing the original disk.

---

### Post by castle4dracula on 2008-09-22
I have had exactly the same problem as you.  I have a packard bell r1005 laptop, with XP on it.  I downloaded the ubuntu 8.04 iso and burned it to disc, then ran the installation sequence and installed it as dual boot system.  

On completeion of install, I removed the CD as requested, then the laptop rebooted.  Ubuntu hadn't recognised the lcd driver, so was stuck in 800 x 600 resolution, but did boot up.  Then it downloaded updates, installed them, then asked for a restart.  

That was the end of ubuntu!  The animated bit appeared, but no login, just a black screen, and ubuntu didn't load.

I tried using the ubuntu recovery option, but got nowhere with it.

As I'm new to linux and have no idea what i'm doing when looking at the command line i gave up.  I'm now back using XP, and feeling quite disappointed about ti too, as I really liked the look of ubuntu.

Any help would be great , thanks.

---

### Post by profexcon on 2008-09-22
> **castle4dracula said:**
> 
I tried using the ubuntu recovery option, but got nowhere with it.

As I'm new to linux and have no idea what i'm doing when looking at the command line i gave up.  I'm now back using XP, and feeling quite disappointed about ti too, as I really liked the look of ubuntu.

I just want to say that I agree with you. This was my first Linux OS and I really like the look and feel of it. It is a little bumpy moving over, but I believe it will be worth it in the long run :)

---

### Post by profexcon on 2008-09-23
Yesterday, shortly after my last reply, I reinstalled Ubuntu from my disk. Since then it has been running great. So far so good. I just hope it crash again.

---

