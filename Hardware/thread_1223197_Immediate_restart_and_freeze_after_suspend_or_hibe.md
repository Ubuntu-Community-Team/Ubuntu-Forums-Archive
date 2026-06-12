---
title: "Immediate restart and freeze after suspend or hibernate"
date: 2009-07-25
forum: Hardware
---

### Post by carlosrve on 2009-07-25
Hi, I bought a Toshiba Satellite P305D-S8900 about two weeks ago 'cause my old laptop died. Almost everything is working fine, but one thing that isn't is suspend or hibernate.

When I do either one of them I have the screen fade out to black and it seems to be doing normal suspend/hibernate process, but then it goes to standby for about half a sec and restarts. But the screen remains black (turned on but black) and all the input (keys, multimedia buttons, mouse) goes dead. A total freeze.

I have tried s2ram, I also installed powersaved, I tried suspending without X, and also suspending from a root shell with the rescue boot option. Always the same.

I am really out of resources for this. Please, if you know something I can try, tell me. This is my work machine, so it is really important for me to have this working.

Thank you

uname -a:
```
Linux cvasquez-laptop 2.6.28-14-generic #46-Ubuntu SMP Wed Jul 8 07:41:18 UTC 2009 x86_64 GNU/Linux
```

lshw:
```
    description: Computer
    product: Satellite P305D
    vendor: TOSHIBA
    version: PSPD8U-00M00C
    serial: 39096377W
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=oem-specific uuid=E0046F34-FA91-E411-B9ED-00238B909E74
  *-core
       description: Motherboard
       product: Satellite P305D
       vendor: TOSHIBA
       physical id: 0
       version: Not Applicable
       serial: 39096377W
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: V2.90 (01/17/2009)
          size: 110KiB
          capacity: 960KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int5printscreen int9keyboard int14serial int17printer int10video acpi usb ieee1394boot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Turion(tm) X2 Dual-Core Mobile RM-70
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: Turion X2 Mobile RM-70
          slot: Socket M2/S1G1
          size: 500MHz
          capacity: 4GHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit cpufreq
```

/proc/apci/sleep:
```
S0 S3 S4 S5
```

/proc/apci/wakeup:
```
Device	S-state	  Status   Sysfs node
PB7	  S4	 disabled  pci:0000:00:07.0
PB6	  S0	 disabled  pci:0000:00:06.0
OHC0	  S4	 disabled  pci:0000:00:12.0
OHC2	  S4	 disabled  pci:0000:00:13.0
OHC3	  S4	 disabled  pci:0000:00:13.1
HDAU	  S3	 disabled  pci:0000:00:14.2
LID	  S4	*enabled
```

---

### Post by carlosrve on 2009-07-30
Bump...

Anyone? Please...

---

### Post by meditatingfrog on 2009-08-02
I'm having the same problem with the freeze after suspending.  I'm going to switch to hibernation to see if I have the same problem with it.  I'm also running Jaunty.  I'm trying to set up a new repository to try and get an updated Intel driver.  I have a feeling it probably has something to do with it, now that I think about it, since that was one of the majory changes about upgrading to Jaunty.  Here's a link on how to do it, you can try it and see if it works for you.

[http://webupd8.blogspot.com/2009/05/graphic-video-drivers-ubuntu-repository.html](http://webupd8.blogspot.com/2009/05/graphic-video-drivers-ubuntu-repository.html)

---

### Post by carlosrve on 2009-08-03
> **meditatingfrog said:**
> I'm having the same problem with the freeze after suspending.  I'm going to switch to hibernation to see if I have the same problem with it.  I'm also running Jaunty.  I'm trying to set up a new repository to try and get an updated Intel driver.  I have a feeling it probably has something to do with it, now that I think about it, since that was one of the majory changes about upgrading to Jaunty.  Here's a link on how to do it, you can try it and see if it works for you.

[http://webupd8.blogspot.com/2009/05/graphic-video-drivers-ubuntu-repository.html](http://webupd8.blogspot.com/2009/05/graphic-video-drivers-ubuntu-repository.html)

My video card is a ATI Radeon HD 3100 (RS600 chip). So the Intel driver won't work. But you don't need to create a repository in order to test the updated Intel Driver. You can do it from a deb package or from source. Tell me if you need some guide with that.

I did a little more debuging since, and I am 99% sure that the problem is happening just when ACPI is trying to stop the CPU to enter in standby. At that time the wakeup routine is called and everything is started.

The freeze part I think is another problem. I am pretty sure that if I get the suspend part working, I won't be able to resume afterwards. That part is a problem somewhere with the chipset on my MB (AMD) or the GPU (ATI). Because when I try to suspend and I get that freeze state, I can login remotely with ssh. That means that the problem is waking up the I/O (keyboard, mouse, screen). But the core and network are being resumed normally.

I am not yet sure that it is the video card that it is causing the second problem, as I tried with no X, from a recovery root console and did the same thing. I also tried within X with radeon free driver and the same thing again.


If someone know something else I can try to get this working, I am willing to do all the tests and stuff needed. I am really tired of having to shutdown and power on every time I have to move (I have meetings all day almost every day).

Thank you,

---

### Post by meditatingfrog on 2009-08-03
> **carlosrve said:**
> My video card is a ATI Radeon HD 3100 (RS600 chip). So the Intel driver won't work. But you don't need to create a repository in order to test the updated Intel Driver. You can do it from a deb package or from source. Tell me if you need some guide with that.

I did a little more debuging since, and I am 99% sure that the problem is happening just when ACPI is trying to stop the CPU to enter in standby. At that time the wakeup routine is called and everything is started.

The freeze part I think is another problem. I am pretty sure that if I get the suspend part working, I won't be able to resume afterwards. That part is a problem somewhere with the chipset on my MB (AMD) or the GPU (ATI). Because when I try to suspend and I get that freeze state, I can login remotely with ssh. That means that the problem is waking up the I/O (keyboard, mouse, screen). But the core and network are being resumed normally.

I am not yet sure that it is the video card that it is causing the second problem, as I tried with no X, from a recovery root console and did the same thing. I also tried within X with radeon free driver and the same thing again.


If someone know something else I can try to get this working, I am willing to do all the tests and stuff needed. I am really tired of having to shutdown and power on every time I have to move (I have meetings all day almost every day).

Thank you,

Never created a repository.  Compiling things from source is pretty much always a fail for me, as far as I can remember.  Dependencies usually cause a problem for me.

Back to your problem.  I think you should communicate with Neon612, I did a search on the forums for your laptop model and Neon612 has the same laptop as you and they started this thread [http://ubuntuforums.org/showthread.php?t=1153644&highlight=P305D-S8900](http://ubuntuforums.org/showthread.php?t=1153644&highlight=P305D-S8900).  They're thread is about extending battery life, so a PM might be your best bet.  Ask them how their Suspend experience is going.  I think it's good for people with similar hardware to work together.

Now, what I can recommend without having the same laptop.  Have you checked var/log/syslog in gedit to see if there are any failures/errors?  It might shed some light on what is going on.  I have a CPU error described in my syslog when I suspend, and after rechecking, still have the ACPI error.  The freezing hasn't happened since I upgraded the intel video driver repository (xorg-video-intel, I think), the freezing for me has been intermittent.  

When your system freezes, you can use Alt-Prtsc(Sysrq) and type REISUB.  It will reboot your system, and according to this website [http://fosswire.com/post/2007/09/fix-a-frozen-system-with-the-magic-sysrq-keys/](http://fosswire.com/post/2007/09/fix-a-frozen-system-with-the-magic-sysrq-keys/) which I found on this thread [http://ubuntuforums.org/showthread.php?t=1206250](http://ubuntuforums.org/showthread.php?t=1206250) it is better than shutting the system down with the power button.  

Another thought, have you tried booting X in failsafe mode?  Not sure how feasible this is for you, but running in failsafe mode for a 24 to 48 hours might show if it's the video driver causing the freeze.  I think the grub menu gives you the option to boot in failsafe.  I might have to try this myself, but I'm not quite there yet.

---

### Post by Uncle Quag on 2009-08-03
I have the same model of this laptop as [carlosrve]("http://ubuntuforums.org/member.php?u=346807") (P305D-S8900, running Jaunty AMD64) with the same symptoms, and was able to solve the suspend and hibernation problems with info gleaned from a bug filed on the subject at [http://bugzilla.kernel.org/show_bug.cgi?id=12873](http://bugzilla.kernel.org/show_bug.cgi?id=12873).

First things first, it should be noted that I have system BIOS version 3.10 installed on my machine.  This may or may not have an effect on the suspend/hibernate functionality (nothing specifically documented in Toshiba's release notes), but a BIOS update was the first thing I did after discovering Sus/Hib weren't working.

Next, you'll want to add the "**acpi_osi=Linux**" boot option to your Grub config.  This will resolve/bypass IRQ9 assignment problems at boot, and has the added benefit of making a few of the machine's FN keys work, such as FN+F9, which enables/disables the touchpad (a godsend for USB mouse users.)  Oddly enough, the Sus & Hib key combos (FN+F3 & FN+F4, respectively) weren't two of the working ones.

Instructions on adding boot options can be found here for those who need them: [https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Permanently%20On%20An%20Existing%20Installation]("https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Permanently%20On%20An%20Existing%20Installation") 

...but note that I added the option to the default boot options rather than "# kopt=" as the instructions list.  e.g.:

```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash **acpi_osi=Linux**
```Finally, if you have the ATI 3100 embedded graphics like the S8900 model does, you'll need to update to the ATI Catalyst 9.7 proprietary driver so XOrg/FGLRX will come back up properly after suspend or hibernate.  If you installed/activated the Ubuntu packaged version of the driver through System -> Administration -> Hardware Drivers, use the same utility to remove/deactivate it.

NB: this is the first time I've personally installed restricted drivers outside of the usual Ubuntu built-in methods, so it's entirely possible that there are better ways of doing this.  Still, it worked, so I'm not complaining... ;-)  Here's a walkthrough of the steps I took.

1. Downloaded the driver files from [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English) to a standalone directory.  Filename is **ati-driver-installer-9-7-x86.x86_64.run**.  Installation instructions are available in PDF form from ATI's driver page.

The "run" file has package-building scripts built in, and I went with the option to create an Ubuntu/9.04-specific .deb package set.  It took some time to run, but it automatically installed any missing dependencies which, I'm betting, will save a lot of headaches down the road.

2. To build the packages, open a terminal and cd to the location of the "run" file, then enter:
```

sudo sh ./ati-driver-installer-9-7-x86.x86_64.run --buildpkg Ubuntu/9.04
```You should end up with 6 package files in the same directory as ati-driver.run:

[LIST]
[*] xorg-driver-fglrx_8.632-0ubuntu1_amd64.deb
[*] xorg-driver-fglrx-dev_8.632-0ubuntu1_amd64.deb
[*] fglrx-kernel-source_8.632-0ubuntu1_amd64.deb
[*] fglrx-amdcccle_8.632-0ubuntu1_amd64.deb
[*] fglrx-modaliases_8.632-0ubuntu1_amd64.deb
[*] libamdxvba1_8.632-0ubuntu1_amd64.deb
[/LIST]
  3. Entered **gksudo gdebi-gtk** in the terminal to bring up the GDebi Package installer.  When running through the installation of each of the packages, I got a "An older version is available in a software channel" message, which I ignored and closed.  I installed the packages one at a time, following this order.[INDENT] 3.1 fglrx-kernel-source_8.632-0ubuntu1_amd64.deb
3.2 xorg-driver-fglrx_8.632-0ubuntu1_amd64.deb
3.3 fglrx-amdcccle_8.632-0ubuntu1_amd64.deb
3.4 fglrx-modaliases_8.632-0ubuntu1_amd64.deb
3.5 libamdxvba1_8.632-0ubuntu1_amd64.deb
3.6 xorg-driver-fglrx-dev_8.632-0ubuntu1_amd64.deb (seriously doubt I needed this, but I installed in anyway just 'cause it was there.)
[/INDENT]As the last step, I used the terminal to initialize the driver using...```
 sudo /usr/bin/aticonfig --initial
```After a Reboot, all was well.  So far, I've tested both suspend and hibernate on AC power and on battery, and everything's working properly, including suspend when the lid's closed.  Better living through reckless experimentation, and all that.

---

### Post by carlosrve on 2009-08-06
Thank you Uncle Quag! I am able to suspend now. It is working as usual.

One more question, to you have a high pitched noise comming from your GPU? I think it is the GPU, the noise is comming from somewhere below the power button.

I have that noise when I use the ATI proprietary drivers, not the radeon or the vesa drivers. Also the noise stops when the screen is being refreshed in some way. And it seems to desapear at all when I am using multi-head video out (VGA).

Thank you again,

---

### Post by Uncle Quag on 2009-08-07
> **carlosrve said:**
> Thank you Uncle Quag! I am able to suspend now. It is working as usual.

One more question, to you have a high pitched noise comming from your GPU? I think it is the GPU, the noise is comming from somewhere below the power button.

I have that noise when I use the ATI proprietary drivers, not the radeon or the vesa drivers. Also the noise stops when the screen is being refreshed in some way. And it seems to desapear at all when I am using multi-head video out (VGA).

Thank you again,
Hmm... I'm not getting any noises, but I'm guessing you're hearing the system's main cooling fan, since the intake is right about in the location you describe.    The new ATI drivers probably do put more of a load on the system, which might explain the higher fan use.

Do you get the noise both when on AC power and when on battery?  Are you using any system throttling/power tweaking tools, like the CPU Frequency Scaling Monitor?  Also, did you update to BIOS 3.10?  Don't know if it matters, but it might.

---

