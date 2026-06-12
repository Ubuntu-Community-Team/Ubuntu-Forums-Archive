---
title: "[ Solution ]  8.10-9.04 Boot Failure Install&amp;LiveCD on Mobo's w/ Intel Onboard Vid"
date: 2009-09-02
forum: Installation &amp; Upgrades
---

### Post by fateinabox on 2009-09-02
I have seen alot of problems related to boot failures with a full installation and LiveCD for versions of ubuntu 8.10 and 9.04 related to motherboards with the Intel Onboard Video who use a PCI/AGP video card as well.

**MY SYSTEM**
[Compaq Presario SR1103WM Desktop]("http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c00191902") click link to view system specifications

Additionally i have added a Nvidia GeForce FX 5500 PCI Video Card
---------------------------------


**SYMPTOMS**
The symptoms of this problem occur at boot time when the system is probing the hardware on the system to load the proper modules into the system it will hang with a Kernel Panic and will require a hard reset of the system to recover from it. Also, the Caps Lock/Num Lock lights may blink on your keyboard as well. It did on mine anyway.

**SUSPECTED CAUSE**
I suspect, that the problem arises with the Intel onboard graphics adapter. What happens is the kernel is attempting to load both the intel onboard graphics adapter as well as the appropriate driver for the Nvidia or alternate video card causing a kernel panic..

**SOLUTION**
I fixed the problem by switching my bios to use the onboard(intel) video adapter. Upon reaching the boot loader for the LiveCD/Installer i added the option to the kernel to set **acpi=off** you can access this option by pressing **F6** and selecting it from the list.

With this change it allowed me to boot the LiveCD/Installer and do a full installation of the base system..

Once completed we need to make a few additional changes..

In my case i needed to install the nvidia-glx-173 proprietary drivers in order for my nvidia card to be fully utilized. For those of you who know how to do so..Great keep going. For those of you who don't it's a rather simple procedure. I will cover 3 ways to do this briefly one GUI and 2 text based methods.

**OPTION 1 > GUI**
This option allows you to use a graphical interface for newly recruited windows users who aren't use to the command line yet. To access this utility you simply need to goto **SYSTEM > ADMINISTRATION > HARDWARE DRIVERS** and it will display a dialog with suggested proprietary drivers for your hardware generally you'll go with the recommended option which in my case was the Nvidia Glx 173 drivers for my Nvidia GeForce FX 5500 video card.

[IMG]http://i28.tinypic.com/211pgye.png[/IMG]

**OPTION 2 > CLI**
This is for a few of the more seasoned users, eventually, if you haven't already. You will love to use apt IMHO it is the best package managing system out there. Assuming you are using an Nvidia gfx card i will continue on since the nvidia drivers are in the ubuntu repo's we won't cover adding additional repo's to the apt sources list.

To install the drivers via the CLI you need only issue the following commands..

*# sudo apt-get install nvidia-settings nvidia-glx-173*

simply replace the nvidia-glx-173 with the version of the nvidia drivers you need.

**Option 3 > CLI**
Option 3 covers using the envyng textual driver installation script.
to acquire the envyng installation script you need only retrieve if via apt like so

# sudo apt-get install envyng-core

additionally, if you want a GUI for envyng you can issue an additional apt command to retreive the envyng-qt package

# sudo apt-get install envyng-qt

but we'll just cover the textual installer

the envyng installer will only install Nvidia or ATI drivers.

to use the installer just simply do

# sudo envyng -t

once you've verified your credentials you will be greeted with a screen that looks similiar to this

[IMG]http://i25.tinypic.com/6dwkt3.png[/IMG]

simply follow the instructions on the screen it's a pretty easy installation procedure. it will automatically download and install the required drivers for your video card.

**FIXING MODPROBE**
In order to fix the problem with the kernel loading both the intel video drivers and the new video cards drivers we need to blacklist the intel_agp and the agpgart modules in modprobes blacklist.

In order to do this we need to modify the modprobe config file located at../etc/modprobe.d

open a shell and enter

# cd /etc/modprobe.d

here is where we'll find the config file we'll need to edit to blacklist those two modules intel_agp and agpgart

you'll need to edit blacklist.conf

# sudo nano blacklist.conf

at the bottom of the file add these 3 lines

#intel
blacklist agpgart
blacklist intel_agp

now modprobe will not load the modules for the intel onboard graphics card and the conflict and the kernel panic should be eliminated entirely

Additionally, i went a step further to ensure that the nvidia drivers were loaded at boot time and went ahead and added the word nvidia to the end of the /etc/modules file.

All that's left to do is to reboot your system enter the bios switch your primary graphics adapter to your other video card and boot into linux, everything should boot properly ^^ Enjoy.

[COLOR="Red"]**NOTE! THIS MIGHT NOT WORK FOR ALL CASES BUT WILL MOST LIKELY WORK FOR PEOPLE IN SIMILIAR SITUATIONS AS MYSELF**[/COLOR]

---

### Post by Jules Delespy on 2009-12-03
I know this is an aged post, but I found it as I went through much trouble installing on an affected machine, and it is likely others will find their way here in the future.
The issue is installation on machines where 1) graphics processing is integrated into the motherboard and 2) a graphics card has been added as an upgrade. The cards are often Nvidia, but not necessarily. Often, the integrated graphics cannot be fully disabled in BIOS, or things go wrong even when the integrated graphics are disabled in BIOS.
This configuration can lead to a variety of problems, with the most severe being kernel panic at boot time, which results in the inability to either try out the liveCD, or install Ubuntu at all.
Since issues related to the combination of integrated graphics+graphics card show up in many forum categories, I collected a list of references *where a solution was proposed*. The first of those references comes from Alberto Milone (tseliot in Ubuntu forums), the author of EnvyNG, among other qualifications. You will notice that his HowTo validates the solution you describe here, and it seems reasonable to think that it is the best current solution. 
The problem has existed in all versions of Ubuntu since at least version 6, and all the way to 27 November 2009 daily releases of 10.4. Strangely, it is possible that 8.04 was not affected. I have checked that the live CD of 8.04 indeed boots properly on affected machines, while none of the other versions do. As illustrated by the following links, other distros are affected as well. As a practical matter, this is very likely to stop many users from installing Linux on entry-level namebrand computers, which seems a shame.

here are the links:
[URL="http://www.albertomilone.com/nvidia_intel_integrated.txt"]
http://www.albertomilone.com/nvidia_intel_integrated.txt[/URL]
[http://ubuntuforums.org/showthread.php?t=1256691]("http://www.albertomilone.com/nvidia_intel_integrated.txt")
[http://ubuntuforums.org/showthread.php?t=1144043]("http://www.albertomilone.com/nvidia_intel_integrated.txt")
[http://ubuntuforums.org/showthread.php?t=675497]("http://www.albertomilone.com/nvidia_intel_integrated.txt")
[http://ubuntuforums.org/showthread.php?t=1308919]("http://www.albertomilone.com/nvidia_intel_integrated.txt")
[URL="http://www.albertomilone.com/nvidia_intel_integrated.txt"]https://bugs.launchpad.net/ubuntu/+source/linux/+bug/55104
http://www.bikechatforums.com/viewtopic.php?p=2356664
http://www.nvnews.net/vbulletin/showthread.php?t=128934
http://ubuntuforums.org/showthread.php?t=196693
http://ubuntuforums.org/showthread.php?t=635943
http://ubuntuforums.org/showthread.php?t=192677
http://ubuntuforums.org/showthread.php?t=496999
http://ubuntuforums.org/showthread.php?t=1328043
http://ubuntuforums.org/showthread.php?t=1078576
http://ubuntuforums.org/showthread.php?t=295133
http://javadocs.wordpress.com/2008/09/29/ubuntus-kernel-panic-freeze-with-an-asrock-motherboard-and-an-nvidia-gfx-card/
http://ubuntuforums.org/showthread.php?t=207303
http://en.opensuse.org/NVidia_Suspend_HOWTO
http://mepislovers.org/forums/showthread.php?t=6487
http://www.opensubscriber.com/message/slug@slug.org.au/6446049.html[/URL]

---

