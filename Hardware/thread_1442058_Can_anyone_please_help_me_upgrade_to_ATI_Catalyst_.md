---
title: "Can anyone please help me upgrade to ATI Catalyst 10.3?!"
date: 2010-03-29
forum: Hardware
---

### Post by Godspell on 2010-03-29
Hello there,

I'm using Ubuntu 9.1 32bit on Acer Aspire 5542 and my GPU is ATI Mobility Radeon HD 4200. I activated proprietary drivers and am using them now but I wanna update them. I found out I can update to Catalyst Control Centre 10.3 and have been trying the whole afternoon doing it.

Basically, I read up this [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) and it's completely hopeless to me. My current **fglrxinfo** is following.

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4200
OpenGL version string: 2.1.9016

Also checked the Catalyst Control Centre version and it says 2.11. 
In order to get CCC 10.3, I need to install 

- XFree86-Mesa-libGL
- XFree86-libs

I've just spent like 3 hours on xfree86 website following the "instructions" but none of them worked. Besides, their guides and explanations seem very complicated to me. 
I'm really tired of reading up all the stuff cause simply they don't work!

So, could somebody please give me a straight forward detailed-dummy guide to update to CCC 10.3???

Thank you very much.

Regards,
GS

---

### Post by cocamoxb on 2010-03-29
That seems awfully complicated, I'd agree. My example process uses Ubuntu 9.10 in x86_64, if you use 32-bit then download that file. I've been upgrading from ATI 9.x drivers and I'm now on 10.3. My typical process is as follows:

1)Download the correct version for your card\OS into /root/
2) cd /usr/share/ati
3) sudo sh ./fglrx-uninstall.sh
4) reboot the machine into recovery mode and select "drop into root prompt"
5) ls -l |grep ati
6) chmod 777 ati-driver-installer-10-3-x86.x86_64.run (Yes, 777 because I just delete the installer when done)
7) ./ati-driver-installer-10-3-x86.x86_64.run
8) follow prompts and agree to license
9) reboot & enjoy
10) delete the installer file (ati-driver-installer-10-3-x86.x86_64.run)


I prefer the command prompt over graphical interfaces. Also, make sure that your user has root (sudo) access prior to performing this process. If you are not familiar with the command prompt, then before doing anything above, just reboot and select recovery mode and drop into a root prompt to be sure it works prior to following the process above.

---

### Post by Godspell on 2010-03-29
Thanks for the reply, you're a light mate. I've got couple of questions regarding on your solution. Hope you won't mind.

> 1)Download the correct version for your card\OS into /root/This is embarrassing (for me) but when you said root is it "**/**" or "**/root**" ?
Already downloaded the installer "*ati-driver-installer-10-3-x86.x86_64.run*", just need to move it.

> 2) cd /usr/share/ati
3) sudo sh ./fglrx-uninstall.shInstead of doing this, can't I go to "**System > Administration > Hardware Drivers**" and remove the current proprietary drivers? And delete the ATI folder afterwards from /user/bin or wherever it is stored?
Just curious, really.

> 
4) reboot the machine into recovery mode and select "drop into root prompt"I'm not very cleared about this because there isn't any sort of menu when the OS starts up. Do I have press any key?

> 5) ls -l |grep ati
6) chmod 777 ati-driver-installer-10-3-x86.x86_64.run (Yes, 777 because I just delete the installer when done)
7) ./ati-driver-installer-10-3-x86.x86_64.run
8) follow prompts and agree to licenseI guess once I'm in CLI as you mentioned above, I should be able to do this, yeah?
As much as I wanna be a geek, bit nervous about rattling in the root.
> 
9) reboot & enjoy
10) delete the installer file (ati-driver-installer-10-3-x86.x86_64.run)


I prefer the command prompt over graphical interfaces. Also, make sure that your user has root (sudo) access prior to performing this process. If you are not familiar with the command prompt, then before doing anything above, just reboot and select recovery mode and drop into a root prompt to be sure it works prior to following the process above.
One more thing mate, the reason why I was trying to install "*XFree86-Mesa-libGL*" and *"XFree-Lib*" was because they were stated as CCC requirements in AMD Drivers Release Notes, but you didn't mention anything about them.
Does it mean I don't need to follow those requirements BEFORE installing the actual driver files? I want to get the most out of my GPU such as being able to use OpenGL and good graphical resources, you know.

Sorry for such a long reply. I'm quite a newbie and hope you don't mind answering my questions.
Again, thanks :)

Regards,
GS

---

### Post by cocamoxb on 2010-03-30
1) Yes, "/root". The reason is that in step #4 you will be put into that directory so you won't need to move files or change directories.

2&3) I'm sure you could but since I installed the drivers with the ATI ".run" file, I figured using their uninstaller would reverse their installer best. Either way should work. Don't worry about deleting the folder though, the new installer uses the same path\folder naming. 

4) My apologies, I assumed you had dual-boot enabled. If your machine only has Ubuntu installed ( have Windows for my wife and Ubuntu) you don't get the Grub boot menu by default. When the machine boots up, before the Ubuntu screen but after the POST (the memory check, BIOS screen, etc) press the "ESC" key a few times and you should get the Grub boot menu. That is where you select the first "recovery" option. This is sort of the same process in Windows as the "Safe Mode" process, but Ubuntu style.

5-7) Yes, once in cli these commands will work fine.

9-10) = good to go


footnotes: "*XFree86-Mesa-libGL*" and *"XFree-Lib*" have non-free versions that are installed by the ATI installer. I *think* you read that part in the "compile your own ATI installer" section of the release notes.

To check what is already installed (my output included):

cocamoxb@home:~$ apt-cache pkgnames |grep xfree
xserver-xfree86-dbg
xfreecd
xserver-xfree86
ttf-xfree86-nonfree-syriac
xfree86-driver-fglrx-dev
ttf-xfree86-nonfree
xfree86-driver-synaptics
t1-xfree86-nonfree
xfonts-xfree86-nonfree
xfree86-common
xfree86-driver-fglrx

Also, here is a list of packages that the 10.3 requires (known as dependencies in Linux-world) and I have installed with the fglrx name:

cocamoxb@home:~$ apt-cache pkgnames |grep fglrx
fglrx-driver-dev
fglrx-driver
xfree86-driver-fglrx-dev
fglrx-control
fglrx-amdcccle
fglrx-modaliases
fglrx-kernel-source
xorg-driver-fglrx
fglrx-control-qt2
xorg-driver-fglrx-dev
xfree86-driver-fglrx





I'd suggest again to reboot, press "ESC", enter the boot menu, select "recovery" mode, drop into root shell, and get familiar with it first. Don't worry about root access. So long as you don't start deleting anything you're fine. Once you're done "testing" root, then go back and go through the original process.

I'm pretty sure the ".run" file will install all the dependencies you need.

---

### Post by Godspell on 2010-03-30
Hey I've just installed the drivers. Everything went well.
There were couple of things I wasn't able to do; "*sh ./fglrx-uninstall.sh*", kept saying it wasn't there.
So, I went back into Ubuntu and remove the drivers from System > Admin > Hardware Drivers.
After that booted back into Recovery Mode for drivers install. Couldn't do "*ls -l grep ati*" either. It kept saying couldn't find any file/folder for this, too.
So, I did the *"chmod 77*" and installation. They went well. I did fglrxinfo and got this.

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4200
OpenGL version string: 3.2.9704 Compatibility Profile Context

My OpenGL version was 2.something before so I guess it's been updated. Funny thing is CCC isn't there anymore. I read it somewhere CCC won't be supported anymore or something like that. Is it because of that??
Also, is there anyway I could check if the 3D settings are right or enabled (not that I understand much)? Just wanna make sure everything that's needed is enabled. 
Anyway, everything went well. Didn't have any error msgs. Thanks you very much for the help :) Especially, for the simple explanations.
Cheers.

Regards,
GS

**EDIT: **I didn't check it properly. ATI CCC is under System > Preferences and they do work well. Cheers!

---

### Post by cocamoxb on 2010-03-31
Glad it worked out. All the best.

---

### Post by anextx on 2010-04-23
Godspell, did your xserver fail after trying this?  i've been having this issue for a while where i'll follow these steps only to reboot to a black screen after GRUB.  i can log in through the command line but cannot display *fglrxinfo* also *aticonfig -initial* gives an error that it cannot find a configuration file.  *aticonfig --initial -f* creates a new xorg.conf file (supposedly) but the xserver still fails after a reboot.

what did you do to configure the driver after installing it?

---

### Post by Godspell on 2010-04-24
> **anextx said:**
> Godspell, did your xserver fail after trying this?  i've been having this issue for a while where i'll follow these steps only to reboot to a black screen after GRUB.  i can log in through the command line but cannot display *fglrxinfo* also *aticonfig -initial* gives an error that it cannot find a configuration file.  *aticonfig --initial -f* creates a new xorg.conf file (supposedly) but the xserver still fails after a reboot.

what did you do to configure the driver after installing it?

Hey, my case was pretty simple. I just installed the drivers according to these steps and reboot. Everything was ordinary.
But I don't know what you mean by "configure the drivers" cause after installation, I didn't do anything. I just use it and no problem was found.
I'm kind of a noob on Ubuntu, so don't know much about GPU.
I've come across several threads with the issue you're having. I'll post it here if I find any solution.

Cheers,
GS

---

### Post by Sepiraph on 2010-04-25
Another confirmed ... success!!!

Graphics Card is ASUS EAH5670

---

