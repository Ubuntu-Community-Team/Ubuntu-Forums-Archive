---
title: "keyboard and mouse doesnt work when upgrading to 9.04"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by keridito on 2009-04-25
Hello,
I have an issue with both the mouse and the keyboard just after upgrade to 9.04 (from 8.10). After booting, in the login screen, neither mouse or keyboard work. Even if you plug any other device. But if I boot in safemode, and in the action screen I choose resume, then the system works perfectly!!!! I have this problem in my two computers, in the laptop and in the desktop...

I connected through ssh to my desktop, and hal seems to work fine...

Any suggestions?

Thanks in advance.

---

### Post by szegedy on 2009-04-26
I have exactly the same problem. I've tried to start ubuntu 9.04 with the older kernel (28) and it worked, and sometimes even the latest works.

---

### Post by keridito on 2009-04-27
I have not tried with the old kernel... I always boot with the safety option and then resume... I think that is not the most convenient method, but at least the system run... And I don't know if there will be some update to fix it...

Best regards,
K.

---

### Post by pistos on 2009-04-27
I have a similar problem in that my laptop will boot up and run as expected, if and only if, I have my USB mouse plugged in at boot up time. But, if I don't have the USB mouse plugged in at boot up, then my keyboard and touch pad work enough for me to get logged in and then a short time later (within 30 seconds), the keyboard and touch pad buttons stop working, and the tracking of the cursor with the touch pad becomes very jerky and laggy. I have to hard reset the machine at that point.

I suspect it to be a bug of some kind in the open source radeon graphics driver, but have not been able to confirm this.

My laptop is an Acer Travelmate 8003 with an ATI Radeon 9700 Mobility chip set with dedicated video memory of 128. That means I am not able to use the latest ATI drivers. I have to use either the vesa driver or the open source radeon driver.

BTW: Old and new kernel have no effect on my issue.

---

### Post by chrisinspace on 2009-05-02
I'm having a similar issue.  About every other time I boot my laptop (see specs in sig), my keyboard and touch pad don't work.  If I reboot, it usually works the next time the system comes up.  Occasionally, it takes a couple of reboots, but I haven't had use safe mode or regress kernels.  Any idea what's causing this?  pistos, you mentioned you think it might have something to do with the ATI driver.  Why would the video driver affect your keyboard/touch pad.  Do you think the drivers are causing X to just freak out in general?  Has anyone come across a solution yet or do you think we'll have to wait for a kernel update?

---

### Post by pistos on 2009-05-02
> **chrisinspace said:**
> pistos, you mentioned you think it might have something to do with the ATI driver.  Why would the video driver affect your keyboard/touch pad.  Do you think the drivers are causing X to just freak out in general?  Has anyone come across a solution yet or do you think we'll have to wait for a kernel update?

My reasoning may be faulty, but when I was using the basic VESA graphics driver, everything appeared to be working OK with my initial upgrade. The problem was, the performance of my machine was suffering after the upgrade using the VESA driver. So, I installed the ATI Catalyst driver, hoping it would give me hardware accelerated graphics and address the performance problem. But, installing the ATI Catalyst driver was a huge mistake because my graphics setup is no longer supported with the new ATI driver from ATI. My machine was almost lost for good. I finally got the ATI driver uninstalled, and replaced with the open source ATI driver which does support my graphics setup. The performance is decent again. But, that is when this weird touchpad button/keyboard problem cropped up.

So, in my fumbling through, the touchpad button/keyboard problem on my machine appears to be related to the use of hardware accelerated graphics. As I think I stated before, if I knew how to reactivate the VESA drivers, without messing my machine up, I could test to see if the problem goes away at that point. But, I am a noob when it comes to Linux, needing serious hand holding through almost anything that ventures outside of the GUI.

---

### Post by mitchd123 on 2009-05-02
I had this problem with my mouse when I booted to the install CD.   Simply unplugging and replugging the USB mouse solved the problem.     Unfortunately you can't do this on a laptop.

---

