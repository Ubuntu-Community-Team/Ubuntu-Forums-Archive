---
title: "Is it too much to Ask. NVIDIA driver problem."
date: 2009-03-30
forum: Installation &amp; Upgrades
---

### Post by thenewmexican on 2009-03-30
Is it too much to ask. For the Ubuntu people to fix the NVIDIA driver problem that exists in 8.04,8.10, and 9.04beta.

Currently I'm running Ubunto 8.04 X64 version. I installed a new video card. It is an PNY 8600GT 512MB. I went through the System->Administration->Hardware drivers. I activated the NDVidia hardware driver. Followed by a system reboot.

Now. The system boots fine. Except when X attempts to start. All I get is a dark blank screen, with nothing else happening.

I then have to reboot, into a fix mode, which I then select XFIX. Which essentially replaces the current xorg.conf, with a working version of this file.

I have googled this problem. And. It seems like there are a myriad of solutions. None of which work for me.

When is this problem finally going to be solved. I tried installing 8.10,
as well as, 9.04. With identical results.

Any help would be greatly appreciated.

Thanks.

---

### Post by amauk on 2009-03-30
> **thenewmexican said:**
> Is it too much to ask. For the Ubuntu people to fix the NVIDIA driver problem that exists in 8.04,8.10, and 9.04beta.Well, Canonical can't fix proprietary drivers. You're asking the wrong people
complain to Nvidia

[IMG]http://www.snoopy.force9.co.uk/prop-drivers.png.png[/IMG]

---

### Post by norwoods on 2009-03-30
i update to the latest nvidia proprietary prereleases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.41 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using System-->Administration-->Synaptic Package Manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev

---

### Post by James_Lochhead on 2009-03-30
> **norwoods said:**
> 
nvidia-glx-180


This is the one you want. Installing that should install all the others that are necessary as well.

---

### Post by Dougie187 on 2009-03-30
> **thenewmexican said:**
> Is it too much to ask. For the Ubuntu people to fix the NVIDIA driver problem that exists in 8.04,8.10, and 9.04beta.

The answer would be yes, it is too much to ask that the Ubuntu people fix the Nvidia problem. As you see your question even defines why it is too much to ask. It isn't an ubuntu problem, it's an nvidia problem.

There are people who might be able to help make your nvidia card, since it sounds like it doesn't, but none of us can fix it. Only nvidia can.

---

### Post by rolandrock on 2009-03-30
Have you tried getting latest Nvidia drivers from:
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Have a good read of the instuctions and any faqs, readme etc.  Lots of things can go wrong.

---

### Post by thenewmexican on 2009-03-30
Thanks to all for the input.
I have downloaded and installed the most recent NVIDIA drivers.
Dated. Today. March 30, 2009.

I still get the same result.

---

### Post by rolandrock on 2009-03-31
Were there errors?  Did the install think it was successful?
Immediately after re-boot, post:
/var/log/Xorg.0.log
/var/log/syslog

Post output from:
tail -200 messsages
glxinfo

What you are probably experiencing is a conflict between different drivers.  When googling for your problem, see if anyone fixed this by blacklisting a module.  This may apply to you.

---

### Post by thenewmexican on 2009-03-31
Yes. Houston we have a problem. Here are the relevant parts of 
Xorg.0.log

(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

And. Also. syslog

Mar 30 19:09:54 localhost kernel: [   73.307209] NVRM: Xid (0001:00): 6, PE0001 
Mar 30 19:09:54 localhost kernel: [   73.307788] NVRM: os_map_kernel_space: can't map 0xe0100000, invalid context!
Mar 30 19:09:54 localhost kernel: [   73.307806] NVRM: os_map_kernel_space: can't map 0xe0100000, invalid context!
Mar 30 19:09:54 localhost kernel: [   73.312770] NVRM: Xid (0001:00): 43, CMDre 00000000 00000000 00000000 00000001 00000001

Mar 30 19:09:57 localhost kernel: ap 0xe0100000, invalid context!
Mar 30 19:09:57 localhost kernel: [   74.368011] NVRM: os_map_kernel_space: can't map 0xe0100000, invalid context!
Mar 30 19:09:57 localhost kernel: [   74.368043] NVRM: os_map_kernel_space: can't map 0xe0100000, invalid context!
Mar 30 19:09:57 localhost kernel: [   74.370494] NVRM: os_map_kernel_space: can't map 0xe0100000, invalid context!
Mar 30 19:09:57 localhost kernel: [   74.370526] NVRM: os_map_kernel_space: can't map 0xe0100000, invalid context!
Mar 30 19:09:57 localhost kernel: [   74.372978] NVRM: os_map_kernel_space: can't map 0xe0100000, invalid context!
Mar 30 19:09:57 localhost kernel: [   74.373010] NVRM: os_map_kernel_space: can't map 0xe0100000, invalid context!

---

### Post by rolandrock on 2009-03-31
Can you post the output of:

lspci

This command lists connected pci devices.

---

### Post by rolandrock on 2009-03-31
Also, check this post [http://ubuntuforums.org/showthread.php?t=598780](http://ubuntuforums.org/showthread.php?t=598780)

---

### Post by thenewmexican on 2009-03-31
lspci 

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

---

### Post by thenewmexican on 2009-03-31
Thanks for the link.
Tried it.

Same result.

Thanks again.

---

### Post by inobe on 2009-03-31
i am thinking onboard video, i haven't researched your motherboard specs but would suggest disabling onboard video in the bios prior to activating a video card.

assuming you used onboard video prior to installing the card.

---

### Post by inobe on 2009-03-31
i checked on the card, it doesn't seem to be up for sale any more ..

a device from 07" 

you may want to test it on another pc to confirm it's operating properly.

---

### Post by norwoods on 2009-03-31
did you install nvidia-180-modaliases?

---

### Post by rolandrock on 2009-03-31
To recap, you have gone to Nvidia's website, downloaded the latest driver for your GPU/platform.  You have used CtrlAltF1 to open a command line, killed gdm, installed the driver successfully by following the instructions provided by the installer program which also configured your xorg.conf to use the correct driver.

Can you check that in System->Administration->HardwareDrivers, there are no proprietary drivers in use.  Although you are using proprietary drivers, you have installed them manually.  The HardwareDrivers program only refers to drivers that it manages.  If there is something enabled here, you could try disabling it and reinstalling your downloaded driver.

If still not working, try posting output of:
grep -i nv /etc/modprobe.d/*

Note, this will normally produce output like:
/etc/modprobe.d/aliases:alias char-major-195-* nvidia
/etc/modprobe.d/blacklist-framebuffer:blacklist nvidiafb

Anthing else might be intresting.

---

### Post by dougalkerr on 2009-03-31
Reports in one of the Linux mags I picked up this week (the one with green fron cover this month) that NVidia have finally fixed broken drivers for Ubuntu 8.10. I didn't buy the mag so can't tell you which one it is but, the report said yyou just had to follow the 'fix' on the NVidia site. If you still have problems let them know... they are the manufacturers.
Personally I install ENVY to get NVidia cards to work and so far no problem if instructions are followed to the letter. The install runs fairly automatically with minimal input needed from you.
Hang in there...

---

### Post by thenewmexican on 2009-03-31
I haven't see nvidia-180-modaliases before.
Is that installabled with apt-get install nvidia-180-modaliases ??

I tried that. But. I get E: Couldn't find package nvidia-180-modaliases.

Thanks anyways.

---

### Post by thenewmexican on 2009-03-31
*to recap, you have gone to Nvidia's website, downloaded the latest driver for your GPU/platform. You have used CtrlAltF1 to open a command line, killed gdm, installed the driver successfully by following the instructions provided by the installer program which also configured your xorg.conf to use the correct driver.*

Yes. All done as you have described above.


*Can you check that in System->Administration->HardwareDrivers, there are no proprietary drivers in use. Although you are using proprietary drivers, you have installed them manually. The HardwareDrivers program only refers to drivers that it manages. If there is something enabled here, you could try disabling it and reinstalling your downloaded driver.*

I have done the above. No proprietary drivers are enabled.

 *grep -i nv /etc/modprobe.d/* produces*
/etc/modprobe.d/aliases:alias char-major-195-* nvidia
/etc/modprobe.d/blacklist-framebuffer:blacklist nvidiafb
/etc/modprobe.d/lrm-video:# Make nvidia/nvidia_legacy and fglrx use /sbin/lrm-video to load
/etc/modprobe.d/lrm-video:install nvidia /sbin/lrm-video nvidia $CMDLINE_OPTS
/etc/modprobe.d/lrm-video:install nvidia_legacy /sbin/lrm-video nvidia_legacy $CMDLINE_OPTS
/etc/modprobe.d/lrm-video:install nvidia_new /sbin/lrm-video nvidia_new $CMDLINE_OPTS
/etc/modprobe.d/nvidia-kernel-nkc:alias char-major-195* nvidia
/etc/modprobe.d/nvidia-kernel-nkc:options nvidia NVreg_DeviceFileUID=0 NVreg_DeviceFileGID=44 NVreg_DeviceFileMode=0660


Thanks again.

---

### Post by inobe on 2009-03-31
> **thenewmexican said:**
> I haven't see nvidia-180-modaliases before.
Is that installabled with apt-get install nvidia-180-modaliases ??

I tried that. But. I get E: Couldn't find package nvidia-180-modaliases.

Thanks anyways.

in synaptic search for nvidia' if nvidia-180-modaliases isn't installed' install it now.

but only do that if you have the 180 driver installed.

i never once thought you didn't do this to begin with

---

### Post by rolandrock on 2009-03-31
There doesn't seem to be anything blacklisted.  Perhaps someone cleverer than me knows if the entries in lrm-video and nvidia-kernel-nkc are relevant.

VastOne has written an excellent clear howto here [http://ubuntuforums.org/showthread.php?t=1110025&page=3](http://ubuntuforums.org/showthread.php?t=1110025&page=3) but the only thing I see not already mentioned is purging the previous installs.

I would start again and follow VastOne's instructions (especialy the 'sudo apt-get remove --purge nvidia*' line) and see if that works.

Could it be hardware failure?  Problems with power connections between PCU and GPU can make the GPU run off the motherboard on low power with unpredictable results.

---

### Post by Panarchy on 2009-03-31
> **rolandrock said:**
> Have you tried getting latest Nvidia drivers from:
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Have a good read of the instuctions and any faqs, readme etc.  Lots of things can go wrong.

I got a kernel source code error...

> **norwoods said:**
> i update to the latest nvidia proprietary prereleases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.41 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using System-->Administration-->Synaptic Package Manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev

Thanks, trying that now.

---

### Post by graysky on 2009-04-02
@op - you probably wanna post your results to the [nv linux forum](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14) as well.

---

### Post by kmnielsen on 2009-04-02
[COLOR="DarkRed"]**@Dougie187**[/COLOR]

I dont think its right too say it too muche too ask. First Ubuntu DOSENT give any warrnings about the problem before installing or in the install proces ! That i dont understand it would be an easy way too get around the nvidia issue !!!

Second we are not all able to have another grafic card, mening the computer came with an onboard nvidia chipset !

For me its more like a... We dont like nvidia, they arnt friends of Ubuntu and wont "play" with us there for we just bla bla bla....

And sec one shoulded be a nerd too install an functionell driver for a standard grafic card.

So with that attitude your one of the "nerds" p.ssing pepl of and making them go other ways and taking bad about Ubuntu wich i like, but cant run because of the driver issue ! 

9.04 i cant even install !!! Install runs fine but cant finish and its 99% because of the nvidia chipset !!!

Why cant Ubuntu make it work when OpenSUSE works just fine with nvidia ???

Well this is just my point of view !

[COLOR="DarkGreen"][B]Thanks too pepl behinde Ubuntu for there work, just missing the crem on top of the cake "nvidia" solution !
[/B][/COLOR]
Best regards
Kim M NIelsen

---

### Post by upchucky on 2009-04-02
the following is the only proper way to set up nvidia on ubuntu **8.04, **other methods including envy are workarounds. they work on some machines, and not on others simply because each machine is different.

i have not tested this on 8.10


Set up Nvidia driver

Print out this guide, you will be in pure CLI for part of the install.

1)  Download the driver for your Nvidia Card from [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
	1.a) Make sure its in your home directory, this will make it so we don't have to change directories later when were in terminal.

2) Open a terminal: Applications--> Accessories--> Terminal

3) sudo apt-get install build-essential

4) gksudo gedit /etc/modules
	4.a) Add "nvidia" without quotes to the list.
	4.b) Save and Exit

5) gksudo gedit /etc/default/linux-restricted-modules-common
	5.a) Add "nv" without quotes to the restricted list. It should look exactly like this: DISABLED_MODULES="nv"
	5.b) Save and Exit

6) sudo cp /etc/X11/xorg.conf ./xorg.conf.backup

7) sudo rm /etc/X11/xorg.conf
	7.a) Were just deleting your old xorg.conf file, we backed it up in step 6 just in case we ever need it back again.
	7.b) Getting rid of old drivers, use one or more of the sections that apply to you:
		-------------------------------------------------------------------------------------------------------
		If you used Envy to attempt a previous nvidia install please run this command now before you go on:

               sudo envy --uninstall-all 
		sudo dpkg -P envy 

		-------------------------------------------------------------------------------------------------------
		If you have some old Ubuntu repository/restricted driver manager attempts installed please run this command before you go on:

		sudo apt-get remove --purge nvidia*
                sudo rm /lib/restricted-modules/.nvidia*

		-------------------------------------------------------------------------------------------------------
		If you have a failed NVIDIA*.run (drivers from the nvidia.com site) run this command before you go on:

		sudo nvidia-installer --uninstall

		-------------------------------------------------------------------------------------------------------
####################################################################################
##................................................................................##
## Alright Now Assuming That You are starting with a clean slate lets move forward##
##................................................................................##
####################################################################################

8) CTRL-ALT-F1
	8.a) Okay were in Command Line only now, we have a little left to do in here.
	8.b)login:
	8.c)Password:

9) sudo /etc/init.d/gdm stop
	9.a) This step shuts down the x-server and gnome desktop manager

10) sudo chmod a+x ./NVIDIA*.run
	10.a) We made the nvidia installer executable.

11) sudo ./NVIDIA*.run
	11.a) Answer to the affirmative for all questions.
	11.b) Be sure to specifically say you DO WANT it to write a new xorg.conf
	11.c) If you somehow answered incorrectly on the last question in the installer then:
		c.I) sudo nvidia-xconfig #this will write a new or attempt repair of
                     an xorg.conf file for you.

12) sudo /etc/init.d/gdm start
	12.a) You should see an Nvidia Logo, and then be put at your login screen, 
              you should also be able to enable desktop effects.

Optional But recommended:
13) To get the driver to update itself when a new kernel is installed from the update
    manager be sure to follow the guide in this link:
     [http://ubuntuforums.org/showpost.php?p=5227704&postcount=1](http://ubuntuforums.org/showpost.php?p=5227704&postcount=1)

---

