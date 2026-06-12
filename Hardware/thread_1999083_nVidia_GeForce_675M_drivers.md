---
title: "nVidia GeForce 675M drivers"
date: 2012-06-07
forum: Hardware
---

### Post by Stonecold1995 on 2012-06-07
I bought a MainGear ex-L 15 SuperStock laptop, and it has the nVidia GeForce GTX 675M GPU.

I've heard that nouveau is horribly incomplete, and this is such a new card too.  Anyway, I want to get the proprietary driver.  Where/when can I get that?  I looked under nVidia's [Linux drivers section]("http://www.nvidia.com/object/linux-display-amd64-295.53-driver.html") but only up to the 635M is supported.  So my questions are this:
- At this rate, when will the proprietary driver for the 675M come out?
- Will the current proprietary driver work even though it's only up to 635M (It supports the 675, but not 675M)?
- How bad is the open source driver?  I am using another computer right now with an AMD 6770M GPU, but I've heard the open source AMD drivers are really good.  So how much worse will nouveau be (It doesn't even do 3D acceleration if I'm right)?

I know the GeForce GTX 675M is a LOT more powerful than the AMD Radeon 6770M, but if the driver isn't very good will this GPU still be better?  Because I may be stuck between choosing either the weaker AMD with good driver support or the powerful nVidia with poor driver support.

Also, when I boot my computer it first says "Error: No video mode selected" (or something like that) for a few seconds before it starts.  Does this mean the GPU isn't detected at all??  All the desktop effects (on KDE) work on both OpenGL and XRender though.

Sorry for all the questions but I'm really nervous because this computer cost over $3,000 and if I have to wait many years for the proprietary driver to come out (or for the open source one to be improved) it'll suck!

---

### Post by mikewhatever on 2012-06-07
> **Stonecold1995 said:**
> I bought a MainGear ex-L 15 SuperStock laptop, and it has the nVidia GeForce GTX 675M GPU.

I've heard that nouveau is horribly incomplete, and this is such a new card too.  Anyway, I want to get the proprietary driver.  Where/when can I get that?  I looked under nVidia's [Linux drivers section]("http://www.nvidia.com/object/linux-display-amd64-295.53-driver.html") but only up to the 635M is supported. 

Nvidia usually releases drivers when they are deemed ready. Try asking at forums.nvidia.com.

>  So my questions are this:
- At this rate, when will the proprietary driver for the 675M come out?
- Will the current proprietary driver work even though it's only up to 635M (It supports the 675, but not 675M)?
- How bad is the open source driver?  I am using another computer right now with an AMD 6770M GPU, but I've heard the open source AMD drivers are really good.  So how much worse will nouveau be (It doesn't even do 3D acceleration if I'm right)?

Lots of questions for Nvidia, not sure why ask them here. Try forums.nvidia.com. ;)

> Sorry for all the questions but I'm really nervous because this computer cost over $3,000 and if I have to wait many years for the proprietary driver to come out (or for the open source one to be improved) it'll suck!
That is life. I'd strongly recommend researching **before** buying, that is, if you need good Linux support.

---

### Post by typhoon_tip on 2012-06-13
Come on, you need to go here:
[http://www.nvidia.com/Download/Find.aspx?lang=en-us](http://www.nvidia.com/Download/Find.aspx?lang=en-us)

Select your GeForce GTX 675M, then select Linux 32 or 64 bits, and click Search, there is a driver already (**295.59 June 11, 2012**).

Happy full-powered Ubuntu ! :popcorn:

EDIT: make sure you read the "how-to" in order to install the driver ! X need to be stopped for installation, so you need to do it from command line. And, if you update the kernel, you will have to reinstall this driver because it will not install DKMS modules.

---

### Post by Stonecold1995 on 2012-06-13
> **typhoon_tip said:**
> Come on, you need to go here:
[http://www.nvidia.com/Download/Find.aspx?lang=en-us](http://www.nvidia.com/Download/Find.aspx?lang=en-us)

Select your GeForce GTX 675M, then select Linux 32 or 64 bits, and click Search, there is a driver already (**295.59 June 11, 2012**).

Happy full-powered Ubuntu ! :popcorn:

EDIT: make sure you read the "how-to" in order to install the driver ! X need to be stopped for installation, so you need to do it from command line. And, if you update the kernel, you will have to reinstall this driver because it will not install DKMS modules.

I looked at the howto, but it didn't make much sense.  For example, it told me to edit xorg.conf, but I don't think Kubuntu (or any *buntus) have it.  It also said to edit some other files.  From what I grasped, this is what I need to do:
-Stop X.
-Run the installer
-Reboot

Is that really all?  Will the installer automatically take care of nouveau or do I have to remove nouveau manually?  The instructions really didn't make any sense...

---

### Post by typhoon_tip on 2012-06-13
> **Stonecold1995 said:**
> I looked at the howto, but it didn't make much sense.  For example, it told me to edit xorg.conf, but I don't think Kubuntu (or any *buntus) have it.  It also said to edit some other files.  From what I grasped, this is what I need to do:
-Stop X.
-Run the installer
-Reboot

Is that really all?  Will the installer automatically take care of nouveau or do I have to remove nouveau manually?  The instructions really didn't make any sense...

OK, sorry indeed, I supposed you would be coming back. I try to give you some instructions, although not sure 100% they work in your case, try it :)

1) Copy the file in your home folder from where you downloaded
2) Restart your Ubuntu
3) At the login, do NOT login
4) Press CTRL+ALT+F1
5) You should be presented a terminal login, enter your user and password and press enter
6) After is ready, type:
```
sudo /etc/init.d/kdm stop
```
7) Wait for a successful message (like "process stop/waiting", unsuccessful would be "Unknown process lightdm")
8) Type ./NV and press tab (attention ! capital letters MATTERS !), it will show the full command name and press enter
9) The installer will start, and will do everything automatically
10) It may ask you to blacklist "nouveau" driver in the Kernel first, it can do automatically and it works, you will need to restart after that and enter the special command session once again
11) At the end, it will ask you if you want to configure XORG automatically, just choose YES !
12) Restart... should be all fine !
13) After login, go to NVIDIA panel and enable "Sync to VBlank", for proper and totally tear free experience.

Just in case, remember this:
./NV then press tab, then type " --uninstall" option to run the command, it will clean up the driver, if you mess up the installation (it will also remove nouveau blacklist).

:)

EDIT: sorry, I just noticed you are using KUBUNTU, and not XUBUNTU, check my edit on the above command on how to properly stop X, or refer to this:
[http://ubuntuforums.org/showthread.php?t=898205](http://ubuntuforums.org/showthread.php?t=898205)

---

### Post by typhoon_tip on 2012-06-13
... and may I ask, with such incredible machine, why don't you run Ubuntu 64 bits with Unity ? Is certainly a greater experience :)

---

### Post by Stonecold1995 on 2012-06-13
UPDATE:  So I sort of installed it.  When I ran the .run file it told me to remove nouveau, so I did (I used the blacklist technique, etc).  Then I ran the setup file and it installed and told me to reboot, but when I did a bunch of problems started happening.  The resolution was stuck at the minimum, XRender was broken, OpenGL worked but all effects were screwed up.  So basically it screwed up my computer pretty bad.  So I decided to restore it from a backup I made minutes before I tried installing the driver.  I backed up lib*, etc, and usr and restored them all and made sure the permissions/ownership were correct, and rebooted.  It at least booted with nouveau this time, but now it had even WORSE problems!  Although X worked fine, upon logging in it instantly said something like "Could not execute /usr/lib/some-kernel-generic-something: success".  When I clicked OK and it logged in, it asked me if it wanted me to make it "forget" a bunch of audio hardware (which I didn't), and also the internet was dead!  It didn't simply "not connect", but wlan0 and eth0 could not be found.  Plus, I tried running something as root and it simply said "Error running as root".  So it was pretty much screwed up.  I kind of gave up then and reinstalled everything (restoring the backed up /home of course).  It's restoring data as I type this, but I'm still stuck with the nouveau driver. ;_;

Anyone know what the problem is (and why the backup didn't work)?

> **typhoon_tip said:**
> ... and may I ask, with such incredible machine, why don't you run Ubuntu 64 bits with Unity ? Is certainly a greater experience :)
I prefer KDE.  Although it's slightly more resource-hungry (which isn't really a problem with my computer), it is MUCH more customizable (I can't stand lack of customization options) and it looks better IMO.  I choose Kubuntu because Ubuntu seemed to "user-friendly" and easy to use, Debian seemed to hard to use (and too unstable), and Fedora has yum which I hate (from experiences with OpenSUSE) and has a smaller user-base, so I decided to go with Kubuntu in the end, and I love it!
inb4 KDE vs Unity flamewar
(I still think KDE is better) :3

---

### Post by typhoon_tip on 2012-06-13
Did it ask you to create X file ? That problem seems to arise from a missing X file. The installer create it at the end, and ask you for it. Before restoring, after finishing install, run this command manually:
nvidia-xconfig

It will create one for you. After that, post the content of what is created here.

> **Stonecold1995 said:**
> I prefer KDE.  Although it's slightly more resource-hungry (which isn't really a problem with my computer), it is MUCH more customizable (I can't stand lack of customization options) and it looks better IMO.  I choose Kubuntu because Ubuntu seemed to "user-friendly" and easy to use, Debian seemed to hard to use (and too unstable), and Fedora has yum which I hate (from experiences with OpenSUSE) and has a smaller user-base, so I decided to go with Kubuntu in the end, and I love it!
inb4 KDE vs Unity flamewar
(I still think KDE is better) :3

I misread your post, thought you were using XFCE loll, waste of resources with such a machine ! KDE is more than fine ;)

---

### Post by typhoon_tip on 2012-06-13
One more thing: it is very likely that your laptop has Hybrid technology (two video card), disable the onboard card in the BIOS before attempting to install the driver, or it may fail like that. Enable only the discreet card. We will concern about power saving after.

---

### Post by Stonecold1995 on 2012-06-13
> **typhoon_tip said:**
> One more thing: it is very likely that your laptop has Hybrid technology (two video card), disable the onboard card in the BIOS before attempting to install the driver, or it may fail like that. Enable only the discreet card. We will concern about power saving after.
It has Nvidia and integrated Intel graphics (I have an i7), but I don't have two video cards, only a single dedicated GPU.

---

### Post by typhoon_tip on 2012-06-13
> **Stonecold1995 said:**
> It has Nvidia and integrated Intel graphics (I have an i7), but I don't have two video cards, only a single dedicated GPU.

Please do this:
```
lspci
```

...and post the output here.

---

### Post by Stonecold1995 on 2012-06-13
> **typhoon_tip said:**
> Please do this:
```
lspci
```

...and post the output here.

```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)
00:1c.3 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 1212 (rev a1)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)
03:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 0a)
04:00.0 Network controller: Atheros Communications Inc. AR9300 Wireless LAN adaptor (rev 01)
05:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller (rev 30)
```

---

### Post by typhoon_tip on 2012-06-13
> **Stonecold1995 said:**
> ```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 **VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)**
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)
00:1c.3 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 **VGA compatible controller: NVIDIA Corporation Device 1212 (rev a1)**
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)
03:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 0a)
04:00.0 Network controller: Atheros Communications Inc. AR9300 Wireless LAN adaptor (rev 01)
05:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller (rev 30)
```

Both cards are enabled, you definitely need to disable the internal GPU before trying the driver again. That's the problem.

---

### Post by Stonecold1995 on 2012-06-13
> **typhoon_tip said:**
> Both cards are enabled, you definitely need to disable the internal GPU before trying the driver again. That's the problem.

So is that why it failed even when nouveau was removed?

How do I disable the nouveau and the Intel graphics driver?  Also, I think maybe the Nvidia GPU I have isn't doing anything (and is practically off), because nouveau keeps giving "Unknown i2c port" errors over and over and over (to the point where it's hard to do anything without X running because errors are spammed everywhere).  So could it be that nouveau is completely incompatible and only the Intel graphics is doing anything?

---

### Post by typhoon_tip on 2012-06-13
> **Stonecold1995 said:**
> So is that why it failed even when nouveau was removed?

How do I disable the nouveau and the Intel graphics driver?  Also, I think maybe the Nvidia GPU I have isn't doing anything (and is practically off), because nouveau keeps giving "Unknown i2c port" errors over and over and over (to the point where it's hard to do anything without X running because errors are spammed everywhere).  So could it be that nouveau is completely incompatible and only the Intel graphics is doing anything?

It's a very, very weird behavior. When you use nouveau, it uses NVIDIA, but if you install the driver, it conflict with Intel. This is typical, I have found it in almost all cases.

To remove nouveau strictly use the installation program (it ask you if you want the install to make the blacklist for you, do not make it manually !).

To disable the Intel internal GPU, use the BIOS. If the BIOS has not this option, you can use switcheroo script as a last resort, but I think such an advanced computer has this option.

---

### Post by Stonecold1995 on 2012-06-13
> **typhoon_tip said:**
> To remove nouveau strictly use the installation program (it ask you if you want the install to make the blacklist for you, do not make it manually !).
That's what I did first.  It asked if it could remove nouveau for me and I said yes, so it generated a blacklist file and did some other stuff but then said it failed.  So I rebooted and tried again, and apparently it's "blacklisting" of nouveau didn't work at all, so I looked online and did followed instructions to do it manually and it worked, but the proprietary Nvidia didn't install.

Also, is there a way to prevent the logs and console from being spammed with "Unknown i2c port" errors so I can at least work and have visual feedback (currently I have to assume what I'm typing because I can't really see much after the errors push it off the screen)?

---

### Post by typhoon_tip on 2012-06-13
> **Stonecold1995 said:**
> Also, is there a way to prevent the logs and console from being spammed with "Unknown i2c port" errors so I can at least work and have visual feedback (currently I have to assume what I'm typing because I can't really see much after the errors push it off the screen)?

Yes, there is, switch off the second VGA card hehe, try to switch it off then I'm sure everything will be OK.

---

### Post by Stonecold1995 on 2012-06-13
> **typhoon_tip said:**
> Yes, there is, switch off the second VGA card hehe, try to switch it off then I'm sure everything will be OK.
I don't know how to do that. -_-

---

### Post by typhoon_tip on 2012-06-13
> **Stonecold1995 said:**
> I don't know how to do that. -_-

Reboot your computer and enter BIOS setup. It should be a key to be pressed (usually F1, or DEL, only works at BIOS boot), then find the graphic option, it should allow you to start as hybrid (both cards), discreet or integrated one only. Choose discreet only.

Be sure you do not change anything else in BIOS settings, if you are not familiar with.

---

### Post by Stonecold1995 on 2012-06-14
> **typhoon_tip said:**
> Reboot your computer and enter BIOS setup. It should be a key to be pressed (usually F1, or DEL, only works at BIOS boot), then find the graphic option, it should allow you to start as hybrid (both cards), discreet or integrated one only. Choose discreet only.

Be sure you do not change anything else in BIOS settings, if you are not familiar with.
I checked my BIOS and see no option for that.  For some reason my computer has a very simple BIOS, with only options for things like system time, boot order, boot password, etc.  It doesn't even have overclock/overvoltage configuration (or any other low-level hardware config for that matter).

Also, I think my Nvidia isn't doing anything, because according to hardinfo, the OpenGL renderer is "Mesa DRI Intel(R) Sandybridge Mobile".  So does that mean nouveau isn't doing anything?  Damn, this computer is making me feel stupid... ;_;

Also, if it is of any use, here's a copy of the hardware report generated by hardinfo a few minutes ago: [http://pastehtml.com/raw/c1fpwhji8.html](http://pastehtml.com/raw/c1fpwhji8.html)

---

### Post by typhoon_tip on 2012-06-14
> **Stonecold1995 said:**
> I checked my BIOS and see no option for that.  For some reason my computer has a very simple BIOS, with only options for things like system time, boot order, boot password, etc.  It doesn't even have overclock/overvoltage configuration (or any other low-level hardware config for that matter).

Also, I think my Nvidia isn't doing anything, because according to hardinfo, the OpenGL renderer is "Mesa DRI Intel(R) Sandybridge Mobile".  So does that mean nouveau isn't doing anything?  Damn, this computer is making me feel stupid... ;_;

Also, if it is of any use, here's a copy of the hardware report generated by hardinfo a few minutes ago: [http://pastehtml.com/raw/c1fpwhji8.html](http://pastehtml.com/raw/c1fpwhji8.html)

Rofll no panic. Is seeing only the integrated video card, thus not using anything else, that's why driver install fails.

If no BIOS settings no problem ! Search the net for vgaswitcheroo, you can use a boot script to turn the power DOWN for the integrated video card and turn the power ON for NVIDIA card, so that then you can install the driver (sorry I cannot point you right now to an exact script... but you will find many examples !).

---

### Post by Stonecold1995 on 2012-06-14
> **typhoon_tip said:**
> Rofll no panic. Is seeing only the integrated video card, thus not using anything else, that's why driver install fails.

If no BIOS settings no problem ! Search the net for vgaswitcheroo, you can use a boot script to turn the power DOWN for the integrated video card and turn the power ON for NVIDIA card, so that then you can install the driver (sorry I cannot point you right now to an exact script... but you will find many examples !).
So I found that vgaswitcheroo is already present in "/sys/kernel/debug/vgaswitcheroo" (with an empty file called "switch" in that directory.  But I looked online and still have no idea how to use it (and I don't want to experiment because I've already screwed up my other computer countless times by experimenting).

So tell me if this is right:
1) I blacklist nouveau by following the instructions [here]("http://linuxers.org/howto/how-remove-nouveau-drivers-ubuntu") (that's what I did last time and it seemed to effectively remove nouveau).
2) Somehow use vgaswitcheroo to inactivate the Intel graphics.
3) Reboot (without nouveau it shouldn't start X automatically, right?)
4) Run the .run installer file.
5) Reboot again.

Then it should work, right?

On a semi-related note, will this proprietary driver enable CUDA for my GPU?

---

### Post by typhoon_tip on 2012-06-14
Try the below:

1) Somehow use vgaswitcheroo to inactivate the Intel graphics** AND power on the NVIDIA (must be done at once, two or three line script, or you have two video cards off, and need to reinstall...)**
2) I blacklist nouveau by following the instructions [here]("http://linuxers.org/howto/how-remove-nouveau-drivers-ubuntu") (that's what I did last time and it seemed to effectively remove nouveau). CORRECT ! The last command (sudo update-initramfs -u) might not be necessary, but running it won't hurt so... It is run by the installer.
3) Reboot (without nouveau it shouldn't start X automatically, right? Yes, it will fail to start X because no driver, and fall directly into command prompt, anyway that's what you need !!)
4) Run the .run installer file.
5) Reboot again.

I'm looking for a correct script for vgaswitcheroo.

---

### Post by typhoon_tip on 2012-06-14
GOT IT !

Referring to this page:
[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

Do exactly what is written at "Script for use during bootup".

This line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash modeset=1 hybridopts=ON,IGD,OFF"
```

**MUST** change to:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash modeset=1 hybridopts=ON,DIS,OFF"
```

Attention ! Before blacklisting nouveau, make sure the computer starts ! In graphic mode ! You may notice some different behavior than with Intel card anyway.

---

### Post by Stonecold1995 on 2012-06-14
> **typhoon_tip said:**
> GOT IT !

Referring to this page:
[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

Do exactly what is written at "Script for use during bootup".

This line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash modeset=1 hybridopts=ON,IGD,OFF"
```

**MUST** change to:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash modeset=1 hybridopts=ON,DIS,OFF"
```

Attention ! Before blacklisting nouveau, make sure the computer starts ! In graphic mode ! You may notice some different behavior than with Intel card anyway.

So I just put the script in "/etc/initramfs-tools/scripts/local-top/" and change the line in "/etc/default/grub"?  Or do I do everything else on that page as well (like doing "echo ON > /sys/kernel/debug/vgaswitcheroo/switch" or whatever)?  If so, which of the vgaswitcheroo options do I use?

---

### Post by Yellow Pasque on 2012-06-14
You need to completely purge nvidia driver and then follow: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

EDIT: you'll probably need to add this PPA before installing bumblebee since you have such a new nvidia GPU: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by Stonecold1995 on 2012-06-14
> **Temüjin said:**
> You need to completely purge nvidia driver and then follow: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

EDIT: you'll probably need to add this PPA before installing bumblebee since you have such a new nvidia GPU: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
I'm confused again.  Do I just have to install Bumblebee and that'll somehow allow Nvidia to be installed or will I always have to use "optirun application_name"?

So is this all I do?
1) Add ppa:/ubuntu-x-swat/x-updates PPA.
2) Install Bumblebee

3) Put the script from [here]("https://help.ubuntu.com/community/HybridGraphics") in the right place.
4) Add GRUB_CMDLINE_LINUX_DEFAULT="quiet splash modeset=1 hybridopts=ON,DIS,OFF" to the grub file.

5) Follow the blacklist instructions [here]("http://linuxers.org/howto/how-remove-nouveau-drivers-ubuntu").
6) Reboot (X shouldn't start).

7) Execute the .run installer.
8) Reboot again and it should be done.

Is that correct?  With things like Bumblebee, will I just leave it alone and it'll somehow enable the proprietary drivers to work or will I have to manually run it ("optirun startx" or something)?  This is really confusing just for installing Nvidia...

Also, when I try "sudo apt-get remove --purge nvidia*", it doesn't work.  Same with using "sudo apt-get purge" and "sudo apt-get remove".  Using "sudo apt-get purge nvidia-common" DOES work, but it's only one package, and I assume nvidia* means all Nvidia packages.

---

### Post by typhoon_tip on 2012-06-15
> **Stonecold1995 said:**
> So I just put the script in "/etc/initramfs-tools/scripts/local-top/" and change the line in "/etc/default/grub"?  Or do I do everything else on that page as well (like doing "echo ON > /sys/kernel/debug/vgaswitcheroo/switch" or whatever)?  If so, which of the vgaswitcheroo options do I use?

No need to do the ECHO ON and so on, just follow the script section I mentioned to you ! It is included in that script the ECHO ON stuff.

Regarding Bumblebee, stick to the old procedure above first, with manual install of the driver, if it doesn't work we then go to plan B. _Do not mix the plans_ ! :P

---

### Post by Stonecold1995 on 2012-06-15
> **typhoon_tip said:**
> No need to do the ECHO ON and so on, just follow the script section I mentioned to you ! It is included in that script the ECHO ON stuff.

Regarding Bumblebee, stick to the old procedure above first, with manual install of the driver, if it doesn't work we then go to plan B. _Do not mix the plans_ ! :P
It did nothing. -_-

I added the line to grub, I put the script in the right directory, made it executable, and I blacklisted nouveau.  Then I rebooted, and tried executing the .run file.  It tried installing, but then said the installation failed.  Also, when I rebooted the first time it started X even though I thought I blacklisted nouveau, put the script in the right directory, and modified grub (I did do update-grub, etc).  Is there something I missed?  The OpenGL renderer is still "Mesa DRI Intel(R) Sandybridge Mobile" according to hardinfo.

EDIT: Could me having / encrypted have anything to do with it?  I just remembered that /boot is unencrypted, while / and /home are.  So could the script be trying to run before I'm able to enter the password, fail, and give up?  I do remember seeing an error about some file not found that displayed before I could enter the password.  If so, should I add "sleep 30" to the beginning of the script so it'll wait for me to mount all my drives??  It can take that long for me to mount both / and /home, because the passkey for / is 42 characters and the passkey for /home is 64.

---

### Post by typhoon_tip on 2012-06-15
Not sure about that... But given the level of attempts so far, why not try with a fresh, normal install ? And make the script work first.

---

### Post by Stonecold1995 on 2012-06-15
Re-installation really isn't an option for me.  Is there a way I can do what that script does but manually (so I don't have to mess with encryption, re-installing, etc)?  I don't know all that many bash commands so I can't decipher what that script does just by reading it.

Is there a script anywhere that can do this all for me, or a modified installer?  Because it's kind of hard to believe Nvidia would make it this hard to install on Linux, unless my computer just isn't compatible with it's configuration.

---

### Post by typhoon_tip on 2012-06-15
> **Stonecold1995 said:**
> Re-installation really isn't an option for me.  Is there a way I can do what that script does but manually (so I don't have to mess with encryption, re-installing, etc)?  I don't know all that many bash commands so I can't decipher what that script does just by reading it.

Is there a script anywhere that can do this all for me, or a modified installer?  Because it's kind of hard to believe Nvidia would make it this hard to install on Linux, unless my computer just isn't compatible with it's configuration.

You can make a manual script and try in the CTRL+ALT+F1 session first !

When logged in, type:
```
nano switchcards.sh
```

Paste into it the following content:
```
echo ON > /sys/kernel/debug/vgaswitcheroo/switch
echo DIS > /sys/kernel/debug/vgaswitcheroo/switch
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```

Press CTRL+O (write file) then enter.

Press CTRL+X to quit the text editor.

Run this command:
```
sudo ./switchcards.sh
```

If it says no permission, give it execute permission first.

If it works, you should see your display flicker for a moment and re-appear. Post here any error that may appear.

---

### Post by Stonecold1995 on 2012-06-15
I got the following errors:
```
alex@kubuntu:~sudo ./switchcards.sh
./switchcards.sh: 1: ./switchcards.sh: cannot create /sys/kernel/debug/vgaswitcheroo/switch: Directory nonexistent
./switchcards.sh: 2: ./switchcards.sh: cannot create /sys/kernel/debug/vgaswitcheroo/switch: Directory nonexistent
./switchcards.sh: 3: ./switchcards.sh: cannot create /sys/kernel/debug/vgaswitcheroo/switch: Directory nonexistent
```
So I tried creating /sys/kernel/debug/vgaswitcheroo, but it said "mkdir: cannot create directory `/sys/kernel/debug/vgaswitcheroo': Operation not permitted", which is weird because I used sudo.  I checked and even doing "cd /sys/kernel/debug" is not allowed (I can't access debug without doing "sudo dolphin" and navigating from there, or doing su.  So apparently the directory vgaswitcheroo doesn't exist, and even root won't let me create the directory.  Which is especially weird because I'm pretty sure I remember being able to open vgaswitcheroo and finding switch in there...

---

### Post by seenthelite on 2012-06-15
With Bumblebee you need to purge the nvidia drivers  you may have installed before installing Bumblebee.
Installing Bumblebee means you will be able to use both cards and will install the correct drivers for both cards, Intel for Intel, nvidia for nvidia. Using optirun<app> in the terminal when you want to use nvidia. 
I use it with Kubuntu and the Intel card handles all the KDE desktop effects anyway, Desktop Cube Animation etc;
All I done was follow the instructions at the Ubuntu Wiki page for Bumblebee, but this was immediately after a fresh install and updating. 
Installing Bumblebee takes care of the nouveau driver during installation.

---

### Post by Yellow Pasque on 2012-06-15
> **Stonecold1995 said:**
> it's kind of hard to believe Nvidia would make it this hard to install on Linux

Well, believe it. Nvidia does not officially support hybrid/Optimus graphics on Linux (which is really irritating given that most laptops sold today with discrete nvidia chips also have an Intel IGP).

> So is this all I do?

The first step is making sure the nvidia driver is purged. Since you installed it by manually running the nvidia installer, you have to run the installer again with --uninstall option.

After that, add x-swat repo:
```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
```

Then, follow the instructions for Bumblebee, and that's it. Do not mess with GRUB or try to manually install nvidia drivers again.

---

### Post by Stonecold1995 on 2012-06-15
I didn't install it manually.  It never successfully installed.  So when I tried running it with --uninstall it just told me it wasn't installed.  I tried installing Bumblebee (after adding that PPA), but optirun isn't working.

I just want to find out how to completely remove nouveau and inactivate the Intel graphics.  I'm pretty sure that's all I need to get the installer working, because conflict with other drivers is all that's preventing it from installing.  Is there a program I can run that will remove all the drivers, or some directory I should delete?  Because every time I do something that is suppose to remove the other drivers, I reboot and X is working perfectly again.  I think the vgaswitcheroo looks promising, but for some reason that directory doesn't exist anymore, I can't create "vgaswitcheroo" in /sys/kernel/debug for some reason, even as root!

---

### Post by Yellow Pasque on 2012-06-15
You don't deactivate the intel drivers because even when optirun uses the nvidia GPU  for rendering, the intel GPU is still used for display. That's how Optimus works.

Oh, and you don't want to run the nvidia installer directly. (Just delete the nvidia installer. It won't help you.) Bumblebee has to install the nvidia driver so that it doesn't interfere with the intel driver and bork your system.

You can blacklist nouveau like so:
```
echo "blacklist nouveau" | sudo tee -a /etc/modprobe.d/blacklist-nouveau.conf
sudo depmod -a
```

---

### Post by Stonecold1995 on 2012-06-15
> **Temüjin said:**
> You don't deactivate the intel drivers because even when optirun uses the nvidia GPU  for rendering, the intel GPU is still used for display. That's how Optimus works.

Oh, and you don't want to run the nvidia installer directly. (Just delete the nvidia installer. It won't help you.) Bumblebee has to install the nvidia driver so that it doesn't interfere with the intel driver and bork your system.

You can blacklist nouveau like so:
```
echo "blacklist nouveau" | sudo tee -a /etc/modprobe.d/blacklist-nouveau.conf
sudo depmod -a
```

How do I get Bumblebee to install it for me?  I installed it and it's not helping.  Also, I want to get the Nvidia to run with everything, not just what I run with optirun.  I know there's a way to do this, but the vgaswitcheroo is very confusing for me.

---

### Post by Yellow Pasque on 2012-06-15
> Also, I want to get the Nvidia to run with everything, not just what I run with optirun
Unless you're running on AC all of the time, that would be a waste of battery.

vgaswitcheroo isn't going to work with the proprietary nvidia driver. What happens when you use optirun? An error?

---

### Post by Stonecold1995 on 2012-06-15
> **Temüjin said:**
> Unless you're running on AC all of the time, that would be a waste of battery.

vgaswitcheroo isn't going to work with the proprietary nvidia driver. What happens when you use optirun? An error?
I am running on AC all the time.  And I'm also running Folding@home (which makes heavy use of the CPU, and can benefit greatly from the GPU).  So when the CPU is preoccupied rendering graphics, Folding@home suffers greatly, and it could simply benefit by using the GPU.  Is there a way to set Bumblebee to run *everything* with the GPU automatically?  Or would running Xorg with Bumblebee do that?

And when I try optirun, I get:
```
[ERROR]Cannot access secondary GPU - error: You need to change the ConnectedMonitor setting in /etc/bumblebee/xorg.conf.nvidia to 

[ERROR]Aborting because fallback start is disabled.
```
I don't know how to "change ConnectedMonitor settings".

Does Bumblebee make use of proprietary drivers, or only open source?  Because I kind of need proprietary for Folding@home...  If I have to, I'll use Bumblebee but it would be preferable to simply install the proprietary drivers (which need the other graphics to be inactivated, which is what's stumping me).

---

### Post by Stonecold1995 on 2012-06-16
Is using vgaswitcheroo all that's needed to do to inactivate the Intel driver so Nvidia can be installed?  I think nouveau was already uninstalled, so I don't need to do anything with that.  If all that's needed is to use vgaswitcheroo then I can add the file with SystemRescueCD, if permission is denied on Kubuntu.

Also, would using "sudo apt-get remove kubuntu-desktop xorg xserver-xorg" be needed?  I could remove X, run the Nvidia installer, then reinstall X.

---

### Post by seenthelite on 2012-06-16
This is an xorg.conf after installing Bumblebee as detailed on the Ubuntu Wiki.

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 295.53  (buildd@louvi)  Wed May 16 19:28:13 UTC 2012

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: builtin, VertRefresh source: builtin
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DFP-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 525M"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "nvidia-auto-select @1366x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

You could do other things like blacklisting or removing nouveau but it will not change this.

---

### Post by typhoon_tip on 2012-06-16
I still think you messed up the install and cannot get trough. Bumblebee should be quite straightforward to install. Perhaps you have an half installed driver somewhere that cannot be purged.

If re-install is not an option... take another hard drive and start with a clean install on that one of Bumblebee directly, to make sure it works.

---

### Post by Stonecold1995 on 2012-06-16
I don't want just open source drivers with Bumblebee, I want the Nvidia proprietary drivers.  I'm pretty sure they can install, but they need Intel graphics turned off temporarily.  That's really all I need to do, but is using vgaswitcheroo all I need to do that or is there more?

So I just need to know how to remove Intel's graphics, then I think Nvidia can be installed.

EDIT: I tried installing it again.  It said it installed successfully with no errors, it validated the install, and finished.  The only error was something like "Distribution provided pre-installation script failed.  Continue anyway?" at the very beginning.  However, at the end of the installation after I rebooted, X was messed up again (minimum resolution, no smooth graphics, partially broken X in general).  So I had to stop X, purge xserver-xorg, xorg, and kubuntu-desktop, and then reinstall them all to get it working again.

So what's with this?  I don't want open source, I need proprietary drivers (with CUDA support) specifically, and I can't fall back to nouveau, etc.  I don't think Bumblebee is an option if I can't set it to run with everything, and if it doesn't support proprietary drivers.

I will try installing Bumblebee on a fresh install as soon as I can and I'll post the results.

---

### Post by seenthelite on 2012-06-17
From my xorg.conf


```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 525M"
EndSection
```  

This is the nvidia proprietary driver installed by following the instructions at the Ubuntu Wiki. And you can run as many applications as you need to using the nvidia driver. My understanding is that if you can not disable the Intel GPU in your Bios and use Linux, you are stuck with Bumblebee.

---

### Post by Stonecold1995 on 2012-06-17
Could [this]("http://www.nvidia.com/object/linux-display-amd64-302.17-driver.html") version help me (v302.17)?  The one I've tried with was v295.59.  They both support the 675M, so could this one be an update that fixes the issue?  I'm hesitant to try it if it messes up X, but I couldn't understand much of the changelog so I couldn't decipher if one of the changes fixed the issue I'm having.

EDIT: I tried installing it, but the installer said my GPU wasn't supported, even though the official site says it's supported.  That's weird.  I know I have the 675M, and I know the updated installer supports it.  But why won't it detect it?

If I can't find out how to get it installed here, can anyone point me to a forum/service that might be able to?  I've tried Nvidia's forums already with no success.  If anyone knows of a paid service that would be fine too, I just really need the driver working.

---

### Post by typhoon_tip on 2012-06-17
I still think you have to look deeper in BIOS settings. I find it hard to believe that such an amazing machine doesn't have this option. Try looking in devices settings (PCI devices, onboard devices and so on), or try to ask the support staff of your laptop manufacturer.

---

### Post by tenmoi on 2012-06-17
> **Stonecold1995 said:**
> Could [this]("http://www.nvidia.com/object/linux-display-amd64-302.17-driver.html") version help me (v302.17)?  The one I've tried with was v295.59.  They both support the 675M, so could this one be an update that fixes the issue?  I'm hesitant to try it if it messes up X, but I couldn't understand much of the changelog so I couldn't decipher if one of the changes fixed the issue I'm having.

EDIT: I tried installing it, but the installer said my GPU wasn't supported, even though the official site says it's supported.  That's weird.  I know I have the 675M, and I know the updated installer supports it.  But why won't it detect it?

If I can't find out how to get it installed here, can anyone point me to a forum/service that might be able to?  I've tried Nvidia's forums already with no success.  If anyone knows of a paid service that would be fine too, I just really need the driver working.


I suggest that you do a clean install of kubuntu. After that install build-essential and libxft-dev

Then 
```
$sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```
```
$sudo add-apt-repository ppa:bumblebee/stable
```
```
$sudo apt-get update
```
```
$sudo apt-get upgrade
```
```
$sudo apt-get install bumblebee bumblebee-nvidia
```

After that reboot

You don't care about anything whatsoever. Just follow verbatim.

You cannot disable the Intel card because it must be there to display all of the graphics. You'd better do a google on 'optimus technology'.

If there still exist any problems, post your questions on [https://github.com/Bumblebee-Project/Bumblebee](https://github.com/Bumblebee-Project/Bumblebee)

After bumblebee is running fine, you can go here [https://github.com/peternguyen93/Bumblebee-Optimus](https://github.com/peternguyen93/Bumblebee-Optimus)

Download the frontend to optirun and run your applications with ease.

WARNING
Don't ever ever install nvidia drivers for YOUR OPTIMUS laptop by any means except bumblebee.

Cheers.

P.S
Nvidia version 302 is out. Wait a couple of days for it to hit the x-updates ppa repository and your machine must be running in no time.

---

### Post by typhoon_tip on 2012-06-17
> **tenmoi said:**
> I suggest that you do a clean install of kubuntu.

I totally agree with you, is better to start over. Backup whatever you have to backup and reinstall Kubuntu, and do not even attempt to install the driver with the .run file, just follow the procedure for Bumblebee (I am pretty sure his card is supported by the 295 driver already).

---

### Post by Stonecold1995 on 2012-06-17
Okay, so I did a fresh install and installed Bumblebee (and all the needed PPAs, etc).  But when I tried using it, I got this:
```
newinstall@kubuntu:~$ optirun glxgears
[ERROR]Cannot access secondary GPU - error: Could not load GPU driver

[ERROR]Aborting because fallback start is disabled.
```
That is similar to what I get on my normal install:
```
alex@kubuntu:~$ optirun glxgears
[ERROR]Cannot access secondary GPU - error: You need to change the ConnectedMonitor setting in /etc/bumblebee/xorg.conf.nvidia to 

[ERROR]Aborting because fallback start is disabled.
```
So the fresh install isn't running Bumblebee either.  Here's the series of commands I did after I first booted the fresh install:

```
sudo add-apt-repository ppa:bumblebee/stable
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install bumblebee bumblebee-nvidia
sudo apt-get install mesa-utils
sudo reboot
... after rebooting ...
optirun glxgears
```

---

### Post by Stonecold1995 on 2012-06-17
So it turns out there is a problem with some of the drivers for GPUs in the 6xx series.  I went to #bumblebee on FreeNode, and here is how the conversation went:

```
[11:43:17] <Stonecold> Can anyone here help me with running Bumblebee on my MainGear laptop?
[11:43:42] <amonakov> what problem do you have?
[11:44:14] <Stonecold> ERROR]Cannot access secondary GPU - error: You need to change the ConnectedMonitor setting in /etc/bumblebee/xorg.conf.nvidia to 
[11:44:23] <Stonecold> and then: [ERROR]Aborting because fallback start is disabled.
[11:46:02] <amonakov> what is the exact model of the nvidia card it has? or the laptop?
[11:46:13] <Stonecold> Nvidia GeForce GTX 675M
[11:46:22] <Stonecold> Laptop is MainGear ex-L 15 SuperStock
[11:47:30] <Stonecold> It uses Optimus, but currently the GPU won't work and all graphics is done by the i7.
[11:54:40] <amonakov> Stonecold: it seems that there's a problem with several new 6xx-series cards: the nvidia driver refuses to work claiming there are no connected monitors
[11:54:52] <Stonecold> Ok.
[11:54:58] <amonakov> (which can be true if in fact all monitors are routed via IGP)
[11:55:06] <Stonecold> So I'll have to wait for a the driver to be updated?
[11:55:36] <amonakov> I don't know. Perhaps. I intend to raise the issue together with one other issue on nvnews.net soon
[11:56:44] <Stonecold> Alright.  If all that's needed is an update, will I have to reconfigure or reinstall anything or will I simply one day do apt-get upgrade and Bumblebee will start working after that?
[11:58:46] <amonakov> if you installed bumblebee and drivers via apt-get, then it should be simple, if we'll be lucky and there will be an update to fix or workaround that
[11:59:09] <Stonecold> Okay thank you.
```
That's probably why I haven't found any solution yet.  I guess I'll just have to wait a bit for a fix to roll out.

---

