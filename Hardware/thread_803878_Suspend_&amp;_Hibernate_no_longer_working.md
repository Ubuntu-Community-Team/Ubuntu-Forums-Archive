---
title: "Suspend &amp; Hibernate no longer working"
date: 2008-05-22
forum: Hardware
---

### Post by dob99 on 2008-05-22
Hi,
I just upgraded to 8.04 and hibernate has stopped working. (I actually did a fresh install.) It was working fine in 7.10 and what happens now is the screen goes blank (not even a cursor) and then nothing, but the machine doesn't turn off and I have to do a cold reset to get it back. The same thing happens with Suspend.

I have tried disabling Compiz (as suggested elsewhere) with no luck. I also tried disabling the NVidia driver, but this wasn't workable as I couldn't then get a decent resolution.

I also upgraded my laptop from 7.04 (through 7.10) and hibernate appears to work correctly there.

Any help appreciated.

---

### Post by anthopleura_elegantissima on 2008-05-23
I have the same problem.  

I am running hardy heron on an HP Pavillion dv6000 (dual boot with windows.) I upgraded from gutsy, for which the hibernate function worked.  

System has nVidia C51 [Geforce 6150 Go] (Presario V6133CL)

---

### Post by TeknoJuce on 2008-05-23
Also same problem and almost same laptop as above :D

Compaq V6120US [Geforce 6150 Go]

Any way for some direction to get to the bottom of this?

---

### Post by NightwishFan on 2008-05-23
My system hibernates fine, however it does not sucessfully sleep or wake up from this "pseudo suspend" state. It may have something to do with my nvidia graphics though.

---

### Post by TeknoJuce on 2008-05-23
I can also manually click the Suspend & Hibernate buttons in the GUI and they seem to work fine but its when I goto sleep and wakeup, I see just a black screen and the back-light seems to be on, same thing if i close the laptop before I sleep.

maybe try something from here seems like a common issue... :S  [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/34043](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/34043)

report back if anything works :/

---

### Post by cabal314 on 2008-05-23
I also have a problem with the "hibernate" option. Fesity Fawn Pentium 2 300mhz 128mb RAM with Xfce 4.2 interface.Aside from that problem I like Xubuntu:)

---

### Post by astadolfo3 on 2008-05-24
Hello,

I had both problems (hibernate and suspend) and I was able to fix them. 

If suspend is working and hibernate is not, you can try the following:

1-make sure that you have enough swap space (at least bigger than your ram size) and that swap is turned on and available to the system.

2-in the /boot/grub/menu.lst file and on the entry of my installation
added a resume option making it look like this:
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=fe14f446-7cc3-4f6a-bcde-e4c58ebab4c1 ro quiet splash resume=UUID=0b13b111-429e-4c4a-b93c-8c0f648c6ca2

Obviously you need to put the UUID of your own swap partition. You may get it at the /etc/fstab file

**Suspend (this could fix also hibernate)**

here is what I did (I'm NOT using uswsusp, but just the standard power management delivered with Hardy):

on this file, /etc/default/acpi-support edited as su, I added the module "ptyq4" to the list of modules to be suspended in this position:

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded
# unless they're listed in MODULES_WHITELIST
**MODULES="ptyq4"**

evidently the module ptyq4 was the one that got the suspend and hibernate process stuck. You can try this first. If this does not work, the module that prevents suspend is not ptyq4 in your case. You can try to find which module must be unloaded in your machine before suspend by [following this procedure]("https://wiki.ubuntu.com/DebuggingKernelSuspend?highlight=(suspend"):



Then insert the module in the file /etc/default/acpi-support

---

### Post by steveneddy on 2008-05-25
Thank you for this. I am posting here so i can find it later. I'm not sure if I am having suspend issues. When I went to lift the laptop lid this morning, it closed again after it was only up for a split second (it slipped out of my fingers) and when it resumed there was a loud beeping sound, then it tried to start up, but didn't.

I restarted and suspend seems to work well again.

It always works after let it suspend overnight so I can save my work.

I test this tonight.

---

### Post by tytoalba on 2008-05-26
> **steveneddy said:**
> Thank you for this. I am posting here so i can find it later. I'm not sure if I am having suspend issues. When I went to lift the laptop lid this morning, it closed again after it was only up for a split second (it slipped out of my fingers) and when it resumed there was a loud beeping sound, then it tried to start up, but didn't.

I restarted and suspend seems to work well again.

It always works after let it suspend overnight so I can save my work.

I test this tonight.

The native suspend/resume and hibernate/resume worked fine under hardy on my sony z1vap until today. I let update-manager pull down some updates without looking too carefully this morning and now neither works.. unloading the pty drives didn't help for me.. if anyone sorts this out, could they please post back or drop me a note?
Thanks,
jamie

---

### Post by steveneddy on 2008-05-26
I just tested and everything seems to be working fine.

I can suspend and hibernate.

---

### Post by impkokay on 2008-05-28
> **tytoalba said:**
> The native suspend/resume and hibernate/resume worked fine under hardy on my sony z1vap until today. I let update-manager pull down some updates without looking too carefully this morning and now neither works.. unloading the pty drives didn't help for me.. if anyone sorts this out, could they please post back or drop me a note?
Thanks,
jamie

I Have the same issue with my Gateway Laptop. Suspend worked fine until I let update-manager install updates yesterday. I am running 8.04 and have never experienced this problem until yesterday.

---

### Post by heavensblade23 on 2008-05-28
I also lost the ability to suspend/resume with a recent update.  Toshiba laptop.

---

### Post by heavensblade23 on 2008-05-29
Someone filed a bug, but it's incomplete.  I attempted to complete some of it.  If you're having the same problem, please help with the bug

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/235274](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/235274)

---

### Post by izanbardprince on 2008-06-09
I would like to add I'm experiencing this problem on my Gateway GM5446E desktop, on suspend and hibernate, I flipped on Hardy-Proposed and am currently downloading kernel 2.6.24-19, which mentions some power management fixes.

I'll report back when I reboot and try a suspend.

---

### Post by izanbardprince on 2008-06-09
OK, anyone that has a suspend or hibernate problem in Hardy needs to enable hardy proposed, reload your apt sources, and get kernel 2.6.24-19 and all associated modules, then I recommend disabling that repo afterwards and reloading the sources again.

This should fix all your Suspend/Hibernate problems.

---

### Post by Burrhead on 2008-06-09
> **izanbardprince said:**
> OK, anyone that has a suspend or hibernate problem in Hardy needs to enable hardy proposed, reload your apt sources, and get kernel 2.6.24-19 and all associated modules, then I recommend disabling that repo afterwards and reloading the sources again.

This should fix all your Suspend/Hibernate problems.

Heads up folks-izanbardprince's tip on 2.6.24-19 fixed my suspend problem that I had spent a week on searching through many many posts that led me nowhere.

I have a Dell 2350 desktop, Intel 2.2 P4, Intel 845G chipset, 512 MB mem that I did a clean install of Ubuntu 8.04 from CD on and the installed kernel 2.6.24-16 worked perfect on suspend and every other function I observed for several weeks before 2.6.24-17 came along. When -17 got loaded suspend become instantly broken-went into suspend but wouldn't wakeup. Had to do hard re-boot with the power switch. Soon after -18 come down the line and no change was noticed in suspend function.

But then I read above post and my problem was resolved just as soon as -19 got loaded. Took only several minutes and all is well. Thank you izanbardprince.

---

### Post by aidave on 2008-06-12
> **izanbardprince said:**
> OK, anyone that has a suspend or hibernate problem in Hardy needs to enable hardy proposed, reload your apt sources, and get kernel 2.6.24-19 and all associated modules, then I recommend disabling that repo afterwards and reloading the sources again.

This should fix all your Suspend/Hibernate problems.

I was very excited to hear this news, so I installed said updates.

However my Dell 1420n pre-installed with Ubuntu, still fails to resume.  

:confused:

---

### Post by King of Dreams on 2008-06-12
> **aidave said:**
> I was very excited to hear this news, so I installed said updates.

However my Dell 1420n pre-installed with Ubuntu, still fails to resume.  

:confused:

Same situation here, only with a Toshiba satellite laptop.  Is anything else needed other than installing and booting off if the -19 revision of the kernel?

---

### Post by aidave on 2008-06-12
I figured it may be the NVIDIA driver.  I've installed the 173.14.05 driver and will see what happens.  It has resumed 10 times in a row so far, more than it ever has before.  Still a white screen most of the time but entering password brings it back.

Is this patch that finally fixes resume??? 

I'd love to finally be able to rely on Ubuntu on my laptop!

---

### Post by yyka on 2008-06-13
hello all, steveneddy, did you use the astadolfo3 tutoriel ?

---

### Post by tendays on 2008-06-13
I just updated from Gutsy to Hardy and hibernate (which used to work 98% of the time) totally stopped working in the process. I have that 2.6.24-19-generic kernel, Nvidia's driver version 173.14.05, and a 64bit cpu.

The machine turns off when I hibernate, but resuming fails - I just get that "ubuntu" image and I have to do a hard shutdown by keeping the power button pressed for a few seconds.

I'll now try some of the tests on [http://lxr.linux.no/linux/Documentation/power/basic-pm-debugging.txt](http://lxr.linux.no/linux/Documentation/power/basic-pm-debugging.txt)

(maybe some of you guys should try those debugging tests too)

EDIT: My conclusions so far:
1. In console mode, hibernate works only if the module b43 (my wireless driver) is removed.

2. Moreover, after resuming, if I try to load the module again (modprobe b43), the system freezes and requires a hard shutdown (but remmod and modprobe work prior to hibernating)

3. When X is loaded, hibernating (or, more accurately, resuming) doesn't work, even if I remove the b43 module.

So it seems that hibernation is neither compatible with the wireless card (broadcomm 4318 with module b43) nor with the graphic card (GeForce Go 7300)

---

