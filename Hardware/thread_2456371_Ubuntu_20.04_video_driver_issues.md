---
title: "Ubuntu 20.04 video driver issues"
date: 2021-01-10
forum: Hardware
---

### Post by mike430 on 2021-01-10
Hello. Upgraded to 20.04 and elected the other drivers Nvidia 340.108 to run my GeForce 210 display card in lieu of the Nouveau driver. Worked fine for about a month, then began having issues. The issue began after restart only to pull a black screen and I could only access command line. Was initially able to get the Nouveau driver working by purging all Nvidia stuff. Should have left it at there, but was eager to get Nvidia working again. Come to find out the card I have is not supported beyond kernel 5.4, and I am at 5.8. Not really sure why it worked in the first place. Before knowing this my endless efforts to get Nvidia's drivers working again has led to neither driver loading my desktop. 

I think my issue was that at some point I tried directly installing the package from Nvidia's site. It created a Blacklist for Nouveau which I believe I have since fixed and perhaps other things behind the scenes. I am at the point where it appears nothing Nvidia driver wise is installed, and Nouveau does appear to be intalled per the 'lshw -c video' command indicates my 'configuration: driver=nouveau latency=0'. 

With that said I feel I am simply a few settings away from getting this working. I appreciate any help in this matter.

Kindly, -Mike

---

### Post by CatKiller on 2021-01-10
> **mike430 said:**
> . I think my issue was that at some point I tried directly installing the package from Nvidia's site.

Yeah, there are essentially no circumstances where that's a good idea. I believe the installer script does come with an uninstall option, which should be able to undo the things it did. How effective it is, I couldn't say.

---

### Post by mike430 on 2021-01-10
Assuming the uninstall option is not effective, any other ideas? In the mean time I'll check Nvidia's site. Thanks for the reply. -Mike

---

### Post by mike430 on 2021-01-10
CatKiller, I posted another thread about a reinstallation of ubuntu 20.04 where I probably should of just asked you. I think my mucking up the video drivers as I did throws the idea of quick fix out the window. Mind I ask you?.. can I reinstall ubuntu 20.04 and still retain most of my configuration settings, samba users, and home directory? 

I appreciate your time and response to my inquiries. Kindly, Mike

---

### Post by mastablasta on 2021-01-11
try to reinstall without formatting the drive. maybe it will work.

also get version 20.04.1 - it will keep kernel the same, so you can use the nvidia driver for next 4 years
[https://releases.ubuntu.com/focal/](https://releases.ubuntu.com/focal/) 

make sure you don't use HWE stack (maybe it's enabled in update settings?!). HWE stack brings new kernel to current Ubuntu version, for better hardware support.

i used 18.04.1 like that. i am still on kernel 4.something and receive security patches only.

---

### Post by Yellow Pasque on 2021-01-11
> Come to find out the card I have is not supported beyond kernel 5.4, and I am at 5.8. 

Yeah, that's the problem. mastablasta suggested comeplete reinstall but that shouldn't be necessary. Show output of:
```
dpkg -l | grep linux-
```

---

### Post by mike430 on 2021-01-11
> **Yellow Pasque said:**
> Yeah, that's the problem. mastablasta suggested comeplete reinstall but that shouldn't be necessary. Show output of:
```
dpkg -l | grep linux-
```
```
ii  binutils-x86-64-linux-gnu                  2.34-6ubuntu1                         amd64        GNU binary utilities, for x86-64-linux-gnu target
ii  linux-base                                 4.5ubuntu3.1                          all          Linux image base package
ii  linux-firmware                             1.187.7                               all          Firmware for Linux kernel drivers
ii  linux-generic-hwe-20.04                    5.8.0.36.40~20.04.21                  amd64        Complete Generic Linux kernel and headers
ii  linux-headers-5.8.0-34-generic             5.8.0-34.37~20.04.2                   amd64        Linux kernel headers for version 5.8.0 on 64 bit x86 SMP
ii  linux-headers-5.8.0-36-generic             5.8.0-36.40~20.04.1                   amd64        Linux kernel headers for version 5.8.0 on 64 bit x86 SMP
ii  linux-headers-generic-hwe-20.04            5.8.0.36.40~20.04.21                  amd64        Generic Linux kernel headers
ii  linux-hwe-5.8-headers-5.8.0-34             5.8.0-34.37~20.04.2                   all          Header files related to Linux kernel version 5.8.0
ii  linux-hwe-5.8-headers-5.8.0-36             5.8.0-36.40~20.04.1                   all          Header files related to Linux kernel version 5.8.0
rc  linux-image-5.4.0-42-generic               5.4.0-42.46                           amd64        Signed kernel image generic
rc  linux-image-5.4.0-54-generic               5.4.0-54.60                           amd64        Signed kernel image generic
rc  linux-image-5.4.0-56-generic               5.4.0-56.62                           amd64        Signed kernel image generic
rc  linux-image-5.4.0-58-generic               5.4.0-58.64                           amd64        Signed kernel image generic
rc  linux-image-5.4.0-59-generic               5.4.0-59.65                           amd64        Signed kernel image generic
ii  linux-image-5.8.0-34-generic               5.8.0-34.37~20.04.2                   amd64        Signed kernel image generic
ii  linux-image-5.8.0-36-generic               5.8.0-36.40~20.04.1                   amd64        Signed kernel image generic
ii  linux-image-generic-hwe-20.04              5.8.0.36.40~20.04.21                  amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                       5.4.0-60.67                           amd64        Linux Kernel Headers for development
rc  linux-modules-5.4.0-42-generic             5.4.0-42.46                           amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-54-generic             5.4.0-54.60                           amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-56-generic             5.4.0-56.62                           amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-58-generic             5.4.0-58.64                           amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-59-generic             5.4.0-59.65                           amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-5.8.0-34-generic             5.8.0-34.37~20.04.2                   amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
ii  linux-modules-5.8.0-36-generic             5.8.0-36.40~20.04.1                   amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-42-generic       5.4.0-42.46                           amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-54-generic       5.4.0-54.60                           amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-56-generic       5.4.0-56.62                           amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-58-generic       5.4.0-58.64                           amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-59-generic       5.4.0-59.65                           amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.8.0-34-generic       5.8.0-34.37~20.04.2                   amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.8.0-36-generic       5.8.0-36.40~20.04.1                   amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
ii  linux-sound-base                           1.0.25+dfsg-0ubuntu5                  all          base package for ALSA and OSS sound systems
ii  syslinux-common                            3:6.04~git20190206.bf6db5b4+dfsg1-2   all          collection of bootloaders (common)
ii  syslinux-legacy                            2:3.63+dfsg-2ubuntu9                  amd64        Bootloader for Linux/i386 using MS-DOS floppies
```

---

### Post by mike430 on 2021-01-11
> **Yellow Pasque said:**
> Yeah, that's the problem. mastablasta suggested comeplete reinstall but that shouldn't be necessary. Show output of:
```
dpkg -l | grep linux-
```
Not entirely sure what I am looking at per this output, but I gather that my geforce 210 worked under what was originally a 5.4 kernel which would have made it compatible. At some juncture my kernel upgraded to 5.8 and my installed nvidia driver was no longer compatible, hence creating the errors and no gui load.
This being the case, is there any hope to avoid a reinstall of my os? Further, if I were to reinstall ubuntu 20.04 how can I prevent a kernel upgrade? Or can I even revert back to the 5.4 kernel? Thanks for your time and help. Kindly, Mike

---

### Post by mastablasta on 2021-01-12
you can use kernel 5.4. i don't know how to downgrade, though. the list shows what kernel are installed so you should be able to load the older kernel at boot and remove the new one.

example:
[https://askubuntu.com/questions/1299429/20-04-how-to-downgrade-kernel-from-5-4-0-56-generic-to-5-4-0-55-61](https://askubuntu.com/questions/1299429/20-04-how-to-downgrade-kernel-from-5-4-0-56-generic-to-5-4-0-55-61)

here is another example (for 18.04, but user had similar issue):
[https://askubuntu.com/questions/1170524/downgrading-18-04-kernel-5-0-to-the-original-kernel-that-came-with-18-04](https://askubuntu.com/questions/1170524/downgrading-18-04-kernel-5-0-to-the-original-kernel-that-came-with-18-04)

in this example they installed generic kernel which brought them the old original kernel for the LTS version.


but it's probably not just the kernel, but xserver and xorg as well that need to be downgraded for driver to work. at least that's how it was with ATI chips. in any case start with kernel downgrade, remove new kernel and install nvidia driver. fingers crossed - you will be good for another 4 years. in the mean time maybe nouvau will progress enough or the card will die on you and you will get AMD card :P

i am in same boat, only probably with next LTS as the 3.90 moved to legacy support.

---

### Post by mike430 on 2021-01-12
> **mastablasta said:**
> you can use kernel 5.4. i don't know how to downgrade, though. the list shows what kernel are installed so you should be able to load the older kernel at boot and remove the new one.

example:
[https://askubuntu.com/questions/1299429/20-04-how-to-downgrade-kernel-from-5-4-0-56-generic-to-5-4-0-55-61](https://askubuntu.com/questions/1299429/20-04-how-to-downgrade-kernel-from-5-4-0-56-generic-to-5-4-0-55-61)

here is another example (for 18.04, but user had similar issue):
[https://askubuntu.com/questions/1170524/downgrading-18-04-kernel-5-0-to-the-original-kernel-that-came-with-18-04](https://askubuntu.com/questions/1170524/downgrading-18-04-kernel-5-0-to-the-original-kernel-that-came-with-18-04)

in this example they installed generic kernel which brought them the old original kernel for the LTS version.


but it's probably not just the kernel, but xserver and xorg as well that need to be downgraded for driver to work. at least that's how it was with ATI chips. in any case start with kernel downgrade, remove new kernel and install nvidia driver. fingers crossed - you will be good for another 4 years. in the mean time maybe nouvau will progress enough or the card will die on you and you will get AMD card :P

i am in same boat, only probably with next LTS as the 3.90 moved to legacy support.
Thanks brother ..  am trying now to load 5.4 kernel and get my vidia workin' .. post the community my results.

---

### Post by mike430 on 2021-01-13
[FONT=arial]AhHa! Got it to work. Truly unbelievable... So I'll make this short. Upgraded from 18.04 to 20.04 a month ago. Running GeForce 210 supported up to Kernel 5.4. During that month Kernel upgraded to 5.8 through updates rendering my geforce 210 incompatible. Was not aware of the incompatibility at the time, but discovered my graphics driver switched to Nouveau because of my cpu being taxed to all could be. Still not aware of the incompatibility of the nvidia 340.108 driver and then attempted to upgrade graphics driver by installing nvidia 340.108 driver directly from nvidia support. After this package install was unable to load nvidia driver or nouveau. Now was facing the prospect of a total reinstall of Ubuntu.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]So what I did was purge all nvidia stuff [sudo apt-get remove --purge '^nvidia-.*][/FONT]
[FONT=arial]Installed 5.4 Kernel [sudo apt install linux-generic][/FONT]
[FONT=arial]Ran [sudo grub-mkconfig | grep -E 'submenu |menuentry '] to identify old Kernel so to start at grub.[/FONT]
[FONT=arial]Updated /etc/default/grub [GRUB_DEFAULT="Advanced options for Ubuntu>Ubuntu, with Linux 5.4.0-60-generic"] Grub menu now defaulted to advanced with the old Kernel highlighted for boot[/FONT]
[FONT=arial]From command line reinstalled [sudo apt install nvidia-340] but created errors, specifically could not overwrite files in /usr/lib/x86_64-linux-gnu/[libGL.so.1 and libGLESv2.so.2.distrib] I simply deleted them[/FONT]
[FONT=arial]Rebooted and I am up and running. [/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Thanks Mastablasta for your help!! Kindly -Mike[/FONT]

---

### Post by mastablasta on 2021-01-13
well thanks for letting us know. i didn't know the exact procedure, but as you did it, it looks like grub has to be reconfigured and updated. so you got 4.5 more years out of the hardware (or more if you buy extended support). i really wish nvidia would at least release the old binaries as opensource. i mean the hardware works and does the job, but lacks software support.

CentOS used to offer 10 years support, but IBM pulled the plug on that. so new linux will likely be forked (Rocky linux?!) and if that one can offer 10 year support, we just might be able to keep this hardware going for 10 more years. or if at least nvidia helped nouveau get the driver to support hardware acceleration. 

I have an old AMD chip that lost support. i stayed on 14.04 LTS for long time because of that. before they had closed source drivers to do the job for that specific chip. opensource drivers were terrible on this chip as CPU was tasked too much. i tried a few live sessions, but it was not good at all. but with the help of AMD, they got the GPU hardware acceleration working. in 2019 i installed 18.04 with HWE kernel and i must say performance on this chip is at same level as with closed source. suddenly even the old games or their opensource implementation work well. nvidia should do something similar.

i am all for new tech, but we should just thrown away old things because we have a newer model available. i really think about transforming my current very old desktop PC to a media server and add a controler or two to it for some light gaming on TV. plenty of ram (4GB) for that, GT730 will take care of old games and such. CPU is not strong (single core) but get's the job done and continues to chug along for the 17th year now.

---

### Post by cberdullas on 2021-01-21
Hi Mike
I read all the thread with great attention.
I'm in the same problem (with same graphic card gen: GT218 obviously same driver 340.108).
As with your PC, my problems begun with the upgrade one and half moths ago.
I partially resumed my PC (desktop) work installing the NOUVEAU driver but...
... my machine resists itself to SUSPEND.
When giving order of SUSPEND, the PC goes into suspension BUT when intending to "revive" the system, refuses to show the DESKTOP.
Reading a lot in ubuntu jungle online, your problem ---> solution comes to be the easiest.
My first question is: once your kernel was downgraded, DO YOU HAVE THE SUSPENSION MODE OPERATIVE in your PC?
Depending on your answer, I may have some more questions :rolleyes:

---

### Post by mastablasta on 2021-01-22
suspend mode depends on motherboard and can also depend on GPU power management. if the opensource nouveau GPU drivers do not offer good support, then they are very likely the ones causing the issues with suspend. 

furthermore there are various ways to do power management and you could also try installing some other services or applications that provide that functionality (if it is necessary for you). for example TLP, laptop-mode-tools.

Arch linux is not too user friendly for people new to linux. But they do have great documentation and i would often use it if nothing else to find some ideas for solutions:
[https://wiki.archlinux.org/index.php/Power_management](https://wiki.archlinux.org/index.php/Power_management)

---

### Post by cberdullas on 2021-01-23
> **mastablasta said:**
> **suspend mode depends on motherboard **and can also depend on GPU power management. if the opensource nouveau GPU drivers do not offer good support, then they are very likely the ones causing the issues with suspend. 
Thanks for your answer, Mastablasta ;)
**Yeps- I already knew this but...**
Two different motherboards (desktops, not laptops: one Intel the other Gigabyte) working with Ubuntu 18 and NVIDIA DRIVERS SUSPENDED with no problem.
THIS PC (motherboard Gigabyte) worked fine (Nvidia drivers under Ubuntu 20.04) until the last month UPDATE (there's been another kernel update three days ago and no solution for the nvidia driver issue).

In another forum there are several mentions to "suspend mode issues" with Ubuntu20 + Nvidia driver BUT NO SOLUTION (all mention the way of solving the black screen after restarting -this also happened to me- but the suspend mode still persisting).

If I have enough free time this weekend I'll try to DOWNGRADE my kernel and... let's see.

BTW: still intending to know if Mike's PC can go into SUSPEND MODE. Would be of great help...:cool:



EDIT: I'd be glad if I'd restore the SUSPEND MODE. Not need to work under Nvidia: the NOUVEAU driver makes it good for my needs.

EDIT 2: I'll try to explain MY ISSUES.

*The system works fine with the NOUVEAU driver.*
When I click on the SUSPEND option, the PC SUSPENDS (ergo ---> the motherboard isn't in truble with ubuntu-OS/kernel)
Here comes the trouble: when I try to WAKE UP the system, the PC wakes up BUT the graphic card DOESN'T and the screen comes PLAIN DOTTED IN CLEAR MULTICOLOR RAINY DOTS/pixels, not showing the DESKTOP.
AND: desktop is HIDDEN BUT RUNNING (ergo---> the system wakes up but the Nvidia graphic card doesn't wake-up running with the NOUVEAU driver).
This issue obliges me to press the RESET button; THEN THE SYSTEM BEGINS NORMALLY.
When installed the Nvidia 340.108 driver the problem comes bigger: it works the FIRST TIME. Then:
a.- When intending to suspend, doesn't obey.
b.- When power-off or reset, the system DOESN'T LOAD and the screen shows only black. Ubuntu doesn't work (I needed to re-install Ubuntu to make my machine work again).

Thanks for any comments :mrgreen:

---

### Post by cberdullas on 2021-01-24
Well... [SIZE=5]**SOLVED**[/SIZE]

Procedure:
From a ROOT CONSOLE (ubuntu settings, advanced) with web connection

[SIZE=3]**sudo apt-get install linux-generic   **[/SIZE]  (in my case, 5.4.1)

[SIZE=3]**sudo dpkg -l | grep linux-image **[/SIZE]

This command gave me the list of kernels INSTALLED in my system

then

**[SIZE=3]sudo apt-get remove --purge linux-image-x.x.x ([/SIZE]**x.x.x. exact name of EACH KERNEL VERSION: I had three 5.8.x which I removed)

[SIZE=3]**reboot **[/SIZE]

Once ubuntu working "normally", opened UPDATES & DRIVERS app

[COLOR=#ff0000][SIZE=3]Downloaded and installed (automatic) the NVIDIA DRIVER 340.108[/SIZE][/COLOR]

Then opened console:

[SIZE=3][B]sudo apt-get remove --purge xserver-xorg-video-nouveau
[/B][/SIZE]
[SIZE=3]**reboot**[/SIZE]

Note 1: all updates are DISABLED after last reboot

[COLOR=#0000ff]**[SIZE=4]Note 2: my PC SUSPENS NORMALLY.[/SIZE]**[/COLOR]

As my PC couldn't suspend with any of the two drivers, _my conclusion is that the problem is in the KERNEL 5.8.X..._

---

### Post by CatKiller on 2021-01-24
Don't forget to remove the Linux HWE metapackage until you're ready to try more kernels from the 5.8 branch.

---

### Post by cberdullas on 2021-01-24
> **CatKiller said:**
> Don't forget to remove the Linux HWE metapackage until you're ready to try more kernels from the 5.8 branch.

Thanks - already done:


[ATTACH=CONFIG]287800[/ATTACH]

;)

---

### Post by mastablasta on 2021-01-26
yes, 5.8 does not seem to support 3.40 drivers and also you have to remove those kernels to begin using 5.4.

so we get working hardware with support dropped by manufacturers. and people wonder why some still use Win XP or win 7...

---

### Post by grabasimo on 2021-01-26
Hi. I had problem with nvidia drivers to. they did't load after installation. I download drivers from nvidia.com and run manually. Removed all dkms from system and install binary drivers. Now nvidia drivers are working

---

