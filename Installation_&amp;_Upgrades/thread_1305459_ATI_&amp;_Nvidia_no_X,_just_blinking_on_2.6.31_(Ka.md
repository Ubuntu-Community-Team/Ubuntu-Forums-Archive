---
title: "ATI &amp; Nvidia: no X, just blinking on 2.6.31 (Karmic 9.10)"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by Jekshadow on 2009-10-29
I recentally upgraded to 9.10, and on doing so, when I rebooted, it had me enter my encryption passphrase, it seemed to boot fine, until it got to where the login screen should be showing. It flickered a lot, and only showed the command line login screen. Whenever it was flickering it would not let me type. Could this be a problem with GDM trying to start but cant? When I rebooted to the 2.6.18 kernel, it worked perfectly.

---

### Post by joewski on 2009-10-29
> **Jekshadow said:**
> Could this be a problem with GDM trying to start but cant? When I rebooted to the 2.6.18 kernel, it worked perfectly.

No unlikely, when you upgraded to 2.6.31 it seems that everything wasn't set up correctly, probably due to something you have set up before..

I would recommend downloading a live ISO first and check out the system from a live disk. That way you can see how approximately a clean install would behave.

If all is well, you need to clean install whichever distro works for you. If 9.10 works then go with it otherwise stick with 9.04.

To reinstall make a backup of your /home directory to another machine. When you restore there will be a few files that will need there permissions correctly set, otherwise you will get errors.

---

### Post by Jekshadow on 2009-10-29
I think its just the upgrade. I remember I had trouble with a similar setup and upgrading 8.10 -> 9.04. I'll just copy my /home directory and reinstall.

---

### Post by markhadman on 2009-10-29
> **Jekshadow said:**
> I recentally upgraded to 9.10, and on doing so, when I rebooted, it had me enter my encryption passphrase, it seemed to boot fine, until it got to where the login screen should be showing. It flickered a lot, and only showed the command line login screen. Whenever it was flickering it would not let me type. Could this be a problem with GDM trying to start but cant? When I rebooted to the 2.6.18 kernel, it worked perfectly.

Ditto, you are not alone!

With kernel 2.6.31-14-generic, I got dropped to a flickering tty 1 login prompt. Ttys 1-6 (ctrl-alt-F1/F6) were all flickering, and the (otherwise blank) tty 7 seemed to intercept half of what I typed on the other ttys, making it damn near impossible to get my password right. It was however possible to login remotely through ssh and do 'sudo stop gdm', which ended the flickering. Rebooting into kernel 2.6.28-16-generic got me to a working gdm and beyond.


Possible hint:

Going back to the offending 2.6.31.-14-generic... I logged in again and did 'startx', which (amongst other errors, I think) gives ```
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting *** 
```

And come to think of it... I did see an error something like 'failed to build module NVIDIA...  aborting' during the upgrade.

Can you repeat this, anyone? And can anyone shed any light?


Athlon 2400+ / A7N8X-X / 1.25Gb ram / NVidia Gforce4 MX440

---

### Post by dspohn23 on 2009-10-30
I'm also seeing the same issue..... Dropping to a flickering shell.

---

### Post by y.t on 2009-10-30
Same here with a HP xw9400 with two Opteron 2389 and NVIDIA!

---

### Post by macogw on 2009-10-30
Can you folks file bugs using "ubuntu-bug xserver-xorg" ?

---

### Post by y.t on 2009-10-30
No, I'm not able to login because I loose the focus each time the screen is flackering - entering password is impossible

I also can't enter grub and choose another kernel. Very frustrating for the moment.

---

### Post by JBAlaska on 2009-10-30
Your Nvidia drivers have to be recompiled (installed) for the new kernel. Go to the Nvidia site, print the instructions (as you have to do this from a CLI), and follow the directions. you should be ok after the final restart of your X server.

---

### Post by fasmike on 2009-10-30
I just got the same thing.  I got a new laptop today and couldn't wait to put 9.10 on it.  I created a new run disk a couple hours ago to try it out and everything worked perfectly, so I went through with the clean install.

I get the same flickering:

[INDENT]Ubuntu 9.10 computername tty1[/INDENT] 
[INDENT]computername login:[/INDENT]

command line login prompt everyone else is describing.

It looks like a message of some kind pops up below the Ubuntu symbol in the center of the screen just before I see the flickering login prompt, but it's much to fast for me to read it.

---

### Post by y.t on 2009-10-30
It works now, I did the following steps:

[LIST]
[*] Boot from the install disk into recovery mode
[*] download from nvidia.com the NVIDIA-Linux-*.run for your hardware and copy it to your PC (I did it with a second PC and transfered via scp)
[*] run the NVIDIA-Linux-*.run
[*] Follow the instructions
[*] reboot
[/LIST]

---

### Post by DustofDust on 2009-10-30
nvidia is not the problem because i have an ati card.

i too can not login. num lock flickers too if i switch it on.

the 9.10 live cd works fine, im posting here with it.

i used the alternate install with no internet connection.

booting with 2.6.28 does not help!

i tried startx but got an error.

where are the logs which may help to help me?

---

### Post by graydo64 on 2009-10-30
I got the same updating from Jaunty. Used the alternate CD downloaded from a torrent. I wouldn't recommend doing that to anyone - the install wasn't complete - I had numerous errors during the upgrade, mostly relating to nvidia drivers and flashplugin-installer. Once completed I noticed I was only booting into the .28 kernel and the boot menu showed Ubuntu 9.04. Used update manager which found a further 200+ updates. Once updated I was still using the .28 kernel, grub still claimed I was on 9.04 and to make matters worse had no sound and wine wouldn't work (supposedly not installed).
 
My 'resolution' - edited /boot/grub/menu.lst, copied the sections for .28.15 generic and recovery and renamed the appropriate files to the .31.14 versions that I could see in /boot/grub/. Put the .31 sections second in the list and restarted, chosing the .31 kernel. At this point I got the tty flickers mentioned above and the boot sequence went no further. Restarted into the recovery option for .31. Chose the fix broken packages option - none needed to be fixed. Then chose to continue with the normal boot. At this point there was further mention of the nvidia drivers and a few seconds later boot continued successfully. Now running 9.10 with the .31 kernel.
 
That was how things were around 1am this morning (having started the upgrade at about 8pm). Oh and though you might think everything's now peachy I get a crash report every time I boot - [see this bug]("https://bugs.launchpad.net/ubuntu/+source/kerneloops/+bug/422536").
 
Wish I'd done a clean install.
 
Appreciate that as an existing and generally content Ubuntu user I'm not Joe Public but if I were I'd have dropped Ubuntu at about 9.30 last night and toddled off to find a copy of Windows 7.

---

### Post by Hillbill on 2009-10-30
I did a fresh install on my laptop, a Lenovo ThinkPad, and i have the same problem. Login is impossible due to the flickering.
My laptop has ATI graphics card, so it can't be the Nvidia issues causing this.

Anyone?

---

### Post by japetus on 2009-10-30
> **y.t said:**
> It works now, it did the following steps:

[LIST]
[*] Boot from the install disk into recovery mode
[*] download from nvidia.com the NVIDIA-Linux-*.run for your hardware and copy it to your PC (I did it with a second PC and transfered via scp)
[*] run the NVIDIA-Linux-*.run
[*] Follow the instructions
[*] reboot
[/LIST]

This method worked for me. Thanks.

---

### Post by DustofDust on 2009-10-30
ubuntu did not fix a critical show stopper bug!

> 
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux dust 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:24 UTC 2009 i686
Kernel command line: root=UUID=bdc35c88-41e7-40b7-8474-41fd4aa55a06 ro  single
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Oct 30 10:37:07 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0:1:0:0) 1002:475a:1002:0084 ATI Technologies Inc 3D Rage IIC AGP rev 122, Mem @ 0xde000000/16777216, 0xdfeff000/4096, I/O @ 0x0000c800/256, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched ati for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "ati"
(WW) Warning, couldn't open module ati
(II) UnloadModule: "ati"
(EE) Failed to load module "ati" (module does not exist, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

so what now?

---

### Post by FrankCy on 2009-10-30
Hello guys.

I'm facing various weird problems after upgrading from 9.04 to 9.10 (32bit), and the most important one is the one described in this thread.

My system does not boot with 2.6.31 Kernel, due to 2 of my hard drives not being "seeing" by the OS. Those 2 HDs are identical (80Gb SATA Hitachi, don't remember the model) and the one contains my Ubuntu installation.

I always got stuck in BusyBox right after Grub tried to find my boot HD unsuccessfully. "Gave up waiting for root device". Increasing the rootdelay time as it's usually suggested, didn't helped.

blkid -c /dev/null    was showing me all other HDs, but the 2 Hitachi ones. For those I was getting:  /dev/sdb: TYPE="isw_raud_member".
And no, I am not using any RAID configuration.

I tried switching SATA controllers between the Hitach HDs and my other working HDs, but the result was the same. HDs in question were still disappeared, but other HDs were fine.

Starting with 9.10 Live CD, although I could see those drives doing an fdisk -l, I couldn't mount them though. Trying to do so resulted into error msg: "mount: unknown filesystem typ "lsw_raid_member"

When I tried starting off a 9.04 LiveCD, there was no problem at all.

Eventually I booted my system using 2.6.28 Kernel. It booted "normally". Screen was scrambled at the beginning. In TTY1, 2 etc, screen was totally messed up too, but when switched back to TTY7 it was all ok. So I can partially use my PC for now.

I still have many other problems though (eg. no audio, no proper VGA card support, etc), but those are of lower priority at the moment, which might be solved after managing to use the latest Kernel...I hope.

I find my problem really weird, as if the specific hardware (HDs) are not supported by the latest Kernel (?). I don't see another logical explanation for this problem. Definitely it wasn't a controller's issue.

Hopefully a proper solution for this problem will come soon. Any suggestions will be highly appreciated.

Thanks.


Some additional hardware info:
 MoBo: Asus P5W Deluxe (intel 975x chipset)
 CPU: Intel Q8200
 VGA: ATI Radeon X1900 XT


***UPDATE: My problem was due to having 2 identical HDs no matter that they were on different SATA controllers! For some reason the new Kernel acts funny in such cases. After removing one of the 2 HDs (who needs Windows anyway :) ), my PC booted normally with the latest Kernel and Video & Audio worked flawlessly too! Little bug, huge frustration! I hope this will help others facing similar problems.

---

### Post by DustofDust on 2009-10-30
*bump*

[https://bugs.launchpad.net/ubuntu/+bug/464591](https://bugs.launchpad.net/ubuntu/+bug/464591)

i did a bugreport here!

---

### Post by fasmike on 2009-10-30
> **y.t said:**
> It works now, I did the following steps:

[LIST]
[*] Boot from the install disk into recovery mode
[*] download from nvidia.com the NVIDIA-Linux-*.run for your hardware and copy it to your PC (I did it with a second PC and transfered via scp)
[*] run the NVIDIA-Linux-*.run
[*] Follow the instructions
[*] reboot
[/LIST]

I was not on a network, so I had some trouble doing exactly what you said above, but your method did work, thanks!  This is what I did:

[LIST=1]
[*]Use a different computer to download the NVIDIA-Linux-*.run for my new laptop
[*]Copy that new driver to a USB drive
[*]Boot to recovery mode on the new laptop [(had to look this up)]("https://wiki.ubuntu.com/RecoveryMode"):
[INDENT]Hit ESC just after your Bios loads when (in theory) you see the "Grub loading blah blah"  (it was WAY too fast to see it on my machine)[/INDENT]
[INDENT]A menu will come up with boot options, select the one that ends in (recovery mode)[/INDENT]
[INDENT]You are dropped at the root@yournmachine:~# prompt[/INDENT]
[*]Plug my USB drive into the laptop (after a few seconds I saw some stuff scroll by the screen)
[*]Mount the USB drive [(had to look this one up):]("http://help.ubuntu.com/community/Mount/USB")
[INDENT]Find the drive with the command: sudo fdisk -l  (mine was /dev/sdb1)[/INDENT]
[INDENT]Create a directory to mount it as: sudo mkdir /media/external [/INDENT]
[INDENT]Mount the drive:  sudo mount -t vfat /dev/sdb1 /media/external -o uid=1000,gid=100,utf8,dmask-027/fmask=137[/INDENT]
[INDENT]NOTE: if your USB is not FAT## you need a different -t option[/INDENT]
[*]Copied the new driver to my home directory (may not have been necessary)
[*]execute the NVIDIA-Linux-*.run file
[INDENT]I had to change permissions on the file before I could run it: chmod 777 NVIDIA*[/INDENT]
[INDENT]Ran the file with: ./NVIDIA*.run[/INDENT]
[*]Follow the instructions
[*]Reboot
[/LIST]

This made the flickering login problem go away and allowed me to get in and start using Ubuntu on my new machine.

---

### Post by tidyfc on 2009-10-30
> **DustofDust said:**
> ubuntu did not fix a critical show stopper bug!



so what now?
I managed to get round this by removing fglrx and doing
sudo apt-get install xserver-xorg-video-ati
sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by airencracken on 2009-10-30
I'm having much the same problem, except older kernels aren't booting into a graphical environment either. I did the alternate-cd install via bittorrent and this is the second time I've had problems with it. That method needs a bit of work. Oh well, I'm not really complaining, this is one of the fun parts about using linux, I like fixing things.

However, I currently don't have a gui (posting this from elinks) and navigating nvidia's site in a text only browser is a major PITA. There were some broken packages after the update so I'm trying an "aptitude safe-upgrade" before I do anything else (which is going to take just as long as a normal upgrade would have, sigh...), but I'll report back here if the problem persists afterwards. Hopefully I won't have to do a clean install.

---

### Post by -=hazard=- on 2009-10-30
Same problem here with flickering shell with 2.6.31 kernel, the screen goes in panic... but it's ok with 2.6.28 kernel. Apart this I got problems with audio too. Example Alsa cant recognise the sound cart and if I go on configure it crash. [Here is the bug reported.]("https://bugs.launchpad.net/ubuntu/+source/gnome-alsamixer/+bug/465723") And pulseaudio device chooser doesn't even start. Apart all this, the start-up is more slower than 9.04 version.

---

### Post by DustofDust on 2009-10-30
> **tidyfc said:**
> I managed to get round this by removing fglrx and doing
sudo apt-get install xserver-xorg-video-ati
sudo dpkg-reconfigure -phigh xserver-xorg

i did not have fglrx installed.

i had to mount the alternate iso disc first, because he asked for disc in cdrom because of media change, it didnt just download the driver if there is no disc.

alt f2 for another bash, because it dont let you escape. 
sudo mount -o loop ~/path/ubuntu-9.10-alternate-i386.iso /mnt/cdrom

i did something like

sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon xorg-driver-fglrx
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
dpkg-reconfigure xserver-xorg
sudo apt-get install xserver-xorg-video-mach64

last line or radeon or fglrx depending which generation of card you have.

this time i did only some of the stuff above, i dont remember what i tried exactly but it works now.

i had such a problem some month ago when i played around with graphic card drivers, so i already knew the possible solution. i remebered this when someone in a mainstream newspaper forum postet that he had an x problem while he was upgrading to karmic.

when will this f u c k i n g problem be fixed? a lot of people have problems with this. it happens very often if someone was reading the forum.

[http://ubuntuforums.org/showthread.php?t=1305924](http://ubuntuforums.org/showthread.php?t=1305924)
more the 40% have problems they can not solve! also there some reported about this problem with x and the driver!

the more people subscribe at the launchpad bug i reported
[https://bugs.launchpad.net/ubuntu/+bug/464591](https://bugs.launchpad.net/ubuntu/+bug/464591)
the more the chance that it get fixed in way it does not happen again and people who dont have a glue what could be the reason and how to solve it, can get a running ubuntu.

but thanks for your try to help! ;)

---

### Post by Regele IONESCU on 2009-10-31
I made a fresh install too on an Acer Aspire 9423wsmi laptop, after I installed Windwos7. When I try to boot I get the same flickering black screen with tty1 and login lines. I hardly manage to type the username, but when it comes to password it types nothing.

---

### Post by DustofDust on 2009-10-31
> **Regele IONESCU said:**
> I made a fresh install too on an Acer Aspire 9423wsmi laptop, after I installed Windwos7. When I try to boot I get the same flickering black screen with tty1 and login lines. I hardly manage to type the username, but when it comes to password it types nothing.

just do similar what i posted above you.

---

### Post by Regele IONESCU on 2009-10-31
> **fasmike said:**
> I was not on a network, so I had some trouble doing exactly what you said above, but your method did work, thanks!  This is what I did:

[LIST=1]
[*]Use a different computer to download the NVIDIA-Linux-*.run for my new laptop
[*]Copy that new driver to a USB drive
[*]Boot to recovery mode on the new laptop [(had to look this up)]("https://wiki.ubuntu.com/RecoveryMode"):
[INDENT]Hit ESC just after your Bios loads when (in theory) you see the "Grub loading blah blah"  (it was WAY too fast to see it on my machine)[/INDENT]
[INDENT]A menu will come up with boot options, select the one that ends in (recovery mode)[/INDENT]
[INDENT]You are dropped at the root@yournmachine:~# prompt[/INDENT]
[*]Plug my USB drive into the laptop (after a few seconds I saw some stuff scroll by the screen)
[*]Mount the USB drive [(had to look this one up):]("http://help.ubuntu.com/community/Mount/USB")
[INDENT]Find the drive with the command: sudo fdisk -l  (mine was /dev/sdb1)[/INDENT]
[INDENT]Create a directory to mount it as: sudo mkdir /media/external [/INDENT]
[INDENT]Mount the drive:  sudo mount -t vfat /dev/sdb1 /media/external -o uid=1000,gid=100,utf8,dmask-027/fmask=137[/INDENT]
[INDENT]NOTE: if your USB is not FAT## you need a different -t option[/INDENT]
[*]Copied the new driver to my home directory (may not have been necessary)
[*]execute the NVIDIA-Linux-*.run file
[INDENT]I had to change permissions on the file before I could run it: chmod 777 NVIDIA*[/INDENT]
[INDENT]Ran the file with: ./NVIDIA*.run[/INDENT]
[*]Follow the instructions
[*]Reboot
[/LIST]

This made the flickering login problem go away and allowed me to get in and start using Ubuntu on my new machine.

Hi!
I managed to boot, to mount and to run nvidia*.run. But when it starts it says "Skipping the runlevel check (the utility runlevel failed to run)", then in the licence page both Accept and Do Not Accept buttons are red and I have no visible way to switch between them(Tab seems no working), and all ends saying "Unable to find the kernel source tree for currently running kernel. ... specify the kernel source path with the '--kernel-source-path' command line option.

---

### Post by Regele IONESCU on 2009-10-31
> **DustofDust said:**
> just do similar what i posted above you.

I have an Nvidia graphics board. I tried to replace ati with nvidia where it says apt-get install xserver but failed.

---

### Post by lapdog on 2009-10-31
Similar update experience:  got flashing text login screen on tty1 with normal bootup--no way to log in since most keystrokes did not register.  tty2 - 6 had the same flashing.  tty7 was blank.  With either "recovery mode" option, got to login but startx gave "screen not found" error, among others.

With the guidance of other posts here, I am now writing from a working 9.10 system.  Yeah!  Since my network connection was working and I apparently needed the latest nVidia driver, I did the following:

1.  Hit ESC after the BIOS loads (at the grub screen).

2.  Select the "recovery mode" with the later kernel:  2.6.31-14.  (The other choice I had was 2.6.28-16.)

3.  Login

4.  Pray that ftp will work and you can download from nVidia's site--necessary step!  don't skip!  :)

5.  ftp

[INDENT]6.  open download.nvidia.com

7.  for username, use:  guest

8.  for password, just press <Enter>

9.  cd XFree86
10. cd Linux-x86
11. cd 190.42

12. binary

13. get NVIDIA-Linux-x86-190.42-pkg1.run
    and wait for it to download; took about a minute for me

14. bye
[/INDENT]
15.  chmod 777 NVIDIA*

16.  sudo ./NVIDIA*.run

17.  Follow instructions in nVidia installation.  Remember to choose Yes when it asks if you want to replace current X config options.

18.  reboot

19.  Praise God with a prayer of thanksgiving when it works, and add a prayer of thanks for the Ubuntu community.


Boot up time for me is about the same, maybe a few seconds longer.  The new graphic defaults look cool and so far have been very fast and non-intrusive.

While I don't mind installing an extra file, getting a huge file onto a machine that doesn't boot correctly is a *major* source of stress.  Please, Ubuntu, put a message for nVidia users in big, bold type on your main 9.10 page saying the latest driver is needed.  Fetching this file beforehand would save a *lot* of trouble, as this thread shows.  This really is a serious issue that should not be present in a standard release.  (More than 40% with major problems?  Is that normal?)

Still don't have working sound or floppy, but nothing new there.  I saw a sound sticky...

On a positive note, thanks to the Ubuntu forum and community members for pointing me in the right direction!!!

---
mobo:  MSI K9N2GM-FIH (nVidia GeForce 8200); proc:  AMD Phenom X3 (AM2+) 8450; 4 Gig mem

---

### Post by DustofDust on 2009-10-31
> **Regele IONESCU said:**
> I have an Nvidia graphics board. I tried to replace ati with nvidia where it says apt-get install xserver but failed.

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
i think these are the nvidia names. dont know if they changed it...

---

### Post by budfrogs on 2009-10-31
> **fasmike said:**
> I was not on a network, so I had some trouble doing exactly what you said above, but your method did work, thanks!  This is what I did:

[LIST=1]
[*]Use a different computer to download the NVIDIA-Linux-*.run for my new laptop
[*]Copy that new driver to a USB drive
[*]Boot to recovery mode on the new laptop [(had to look this up)]("https://wiki.ubuntu.com/RecoveryMode"):[INDENT]Hit ESC just after your Bios loads when (in theory) you see the "Grub loading blah blah"  (it was WAY too fast to see it on my machine)[/INDENT][INDENT]A menu will come up with boot options, select the one that ends in (recovery mode)[/INDENT][INDENT]You are dropped at the root@yournmachine:~# prompt[/INDENT]
[*]Plug my USB drive into the laptop (after a few seconds I saw some stuff scroll by the screen)
[*]Mount the USB drive [(had to look this one up):]("http://help.ubuntu.com/community/Mount/USB")[INDENT]Find the drive with the command: sudo fdisk -l  (mine was /dev/sdb1)[/INDENT][INDENT]Create a directory to mount it as: sudo mkdir /media/external [/INDENT][INDENT]Mount the drive:  sudo mount -t vfat /dev/sdb1 /media/external -o uid=1000,gid=100,utf8,dmask-027/fmask=137[/INDENT][INDENT]NOTE: if your USB is not FAT## you need a different -t option[/INDENT]
[*]Copied the new driver to my home directory (may not have been necessary)
[*]execute the NVIDIA-Linux-*.run file[INDENT]I had to change permissions on the file before I could run it: chmod 777 NVIDIA*[/INDENT][INDENT]Ran the file with: ./NVIDIA*.run[/INDENT]
[*]Follow the instructions
[*]Reboot
[/LIST]

This made the flickering login problem go away and allowed me to get in and start using Ubuntu on my new machine.

I had the same problem.  I also had no sound after the upgrade with tty flashing on kernel 31 and not able to login.

I booted into recover mode for 31 kernel.
Once logged in I went to the director my NVIDIA driver was and tried to install it again.
No luck
Not ROOT
Logged in as Root
Tried again.  No Luck at Run level 1 Nvidia said to change to Run level 3.
Typed telinit 3  I think and it went to the next run level
Tried the NVIDIA install again and it started.  It did have an error but did some type of recovery and finished the install with no issue.

Rebooted the machine in to 31 kernel and it started up fine.  I even had sound back.  Bonus.  I am definitely a noob on Ubuntu and it seems to me the new kernel has issues with the video drivers and need them reinstalled on that kernel.  If that makes sense.
Good luck guys.  I think I will not upgrade for a while.  :D

---

### Post by dodgy69 on 2009-10-31
I'm a newbie to Linux, and I had a hard time following the above instructions. I had the same problem but couldn't follow a lot of the technical stuff. If you're like me and you need a more "Linux for dummies" approach, here's how I got it to work, newbie-friendly style:

HOW TO UPGRADE YOUR NVIDIA DRIVER - For Linux dummies like me

1. Go to the NVIDIA site and download [this driver]("http://www.nvidia.com/object/linux_display_ia32_190.42.html") to your 'HOME' directory.
2. Go to your HOME directory and RIGHT CLICK on the driver package ("NVIDIA-Linux-x86-190.42-pkg1.run")
3. Select PROPERTIES. Select PERMISSIONS tab. MaKe sure first dropdown menu says "Read and Write". Check box that says "Allow executing file as program"
4. Reboot your system. At the boot menu, select 2.6.31 kernel - safe mode.
5. You'll come to a menu. Select "Continue boot" (or something like that)
6. A command line will prompt you for your login name and password. Enter them.
7. You'll come to a terminal line. Enter this:   sudo ./NVIDIA*.run
8. The NVIDIA install manager should run and update your driver. 
9. Reboot your system. The new kernel should work.

---

### Post by junamuno on 2009-10-31
Have you found any solutions for ATI cards. I have an HP dv6 and I have the same flickering problem, but I have an ATI card. 

Please help...

---

### Post by macogw on 2009-10-31
> **DustofDust said:**
> ubuntu did not fix a critical show stopper bug!

Hard to fix before release a bug that wasn't filed until after release...

---

### Post by DustofDust on 2009-10-31
> **junamuno said:**
> Have you found any solutions for ATI cards. I have an HP dv6 and I have the same flickering problem, but I have an ATI card. 

Please help...

read my other posts

---

### Post by DustofDust on 2009-10-31
> **macogw said:**
> Hard to fix before release a bug that wasn't filed until after release...

this is not the first time people had such problems iirc...

anyway, i filled a bug report
[https://bugs.launchpad.net/ubuntu/+bug/464591](https://bugs.launchpad.net/ubuntu/+bug/464591)

and i see in the next year a lot of problems coming through a lot of changes are going on, new x, mesa, kms, dri2, driver and so on with all the kombinations. maybe a test cd with scripts for testing and upload the results to launchpad would be a help to solve issues in the future before such problems evolve in the distro.

---

### Post by macogw on 2009-10-31
> **DustofDust said:**
> this is not the first time people had such problems iirc...

anyway, i filled a bug report
[https://bugs.launchpad.net/ubuntu/+bug/464591](https://bugs.launchpad.net/ubuntu/+bug/464591)

and i see in the next year a lot of problems coming through a lot of changes are going on, new x, mesa, kms, dri2, driver and so on with all the kombinations. maybe a test cd with scripts for testing and upload the results to launchpad would be a help to solve issues in the future before such problems evolve in the distro.

Yes, but you filed it after release...would've been helpful to have a month ago.  Anyway, I set the importance to High, put it as affecting xorg (so the Xorg team will give it a look), and updated to include a mention that this is for Nvidia & ATI users.

---

### Post by CRIMPS on 2009-10-31
> **lapdog said:**
> Similar update experience:  got flashing text login screen on tty1 with normal bootup--no way to log in since most keystrokes did not register.  tty2 - 6 had the same flashing.  tty7 was blank.  With either "recovery mode" option, got to login but startx gave "screen not found" error, among others.

With the guidance of other posts here, I am now writing from a working 9.10 system.  Yeah!  Since my network connection was working and I apparently needed the latest nVidia driver, I did the following:

1.  Hit ESC after the BIOS loads (at the grub screen).

2.  Select the "recovery mode" with the later kernel:  2.6.31-14.  (The other choice I had was 2.6.28-16.)

3.  Login

4.  Pray that ftp will work and you can download from nVidia's site--necessary step!  don't skip!  :)

5.  ftp

[INDENT]6.  open download.nvidia.com

7.  for username, use:  guest

8.  for password, just press <Enter>

9.  cd XFree86
10. cd Linux-x86
11. cd 190.42

12. binary

13. get NVIDIA-Linux-x86-190.42-pkg1.run
    and wait for it to download; took about a minute for me

14. bye
[/INDENT]
15.  chmod 777 NVIDIA*

16.  sudo ./NVIDIA*.run

17.  Follow instructions in nVidia installation.  Remember to choose Yes when it asks if you want to replace current X config options.

18.  reboot

19.  Praise God with a prayer of thanksgiving when it works, and add a prayer of thanks for the Ubuntu community.


Boot up time for me is about the same, maybe a few seconds longer.  The new graphic defaults look cool and so far have been very fast and non-intrusive.

While I don't mind installing an extra file, getting a huge file onto a machine that doesn't boot correctly is a *major* source of stress.  Please, Ubuntu, put a message for nVidia users in big, bold type on your main 9.10 page saying the latest driver is needed.  Fetching this file beforehand would save a *lot* of trouble, as this thread shows.  This really is a serious issue that should not be present in a standard release.  (More than 40% with major problems?  Is that normal?)

Still don't have working sound or floppy, but nothing new there.  I saw a sound sticky...

On a positive note, thanks to the Ubuntu forum and community members for pointing me in the right direction!!!

---
mobo:  MSI K9N2GM-FIH (nVidia GeForce 8200); proc:  AMD Phenom X3 (AM2+) 8450; 4 Gig mem

The directions for downloading the proper NVidia driver for x64 architecture is slightly different.  Let me add to this starting with step 10:

Step 10.  cd Linux-x86[COLOR="Red"]_64[/COLOR]
Step 11.  cd 190.42
Step 12.  cd binary
Step 13.  get NVNIDIA-Linux-x86[COLOR="Red"]_64-190.42-pkg1.run[/COLOR]

In case you have already downloaded the x86 package, just change the next commands to:
15.  chmod 777 NVIDIA[COLOR="Red"]-Linux-x86_64[/COLOR]*

16.  sudo ./NVIDIA[COLOR="Red"]-Linux-x86_64[/COLOR]*.run

---

### Post by Regele IONESCU on 2009-10-31
I managed to get that NVIDIA*.run package on my computer,both via USB stick and ftp. None of them works. 

I typed the chmod comand. 

When I type sudo ./NVIDIA*.run I get "command not found". 


If I use sh instead of ./ the archive opens, it runs a bit then I get a message saying I am missing some kernel.



What should I do?????????????????????????????

New: I did a new ftp download. When doing ./Nvidia*.run  I got "Error opening terminal: bterm."

---

### Post by DustofDust on 2009-10-31
> **macogw said:**
> Yes, but you filed it after release...would've been helpful to have a month ago.  Anyway, I set the importance to High, put it as affecting xorg (so the Xorg team will give it a look), and updated to include a mention that this is for Nvidia & ATI users.

yes, because i need my working pc and can not risk to try an alpha. time for a test suite which does not destroy a working installation for people who need their pc.

strange that no one found the bug before...

---

### Post by Regele IONESCU on 2009-11-01
I did it!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!:D

Here is what I did:

**I simply removed 1Gb of 3Gb of RAM**. The installation, boot and start went all fine!!! No need to do anytrick with USB flash drive or ftp downloads. It simply works.

I have an Acer Aspire 9423wsmi.


After installing and successfully running Ubuntu 9.10 for a few times I reinserted the 1Gb RAM and still works fine!!!! So, it is a matter of OS install only.

---

### Post by efflandt on 2009-11-01
Regele IONESCU have you tried running memtest86+ on that RAM?  When I originally got RAM for my AMD64 it seemed to work in WinXP, but Linux had some issues with it and memtest86+ revealed was not quite compatible and had occasional errors.  But it was OCZ RAM I got on sale at Frys, and OCZ exchanged it for different model RAM that worked (for about 5 years now).

We also had Crucial RAM that would occasionally blue screen a PC at work (and memtest86+ errors).  But since that PC has been retired, that RAM has worked fine in another PC (no memtest86+ errors).

So apparently sometimes RAM is not quite compatible with other hardware.

But I am one who got supposedly critical (but non-fatal) errors in /var/crash from 9.10 64-bit kernel 2.6.31-14 due to a module assuming ECC should be enabled for RAM (when I have no such BIOS setting).  So I am using alternate kernel 2.6.28-16 until that is resolved.

---

### Post by EdGy28376 on 2009-11-01
Upgrade from 9.04 to 9.10 now I have no gui.
Issued the following command:
lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV530LE [Radeon X1600/X1650 PRO]

In /var/log/Xorg.0.log I have the following warnings and errors:
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.  
(II) Cannot locate a core pointer device
(II Cannot locate a core keyboard device
.
.
.
(II) LoadModule "ati"
(WW) Warning, couldn't open module ati
(II) UnloadModule: "ati"
(EE) Failed to load module "ati" (module does not exist,0)
(EE) No drivers availble.

Fatal server error:
no screen found


Everthing was working fine in 9.04.

---

### Post by EdGy28376 on 2009-11-01
Ran- fglrinfo
The program 'fglrinfo' is currently not installed. You can install it by typing: sudo apt-get install xorg-driver-fglrx

Continuing to research problem. Have came accross several posts concerning ATI drivers and 9.10.

---

### Post by andisl on 2009-11-01
I have the same problem with Acer Aspire 9420. I also upgraded system from 9.04. Historically I continue upgrades from times of Dapper. 
I tried instruction for dummies, but also got error message about missing path to kernel sources. The worst thing with old kernel is that there is no sound and mounting of devices is problematic - external drive doesn't mount at startup, but I have to unplug and then to plug in it again, when ubuntu is already loaded.
I'm ready to reinstall ubuntu, but I'm afraid, that I will lost also the only working kernel during reinstall.

---

### Post by Regele IONESCU on 2009-11-01
> **efflandt said:**
> Regele IONESCU have you tried running memtest86+ on that RAM?  When I originally got RAM for my AMD64 it seemed to work in WinXP, but Linux had some issues with it and memtest86+ revealed was not quite compatible and had occasional errors.  But it was OCZ RAM I got on sale at Frys, and OCZ exchanged it for different model RAM that worked (for about 5 years now).

We also had Crucial RAM that would occasionally blue screen a PC at work (and memtest86+ errors).  But since that PC has been retired, that RAM has worked fine in another PC (no memtest86+ errors).

So apparently sometimes RAM is not quite compatible with other hardware.

But I am one who got supposedly critical (but non-fatal) errors in /var/crash from 9.10 64-bit kernel 2.6.31-14 due to a module assuming ECC should be enabled for RAM (when I have no such BIOS setting).  So I am using alternate kernel 2.6.28-16 until that is resolved.

Unfortunately I have not at the time I had troubles. It looks it was an install time only problem. Is it possible to have a bad RAM that causes install to fail and to be ok once the system installed?

Now it works fine, very fine, perfect. I spent more then 72 hours, lots of coffee, very few food and almost no sleep, to sort it out and I am not willing at all to go over again.

---

### Post by Regele IONESCU on 2009-11-01
> **andisl said:**
> I have the same problem with Acer Aspire 9420. I also upgraded system from 9.04. Historically I continue upgrades from times of Dapper. 
I tried instruction for dummies, but also got error message about missing path to kernel sources. The worst thing with old kernel is that there is no sound and mounting of devices is problematic - external drive doesn't mount at startup, but I have to unplug and then to plug in it again, when ubuntu is already loaded.
I'm ready to reinstall ubuntu, but I'm afraid, that I will lost also the only working kernel during reinstall.

Try a fresh install, not an upgrade and physically limit your memory to up to 2Gb during install time.

God bless us all!

---

### Post by EdGy28376 on 2009-11-01
Ran sudo apt-get install xserver-xorg-video-radeon which tells me I have the latest drivers installed.

Ran sudo apt-get install xserver-xorg-video-ati whick intalled the driver.

Conducted a reboot. Boot came up to a XRDP login prompt. logged in and now I have what appears to be a normal looking desktop.

Need to investigate login screen.

---

### Post by andisl on 2009-11-01
I'm afraid that new kernel will not work, therefore I would like to have solution for upgrade. RAM is already 2 GB.

---

### Post by DustofDust on 2009-11-01
[http://ubuntuforums.org/showpost.php?p=8201026&postcount=23](http://ubuntuforums.org/showpost.php?p=8201026&postcount=23)

read my post if you have problems with upgrade...

---

### Post by Sunflower1970 on 2009-11-01
I thought I'd throw this up here, since I had the same problem. My solution's a bit different:

Using an nVidia 7600 GT card for graphics. What I had to do to get to the desktop is this:

In Grub, choose the safety mode to log in. When the menu comes up, choose 'normal boot' This will get to a prompt that won't be blinking.

1. log in at command prompt
2. edit the xorg.conf like so: 
```
sudo nano /etc/X11/xorg.conf
```
3. look for a section that will say something like this: 
```
Section "Device"
	Identifier	"Default Device"
	Driver	"the driver here"
	Option	"NoLogo"	"True"
EndSection
```
4. Change the Driver to vesa
5. To save in nano, Ctrl+X, then when prompted to Save, hit the 'Y', then hit enter.
6. Reboot

And it worked. I'm typing from my desktop using the restricted nvidia driver with no problem

(Now, to tackle the install on my laptop and see if I can get it to work too)

---

### Post by kiwibonga on 2009-11-01
I got this problem when I manually added an entry to /usr/share/jockey/modaliases/fglrx-modules.alias.override so that Restricted Drivers would recognize my now-obsolete Radeon 9600XT (RV350) as supported by fglrx... Figured I could maybe get partial support, but I guess that's not how it works :p

Anyway, if you don't want to go through the hassle of manually cleaning things up, there's always EnvyNG.

Start in Recovery Mode, drop to root shell (netroot if you need to download EnvyNG)...

(optional) apt-get install envyng
envyng -t

Select the driver to uninstall... And presto, it'll clean up everything beautifully on its own.

Make sure to delete or modify the /etc/X11/xorg.conf that EnvyNG creates, as it'll usually force X to use the vesa driver instead of the appropriate one.

---

### Post by bummpr on 2009-11-01
None of these instructions make any sense to me (I use wubi using an nVidia card)...I had 9.04 working just fine...I attempted 9.10 clean install (multiple times) with same results listed above by many people.

Utter FAIL!!!!  This is an incredible hurt to Ubuntu trying to lure us Windows fans over.

Hope you figure out how this happened.

---

### Post by rhgrice on 2009-11-01
> **DustofDust said:**
> 

sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon xorg-driver-fglrx
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
dpkg-reconfigure xserver-xorg
sudo apt-get install xserver-xorg-video-mach64



so this worked for me and I no longer have the blinking terminal login.  I now can get to a gui login.  After I login however, nothing else loads.  I get a white terminal window.  Is there a command I can use to get everything else to load?  Any other suggestions?

---

### Post by Brownedwg89 on 2009-11-01
I have the same problem. I found out that you can stop the "rave party" (as I like to call it) by holding ctrl-alt and rapidly pressing f1 until it settles down.

Well anyways, I have a Nvidia card. I've been trying to install the drivers. How would you install the Nvidia drivers? I looked at this: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) but it only provides the gui way of installing the drivers. How would I do it from the terminal? I've tried:
```
sudo apt-get install nvidia-glx-185
sudo nvidia-xconfig
```
but that's not fixing it.

I've also tried installing the drivers from Nvidia, but when I run the installer, it tells me:

"ERROR: Unable to find the kernel source tree for the currently running kernel. Please make sure you have installed the kernel source files for your kernel and that they are properly configured; on Red Hat Linux systems, for example, be sure you have the 'kernel-source' or 'kernel-devel' RPM installed. If you know the correct kernel source files are installed, you may specify the kernel source path with the '--kernel-source-path' command line option."

This is weird because I was getting this error when i was trying to install my drivers before I updated (and I did a clean install update), I even downloaded the linux-source from the repositories, extracted it and configured it, and the driver install still did not work, so I am lost, especially since I haven't seen an error like that for anyone else in this thread.

---

### Post by brolin_1911a1 on 2009-11-01
> **dspohn23 said:**
> I'm also seeing the same issue..... Dropping to a flickering shell.

I'm also getting the same problem with an Athlon64 3700+ CPU, NVidia 6600 video card, and ASUS A8V-E SE MB.

The LiveCD runs beautifully but does give me a driver message saying that NVidia drivers are proprietary and offering to activate the needed driver. However, such activation is meaningless since I have to reboot for it to work and that activation is lost if rebooting to the LiveCD and I can't boot to the hard drive.

I can boot into rescue mode o the hard drive but only into terminal mode and I get an error message saying that there are no drivers when I try to startx.

---

### Post by DustofDust on 2009-11-01
> **rhgrice said:**
> so this worked for me and I no longer have the blinking terminal login.  I now can get to a gui login.  After I login however, nothing else loads.  I get a white terminal window.  Is there a command I can use to get everything else to load?  Any other suggestions?

if you mean after login and finished start you don't get the look you had before or the livecd look, you only get a terminal window? than im sorry i don't know. if the right drivers and x are installed again than it should look normal after the boot process is finished.

---

### Post by Meroveus on 2009-11-01
> **brolin_1911a1 said:**
> I'm also getting the same problem with an Athlon64 3700+ CPU, NVidia 6600 video card, and ASUS A8V-E SE MB.

The LiveCD runs beautifully but does give me a driver message saying that NVidia drivers are proprietary and offering to activate the needed driver. However, such activation is meaningless since I have to reboot for it to work and that activation is lost if rebooting to the LiveCD and I can't boot to the hard drive.

I cannot tell you how to solve the problem definitively, however this may help.
I re-partitioned my dual XP/Edgy Eft dual-Opteron box and experienced the symptoms described, that is:
Live CD worked fine first time, and on install got the flashy thing happening.

Being a bit of a noob, I figured I had selected something wrong on the first install, so I re-installed, planning to use the same partitions.
Being a bit of a noob (see above), I screwed up yet again, and added a second instance of 9.10 to the same system -- however this one works!

I did have[ issues]("http://ubuntuforums.org/showthread.php?t=1308743") w/ the supplied nvidia drivers not allowing me to select my monitor's native resolution, but I have solved that, and I'm good to go. ([see this thread]("http://ubuntuforums.org/showthread.php?t=1308743"))

Now to get rid of the failed install and reclaim the space.

--Meroveus

---

### Post by DustofDust on 2009-11-01
> **brolin_1911a1 said:**
> I'm also getting the same problem with an Athlon64 3700+ CPU, NVidia 6600 video card, and ASUS A8V-E SE MB.

The LiveCD runs beautifully but does give me a driver message saying that NVidia drivers are proprietary and offering to activate the needed driver. However, such activation is meaningless since I have to reboot for it to work and that activation is lost if rebooting to the LiveCD and I can't boot to the hard drive.

I can boot into rescue mode o the hard drive but only into terminal mode and I get an error message saying that there are no drivers when I try to startx.

read my posts above to solve your problem und use the nvidia driver names instead of ati...

---

### Post by brolin_1911a1 on 2009-11-01
> **lapdog said:**
> Similar update experience:  got flashing text login screen on tty1 with normal bootup--no way to log in since most keystrokes did not register.  tty2 - 6 had the same flashing.  tty7 was blank.  With either "recovery mode" option, got to login but startx gave "screen not found" error, among others.

With the guidance of other posts here, I am now writing from a working 9.10 system.  Yeah!  Since my network connection was working and I apparently needed the latest nVidia driver, I did the following:

1.  Hit ESC after the BIOS loads (at the grub screen).

2.  Select the "recovery mode" with the later kernel:  2.6.31-14.  (The other choice I had was 2.6.28-16.)

3.  Login

4.  Pray that ftp will work and you can download from nVidia's site--necessary step!  don't skip!  :)

5.  ftp

[INDENT]6.  open download.nvidia.com

7.  for username, use:  guest

8.  for password, just press <Enter>

9.  cd XFree86
10. cd Linux-x86
11. cd 190.42

12. binary

13. get NVIDIA-Linux-x86-190.42-pkg1.run
    and wait for it to download; took about a minute for me

14. bye
[/INDENT]
15.  chmod 777 NVIDIA*

16.  sudo ./NVIDIA*.run

17.  Follow instructions in nVidia installation.  Remember to choose Yes when it asks if you want to replace current X config options.

18.  reboot

19.  Praise God with a prayer of thanksgiving when it works, and add a prayer of thanks for the Ubuntu community.


Boot up time for me is about the same, maybe a few seconds longer.  The new graphic defaults look cool and so far have been very fast and non-intrusive.

While I don't mind installing an extra file, getting a huge file onto a machine that doesn't boot correctly is a *major* source of stress.  Please, Ubuntu, put a message for nVidia users in big, bold type on your main 9.10 page saying the latest driver is needed.  Fetching this file beforehand would save a *lot* of trouble, as this thread shows.  This really is a serious issue that should not be present in a standard release.  (More than 40% with major problems?  Is that normal?)

Still don't have working sound or floppy, but nothing new there.  I saw a sound sticky...

On a positive note, thanks to the Ubuntu forum and community members for pointing me in the right direction!!!

---
mobo:  MSI K9N2GM-FIH (nVidia GeForce 8200); proc:  AMD Phenom X3 (AM2+) 8450; 4 Gig mem

Thank you, thank you, thank you!  That fixed it for me, also.  However, since I'm running the amd64 version, two changes to the above procedure needed to be made.

Instead of cd XFree-x86, I had to 
cd XFree-X86_64 
cd 190.42 
get NVIDIA-Linux-x86_64-190.42-pkg.run 
as the one you cited won't run on a 64-bit installation.

But, thanks to you I'm typing this on my properly booted Karmic Koala installation. Thank you, again, for pointing me to the proper solution.

---

### Post by UltraZone on 2009-11-01
The problem with proprietary Nvidia drivers seems to crop up with every new distribution.  This will be the third time I have to manually fix this.  Honestly I kind of like it... :-k however, it seems that the problem here might be political, as in Canonical not wanting to ruffle the FSF's feathers too much.  Frankly, the FSF won't "certify" Ubuntu as truly open source anyway, so why not make it easier for us to manage Nvidia drivers from Synaptic?  SuSE users get a repository from Nvidia (read Nvidia's own Suse Linux User's How To, and they list the repository addresses) why can't Ubuntu get a repository from Nvidia and let Synaptic work the magic behind the scenes?  It seems to me that this should theoretically eliminate this problem from the root... [-o<

---

### Post by andisl on 2009-11-02
*When I tried solution with terminal installation of NVIDIA drivers, I also got this message [FONT="Courier New"][SIZE="1"]"ERROR: Unable to find the kernel source tree for the currently running kernel. Please make sure you have installed the kernel source files for your kernel and that they are properly configured; on Red Hat Linux systems, for example, be sure you have the 'kernel-source' or 'kernel-devel' RPM installed. If you know the correct kernel source files are installed, you may specify the kernel source path with the '--kernel-source-path' command line option."[/SIZE][/FONT] If there are any simple solution for dummies to get further with installation?*

I found solution for the problem with missing kernel sources in another forum:
[FONT="Courier New"]
$ sudo apt-get install linux-headers-rt
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
linux-headers-2.6.31-9-rt linux-rt-headers-2.6.31-9
The following NEW packages will be installed:
linux-headers-2.6.31-9-rt linux-headers-rt linux-rt-headers-2.6.31-9
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.2MB of archives.
After this operation, 82.8MB of additional disk space will be used.
Do you want to continue [Y/n]? n

Of course not:
$ uname -r
2.6.31-14-generic

So you need to cheat:
$ sudo apt-get install linux-headers-2.6.31-14-generic
This will do:
The following extra packages will be installed:
linux-headers-2.6.31-14
The following NEW packages will be installed:
linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic[/FONT]

After that I was able to install NVIDIA according to upgrade manual "for dummies" from this thread. No flickering anymore :p

---

### Post by ACanuck on 2009-11-02
I don't need help, but figured I would mention this anyway.

Don't know about the flickering mentioned, but I installed Ubuntu 9.10 64bit today(via livecd, not alternate) and on booting up the first time I was met with a commandline login. IIRC the only error was the "no screens" thing. I stuck the livecd back in, edited my xorg file removing the fglrx line, booted the new install again and it went fine, then just downloaded the drivers from ATI's website and installed them and everything runs perfect now. Compiz, dual monitors, everything running as good as I could hope for!

Oddly on installing the 32bit version it worked fine from the start, only problem with that was for some reason it didn't add the other operating systems to the grub.cfg file like the 64bit install did(I installed both, first 64, then 32), but that is unrelated to this topic, and easy enough to fix anyway.


System info:
C2D E8500
Asus P5B Deluxe
4GB ram
ATI HD3870
Booting Ubuntu32, Ubuntu64, WinXP, & Win7

---

### Post by brolin_1911a1 on 2009-11-02
> **ACanuck said:**
>  ... Oddly on installing the 32bit version it worked fine from the start, only problem with that was for some reason it didn't add the other operating systems to the grub.cfg file like the 64bit install did(I installed both, first 64, then 32), but that is unrelated to this topic, and easy enough to fix anyway. 

ACanuck, you have, I think, explained something I wondered about. I've been using Ubuntu since 5.04 and I'd never encountered the driver problem with previous versions. However, I'd always installed the 32-bit versions. Karmic Koala is the first time I've ever had this NVIDIA problem but it's also the first time I've tried a 64-bit version.

Now I just need to figure out how to restore my OS choice order in GRUB to put WinXP as the default again.  /etc/grub/menu.lst does not exist so the boot OS order list must be somewhere else now.

---

### Post by mattgreen on 2009-11-02
I'm seeing the same problem but I have Intel graphics hardware:-

> $ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)I'll report back if I get it fixed....

---

### Post by cosmic_kid on 2009-11-02
I had the same problem on 'upgrade' where the system would start to a flashing prompt.  I don't have ATI or Nvidia, so it's not tied to those drivers.  In fact, I'm using VirtualBox, which you'd think would be pretty easy to test on.

Second, you can't submit a bug report a month ago when the option to upgrade just became available the other day.

Anyway, this worked for me:

> **Sunflower1970 said:**
> I thought I'd throw this up here, since I had the same problem. My solution's a bit different:

In Grub, choose the safety mode to log in. When the menu comes up, choose 'normal boot' This will get to a prompt that won't be blinking.

1. log in at command prompt
2. edit the xorg.conf like so: 
```
sudo nano /etc/X11/xorg.conf
```3. look for a section that will say something like this: 
```
Section "Device"
    Identifier    "Default Device"
    Driver    "the driver here"
    Option    "NoLogo"    "True"
EndSection
```4. Change the Driver to vesa
5. To save in nano, Ctrl+X, then when prompted to Save, hit the 'Y', then hit enter.
6. Reboot

And it worked. I'm typing from my desktop using the restricted nvidia driver with no problem
I commented out the existing Device section and added Sunflower's, then restarted x and I'm back up and running.  Thank you!

---

### Post by jessiebrownjr on 2009-11-02
I just want to point out that using the bitorrent download has nothing to do with anything if you verify your downloads. Please stop blaming that method and do soem research.

---

### Post by Brownedwg89 on 2009-11-02
> **andisl said:**
> *When I tried solution with terminal installation of NVIDIA drivers, I also got this message [FONT="Courier New"][SIZE="1"]"ERROR: Unable to find the kernel source tree for the currently running kernel. Please make sure you have installed the kernel source files for your kernel and that they are properly configured; on Red Hat Linux systems, for example, be sure you have the 'kernel-source' or 'kernel-devel' RPM installed. If you know the correct kernel source files are installed, you may specify the kernel source path with the '--kernel-source-path' command line option."[/SIZE][/FONT] If there are any simple solution for dummies to get further with installation?*

I found solution for the problem with missing kernel sources in another forum:
[FONT="Courier New"]
$ sudo apt-get install linux-headers-rt
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
linux-headers-2.6.31-9-rt linux-rt-headers-2.6.31-9
The following NEW packages will be installed:
linux-headers-2.6.31-9-rt linux-headers-rt linux-rt-headers-2.6.31-9
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.2MB of archives.
After this operation, 82.8MB of additional disk space will be used.
Do you want to continue [Y/n]? n

Of course not:
$ uname -r
2.6.31-14-generic

So you need to cheat:
$ sudo apt-get install linux-headers-2.6.31-14-generic
This will do:
The following extra packages will be installed:
linux-headers-2.6.31-14
The following NEW packages will be installed:
linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic[/FONT]

After that I was able to install NVIDIA according to upgrade manual "for dummies" from this thread. No flickering anymore :p

Thank you for that. In Jaunty I was getting the same problem and thought I had the headers installed, but I guess not. And it completely slipped my mind this time.

So now I've got no flickering and I can get to the login screen! yay!

However, now when I try to login, it goes black, flickers for a second and then returns to the login screen... Any ideas about that?

---

### Post by rgeddes on 2009-11-02
I have an NVidia video card and am experiencing the same issues on upgrade... here's my problem:

- I have a password for root (makes sense for security)
- when I try to get into safe mode, the I/O is flaky and every time I type a password character, it seems to include an lf (line feed) character so I can't log in with safe mode.
- I tried to reset the root password to "nothing", but the system won't let me do that as well.

Is there a way to include the selections (the safe mode options and account password) in the grub menu.lst file?

Thanx

---

### Post by Brownedwg89 on 2009-11-02
> **rgeddes said:**
> I have an NVidia video card and am experiencing the same issues on upgrade... here's my problem:

- I have a password for root (makes sense for security)
- when I try to get into safe mode, the I/O is flaky and every time I type a password character, it seems to include an lf (line feed) character so I can't log in with safe mode.
- I tried to reset the root password to "nothing", but the system won't let me do that as well.

Is there a way to include the selections (the safe mode options and account password) in the grub menu.lst file?

Thanx

maybe this will help?
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by rgeddes on 2009-11-02
Nice resource... bookmarked it.
My problem is that the **root** account on my machine has a password... so when I try to 'drop into the root account' from the safe mode, it asks me for the password, and since my I/O is flaky, I'm assuming due to the video driver issue, I can't get the root password into the system.

---

### Post by sloggerkhan on 2009-11-02
> **y.t said:**
> No, I'm not able to login because I loose the focus each time the screen is flackering - entering password is impossible

I also can't enter grub and choose another kernel. Very frustrating for the moment.

I encountered this installing custom nvidia driver.
Basically, gdm is not controlled through a services dialog, and otherwis continually tries to restart itself causing screen flicker and making it impossible to use.

Solution is to reboot and use root/recovery mode. 

Your upgrade issue is because your system is set up to use nvidia driver, but you now lack custom kernel module and nvidia is not tied into dkms system normally.

---

### Post by sloggerkhan on 2009-11-02
> **Brownedwg89 said:**
> Thank you for that. In Jaunty I was getting the same problem and thought I had the headers installed, but I guess not. And it completely slipped my mind this time.

So now I've got no flickering and I can get to the login screen! yay!

However, now when I try to login, it goes black, flickers for a second and then returns to the login screen... Any ideas about that?

Improper permissions on home folder maybe? Or maybe you need to reinitialize your nvidia xorg.conf file?

Check system logs in /var/log to see if any weird message show up.
Useful way to do so is tail command, though you could also just do less and hit the end key.

---

### Post by DustofDust on 2009-11-02
> **rgeddes said:**
> Nice resource... bookmarked it.
My problem is that the **root** account on my machine has a password... so when I try to 'drop into the root account' from the safe mode, it asks me for the password, and since my I/O is flaky, I'm assuming due to the video driver issue, I can't get the root password into the system.

that is the reason you need to boot in recovery mode. to get there press esc at the boot.

---

### Post by jdeca57 on 2009-11-02
Well, this is really a showstopper. You really can't solve it unless you boot from a CD. Of course, if you don't install proprietary drivers, everything works...

---

### Post by DustofDust on 2009-11-02
> **jdeca57 said:**
> Well, this is really a showstopper. You really can't solve it unless you boot from a CD. Of course, if you don't install proprietary drivers, everything works...

you dont need to boot from cd. didnt you read the other posts?

---

### Post by rgeddes on 2009-11-02
> **DustofDust said:**
> that is the reason you need to boot in recovery mode. to get there press esc at the boot.

Yes... I did go down that tunnel... no cheese, though.

When I Esc and select the Recovery mode, there is an ncurses type selector window... I select "root  ..." and ***now*** since my system has a root password, it asks for the root password.... when I try to input the password for root, the keyboard input is messed up so I can't get it to accept the root password... If root did not have a password assigned, I would just hit the Enter key and I would be in as root.

I assume that the root account on your system does not have a password set, leaving it vulnerable to people who have physical access to your machine

---

### Post by DustofDust on 2009-11-02
> **rgeddes said:**
> Yes... I did go down that tunnel... no cheese, though.

When I Esc and select the Recovery mode, there is an ncurses type selector window... I select "root  ..." and ***now*** since my system has a root password, it asks for the root password.... when I try to input the password for root, the keyboard input is messed up so I can't get it to accept the root password... If root did not have a password assigned, I would just hit the Enter key and I would be in as root.

I assume that the root account on your system does not have a password set, leaving it vulnerable to people who have physical access to your machine

there is no root to select... you select a kernel, there are no alternatives. ah, memtest iirc...

just let the recovery version boot without root if you did not change something in the bios or mbr. if you have an usb keyboard you could be in troubles if the mainboard does not support this with bios in the options. but than you would not be able to use the bios...

if you have have a ps/2 keyboard you can not have these problems at pre boot time, because this runs on the deepest hardware level! this combined with a 3,5" floppy brings EVERY system up!

---

### Post by rgeddes on 2009-11-02
> **DustofDust said:**
> there is no root to select... you select a kernel, there are no alternatives. ah, memtest iirc...

just let the recovery version boot without root if you did not change something in the bios or mbr. if you have an usb keyboard you could be in troubles if the mainboard does not support this with bios in the options. but than you would not be able to use the bios...

if you have have a ps/2 keyboard you can not have these problems at pre boot time, because this runs on the deepest hardware level! this combined with a 3,5" floppy brings EVERY system up!

After I select the (Recovery Mode)from the grub menu, a Recovery Menu pops up... this is the ncurses thing I was refering to... you can also see it on the url you referenced:

[http://www.psychocats.net/ubuntu/resetpassword]("http://www.psychocats.net/ubuntu/resetpassword")

it would be the second image in the paragraph with the heading:

Note for Ubuntu 9.10 (Karmic)

if you click on the image you'll see that the selection to make is "root    Drop to root shell prompt" 

if you don't have the root account protected with a password, I imagine you won't be asked for a password... 

I do protect the root account with a password... and I know the password... but since the video driver is messed up, I can't get the password to be accepted...  for each character I input, a line feed character (the Enter key)seems to be appended to it.

This makes sense since the only other user that can change passwords, other than the owner of the account, is root...

BTW, I'm using a ps2 keyboard.

---

### Post by DustofDust on 2009-11-02
i too needed to login, i also needed to type the commands, i didnt see a xfix in ncurses and i also had some graphics failures there.

livecd and to use chroot and chown to uninstall the drivers or to change the stuff with the password.

if you find out how it works, please let me know. i was in the need in the past but did find another solution, maybe i need such in the future...

or you make a complete backup with the live cd and do a fresh install.

---

### Post by Brownedwg89 on 2009-11-02
> **rgeddes said:**
> Nice resource... bookmarked it.
My problem is that the **root** account on my machine has a password... so when I try to 'drop into the root account' from the safe mode, it asks me for the password, and since my I/O is flaky, I'm assuming due to the video driver issue, I can't get the root password into the system.

Did you try the method shown in the video? It shows how to change the password from a LiveCD, maybe you could take care of your problem using similar steps.

Or maybe you could mount your drive and chroot in it. From there ,it would be as if you had root access to your filesystem.

Also, I don't know if this would work for you, but when it dropped me to the flickering tty1, I could make it stop flickering by holding ctrl-alt and tapping f1 repeatedly (it sometimes took a while).

---

### Post by chessmani on 2009-11-02
Hi. I use Kubuntu and had the same issue with my Nvidia NVS 140M which I solved by upgrading the driver to 190.42

This link made my day: [http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html](http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html)

The steps I followed were:

1. Add PPA

```
sudo add-apt-repository ppa:nvidia-vdpau/ppa
```

2. Update sources

```
sudo apt-get update
```

3. Install envyng-core. This command-line program is very handy since you can uninstall the driver afterwards from the console in case you can't login.

```
sudo apt-get install envyng-core
```

4. Install nvidia-190-modaliases so that envyng-core will detect the driver.

```
sudo apt-get install nvidia-190-modaliases
```

5. Run envyng and Install the driver. Please remove the older driver if it was installed.

```
sudo envyng -t
```

And if you're lucky everything should be back to normal :)

If not, use envyng -t to remove the driver and revert to the old state, if it was better of course... In my case the nv driver gave me a working system before I installed this.

---

### Post by Brownedwg89 on 2009-11-02
> **sloggerkhan said:**
> Improper permissions on home folder maybe? Or maybe you need to reinitialize your nvidia xorg.conf file?

Check system logs in /var/log to see if any weird message show up.
Useful way to do so is tail command, though you could also just do less and hit the end key.

all the permissions in my home folder seem to be fine. The X server is working for me, since I am getting to the login screen, but I keep getting kicked out right after logging in.

The logs seem fine, I guess... Is there any specific one I should be looking at? 

Thanks

---

### Post by sloggerkhan on 2009-11-02
> **Brownedwg89 said:**
> all the permissions in my home folder seem to be fine. The X server is working for me, since I am getting to the login screen, but I keep getting kicked out right after logging in.

The logs seem fine, I guess... Is there any specific one I should be looking at? 

Thanks

You kinda have to just look through them.
I'd give auth.log, dmesg, messages, syslog, Xorg logs, and user.log a shot. Some of them might share messages, not 100% sure.

---

### Post by hazy on 2009-11-03
> **chessmani said:**
> Hi. I use Kubuntu and had the same issue with my Nvidia NVS 140M which I solved by upgrading the driver to 190.42

This link made my day: [http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html](http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html)

The steps I followed were:

1. Add PPA

```
sudo add-apt-repository ppa:nvidia-vdpau/ppa
```2. Update sources

```
sudo apt-get update
```3. Install envyng-core. This command-line program is very handy since you can uninstall the driver afterwards from the console in case you can't login.

```
sudo apt-get install envyng-core
```4. Install nvidia-190-modaliases so that envyng-core will detect the driver.

```
sudo apt-get install nvidia-190-modaliases
```5. Run envyng and Install the driver. Please remove the older driver if it was installed.

```
sudo envyng -t
```And if you're lucky everything should be back to normal :)

If not, use envyng -t to remove the driver and revert to the old state, if it was better of course... In my case the nv driver gave me a working system before I installed this.
tnx a lot this solved my problem :D

---

### Post by mattgreen on 2009-11-03
> **mattgreen said:**
> I'm seeing the same problem but I have Intel graphics hardware:-

 Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)                      

I'll report back if I get it fixed....


I fixed this by deleting /etc/X11/xorg.conf

System booted ok with the 2.6.31 Kernel and I have control of my desktop resolution no problem.

Oh, I also removed the compizconfig-settings-manager package but I don't think that affected it.

---

### Post by DustofDust on 2009-11-03
i posted a bug report
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/464591](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/464591)

now i got some answers:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/464591/comments/10](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/464591/comments/10)
> Regarding the flickering on boot, that is a known issue between gdm and upstart, bug #441638.

"so can i spread out your word that graphics problems are not going to be fixed?"

If you wish to make yourself look foolish, that is your own business.

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/441638](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/441638)
Bug #441638 reported by hatchetman82  on 2009-10-03

> 
upstart job keeps restarting a dying gdm
CancelOk

   1. Ubuntu
   2. “gdm” package
   3. Bugs
   4. Bug #441638

Affects 	Status 	Importance 	Assigned to 	Milestone
  	gdm (Ubuntu) Edit
	
In Progress
	
High
	
Martin Pitt Edit
	
Target to milestone Ubuntu karmic-updates
Affecting: 	gdm (Ubuntu)
Filed here by: 	hatchetman82
When: 	2009-10-03
Confirmed: 	2009-10-24
Assigned: 	2009-10-27
Started work: 	2009-10-28
Package
(Choose…)
Status 	Importance 	Milestone
	High 	Ubuntu karmic-updates
Assigned to
	Nobody
	Me
	Martin Pitt (pitti)
	
(Choose…)
Comment on this change (optional)
E-mail me about changes to this bug report
  	Karmic 	
In Progress
	
High
	
Martin Pitt Edit
	
Target to milestone Ubuntu karmic-updates
Affecting: 	gdm (Ubuntu Karmic)
Filed here by: 	Martin Pitt
When: 	2009-10-27
Confirmed: 	2009-10-24
Assigned: 	2009-10-27
Started work: 	2009-10-28
Package
(Choose…)
Status 	Importance 	Milestone
	High 	Ubuntu karmic-updates
Assigned to
	Nobody
	Me
	Martin Pitt (pitti)
	
(Choose…)
Comment on this change (optional)
E-mail me about changes to this bug report
Also affects project Also affects distribution Nominate for release
This bug doesn't affect me Edit Does this bug affect you? Edit
 
Bug Description

after completing the karmic beta install wizard, there appears a dialog box instructing the user to reboot to boot into the new installation.
after confirming a reboot, gdm started dying and respawning in an endless loop (or at least for a few minutes before i shut down the machine).
this does not happen when booting into the installed OS and shutting it down/rebooting, only when rebooting after installing from the CD..

this causes the screen to flicker horribly, and the machine is just stuck like that until shut down.

this is how it looks like :
[http://www.youtube.com/watch?v=VpWpY-0A8Jo](http://www.youtube.com/watch?v=VpWpY-0A8Jo)

the text flashing on the screen is an endless loop of:

init: gdm main procedd ([pid]) terminated with status 1
init: gdm main process ended, respawning
init: ubiquity main process ([pid]) terminated with status 1


so the report of the bug is 1 month old and was not fixed for karmic release. they let us run into the open knife. that is a disastrous behavior in my eyes!

the second part of the problem is, why gdm dies.

---

### Post by Arsemyth on 2009-11-03
Hi Lapdog, I had similar problems to those listed above.  I was beginning to panic before I saw your detailed solution.  I printed out a copy, went through it carefully word for word, and yes, now I have a fully working Ubuntu system.  I'm sure it was the prayers that did the trick!

many thanks

---

### Post by frodon on 2009-11-03
> **DustofDust said:**
> so the report of the bug is 1 month old and was not fixed for karmic release. they let us run into the open knife. that is a disastrous behavior in my eyes!Stick with LTS releases, such thing can happen on any non-LTS release.

Don't use anything else than LTS release if what you want is a painless experience or at least if you don't want to stick with LTS releases wait a month after the release before upgrading thus no server overload and major bugs already fixed.

---

### Post by bjcubsfan on 2009-11-03
> **Sunflower1970 said:**
> I thought I'd throw this up here, since I had the same problem. My solution's a bit different:

Using an nVidia 7600 GT card for graphics. What I had to do to get to the desktop is this:

In Grub, choose the safety mode to log in. When the menu comes up, choose 'normal boot' This will get to a prompt that won't be blinking.

1. log in at command prompt
2. edit the xorg.conf like so: 
```
sudo nano /etc/X11/xorg.conf
```
3. look for a section that will say something like this: 
```
Section "Device"
	Identifier	"Default Device"
	Driver	"the driver here"
	Option	"NoLogo"	"True"
EndSection
```
4. Change the Driver to vesa
5. To save in nano, Ctrl+X, then when prompted to Save, hit the 'Y', then hit enter.
6. Reboot

And it worked. I'm typing from my desktop using the restricted nvidia driver with no problem

(Now, to tackle the install on my laptop and see if I can get it to work too)

I had this problem when booting immediately after install (did not install the proprietary drivers yet).  I booted into rescue mode off of the install CD and performed the fix suggested by Sunflower above.  Making this change allowed the system to boot normally, from which point I assume I will be able to install normal video drivers.   Thanks for the instructions.

BJ

---

### Post by DustofDust on 2009-11-03
> **frodon said:**
> Stick with LTS releases, such thing can happen on any non-LTS release.

Don't use anything else than LTS release if what you want is a painless experience or at least if you don't want to stick with LTS releases wait a month after the release before upgrading thus no server overload and major bugs already fixed.

on one side, with the lts release you are absolute right.

on the other side, the release with showstopper bugs is unacceptable.

if the targeted audience is the desktop user, beginners and switchers from other os, than not being able to boot to the desktop, loosing data, not being able to go into the internet is a showstopper. these are basic und fundamental functions of a desktop os. the release date has to be postponed until such mayor problems are solved.

the bug with gdm, x and driver was known in launchpad, [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/441638](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/441638) there was never any hint in the release notes, which i read before the upgrade. to ignore problems and play them down does not work, you need to solve the cause as it comes bigger back.

and now it is even bigger an issue
[http://www.theregister.co.uk/2009/11/03/karmic_koala_frustration/](http://www.theregister.co.uk/2009/11/03/karmic_koala_frustration/)
Early adopters bloodied by Ubuntu's Karmic Koala

---

### Post by frodon on 2009-11-03
> **DustofDust said:**
> if the targeted audience is the desktop user, beginners and switchers from other osIt isn't.

What you are talking about is the LTS release audience.

---

### Post by DustofDust on 2009-11-03
> **frodon said:**
> It isn't.

What you are talking about is the LTS release audience.

[http://www.ubuntu.com/](http://www.ubuntu.com/)
> 
    <h1>Ubuntu 9.10 is here</h1>
    <h2>Free operating system for your desktop or laptop</h2>


> <dt>Faster, smoother, more beautiful...</dt>
        <dd>New features, fixes and applications designed around you</dd>
        <dt>Developing at speed...</dt>

        <dd>Fun tools make it write and deploy apps to Ubuntu</dd>
        <dt>...and introducing your personal cloud</dt>
        <dd>Store and share files and contacts in a couple clicks with Ubuntu One</dd>


> What is Ubuntu?

Ubuntu is an operating system built by a worldwide team of expert developers. It contains all the applications you need: a web browser, office suite, media apps, instant messaging and much more.

Ubuntu is an open-source alternative to Windows and Office.

[http://www.ubuntu.com/products/whatisubuntu](http://www.ubuntu.com/products/whatisubuntu)
> What is Ubuntu?

Ubuntu is a community developed operating system that is perfect for laptops, desktops and servers. Whether you use it at home, at school or at work Ubuntu contains all the applications you'll ever need, from word processing and email applications, to web server software and programming tools. 

than the website gives a wrong impression!

---

### Post by frodon on 2009-11-03
Ok now that we've both said what we have to say lets focus back on topic now.

---

### Post by rgeddes on 2009-11-03
> **Brownedwg89 said:**
> Did you try the method shown in the video? It shows how to change the password from a LiveCD, maybe you could take care of your problem using similar steps.

Or maybe you could mount your drive and chroot in it. From there ,it would be as if you had root access to your filesystem.

Also, I don't know if this would work for you, but when it dropped me to the flickering tty1, I could make it stop flickering by holding ctrl-alt and tapping f1 repeatedly (it sometimes took a while).

I'm using the LiveCD to post to the forum, and couldn't get the flash video, but I switched over to Windows and checked it out... very interesting video... anyone with physical access, a LiveCD, and about 5 minutes can re-assign passwords... and as all those hardware and software speed-ups keep happening, it will be less than 5 minutes.  

The technique works to reset the root password as well... at least it worked in my case.

Anyway, I booted into the Recovery Mode of the 2.6.31 kernel and selected the "drop into root shell" option from the Recovery Menu, and proceeded to install the NVIDIA driver for my os (amd64).. 

After a reboot, the the system keeps dropping into a tty with the flashing business I'm hearing so much about... anyway, I think I'm going to try to backup all my stuff (500GB+) and do a fresh install.

I'm having problems with my audio as well, so I think working with a fresh install will reduce the layering of bugs and issues from previous/custom installs...

---

### Post by fooons on 2009-11-03
I tried all the solutions that have been published but none has succeeded. I tried all the nvidia drivers without outcome. This bug is causing us headaches and there is currently no solution. The only version that works well is me in 8.04.

---

### Post by luvr on 2009-11-03
> **ACanuck said:**
> I installed Ubuntu 9.10 64bit today(via livecd, not alternate) and on booting up the first time I was met with a commandline login. IIRC the only error was the "no screens" thing. I stuck the livecd back in, edited my xorg file removing the fglrx line, booted the new install again and it went fine
That's the exact same problem I had: There was a **fglrx** line in the *"xorg.conf"* file, and I had to delete this line to correct the problem.
Only, I didn't need to reboot from the CD, since I know just enough about the old-fashioned **vi** text editor to make such simple edits from a character-based session.

**Update:** I retried the install, and didn't encounter the problem again this time. Just like the first time, I did a fresh install of the Ubuntu 9.10, 64-Bit version. **However,** the first time, I had installed the proprietary ATI driver to the LiveCD session before I started the install; the second time, I did *not* install the proprietary driver prior to installing the system.

---

### Post by manzdagratiano on 2009-11-03
I am not entirely clear on the status of this problem; I had this issue when I was upgrading to the karmic release candidate from jaunty on the 28th - while the nvidia driver 185.xx was being installed, there were errors that mentioned something to the effect "this driver has no modules in kernel 2.6.31; installing in 2.6.28", which I believe means that the packaged nvidia driver did not compile correctly into the kernel it was supposed to. The upgrade completed with some minor whinings, and on reboot, I did not get a flickering screen, rather my screen was plagued with artefacts which would cause it to be sluggish and eventually lead to a reboot. This I have read around is an issue with nvidia's powermizer in this driver version; apparently the newer drivers (190.xx) have some setting for powermizer which can prevent this. This is related to the following bug:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/456637](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/456637)

This mentions the workaround for this case, but the solution I believe is to change the packaging of the included nvidia driver. The bug status is however "new" and it is "undecided" and "unsassigned" at the moment, so I have no idea what is happening there, and I would request some enlightenment.

I then decided to go for a clean install on the 29th; while I was in the LiveCD mode, I was notified by jockey about proprietary nvidia drivers available for the system. I installed them upon which I got the message that the computer needed to be rebooted for them to take effect, which was meaningless as I was on the LiveCD. I then however installed karmic on my hard drive; and booting gave me the flicker of death. I do not have a dual boot system (I got rid of windows vista and its serfdom completely four months ago), so I decided to stop playing around and reinstalled jaunty on my system.

I have a question - does the second scenario imply that the nvidia drivers that I installed on the LiveCD were also installed onto the hard drive? Or am I running into two unrelated issues? - one the packaging of the nvidia drivers, and the other the flickering screen? From the bug report mentioned in the posts that precede

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/441638](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/441638)

it appears to me that this is a bug in gdm and not in nvidia. Or maybe it is the case that the bug in nvidia **causes** the bug in gdm to surface. What I would love to know is whether the powers-that-be in ubuntu are taking care of the two issues (the latter certainly, the former is the doubtful), or would this require the nvidia people to spring into action?

Though the packaged driver 185.xx is the cause, the solutions in this thread suggest that the 190.xx driver directly available from nvidia is able to compile correctly into the 2.6.31 kernel; I would therefore imagine that the solution would be to replace the 185.xx driver in the karmic upgrade by the 190.xx driver.

I am sticking to jaunty at the moment until these issues are fixed; I have tried many times to obtain workrounds for issues - for instance the headphone jack sense issue which can be fixed by editiing the alsa-base.conf file; however I believe that if we are to defeat Windows from having number 1 market share (c.f. bug #1 [https://bugs.launchpad.net/ubuntu/+bug/1](https://bugs.launchpad.net/ubuntu/+bug/1)), the primary focus must be on making hardware detection seamless and effortless; Ubuntu has already done a phenomenal job on that in many arenas (Ubuntu gave me no trouble with my intel WiFi where I continually failed in Debian to install the available iwlwifi drivers; it also showed me the full potential of my GeForce 8400M without me making any effort whatsoever, something which in vista was clogged by the humongous pile of nonsense it comes with); it is the remainder that will win the battle!

Ubuntu and GNU/Linux to the grave... I will not let Windows touch any of my machines ever again!

---

### Post by ACanuck on 2009-11-03
> **luvr said:**
> That's the exact same problem I had: There was a **fglrx** line in the *"xorg.conf"* file, and I had to delete this line to correct the problem.
Only, I didn't need to reboot from the CD, since I know just enough about the old-fashioned **vi** text editor to make such simple edits from a character-based session.
I've never been able to figure them out myself lol 

> **luvr said:**
> **Update:** I retried the install, and didn't encounter the problem again this time. Just like the first time, I did a fresh install of the Ubuntu 9.10, 64-Bit version. **However,** the first time, I had installed the proprietary ATI driver to the LiveCD session before I started the install; the second time, I did *not* install the proprietary driver prior to installing the system.
You know what? Now that I think about it, I did the same thing on the 64bit install and not the 32bit, I guess that was the problem! Nice catch!

---

### Post by amazing mustard on 2009-11-03
> **y.t said:**
> No, I'm not able to login because I loose the focus each time the screen is flackering - entering password is impossible

I also can't enter grub and choose another kernel. Very frustrating for the moment.

in grub, try your kernel version in recovery mode and enter root with network possibility. if this is not possible, your only way out is booting from usb, cd, dvd or network and fix grub, X or preferably both. if this is the case, i'd research this problem first or maybe start a new topic.

if you **can** drop back to root shell, do the following:

backup /etc/X11/xorg.conf and overwrite it with the following:
```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "Module"
	Load	"dri"
	Load	"GLcore"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"vesa"
EndSection
```

then restart and you should at least be able to start in 800x600 mode

the following *how to* helped me to restore my nvidia drivers after update 9.04 --> 9.10: [http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html](http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html)

(after executing the commands in the how to do *sudo nvidia-xconfig* and restart X (or the whole pc)

good luck

---

### Post by luvr on 2009-11-03
> **manzdagratiano said:**
> I have a question - does the second scenario imply that the nvidia drivers that I installed on the LiveCD were also installed onto the hard drive?

I don't think so--the way I see it (albeit with ATI instead of nVIDIA), the installer will set up an *"xorg.conf"* file that **wants** to run the proprietary driver, while the driver itself will **not** get installed.

It appears that you can circumvent the problem by making sure that the proprietary driver is **not installed** on the system from which you initiate the installation to harddisk. I imagine that, if you want to do an *upgrade* and avoid the problem, you will have to **uninstall** the proprietary driver (be it ATI or nVIDIA) *prior* to performing the upgrade.

Definitely a bug in the installer, if my suspicion is correct: If it sets up your *"xorg.conf"* to run the  proprietary driver, it had better **install** the driver as well; conversely, if it won't install the proprietary driver, it should **not** set up *"xorg.conf"* to require it.

---

### Post by manzdagratiano on 2009-11-03
Then we are definitely talking about two separate issues here - one with nvidia which does not correctly compile into the 2.6.31 kernel as far as the included 185.xx drivers are concerned, and the other with gdm, which respawns eternally after a failure to find the proprietary drivers and does not fall back onto vesa. I hope these issues shall be fixed soon - the gdm issue, and that the newer 190.xx drivers which do not have the powermizer issue be included in the karmic upgrade. And then I shall proceed to have a taste of karmic before lynx!

---

### Post by m3topaz on 2009-11-03
I've also had the flickering screen on boot, which ends up with a conventional non-graphical login prompt. The flickering meant that entering username was just about possible as you can get a few goes to get the letters in, but password entry was a non-starter. This occurred on upgrade from 32-bit Jaunty to Karmic on my desktop PC (Asus P5QL Pro MoBo, S775 Intel P43, Gigabyte GF 9600GT 1Gb GDDR3 PCIE, twin screens CTX PR960F CRT and AOC LM919 TFT).
I managed to get a root prompt when booting into recovery mode, and bearing in mind the slight quirkiness of the Nvidia setup managed to stumble to a fix with the following:
1) # vi /etc/usplash.conf - changed xres to 1024 and yres to 768
2) # update-initramfs -u
3) # apt-get remove usplash usplash-theme-ubuntu
4) # apt-get autoremove
5) # apt-get install nvidia-modaliases nvidia-glx-185
Frankly, I'm unsure if one or all of these were needed - and there was the odd reboot in between to see what might have happened! Reading up online it seemed like a few folk had problems with usplash and Nvidia, and these 'felt' like the likely culprits for the problem I had. Once done, everything booted up fine - to my considerable relief, as the prospect of flattening was not pleasant - and the system is working just great now. Including the Nvidia setup under System - Administration - NVIDIA X Server Settings.
I would suggest that the flickering problem at boot for systems similar to mine *might* be cured by getting a recovery session and re-installing the Nvidia drivers.

(Edit)
# uname -a
Linux <me> 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

---

### Post by apostate on 2009-11-03
Guys,

I saw this (the flickering shell) when I tried to install and boot the desktop-pae kernel. I resolved it by installing all the headers, kernel-source, etc. I think it may be related to the proprietary graphics drivers and the on-the-fly compilation of suitable modules. Try logging in to the cli on another tty and install the restricted-modules, kernel headers, source, etc. for your kernel and then reboot.

---

### Post by luinav on 2009-11-03
Hi all,

I had the same issue with a Silicon Integrated Systems card.

I booted in the recovery mode and moved xorg.conf to xorg.conf.old. Then rebooted again and the problem solved.

Just my two cents.

Regards,
Luis Miguel Navas

---

### Post by TruePhase on 2009-11-03
This resolved it for me. I was missing linus-headers-generic-pae. The first reboot after installing this package, almost looked like it didn't work (still flickering) but after waiting a minute or two X eventually came up fine. Subsequent reboots worked perfectly with no flicker.

> **apostate said:**
> Guys,

I saw this (the flickering shell) when I tried to install and boot the desktop-pae kernel. I resolved it by installing all the headers, kernel-source, etc. I think it may be related to the proprietary graphics drivers and the on-the-fly compilation of suitable modules. Try logging in to the cli on another tty and install the restricted-modules, kernel headers, source, etc. for your kernel and then reboot.

---

### Post by Hyppy on 2009-11-04
I was having this flickering screen on the TTY1 prompt problem.
My fix for a Dell E1750 with an ATI Mobility Radeon X1400 Card:
 

(ssh into the machine if possible, or boot in recovery mode)

```
su -
service stop gdm
apt-get remove xorg-driver-fglrx xserver-xorg-video-radeon xserver-xorg-video-ati
apt-get autoremove
apt-get install xserver-xorg-video-radeon xserver-xorg-video-ati libdrm-radeon1
Xorg -configure
cp /root/xorg.conf.new /etc/X11/xorg.conf
init 6
```
 This will blast your current xorg.conf away.  Sorry.  Back it up if you're sentimental.
 

The big problem I had, besides the initial graphics floundering, was that when the xserver-xorg-video-radeon package was installed, it didn't install libdrm-radeon1.  This caused Xorg -configure to spit out a nasty segfault.

---

### Post by Shikhar Saxena on 2009-11-04
> **fasmike said:**
> I was not on a network, so I had some trouble doing exactly what you said above, but your method did work, thanks!  This is what I did:

[LIST=1]
[*]Use a different computer to download the NVIDIA-Linux-*.run for my new laptop
[*]Copy that new driver to a USB drive
[*]Boot to recovery mode on the new laptop [(had to look this up)]("https://wiki.ubuntu.com/RecoveryMode"):[INDENT]Hit ESC just after your Bios loads when (in theory) you see the "Grub loading blah blah"  (it was WAY too fast to see it on my machine)[/INDENT][INDENT]A menu will come up with boot options, select the one that ends in (recovery mode)[/INDENT][INDENT]You are dropped at the root@yournmachine:~# prompt[/INDENT]
[*]Plug my USB drive into the laptop (after a few seconds I saw some stuff scroll by the screen)
[*]Mount the USB drive [(had to look this one up):]("http://help.ubuntu.com/community/Mount/USB")[INDENT]Find the drive with the command: sudo fdisk -l  (mine was /dev/sdb1)[/INDENT][INDENT]Create a directory to mount it as: sudo mkdir /media/external [/INDENT][INDENT]Mount the drive:  sudo mount -t vfat /dev/sdb1 /media/external -o uid=1000,gid=100,utf8,dmask-027/fmask=137[/INDENT][INDENT]NOTE: if your USB is not FAT## you need a different -t option[/INDENT]
[*]Copied the new driver to my home directory (may not have been necessary)
[*]execute the NVIDIA-Linux-*.run file[INDENT]I had to change permissions on the file before I could run it: chmod 777 NVIDIA*[/INDENT][INDENT]Ran the file with: ./NVIDIA*.run[/INDENT]
[*]Follow the instructions
[*]Reboot
[/LIST]

This made the flickering login problem go away and allowed me to get in and start using Ubuntu on my new machine.

This solved the flickering problem(after a clean install on hp dv5) for me (thankfully,hv a working installation now ).Many Thanks.

---

### Post by fooons on 2009-11-04
> **Shikhar Saxena said:**
> This solved the flickering problem(after a clean install on hp dv5) for me (thankfully,hv a working installation now ).Many Thanks.
 No success for me with this configuration I'm using a GForce Go 7600 with latest 190.40 and 185, and this one patched.
 
I only managed to stop blinking for 2 seconds, then blink again

---

### Post by Shikhar Saxena on 2009-11-04
> **fooons said:**
> No success for me with this configuration I'm using a GForce Go 7600 with latest 190.40 and 185, and this one patched.
 
I only managed to stop blinking for 2 seconds, then blink again

You could try the other way of downloading directly from the nvidia ftp(the 'prayer' way,though that didn't work for me) as said above.there are some more options, but i am also new to this and don't hv that much know how.(btw, i hv a 9600 gt if that helps ).Hope u get it working .

---

### Post by Hillbill on 2009-11-04
By now i have tried most of the solutions posted here. So far i've had no luck.

I have a Lenovo T400 laptop with ATI graphics. I installed 9.10 and have XP Pro installed as well, in a dual boot.

I tried to download ATI drivers manually, tried to have 9.10 install it for me(the small icon telling you proprietary drivers are available), and i tried envy. Every time i'm rewarded with the flickering login screen. Envy made it even worse, as trying to use envyng -t from the recovery apparently did not manage to remove the drivers entirely, so i'm left with a black screen when i should see the login.

Using Vesa drivers really is not a option, other than for emergency recovery.
I see people get their Nvidia graphics issues fixed, but has anyone been able to get ATI drivers up and running at all?

---

### Post by DustofDust on 2009-11-04
> **Hillbill said:**
> By now i have tried most of the solutions posted here. So far i've had no luck.

I have a Lenovo T400 laptop with ATI graphics. I installed 9.10 and have XP Pro installed as well, in a dual boot.

I tried to download ATI drivers manually, tried to have 9.10 install it for me(the small icon telling you proprietary drivers are available), and i tried envy. Every time i'm rewarded with the flickering login screen. Envy made it even worse, as trying to use envyng -t from the recovery apparently did not manage to remove the drivers entirely, so i'm left with a black screen when i should see the login.

Using Vesa drivers really is not a option, other than for emergency recovery.
I see people get their Nvidia graphics issues fixed, but has anyone been able to get ATI drivers up and running at all?

yes, me with ati.

try an emergency boot with vesa. go into synaptics and uninstall completely all the ati drivers. just search for ati and look what is installed.

my sollution was:
[http://ubuntuforums.org/showpost.php?p=8201026&postcount=23](http://ubuntuforums.org/showpost.php?p=8201026&postcount=23)
> sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon xorg-driver-fglrx
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
dpkg-reconfigure xserver-xorg
sudo apt-get install xserver-xorg-video-mach64

last line or radeon or fglrx depending which generation of card you have.

hope that helps...

---

### Post by Not on 2009-11-04
I had a similar issue, but now have 9.10 running smoothly.

It seems that the upgrade process disables all proprietary drivers, but does so without updating xorg.conf to use the default non-proprietary drivers.

All I did to fix this was login via a rescue shell, edit xorg.conf so that nothing was listed in the "Device" section. hal recgnised my hardware and I could boot normally (of course my twinview was now broken). I installed the proprietary driver and reverted to my old xorg.conf - no issues.

The fix - just search xorg.conf for proprietary drivers and edit accordingly - can probably be included in the uprage sequesnce quite easily.

---

### Post by simple simon on 2009-11-04
> **DustofDust said:**
> yes, me with ati.

try an emergency boot with vesa. go into synaptics and uninstall completely all the ati drivers. just search for ati and look what is installed.

my sollution was:
[http://ubuntuforums.org/showpost.php?p=8201026&postcount=23](http://ubuntuforums.org/showpost.php?p=8201026&postcount=23)


hope that helps...


Having read a fair bit of this thread it would be great if someone who understood most of what has been posted (unlike me) cold post a "How To install Karmic".  Ideally it would separate fresh install/upgrade/ATI/nvidia.  For me all these things are completely jumbled and I can't see what I'm supposed to do.

I'm hoping to do a fresh install for an HP 6735s Ati 3200.

---

### Post by sm108 on 2009-11-04
I had the same problem.  On Jaunty I was using an Nvidia driver downloaded from Nvidia, not the one that you can install using Hardware Drivers in Ubuntu.

On first boot after the upgrade I had the exact same symptoms as described above.

If you also have the Nvidia driver and you still have (or you can download) the Nvidia installer, you should be able to fix the problem as follows:

- reboot (either by Ctrl+Alt+Del or reset if that doesn't work)

- at the grub prompt boot in recovery mode

- at the recovery prompt choose "Root console"

- run the Nvidia installer with the --uninstall flag (it may throw some warnings)

- run the Nvidia installer with no options and follow the prompts

- reboot

---

### Post by tomveil on 2009-11-04
Hello,

After installing Ubuntu 9.10 I have experienced a problem where my screen is split horizontally. Not just while in Ubuntu, but immediately after powering up. It remains split in Windows, and older versions of Ubuntu that I have installed on USB disks.

AS IT STANDS MY COMPUTER IS BROKEN, not just the Ubuntu install.

My screen looks very similar to [B][http://www.flickr.com/photos/37784226@N07/](http://www.flickr.com/photos/37784226@N07/)

[/B]A person on an Nvidia group reported a similar problem [http://forums.nvidia.com/index.php?s...0&#entry944477]("http://forums.nvidia.com/index.php?showtopic=95492&pid=944477&st=0&#entry944477"). He was using ubuntu 9.04 and the problem occurred immediately after ubuntu was released. 

My system - Dell Vostro 1400 (Laptop - two years and one month old)
  V1400 CORE 2 DUO T7250 2.00GHZ, 800, 2M
  DISPLAY : 14.1IN WXGA+ (1440X900)
  GRAPHICS : 128 MB NVIDIA GEFORCE 8400M GS

Any suggestions, anyone having similar problems?

Please help.

Tom

---

### Post by Brownedwg89 on 2009-11-04
So I still cannot get into gnome.

I can get to the login screen, but when I login, the screen goes black, blinks, then returns to the login screen. I have tried replacing my ~ with files from other installations (such as from my laptop). I've tried making a new user and using that to log in. That did not work.

My .xsession-error contains:
> /etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US. 
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/etc/gdm/Xsession: Beginning session setup...
.: 34: Can't open /home/[user]/.profile

This is for both my user and the test user I created to try this with... The permissions for .profile are fine (644 and owned by the user). I've tried setting it to 777, but that does not fix it.

Any clues?

---

### Post by Leebo on 2009-11-04
I had the same problem mention previously, and all i did was:

1. Download the newest drivers from Nvidia (190)
2. Boot into 2.6.31 recovery mode
3. Change to run level 3 (telinit 3)
4. chmod +x Nvidia script to make it executable
5. Execute install script as root

This not only repaired the flickering screen, but it also somehow magically fixed my Intel HDA integrated sound card that wasnt working either. So whatever works :)

---

### Post by scaldeddog79 on 2009-11-05
I had been experiencing this problem after a clean install of Mythbuntu.  Previous version had worked with the restricted driver, bu I usually had to add  VMALLOC and PCI parameter to the boot command in grub.  From my reading this was a result of the hadware combo I have:  64bit AMD Athlon X2 4600+ dual core, mobo with Nforce4 chipset and NVIDIA 9 series graphics.

Back to the issue at hand, I had tried all of the solutions posted and except for using the nv driver (unacceptable), none worked.

My solution was to install the AMD64 build of the distro.  Chose restricted drivers right off the bat and everything worked, no fuss no muss.

I had been avoiding the AMD64 build because past experiences were less reliable than the 32bit version.  So far (2 days) I have had no issues and everything is smooth.

---

### Post by mightymouse3062 on 2009-11-05
> **lapdog said:**
> I did the following:

1.  Hit ESC after the BIOS loads (at the grub screen).

2.  Select the "recovery mode" with the later kernel:  2.6.31-14.  (The other choice I had was 2.6.28-16.)

3.  Login

4.  Pray that ftp will work and you can download from nVidia's site--necessary step!  don't skip!  :)

5.  ftp

[INDENT]6.  open download.nvidia.com

7.  for username, use:  guest

8.  for password, just press <Enter>

9.  cd XFree86
10. cd Linux-x86
11. cd 190.42

12. binary

13. get NVIDIA-Linux-x86-190.42-pkg1.run
    and wait for it to download; took about a minute for me

14. bye
[/INDENT]
15.  chmod 777 NVIDIA*

16.  sudo ./NVIDIA*.run

17.  Follow instructions in nVidia installation.  Remember to choose Yes when it asks if you want to replace current X config options.

18.  reboot

19.  Praise God with a prayer of thanksgiving when it works, and add a prayer of thanks for the Ubuntu community.



I had the same problem and I was running 64bit. I did the exact same as lapdog suggested however I changed #13 to NVIDIA-Linux-x86_64-190.42-pkg1.run and instead of doing 15 I had to type in telinit 3 and then chmod the file and run it as root. 

Thank you very much for helping fix the problem. 

~Mike

---

### Post by jc66 on 2009-11-05
Hi,

I just registered to post this.

I have had the same problem since I upgraded at the weekend, I managed to get a working desktop by swapping first to 'vesa' driver and then to the 'nv'. 

The 'nv' driver (open source from xorg) is actually quite nice, but of course lacks any 3D support.

Anyway, I have been following this and other threads, but have avoided any solutions that require installing files from anywhere outside the repositories (just my personal choice!)

I've also been continuously reinstalling the nvidia-glx drivers and chasing up the various error messages that come with it.

The last of these led me to this page:

[http://www.nvnews.net/vbulletin/showthread.php?p=2115219](http://www.nvnews.net/vbulletin/showthread.php?p=2115219)

and following the advice I tried

$> apt-get install linux-headers-`uname -r`
$> sudo aptitude reinstall nvidia-96-kernel-source

And it worked! (the '96' is for my old geforce2 card, most people will use one of the newer drivers.)

It might not work for everyone - I've updated a lot of other things, and it seems like this is a combination of a few separate problems together, but it might help someone along the way.

mfg,

john

---

### Post by kleeman on 2009-11-05
Just a heads up. A new gdm package is in the proposed repository at present which is supposed to fix this problem.

---

### Post by pdoes on 2009-11-05
I had similar problem after upgrade from Jaunty.

I didn't read through all the pages but I couldn't even get in recovery mode.

Solved it following these steps:
[LIST=1]
[*]Boot up from Live CD
[*]Mount /dev/sda1 (root partition) on /mnt
[*]In /mnt/etc/X11 I had a xorg.conf.failsafe. Deleted the xorg.cong, copied the failsafe to xorg.conf and rebooted.
[*]Everything started up normally.
[*]Restarted in recovery mode which worked again.
[*]Reinstalled the proprietary nVidia driver.
[*]Rebooted and everything worked like a charm.
[/LIST]

If you don't have the xorg.conf.failsafe this is the contents.
```
# xorg.conf.failsafe (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

---

### Post by tsh on 2009-11-05
i had some issues with the nvidia driver after upgrading, even after the 4-nov updates. Finally got it working by installing 190.42 of the driver, and also adding
```
    Option         "UseDisplayDevice" "DFP"
```
to the Screen section of my /etc/X11/xorg.conf. i use a LCD TV for a monitor, and since the upgrade seem it didn't seem to be detected properly by the driver. X would start, but the screen would be blank (using hte CRT output, i guess)

---

### Post by dmedell on 2009-11-06
> **Hillbill said:**
> I did a fresh install on my laptop, a Lenovo ThinkPad, and i have the same problem. Login is impossible due to the flickering.
My laptop has ATI graphics card, so it can't be the Nvidia issues causing this.

Anyone?

I'm using an IBM T30 with ATI as well and the 2.6.31-14 generic kernel doesn't allow me to boot. In recovery mode the error is

BUG: soft lock up cpu paused for 61 s

Any one have any thoughts?
Thanks Dan

p.s. I had a similar issue with kernel 2.6.28-15.52 in 9.04 about a month ago bug [[SIZE="5"][COLOR="Red"]442364[/COLOR][/SIZE]]("http://bugs.launchpad.net/ubuntu/+bug/442364"). I was able to get help and fix the problem with a patch. The issue is that kernel patches are hardware specific,

---

### Post by jlr1701 on 2009-11-06
> **lapdog said:**
> Similar update experience:  got flashing text login screen on tty1 with normal bootup--no way to log in since most keystrokes did not register.  tty2 - 6 had the same flashing.  tty7 was blank.  With either "recovery mode" option, got to login but startx gave "screen not found" error, among others.

With the guidance of other posts here, I am now writing from a working 9.10 system.  Yeah!  Since my network connection was working and I apparently needed the latest nVidia driver, I did the following:

1.  Hit ESC after the BIOS loads (at the grub screen).

2.  Select the "recovery mode" with the later kernel:  2.6.31-14.  (The other choice I had was 2.6.28-16.)

3.  Login

4.  Pray that ftp will work and you can download from nVidia's site--necessary step!  don't skip!  :)

5.  ftp

[INDENT]6.  open download.nvidia.com

7.  for username, use:  guest

8.  for password, just press <Enter>

9.  cd XFree86
10. cd Linux-x86
11. cd 190.42

12. binary

13. get NVIDIA-Linux-x86-190.42-pkg1.run
    and wait for it to download; took about a minute for me

14. bye
[/INDENT]
15.  chmod 777 NVIDIA*

16.  sudo ./NVIDIA*.run

17.  Follow instructions in nVidia installation.  Remember to choose Yes when it asks if you want to replace current X config options.

18.  reboot

19.  Praise God with a prayer of thanksgiving when it works, and add a prayer of thanks for the Ubuntu community.


Boot up time for me is about the same, maybe a few seconds longer.  The new graphic defaults look cool and so far have been very fast and non-intrusive.

While I don't mind installing an extra file, getting a huge file onto a machine that doesn't boot correctly is a *major* source of stress.  Please, Ubuntu, put a message for nVidia users in big, bold type on your main 9.10 page saying the latest driver is needed.  Fetching this file beforehand would save a *lot* of trouble, as this thread shows.  This really is a serious issue that should not be present in a standard release.  (More than 40% with major problems?  Is that normal?)

Still don't have working sound or floppy, but nothing new there.  I saw a sound sticky...

On a positive note, thanks to the Ubuntu forum and community members for pointing me in the right direction!!!

---
mobo:  MSI K9N2GM-FIH (nVidia GeForce 8200); proc:  AMD Phenom X3 (AM2+) 8450; 4 Gig mem

This worked for me after a bad partial update involving some Karmic updates and the OpenShot video editor hosed my system. I'm using 64-bit, so I just downloaded that driver instead. Fortunately, I know the "ls" command, so I could get a list of available files. Never done ftp from the command prompt before! 

Anyway... thanks very much!!! My system works again after I went through the predictable "still pretty much a Linux noob" stages of:

1. Linux sucks and it breaks amazingly easily!

2. Karmic sucks! Bad release of a great distro...

3. Windows 7 works perfectly. Screw Linux!!!

4. Think I'll go check the Ubuntu forums for a solution to my problem.

5. Find detailed, workable solution.

6. Hail the provider of the solution as a hero, and those like him providing similar workable solutions.

7. Be happy again! :)

Thanks again very much!!:D

---

### Post by jc66 on 2009-11-06
[FONT=Arial][SIZE=2][SIZE=2]In my earlier post #120 I listed something that had worked for me fixing this problem.
 
Now I have checked it out further, and I am pretty sure it is the proper fix to the problem of the nvidia drivers not loading (the flashing screen is a by-product of this, and I am not sure about ati drivers.) It works like this:
 
1. [/SIZE][FONT=Arial][SIZE=2]Nvidia supply a binary driver for their graphics cards. The kernel can't talk to this directly, and so a kernel module is required to act as a 'shim'.
 
2. This source code for this kernel module is in the package nvidia-xxx-kernel-source, where 'xxx' is the version of the driver.
 
3. When this kernel source package is loaded, the module is built on the fly by the 'dkms' program. But to do this, the kernel header package is needed.
 
On my system, the module didn't build because the kernel headers were not installed!
 
**So the whole problem is due to the kernel header package not being listed as a dependency to the nvdia driver!**
 
If the ubuntu developers add this dependency, everything should start working again.
 
**To reiterate: If you have the problem with the nvidia drivers not loading, before doing anything else, try the following:**
 
First
 
[FONT=Courier New]$> sudo aptitude install linux-headers-`uname -r`[/FONT]
 
And then one of the lines below, depending on the version of the driver you are using
 
[FONT=Courier New]$> sudo aptitude reinstall nvidia-96-kernel-source[/FONT]
or,
[FONT=Courier New]$> sudo aptitude reinstall nvidia-173-kernel-source
[/FONT]or,
[FONT=Courier New]$> sudo aptitude reinstall nvidia-180-kernel-source
[/FONT]or,
[FONT=Courier New]$> sudo aptitude reinstall nvidia-185-kernel-source[/FONT]

 
Do this before installind drivers direct from the nvidia site as that will break future automatic updates.
 
mfg,
 
 
john
[/SIZE][/FONT][/SIZE][/FONT]

---

### Post by chessmani on 2009-11-06
After several days using the new driver I have to add that sometimes I still get the flickering and boot into the terminal. I can keep rebooting until it works, which is about one or two times at most, but there's still something wrong here...

---

### Post by chessmani on 2009-11-06
> **jc66 said:**
> [FONT=Arial][SIZE=2][SIZE=2]In my earlier post #120 I listed something that had worked for me fixing this problem.
 
Now I have checked it out further, and I am pretty sure it is the proper fix to the problem of the nvidia drivers not loading (the flashing screen is a by-product of this, and I am not sure about ati drivers.) It works like this:
 
1. [/SIZE][FONT=Arial][SIZE=2]Nvidia supply a binary driver for their graphics cards. The kernel can't talk to this directly, and so a kernel module is required to act as a 'shim'.
 
2. This source code for this kernel module is in the package nvidia-xxx-kernel-source, where 'xxx' is the version of the driver.
 
3. When this kernel source package is loaded, the module is built on the fly by the 'dkms' program. But to do this, the kernel header package is needed.
 
On my system, the module didn't build because the kernel headers were not installed!
 
**So the whole problem is due to the kernel header package not being listed as a dependency to the nvdia driver!**
 
If the ubuntu developers add this dependency, everything should start working again.
 
**To reiterate: If you have the problem with the nvidia drivers not loading, before doing anything else, try the following:**
 
First
 
[FONT=Courier New]$> sudo aptitude install linux-headers-`uname -r`[/FONT]
 
And then one of the lines below, depending on the version of the driver you are using
 
[FONT=Courier New]$> sudo aptitude reinstall nvidia-96-kernel-source[/FONT]
or,
[FONT=Courier New]$> sudo aptitude reinstall nvidia-173-kernel-source
[/FONT]or,
[FONT=Courier New]$> sudo aptitude reinstall nvidia-180-kernel-source
[/FONT]or,
[FONT=Courier New]$> sudo aptitude reinstall nvidia-185-kernel-source[/FONT]

 
Do this before installind drivers direct from the nvidia site as that will break future automatic updates.
 
mfg,
 
 
john
[/SIZE][/FONT][/SIZE][/FONT]
I've always had linux-headers installed and I had the problem. The only package I don't have is the linux-headers-...-pae. Is this package necessary as well? What's the difference between this one and the generic one?

---

### Post by jc66 on 2009-11-06
> **chessmani said:**
> I've always had linux-headers installed and I had the problem. The only package I don't have is the linux-headers-...-pae. Is this package necessary as well? What's the difference between this one and the generic one?
 
I would guess you only need the headers for whichever kernel you are using (pae seems to be a special version for large files.)
 
If you use the commands as I put them, they should ensure you have the right ones installed. Btw, I was also surprised that I didnt have the headers installed, at some point in the past i definatly did and I never remember removing them - perhaps there was also an error in them not getting updated with the kernel itself.
 
Other than that, try the following things:
 
1. As you run the command to reinstall the nvidia-xxx-kernel-source, check to see if any errors come up - if they do you can post them here to see if me or someone else understands them.
 
2. After that has done, if there do not appear to be any errors, try 'sudo modprobe nvdia'
 
3. If that gives no errors, then make sure you have the Device in your xorg.conf file set to 'nvidia'
 
Its very likely there were several different problems straight after the upgrade, I have been going through and changing all sorts of thigns the last few days, and so this might simply have been the last thing needed to finally get it working and not the sole problem on its own.
 
btw, I just noticed someone else had already spotted this thing wth the missing headers a few pages earlier in the thread, so I was not quite as clever as I thought!
 
john

---

### Post by jlr1701 on 2009-11-06
> **jc66 said:**
> [FONT=Arial][SIZE=2][SIZE=2]In my earlier post #120 I listed something that had worked for me fixing this problem.
 
Now I have checked it out further, and I am pretty sure it is the proper fix to the problem of the nvidia drivers not loading (the flashing screen is a by-product of this, and I am not sure about ati drivers.) It works like this:
 
1. [/SIZE][FONT=Arial][SIZE=2]Nvidia supply a binary driver for their graphics cards. The kernel can't talk to this directly, and so a kernel module is required to act as a 'shim'.
 
2. This source code for this kernel module is in the package nvidia-xxx-kernel-source, where 'xxx' is the version of the driver.
 
3. When this kernel source package is loaded, the module is built on the fly by the 'dkms' program. But to do this, the kernel header package is needed.
 
On my system, the module didn't build because the kernel headers were not installed!
 
**So the whole problem is due to the kernel header package not being listed as a dependency to the nvdia driver!**
 
If the ubuntu developers add this dependency, everything should start working again.
 
**To reiterate: If you have the problem with the nvidia drivers not loading, before doing anything else, try the following:**
 
First
 
[FONT=Courier New]$> sudo aptitude install linux-headers-`uname -r`[/FONT]
 
And then one of the lines below, depending on the version of the driver you are using
 
[FONT=Courier New]$> sudo aptitude reinstall nvidia-96-kernel-source[/FONT]
or,
[FONT=Courier New]$> sudo aptitude reinstall nvidia-173-kernel-source
[/FONT]or,
[FONT=Courier New]$> sudo aptitude reinstall nvidia-180-kernel-source
[/FONT]or,
[FONT=Courier New]$> sudo aptitude reinstall nvidia-185-kernel-source[/FONT]

 
Do this before installind drivers direct from the nvidia site as that will break future automatic updates.
 
mfg,
 
 
john
[/SIZE][/FONT][/SIZE][/FONT]

What about the new 190 drivers from Nvidia's site? I need to use those as they solved a very annoying crashing problem for me after I installed Karmic. I used to have to do a hard reboot after the screen went nuts and became unusable. With the 190 drivers, all is OK and much faster as well.

Thanks,

Jeff

---

### Post by jc66 on 2009-11-06
[quote=jlr1701;8256298]What about the new 190 drivers from Nvidia's site? I need to use those as they solved a very annoying crashing problem for me after I installed Karmic. I used to have to do a hard reboot after the screen went nuts and became unusable. With the 190 drivers, all is OK and much faster as well.
 
My comment about not downloading straight from the nvidia site was meant for the driver versions that are in the repositories but are currently broken.
 
If you want to use a driver that is not in the repositories then sure that is what you have to do. 
 
Do you know what happens when there is a kernel update? I would guess they need to be reinstalled everytime, but I might be wrong.
 
I am pretty sure they will need to be uninstalled before you do a full upgrade next April - hopefully by that time they might be in the official distros though.

---

### Post by sunnyabc on 2009-11-06
I have had two issues since upgrade from jaunty to karmic.
One is no gdm with flickering black screen. The other is no sound.
Installing linux-headers solved the two issues at once.
This is what I did.

sudo apt-get install linux-headers-2.6.31-14-generic
sudo apt-get install linux-headers-2.6.31-14-generic-pae
sudo apt-get install --reinstall nvidia-glx-185
reboot

Those are all I did.
Thanks and good luck

---

### Post by alakin on 2009-11-06
> **jc66 said:**
> [FONT=Arial][SIZE=2][SIZE=2]In my earlier post #120 I listed something that had worked for me fixing this problem.
 
Now I have checked it out further, and I am pretty sure it is the proper fix to the problem of the nvidia drivers not loading (the flashing screen is a by-product of this, and I am not sure about ati drivers.) It works like this:
 
1. [/SIZE][FONT=Arial][SIZE=2]Nvidia supply a binary driver for their graphics cards. The kernel can't talk to this directly, and so a kernel module is required to act as a 'shim'.
 
2. This source code for this kernel module is in the package nvidia-xxx-kernel-source, where 'xxx' is the version of the driver.
 
3. When this kernel source package is loaded, the module is built on the fly by the 'dkms' program. But to do this, the kernel header package is needed.
 
On my system, the module didn't build because the kernel headers were not installed!
 
**So the whole problem is due to the kernel header package not being listed as a dependency to the nvdia driver!**
 
If the ubuntu developers add this dependency, everything should start working again.
 
**To reiterate: If you have the problem with the nvidia drivers not loading, before doing anything else, try the following:**
 
First
 
[FONT=Courier New]$> sudo aptitude install linux-headers-`uname -r`[/FONT]
 
And then one of the lines below, depending on the version of the driver you are using
 
[FONT=Courier New]$> sudo aptitude reinstall nvidia-96-kernel-source[/FONT]
or,
[FONT=Courier New]$> sudo aptitude reinstall nvidia-173-kernel-source
[/FONT]or,
[FONT=Courier New]$> sudo aptitude reinstall nvidia-180-kernel-source
[/FONT]or,
[FONT=Courier New]$> sudo aptitude reinstall nvidia-185-kernel-source[/FONT]

 
Do this before installing drivers direct from the nvidia site as that will break future automatic updates.
 
mfg,
 
 
john
[/SIZE][/FONT][/SIZE][/FONT]

John,

Having read your solution I was convinced it would work. Sadly it didn't :( I am running Xubuntu. Not sure whether that uses gdm or something else?

I am running with the nv driver currently. The system is so slow to log into however. Intrepid is up to speed in 11 seconds from the login screen - Karmic takes 39! How much this is to do with the graphics driver I don't know. I had to give Jaunty a miss because of similar problems, but worse (couldn't save gui settings and login time was well over a minute).

---

### Post by homunq on 2009-11-06
When I initially upgraded to Karmic, I had BOTH NVidia (binary) AND nouveau drivers running (!) according to "system:Hardware Drivers". I considered that a problem and turned them both off, hoping to reboot and turn just nouveau on. On reboot, I had no X - just some random crap on my screen until I dropped to the terminal. I messed around. If I tried to use the nvidia drivers, I'd get the flickering. Eventually (as root)

mv /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf #has vesa driver
apt-get remove nvidia*

(of course, I'd previously gotten
apt-get install xserver-xorg-video-nouveau 
to work - I had to fix dkms to get it to install correctly, I think I had it wedged from earlier)

... got me booting with just the vesa driver. Then, I could go into "Hardware drivers" and enable nouveau, and it would immediately start to work with acceleration.

BUT - on reboot, the acceleration is gone. I have to turn off nouveau, reboot, and turn nouveau back on, in order to get it to work again, until the next reboot.

Anyway, for those struggling with the nvidia binaries, I recommend nouveau - when it works, it's great - but I'd love some help getting it to load consistently.

---

### Post by alakin on 2009-11-06
I have checked the processes running and gdm is there. I tried running from recovery mode and executing startx. The gui launched very quickly and on checking the processes again gdm wasn't running. This got me thinking, it would be good to boot into a console, login and then startx to avoid gdm. I get the feeling my system will zip along if I do this. I am not familiar with how to change the run level at boot? If I can get this far without all the speed issues with the nv driver I will change back to the nvidia driver and see what happens. Worth a go if someone can guide me on the run level issue.

Thanks.

---

### Post by musarraf172 on 2009-11-06
I am having a very bitter experience with ubuntu 9.10.on my IBM R51 2887 AE4 laptop.

9.04 worked flawlessly with any problem. Sound , wifi , booting time
everything was very good. But after 9.10 upgrade I had the following issue.

1. Can not boot with 2.6.31-14 kernel. The boot process does not end
while premounting local file systems.

2. Can boot with old 2.6.28-16 but synaptic touchpad does not work. It has conflict with ps2 mouse. ps2 or usb mouse is working. Sound hardware is not detected.Tried manual probing but without success.

3. Total system is jerky. Firefox stucks. Boot time is longer than 9.04..

4. If the default uspalsh theme is changed system does not boot.

5. got touchpad working by this work around : "echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe"

6. X server hangs when system is idol for a long time. If we change the console and again comeback tty7 then x is working again.

---

### Post by alan_tam_sh on 2009-11-07
QUOTE=Jekshadow;8192916]I recentally upgraded to 9.10, and on doing so, when I rebooted, it had me enter my encryption passphrase, it seemed to boot fine, until it got to where the login screen should be showing. It flickered a lot, and only showed the command line login screen. Whenever it was flickering it would not let me type. Could this be a problem with GDM trying to start but cant? When I rebooted to the 2.6.18 kernel, it worked perfectly.[/QUOTE]

I too encountered similar problem when upgrade to 9.10!
It was a kind of frustration almost make me give up on Ubuntu or linux in general. 
Nevertheless I did a clean installation with CD, this time everything looks fine and nice but not until i activate the Nvidia driver, the system starts to goes haywire at booting after i activated the graphic card driver and by no way I can turn it back but to have to reinstall the entire system again one more time.
From the symptom it seems there are serious incompatible issue between Nvidia hardware and software driver. Hope this problem can be resolve immediately!
I think with this problematic release will surely cause much damages to Ubuntu and tarnished its image. Worst case it scares away many of whom wishes to tryout linux!

---

### Post by alan_tam_sh on 2009-11-07
If you are using Nvdia graphic card (or other cards may also the same)I suggest you do a clean installation and never (remember NEVER!) activate your graphic card driver! Of cause by doing this you looses your eyes candy but you still can run ubuntu without eyes candy.
Next, we pray Ubuntu will release updates real soon to correct this problem otherwise we have the options to move back to MS of which recently had a new wonderful release!

---

### Post by Crusader452 on 2009-11-07
Ok guys, Here's what I've got

ATI Mobility Radeon HD 3650 with all sorts of problems

I have tried to follow the suggestions laid out in this thread with no success.  I am running the 64-bit version of Ubuntu 9.10 and get an error with the linux-headers-generic-pae package when trying to install it.  I keep getting an error message that says the package does not exist, and when I try and download the .deb from ubuntu's package list, I can only find the 32 bit package.

I have tried multiple ways of installing this driver, and it looks like with everyone of them the problem is with the kernel module not being built right or being placed in the right location, but I got no error when making installing the module using the .deb I built using the ati-driver-install.run file from the ati site, so i'm not real sure what is going on here.

Could someone post a synopsis post of the past 14 pages and compile a way to fix the various errors.  I'm not sure what I have been doing is correct, though what I've tried has not worked, and I think I have followed what was going on in this thread.........

---

### Post by jc66 on 2009-11-07
> **alakin said:**
> 
Having read your solution I was convinced it would work. Sadly it didn't :( I am running Xubuntu. Not sure whether that uses gdm or something else?



There were (at least) two problems - the first is that the graphics drivers didn't install properly with Xorg, and is nothing to do with which version of ubuntu you are using (I use kubuntu.)

The second problem with the flickering screen was I think due to gdm, but I never had it.

Sorry that what I suggested didn't work, to go further you need to look at the errors you get if you run startx from the command line, and then at any errors when loading the nvidia driver packages.

However, I would say that if you have a useable system with the nv driver then stick with it for now. Hopefully at some point this bug will be officially fixed and there will be some announcment - then is probably the time to try resintalling the nvidia drivers.

> **alakin said:**
> 
I am running with the nv driver currently. The system is so slow to log into however. Intrepid is up to speed in 11 seconds from the login screen - Karmic takes 39! How much this is to do with the graphics driver I don't know. I had to give Jaunty a miss because of similar problems, but worse (couldn't save gui settings and login time was well over a minute).


If it is a video driver issue, then you need to compare how it takes *to* the login screen - but there will be loads of other factors too so you can't say for sure it is a video driver problem without directly comparing.

---

### Post by jc66 on 2009-11-07
> **alakin said:**
> 
Having read your solution I was convinced it would work. Sadly it didn't :( I am running Xubuntu. Not sure whether that uses gdm or something else?



There were (at least) two problems - the first is that the graphics drivers didn't install properly with Xorg, and is nothing to do with which version of ubuntu you are using (I use kubuntu.)

The second problem with the flickering screen was I think due to gdm, but I never had it.

Sorry that what I suggested didn't work, to go further you need to look at the errors you get if you run startx from the command line, and then at any errors when loading the nvidia driver packages.

However, I would say that if you have a useable system with the nv driver then stick with it for now. Hopefully at some point this bug will be officially fixed and there will be some announcment - then is probably the time to try resintalling the nvidia drivers.

> **alakin said:**
> 
I am running with the nv driver currently. The system is so slow to log into however. Intrepid is up to speed in 11 seconds from the login screen - Karmic takes 39! How much this is to do with the graphics driver I don't know. I had to give Jaunty a miss because of similar problems, but worse (couldn't save gui settings and login time was well over a minute).


If it is a video driver issue, then you need to compare how it takes *to* the login screen - but there will be loads of other factors too so you can't say for sure it is a video driver problem without directly comparing.

---

### Post by fostytou on 2009-11-07
Why are you guys using USB drives and SCP?

Boot to recovery mode from GRUB (hit esc)
Open command line with networking
wget [http://us.download.nvidia.com/XFree86/Linux-x86_64/185.18.36/NVIDIA-Linux-x86_64-185.18.36-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/185.18.36/NVIDIA-Linux-x86_64-185.18.36-pkg2.run)
chmod 777 NVIDIA-Linux-x86_64-185.18.36-pkg2.run
telinit3
./NVIDIA-Linux-x86_64-185.18.36-pkg2.run


Fixed it for me on a 9800GT

---

### Post by alakin on 2009-11-07
Thanks John. It is actually getting worse with the nv driver. If I log out and then log back in it takes ages c.2 minutes to get back in. I have deemed karmic unusable and reverted to my Intrepid installation for now. I downloaded the net install of debian squeeze earlier but haven't had time to run the install yet. I have decided my time will be better spent building my own debian installation rather than mess around with xubuntu that that doesn't want to work.

---

### Post by obviator on 2009-11-08
For me, I had to recompile the graphics drivers (ATI in my case) for the new kernel. I had manually installed them by downloading and running a file from ATI's site, and apparently they were'nt compatible with the new kernel version.

I booted from recovery mode, and ran:

apt-get remove xorg-video-fglrx

in my case though, this said the packages weren't installed. So then I installed them from the repository:

apt-get install xorg-video-fglrx

Then a reboot, and the system came up fine! I think if I hadn't manually installed the drivers and had used the version in the repository to start with I wouldn't have had these troubles. Hope it helps solve yours!

---

### Post by chessmani on 2009-11-08
> **jc66 said:**
> I would guess you only need the headers for whichever kernel you are using (pae seems to be a special version for large files.)
 
If you use the commands as I put them, they should ensure you have the right ones installed. Btw, I was also surprised that I didnt have the headers installed, at some point in the past i definatly did and I never remember removing them - perhaps there was also an error in them not getting updated with the kernel itself.
 
Other than that, try the following things:
 
1. As you run the command to reinstall the nvidia-xxx-kernel-source, check to see if any errors come up - if they do you can post them here to see if me or someone else understands them.
 
2. After that has done, if there do not appear to be any errors, try 'sudo modprobe nvdia'
 
3. If that gives no errors, then make sure you have the Device in your xorg.conf file set to 'nvidia'
 
Its very likely there were several different problems straight after the upgrade, I have been going through and changing all sorts of thigns the last few days, and so this might simply have been the last thing needed to finally get it working and not the sole problem on its own.
 
btw, I just noticed someone else had already spotted this thing wth the missing headers a few pages earlier in the thread, so I was not quite as clever as I thought!
 
john
OK, so I've installed the pae headers which were the only ones I had missing and the problem still remains.

Mind I use the latest 190.42 drivers and I can login most times. Normally after a successful shutdown the next time I start the system I'll be thrown to the terminal. Then I'll ctrl+alt+supr and the next time it'll normally work, or I'll have to reboot for the last time.

In summary, I can use the system, but there's still something wrong somewhere.

---

### Post by Sistershaft on 2009-11-08
The USB idea seemed a bit too much for me so I resolved the flickering screen by doing this from the prompt in recovery mode:

sudo apt-get clean all
sudo apt-get update
sudo apt-get install nvidia-glx

whereupon I was asked to choose from three versions. I chose the -96 option and did a reboot.

Now I've managed to get into the graphics mode but my resolution is stuck at a miserable 640x800 and I can only see about 3/4 of each window! The nVidia xserver settings don't detect my monitor :(

I know this is a third-party issue, but I'm just kinda starting out with Ubuntu.

---

### Post by Zoot7 on 2009-11-08
I got this issue when I installed Karmic on my home built desktop (which has an ATi HD4870), X wouldn't start at all.
Ctrl + Alt + F1 and using
```
sudo service gdm stop 
```
and
```
sudo service gdm start
```

Got it to work for me, since I installed the ATi driver, I haven't had the problem at all.

---

### Post by mr_gourami on 2009-11-08
I get that the nvidia driver screwed it up. I installed driver 173. so now i can't get past the flicker. But i can't figure out how yall keep saying boot in recovery mode. In grub if i select recovery mode i get a dos like selection menu, boot normal, make space, root with internet, root. If i try root i just get command line. 

I see i should install the nvidia driver but how? I don't have live cd, i do have flash drive boot. 

Computer is dual boot and i am on my xp side right now.

---

### Post by Subban on 2009-11-08
I just clean installed my PC after getting sick of errors and crash reports after a dist upgrade.

I ended up with the flashing screen with just the login prompt showing, keyboard very unpresonsive to typing making it impossible to enter a password. _I did find that repeatedly skipping between virtual terminals would eventually give you me a screen/login that didn't flash.. Use ctrl+alt+F1-6 to jump between virtual terminals and see if it works for you._

Soon as you get one that doesn't flash, log in as normal.

I proceeded to fix it with the solution offered on page 3 by Lapdog, basically download the nvidia 190.42 package and install it. I think I saw methods using wget also, they would use less typing, I just found it easier to remember the nvidia download address for ftp then navigate in ftp to the right package needed.

The only addition to Lapdogs solution using the "trick" to get a stable screen is before doing **./NVIDIA*.run** I had to do:
```
sudo service gdm stop
```

Then you can run the nvidia installer with **./NVIDIA*.run** and allow it to rewrite the xorg.conf.

---

### Post by necochino on 2009-11-08
Suffer the same blinking problem.  Tried just about everything offered in the forum as solution to no avail.  Re-imaged with Ubuntu, Xubuntu and Kubuntu, same issue.  Went back to Jaunty... same blinking issue !!!  Then tried Debian... oh boy... better go back to Ubuntu.  

The last several days have been a continuous nightmare.  I have two boxes where I ran MythTV and XBMC.  The one I'm working on is the master MythTV.  I can't record anything for the last week.  Now I'm trying a fresh Jaunty installation....

My boxes are Dell GX520 with 4GB RAM and 500GB HDD.  This one has a NVIDIA GS8400 512MB.  The other a NVIDIA GT9400 1GB. 

This time, to know that I'm not alone in this offers little consolation...

---

### Post by Amazona aestiva on 2009-11-08
Well, I wanted a clean install of Karmic, but unforunately even the live CD can't load gdm and falls back to a flickering shell. It is very hard but I can kill gdm and then it stops flickering.

Is there any way to install ubuntu from that terminal after I kill gdm?

---

### Post by necochino on 2009-11-08
I think I may have finally found the problem....

Found a posting with a reference to a conflict between NVIDIA and the Hauppage 1600 card (which I have).  Apparently the system tries to load both the NVIDIA and the CX18 drivers at the same time (?) causing the NVIDIA error.  A VM=256 (or something like that) in the start command in GRUB should fix it.

I have no more patience for this.  I removed the Hauppage card and presto !  NVIDIA driver works.  No more MythTV for me (I have DVRs anyway).

Jaunty did work.  I am now installing Karmic Koala (from CD) again.  The eternal masochist I am...

---

### Post by necochino on 2009-11-08
Success !!! Removing the Hauppage 1600 card did the trick.  I have now successfully installed Karmic Koala and the NVIDIA drivers.  Installed XBMC... everything works !!!

---

### Post by jc66 on 2009-11-09
Well done necochino on getting your system working! It seems like you had the same experience as me in finding that 'one last thing' that was keeping it broken.
 
Over the weekend the I installed the updated kernel (2.6.31-15) and found that it broke my system ***again*** with the same error - the kernel headers didn't load and so the nvida kernel module couldn't automatically build.
 
Luckily, now I know what my error was I could fix it quickly (simply installing the kernel header package triggered the nvidia drivers to build and it all worked) but it makes me wonder if any of the devs and package maintainers are watching these threads.
 
In addition to that I noticed that the appamour package that appeared in an update and installed itselt appears to also be broken, and seems to be slowing down the system startup by trying to access a mysql database which doesn't exist
 
I have had the same experience as someone else in this thread, I had previously encouraged a few freinds of mine to move to ubuntu, and now one of those is stuck with a broke system.
 
Putting all these things together, I would have to say that if anyone was asking me right now, I think my advice would be to install Jaunty, and to wait a month until hopefully this has all been fixed, and only then to try and upgrade.

---

### Post by golfdiesel on 2009-11-09
I have just downloaded the 9.10 live CD (AMD64 version) and it boots nicely and X is starting but then the top and bottom bars of the desktop (menu bar and the bottom bar) start flashing like mad and the PC is getting very slow in responding to key presses.
Sometimes I can get X to shutdown but I can't seem to be able to stop the flashing screen.

I have a Intel C2D E8500 processor on a MSI P35 platinum combo mainboard with a Nvidia 8600GTS PCI-E card.

---

### Post by thoughto on 2009-11-09
I have an nvidia gts 250, and I followed sunnyabc's advice:
sudo apt-get **[COLOR=#ff0000]install[/COLOR]** linux-headers-2.6.31-14-generic
sudo apt-get **[COLOR=#ff0000]install[/COLOR]** linux-headers-2.6.31-14-generic-pae
sudo apt-get **[COLOR=#ff0000]install[/COLOR]** --reinstall nvidia-glx-185
then startx and it worked. 
That was fantastic. The first and third line are definitely doing a lot, second line I don't know.
Don't give up if everything is flashing and hopeless looking. Go in in recovery mode with internet support, get the headers and driver you need, then x will work. If you have wifi and it is not working straight off try to connect by conventional network first. Once you can enter x-windows you'll be able to set up wireless.
Good luck!

---

### Post by jlr1701 on 2009-11-09
Well, it seems that every time I reboot, my system is broken again. I find myself back at the flashing cursor. This very serious bug is a deal-breaker for me. I'll be checking out Ultimate Edition, but it's based on Karmic, so I dunno.. we'll see...

Linux is great fun to play with and I would love to use it as my primary OS, but... in the end, I need a system that WORKS... and as much as I don't like MS, Windows does WORK, and Win 7 is very nice compared to the disaster that was Vista. Windows is not as  cool as Linux is, but nice.

I haven't had any issues with Ubuntu on my new Dell netbook... yet. So hopefully I can continue to enjoy the Linux world there. And hopefully Ultimate Edition will work out. Or maybe Linux Mint when Mint 8 comes out. But I am bidding Ubuntu itself goodbye, at least until the next hopefully much better and much less buggy release...

---

### Post by pmp on 2009-11-10
I got pass the similar symptoms by basically fixing the xorg.conf, see my experiences at:

[http://ubuntuforums.org/showthread.php?t=1315319](http://ubuntuforums.org/showthread.php?t=1315319)

---

### Post by MichealH on 2009-11-10
I had the same problem when I upgraded to the beta a month ago! But doesn't matter now I have the correct final version!

---

### Post by XanII on 2009-11-11
Now this one is a real show stopper problem. had the flashing screen and logon was impossible even if was able to produce a prompt that allowd me to type. typing speed was so out of synch that typing in the password was impossible as it is not visible as you type.

Used the tips on this thread to get nvidia drivers activated but couldnt get them to work no matter what. 173,186 or 190.42 series drivers all of them fail so right now it just ubuntu without proprietary drivers activated. 

And whats the deal with Grub2 installing? i got my system so unstable after 9.10 upgrade that i made a clean install (got / and /home separated so it's easy) whoops! grub2 is installed on clean install, it's liike messing up the upgrade on purpose and then booby trapping the clean install option.Luckily i have fought many battles with grub before so it took only a while to fix this. 

Restored the system now to almost what it was but i had to use a live-cd many times (usb stick). 

But i was lucky: i admin a whole bunch of computers at home & friends and luckily only one of them upgraded before me (she didnt use proprietary drivers so she was spared of all the trouble). Now we are in the 'lets wait for service pack2 -mode' here and 9.10 is banned until further notice. 

Good news also though: The system does boot faster now. though Grub2 uses more seconds to scan through the disks to time is wasted.

---

### Post by bt107 on 2009-11-11
I've been reading this thread with interest. I just did a clean install of Karmic on a machine with a nvidia GeForce4 MX chip. It works fine without the restricted driver (96) but only has 800x600 resolution. Installing the restricted driver from the repository causes a hard freeze up anywhere from the login screen to 2-3 minutes into the session. Anybody have any ideas what causes this?

---

### Post by jc66 on 2009-11-11
> **bt107 said:**
> I've been reading this thread with interest. I just did a clean install of Karmic on a machine with a nvidia GeForce4 MX chip. It works fine without the restricted driver (96) but only has 800x600 resolution. Installing the restricted driver from the repository causes a hard freeze up anywhere from the login screen to 2-3 minutes into the session. Anybody have any ideas what causes this?

If it is working without the restricted driver, then which driver is it using? 

If it is the vesa driver, then that might explain why you can go above 800x600 - in this case, try switching to the nv driver (you might need to load the xorg nivdia module for this.)

I liked the 2D results with this, but there is no 3D acceleration. On mine it detected all available resolutions, but if it doesn't on yours you can either try running some of various automatic setup programs, or else play about with adding modelines to your xorg.conf file - there are 100s of threads about doing this so just try searching on here.

Lockups are something different, try swapping drivers or watch out for things like screen savers kicking in.

---

### Post by amites on 2009-11-11
Nvidia 6200 LE Dual View working with the new Kernel following the previous instructions

download the latest Linux driver from Nvidia and install through safemode

still no sound but that's relatively minor (to fix atleast)

---

### Post by awwong on 2009-11-12
> **Amazona aestiva said:**
> Well, I wanted a clean install of Karmic, but unforunately even the live CD can't load gdm and falls back to a flickering shell. It is very hard but I can kill gdm and then it stops flickering.

Is there any way to install ubuntu from that terminal after I kill gdm?I have the same issue with the Live CD - slow burned and md5 checked.

My system is a Dell XPS 3.0 GHz, 2.0 GB RAM, nVidia GeForce 7600 GS.

---

### Post by wizzer on 2009-11-12
> **lapdog said:**
> Similar update experience:  got flashing text login screen on tty1 with normal bootup--no way to log in since most keystrokes did not register.  tty2 - 6 had the same flashing.  tty7 was blank.  With either "recovery mode" option, got to login but startx gave "screen not found" error, among others.

With the guidance of other posts here, I am now writing from a working 9.10 system.  Yeah!  Since my network connection was working and I apparently needed the latest nVidia driver, I did the following:

1.  Hit ESC after the BIOS loads (at the grub screen).

2.  Select the "recovery mode" with the later kernel:  2.6.31-14.  (The other choice I had was 2.6.28-16.)

3.  Login

4.  Pray that ftp will work and you can download from nVidia's site--necessary step!  don't skip!  :)

5.  ftp

[INDENT]6.  open download.nvidia.com

7.  for username, use:  guest

8.  for password, just press <Enter>

9.  cd XFree86
10. cd Linux-x86
11. cd 190.42

12. binary

13. get NVIDIA-Linux-x86-190.42-pkg1.run
    and wait for it to download; took about a minute for me

14. bye
[/INDENT]
15.  chmod 777 NVIDIA*

16.  sudo ./NVIDIA*.run

17.  Follow instructions in nVidia installation.  Remember to choose Yes when it asks if you want to replace current X config options.

18.  reboot

19.  Praise God with a prayer of thanksgiving when it works, and add a prayer of thanks for the Ubuntu community.


Boot up time for me is about the same, maybe a few seconds longer.  The new graphic defaults look cool and so far have been very fast and non-intrusive.

While I don't mind installing an extra file, getting a huge file onto a machine that doesn't boot correctly is a *major* source of stress.  Please, Ubuntu, put a message for nVidia users in big, bold type on your main 9.10 page saying the latest driver is needed.  Fetching this file beforehand would save a *lot* of trouble, as this thread shows.  This really is a serious issue that should not be present in a standard release.  (More than 40% with major problems?  Is that normal?)

Still don't have working sound or floppy, but nothing new there.  I saw a sound sticky...

On a positive note, thanks to the Ubuntu forum and community members for pointing me in the right direction!!!

---
mobo:  MSI K9N2GM-FIH (nVidia GeForce 8200); proc:  AMD Phenom X3 (AM2+) 8450; 4 Gig mem

:popcorn::popcorn::popcorn:     Thank you so much!!!!   Worked like a charm ;)

---

### Post by bt107 on 2009-11-12
> **jc66 said:**
> If it is working without the restricted driver, then which driver is it using? 

If it is the vesa driver, then that might explain why you can go above 800x600 - in this case, try switching to the nv driver (you might need to load the xorg nivdia module for this.)

I liked the 2D results with this, but there is no 3D acceleration. On mine it detected all available resolutions, but if it doesn't on yours you can either try running some of various automatic setup programs, or else play about with adding modelines to your xorg.conf file - there are 100s of threads about doing this so just try searching on here.

Lockups are something different, try swapping drivers or watch out for things like screen savers kicking in.

Thanks. I haven't tried the nv driver. I suspect there's some kind of conflict at the kernel level since it locks up solid. I've dumped the whole thing for now. I'll try again when a kernel update comes out.

---

### Post by CyberWind on 2009-11-12
Reinstalling NVidia drivers after adding their repository helps me in the same situation.

---

### Post by golfdiesel on 2009-11-12
But there is still no solution for the LiveCD, is there?

This is really a huge f*ck up from the part of Canonical... It would be a good gesture from them to put a notice on the website [www.ubuntu.com](www.ubuntu.com) that the current version is broken and that a new release will be made ASAP...

---

### Post by bgiannes on 2009-11-12
same here, Atom, ION PC (mythtv frontend).  no X just flashing login.  I ran out of time last night, and didn't try to fix it....  

Before the "upgrade" i was running 185 navida drivers, manual installed w/o problems.  Must be the kernel?

Thank god this didn't happen on my main server/mythtvbackend my wife would have killed me.

---

### Post by nilgiri on 2009-11-12
So, the blinking has been fixed as it was just a loop cause by gdm being restarted constantly.  There is a fix to the gdm package in the proposed repos and it should be released into main soon if it has not already.

That said, if you had the blinking, this means something was causing gdm to crash in the first place.  I get a "no screens found" error when I try startx and I have found no useful information for this error.  I found that text in Launchpad for one issue that affected some one calling himself Mark Shuttleworth (the real deal?).  It was bug causing confusion on dual head setups and has been fixed, but that does not apply to me.

Mine is an ATI Radeon 9600.  I did a clean 64-bit server install to setup RAID6 and then an *apt-get install ubuntu-desktop* to get the rest.  I doubt it has anything to do with using the server install disk or RAID6 because I also have to specify safe graphics mode to get a GUI desktop installer.

Of course, everything worked just fine under Jaunty, but I did a clean install since I wanted GRUB2 to boot off a RAID6 with ext4, 64-bit (was running 32-bit Jaunty for better Flash/Hulu), and because I have never had good luck with an upgrade.  Well, once, from hardy to intrepid on my work laptop.

Another thing worth noting was that I have seen a lot of talk and focus on changes to xorg.conf, but it does not exist on my system, or at least it is not in /etc/X11/ any more.  When I create one using *Xorg -configure* and put it there, I see no change.

Putting my Jaunty drives back in now.

---

### Post by golfdiesel on 2009-11-12
Now that they have found the bug, are they going to fix the livecd as well?

---

### Post by jerryscuba on 2009-11-14
I had a similar issue after upgrading my Mythbuntu. The fact that the Nvidia drivers could not get activated guided me to the solution. Installing the Nvidia drivers requires the headers. But since the kernel headers were installed I dug in a little deeper just to find out that I was still running on a old kernel version. It turned out that I answered the question wrong about what to do with menu.1st during installation. By keeping the old version grub loaded the old kernel. After uninstalling all old kernels and accepting the new menu.1st the system ran without a problem and I could activate the NVidia driver.

Hope that helps somebody.

JS

---

### Post by TaxAlien on 2009-11-14
I found myself in the same place as you all with my Nvidia card, but I eventually found that there was a way to reinstall Nvidia using synaptic. 

Assuming that you have started up in recovery mode, with root shell with networking, edit /etc/X11/xorg.conf and comment out the Nvidia driver:

> 
Section "Device"
    Identifier     "Configured Video Device"
    Option        "UseDisplayDevice" "DFP"
**#    Driver    "nvidia"**
    Option    "NoLogo"    "True"
EndSection


Then use "telinit 3" or startx to get up and running again.
I added the Nvidia 190 driver using their repository:

> 
sudo add-apt-repository ppa:nvidia-vdpau/ppa
sudo apt-get update
My current driver was 185 and I noticed that 190 would not install everything required when ticking the 190 driver. For some reason there is a lot of dependencies on the package **nvidia-185-libvdpau** as can be seen in my install log below. You need to manually remove it by selecting the equivalent 190 alongside the other 190 packages. It will then deinstall lots of stuff including amarok?! but the end result is that you get a clean install. When you then go into (3rd party) hardware drivers under administration you will find that the 190 driver is lightning up green again (available but not in use) or if not if you do select activate it should go green. If it doesn't then you are still not quite there and maybe there is something you missed or I overlooked in writing this guide... 

Logout from your hacked /etc/X11/xorg.conf session and restart with startx and everything is fine again (because the install or hardware drivers util will have fixed your xorg.conf automatically).

> 
2009-11-14 17:18:29 startup packages remove
2009-11-14 17:18:29 status installed amarok 2:2.2.0-0ubuntu2
2009-11-14 17:18:29 remove amarok 2:2.2.0-0ubuntu2 2:2.2.0-0ubuntu2
2009-11-14 17:18:29 status half-configured amarok 2:2.2.0-0ubuntu2
2009-11-14 17:18:29 status half-installed amarok 2:2.2.0-0ubuntu2
2009-11-14 17:18:29 status triggers-pending man-db 2.5.6-2
2009-11-14 17:18:29 status half-installed amarok 2:2.2.0-0ubuntu2
2009-11-14 17:18:29 status triggers-pending desktop-file-utils 0.15-2ubuntu1
2009-11-14 17:18:29 status half-installed amarok 2:2.2.0-0ubuntu2
2009-11-14 17:18:30 status triggers-pending libc-bin 2.10.1-0ubuntu15
2009-11-14 17:18:30 status config-files amarok 2:2.2.0-0ubuntu2
2009-11-14 17:18:30 status config-files amarok 2:2.2.0-0ubuntu2
2009-11-14 17:18:30 status installed kdemultimedia-kio-plugins 4:4.3.2-0ubuntu1
2009-11-14 17:18:30 remove kdemultimedia-kio-plugins 4:4.3.2-0ubuntu1 4:4.3.2-0ubuntu1
2009-11-14 17:18:30 status half-configured kdemultimedia-kio-plugins 4:4.3.2-0ubuntu1
2009-11-14 17:18:30 status half-installed kdemultimedia-kio-plugins 4:4.3.2-0ubuntu1
2009-11-14 17:18:30 status config-files kdemultimedia-kio-plugins 4:4.3.2-0ubuntu1
2009-11-14 17:18:30 status config-files kdemultimedia-kio-plugins 4:4.3.2-0ubuntu1
2009-11-14 17:18:30 status installed libkcddb4 4:4.3.2-0ubuntu1
2009-11-14 17:18:30 remove libkcddb4 4:4.3.2-0ubuntu1 4:4.3.2-0ubuntu1
2009-11-14 17:18:30 status half-configured libkcddb4 4:4.3.2-0ubuntu1
2009-11-14 17:18:30 status half-installed libkcddb4 4:4.3.2-0ubuntu1
2009-11-14 17:18:30 status config-files libkcddb4 4:4.3.2-0ubuntu1
2009-11-14 17:18:30 status config-files libkcddb4 4:4.3.2-0ubuntu1
2009-11-14 17:18:30 status installed khelpcenter4 4:4.3.2-0ubuntu4
2009-11-14 17:18:30 remove khelpcenter4 4:4.3.2-0ubuntu4 4:4.3.2-0ubuntu4
2009-11-14 17:18:30 status half-configured khelpcenter4 4:4.3.2-0ubuntu4
2009-11-14 17:18:30 status half-installed khelpcenter4 4:4.3.2-0ubuntu4
2009-11-14 17:18:30 status half-installed khelpcenter4 4:4.3.2-0ubuntu4
2009-11-14 17:18:30 status config-files khelpcenter4 4:4.3.2-0ubuntu4
2009-11-14 17:18:30 status config-files khelpcenter4 4:4.3.2-0ubuntu4
2009-11-14 17:18:30 status config-files khelpcenter4 4:4.3.2-0ubuntu4
2009-11-14 17:18:30 status config-files khelpcenter4 4:4.3.2-0ubuntu4
2009-11-14 17:18:30 status not-installed khelpcenter4 <none>
2009-11-14 17:18:30 status installed kdebase-runtime 4:4.3.2-0ubuntu4
2009-11-14 17:18:30 status installed kdebase-runtime-bin-kde4 4:4.3.2-0ubuntu4
2009-11-14 17:18:30 status installed miro 2.5.3-1ubuntu1
2009-11-14 17:18:30 remove miro 2.5.3-1ubuntu1 2.5.3-1ubuntu1
2009-11-14 17:18:30 status half-configured miro 2.5.3-1ubuntu1
2009-11-14 17:18:30 status triggers-pending python-support 1.0.3ubuntu1
2009-11-14 17:18:30 status half-installed miro 2.5.3-1ubuntu1
2009-11-14 17:18:31 status triggers-pending hicolor-icon-theme 0.10-2
2009-11-14 17:18:31 status half-installed miro 2.5.3-1ubuntu1
2009-11-14 17:18:31 status triggers-pending shared-mime-info 0.70-0ubuntu1
2009-11-14 17:18:31 status half-installed miro 2.5.3-1ubuntu1
2009-11-14 17:18:31 status half-installed miro 2.5.3-1ubuntu1
2009-11-14 17:18:31 status half-installed miro 2.5.3-1ubuntu1
2009-11-14 17:18:31 status config-files miro 2.5.3-1ubuntu1
2009-11-14 17:18:31 status config-files miro 2.5.3-1ubuntu1
2009-11-14 17:18:31 status installed phonon-backend-xine 4:4.3.1-4ubuntu1
2009-11-14 17:18:31 remove phonon-backend-xine 4:4.3.1-4ubuntu1 4:4.3.1-4ubuntu1
2009-11-14 17:18:31 status half-configured phonon-backend-xine 4:4.3.1-4ubuntu1
2009-11-14 17:18:31 status half-installed phonon-backend-xine 4:4.3.1-4ubuntu1
2009-11-14 17:18:31 status config-files phonon-backend-xine 4:4.3.1-4ubuntu1
2009-11-14 17:18:31 status config-files phonon-backend-xine 4:4.3.1-4ubuntu1
2009-11-14 17:18:31 status config-files phonon-backend-xine 4:4.3.1-4ubuntu1
2009-11-14 17:18:31 status not-installed phonon-backend-xine <none>
2009-11-14 17:18:31 status installed libxine1 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed libxine1-x 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed libxine1-plugins 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 remove libxine1-plugins 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status half-configured libxine1-plugins 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status half-installed libxine1-plugins 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status config-files libxine1-plugins 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status config-files libxine1-plugins 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status config-files libxine1-plugins 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status not-installed libxine1-plugins <none>
2009-11-14 17:18:31 status installed libxine1-misc-plugins 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed libxine1-ffmpeg 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 remove libxine1-ffmpeg 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status half-configured libxine1-ffmpeg 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status half-installed libxine1-ffmpeg 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status config-files libxine1-ffmpeg 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status config-files libxine1-ffmpeg 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status config-files libxine1-ffmpeg 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status not-installed libxine1-ffmpeg <none>
2009-11-14 17:18:31 status installed libxine1-console 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed libxine1-bin 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed nvidia-185-libvdpau 185.18.36-0ubuntu9
2009-11-14 17:18:31 status installed nvidia-settings 180.25-0ubuntu1
2009-11-14 17:18:31 remove nvidia-settings 180.25-0ubuntu1 180.25-0ubuntu1
2009-11-14 17:18:31 status half-configured nvidia-settings 180.25-0ubuntu1
2009-11-14 17:18:31 status half-installed nvidia-settings 180.25-0ubuntu1
2009-11-14 17:18:31 status half-installed nvidia-settings 180.25-0ubuntu1
2009-11-14 17:18:31 status half-installed nvidia-settings 180.25-0ubuntu1
2009-11-14 17:18:31 status config-files nvidia-settings 180.25-0ubuntu1
2009-11-14 17:18:31 status config-files nvidia-settings 180.25-0ubuntu1
2009-11-14 17:18:31 status installed kdebase-runtime 4:4.3.2-0ubuntu4
2009-11-14 17:18:31 status installed kdebase-runtime-bin-kde4 4:4.3.2-0ubuntu4
2009-11-14 17:18:31 status installed libxine1 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed libxine1-x 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed libxine1-misc-plugins 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed libxine1-console 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed libxine1-bin 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed nvidia-185-libvdpau 185.18.36-0ubuntu9
2009-11-14 17:18:31 status installed kdebase-runtime 4:4.3.2-0ubuntu4
2009-11-14 17:18:31 status installed kdebase-runtime-bin-kde4 4:4.3.2-0ubuntu4
2009-11-14 17:18:31 status installed libxine1 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed libxine1-x 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed libxine1-misc-plugins 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed libxine1-console 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed libxine1-bin 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed nvidia-185-libvdpau 185.18.36-0ubuntu9
2009-11-14 17:18:31 status installed kdebase-runtime 4:4.3.2-0ubuntu4
2009-11-14 17:18:31 status installed kdebase-runtime-bin-kde4 4:4.3.2-0ubuntu4
2009-11-14 17:18:31 status installed libxine1 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed libxine1-x 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed libxine1-misc-plugins 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed libxine1-console 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed libxine1-bin 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed nvidia-185-libvdpau 185.18.36-0ubuntu9
2009-11-14 17:18:31 status installed kdebase-runtime 4:4.3.2-0ubuntu4
2009-11-14 17:18:31 status installed kdebase-runtime-bin-kde4 4:4.3.2-0ubuntu4
2009-11-14 17:18:31 status installed libxine1 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed libxine1-x 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed libxine1-misc-plugins 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed libxine1-console 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed libxine1-bin 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed nvidia-185-libvdpau 185.18.36-0ubuntu9
2009-11-14 17:18:31 status installed kdebase-runtime 4:4.3.2-0ubuntu4
2009-11-14 17:18:31 status installed kdebase-runtime-bin-kde4 4:4.3.2-0ubuntu4
2009-11-14 17:18:31 status installed libxine1 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed libxine1-x 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed libxine1-misc-plugins 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed libxine1-console 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed libxine1-bin 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed nvidia-185-libvdpau 185.18.36-0ubuntu9
2009-11-14 17:18:31 status installed kdebase-runtime 4:4.3.2-0ubuntu4
2009-11-14 17:18:31 status installed kdebase-runtime-bin-kde4 4:4.3.2-0ubuntu4
2009-11-14 17:18:31 status installed libxine1 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed libxine1-x 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed libxine1-misc-plugins 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed libxine1-console 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed libxine1-bin 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed nvidia-185-libvdpau 185.18.36-0ubuntu9
2009-11-14 17:18:31 status installed kdebase-runtime 4:4.3.2-0ubuntu4
2009-11-14 17:18:31 status installed kdebase-runtime-bin-kde4 4:4.3.2-0ubuntu4
2009-11-14 17:18:31 status installed libxine1 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed libxine1-x 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed libxine1-misc-plugins 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed libxine1-console 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed libxine1-bin 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:31 status installed nvidia-185-libvdpau 185.18.36-0ubuntu9
2009-11-14 17:18:31 status installed kdebase-runtime 4:4.3.2-0ubuntu4
2009-11-14 17:18:31 status installed kdebase-runtime-bin-kde4 4:4.3.2-0ubuntu4
2009-11-14 17:18:32 status installed libxine1 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 status installed libxine1-x 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 status installed libxine1-misc-plugins 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 status installed libxine1-console 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 status installed libxine1-bin 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 status installed nvidia-185-libvdpau 185.18.36-0ubuntu9
2009-11-14 17:18:32 status installed kdebase-runtime 4:4.3.2-0ubuntu4
2009-11-14 17:18:32 remove kdebase-runtime 4:4.3.2-0ubuntu4 4:4.3.2-0ubuntu4
2009-11-14 17:18:32 status half-configured kdebase-runtime 4:4.3.2-0ubuntu4
2009-11-14 17:18:32 update-alternatives: run with --remove kdesu /usr/lib/kde4/libexec/kdesu-distrib/kdesu
2009-11-14 17:18:32 update-alternatives: link group kdesu fully removed
2009-11-14 17:18:32 status half-installed kdebase-runtime 4:4.3.2-0ubuntu4
2009-11-14 17:18:32 status half-installed kdebase-runtime 4:4.3.2-0ubuntu4
2009-11-14 17:18:32 status config-files kdebase-runtime 4:4.3.2-0ubuntu4
2009-11-14 17:18:32 status config-files kdebase-runtime 4:4.3.2-0ubuntu4
2009-11-14 17:18:32 status installed kdebase-runtime-bin-kde4 4:4.3.2-0ubuntu4
2009-11-14 17:18:32 remove kdebase-runtime-bin-kde4 4:4.3.2-0ubuntu4 4:4.3.2-0ubuntu4
2009-11-14 17:18:32 status half-configured kdebase-runtime-bin-kde4 4:4.3.2-0ubuntu4
2009-11-14 17:18:32 status half-installed kdebase-runtime-bin-kde4 4:4.3.2-0ubuntu4
2009-11-14 17:18:32 status config-files kdebase-runtime-bin-kde4 4:4.3.2-0ubuntu4
2009-11-14 17:18:32 status config-files kdebase-runtime-bin-kde4 4:4.3.2-0ubuntu4
2009-11-14 17:18:32 status config-files kdebase-runtime-bin-kde4 4:4.3.2-0ubuntu4
2009-11-14 17:18:32 status not-installed kdebase-runtime-bin-kde4 <none>
2009-11-14 17:18:32 status installed libxine1 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 remove libxine1 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 status half-configured libxine1 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 status half-installed libxine1 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 status config-files libxine1 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 status config-files libxine1 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 status config-files libxine1 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 status not-installed libxine1 <none>
2009-11-14 17:18:32 status installed libxine1-x 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 remove libxine1-x 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 status half-configured libxine1-x 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 status half-installed libxine1-x 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 status config-files libxine1-x 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 status config-files libxine1-x 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 status config-files libxine1-x 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 status not-installed libxine1-x <none>
2009-11-14 17:18:32 status installed libxine1-misc-plugins 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 remove libxine1-misc-plugins 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 status half-configured libxine1-misc-plugins 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 status half-installed libxine1-misc-plugins 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 status config-files libxine1-misc-plugins 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 status config-files libxine1-misc-plugins 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 status config-files libxine1-misc-plugins 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 status not-installed libxine1-misc-plugins <none>
2009-11-14 17:18:32 status installed libxine1-console 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 remove libxine1-console 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 status half-configured libxine1-console 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 status half-installed libxine1-console 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 status config-files libxine1-console 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 status config-files libxine1-console 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 status config-files libxine1-console 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 status not-installed libxine1-console <none>
2009-11-14 17:18:32 status installed libxine1-bin 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 remove libxine1-bin 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 status half-configured libxine1-bin 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 status half-installed libxine1-bin 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 status half-installed libxine1-bin 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 status config-files libxine1-bin 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 status config-files libxine1-bin 1.1.16.3-0ubuntu2~xine-vdpau~karmic~nvidiavdpauppa1
2009-11-14 17:18:32 status installed nvidia-185-libvdpau 185.18.36-0ubuntu9
**2009-11-14 17:18:32 remove nvidia-185-libvdpau 185.18.36-0ubuntu9 185.18.36-0ubuntu9**
2009-11-14 17:18:32 status half-configured nvidia-185-libvdpau 185.18.36-0ubuntu9
2009-11-14 17:18:32 status half-installed nvidia-185-libvdpau 185.18.36-0ubuntu9
2009-11-14 17:18:32 status config-files nvidia-185-libvdpau 185.18.36-0ubuntu9
2009-11-14 17:18:32 status config-files nvidia-185-libvdpau 185.18.36-0ubuntu9
2009-11-14 17:18:32 trigproc man-db 2.5.6-2 2.5.6-2
2009-11-14 17:18:32 status half-configured man-db 2.5.6-2
2009-11-14 17:18:32 status installed man-db 2.5.6-2
2009-11-14 17:18:32 trigproc desktop-file-utils 0.15-2ubuntu1 0.15-2ubuntu1
2009-11-14 17:18:32 status half-configured desktop-file-utils 0.15-2ubuntu1
2009-11-14 17:18:32 status installed desktop-file-utils 0.15-2ubuntu1
2009-11-14 17:18:32 trigproc libc-bin 2.10.1-0ubuntu15 2.10.1-0ubuntu15
2009-11-14 17:18:32 status half-configured libc-bin 2.10.1-0ubuntu15
2009-11-14 17:18:33 status installed libc-bin 2.10.1-0ubuntu15
2009-11-14 17:18:33 trigproc python-support 1.0.3ubuntu1 1.0.3ubuntu1
2009-11-14 17:18:33 status half-configured python-support 1.0.3ubuntu1
2009-11-14 17:18:35 status installed python-support 1.0.3ubuntu1
2009-11-14 17:18:35 trigproc hicolor-icon-theme 0.10-2 0.10-2
2009-11-14 17:18:35 status half-configured hicolor-icon-theme 0.10-2
2009-11-14 17:18:36 status installed hicolor-icon-theme 0.10-2
2009-11-14 17:18:36 trigproc shared-mime-info 0.70-0ubuntu1 0.70-0ubuntu1
2009-11-14 17:18:36 status half-configured shared-mime-info 0.70-0ubuntu1
2009-11-14 17:18:37 status installed shared-mime-info 0.70-0ubuntu1
2009-11-14 17:18:38 startup archives unpack
2009-11-14 17:18:38 install nvidia-190-libvdpau <none> 190.42-0ubuntu1~karmic~nvidiavdpauppa2
2009-11-14 17:18:38 status half-installed nvidia-190-libvdpau 190.42-0ubuntu1~karmic~nvidiavdpauppa2
2009-11-14 17:18:38 status unpacked nvidia-190-libvdpau 190.42-0ubuntu1~karmic~nvidiavdpauppa2
2009-11-14 17:18:38 status unpacked nvidia-190-libvdpau 190.42-0ubuntu1~karmic~nvidiavdpauppa2
2009-11-14 17:18:38 install nvidia-190-libvdpau-dev <none> 190.42-0ubuntu1~karmic~nvidiavdpauppa2
2009-11-14 17:18:38 status half-installed nvidia-190-libvdpau-dev 190.42-0ubuntu1~karmic~nvidiavdpauppa2
2009-11-14 17:18:38 status unpacked nvidia-190-libvdpau-dev 190.42-0ubuntu1~karmic~nvidiavdpauppa2
2009-11-14 17:18:38 status unpacked nvidia-190-libvdpau-dev 190.42-0ubuntu1~karmic~nvidiavdpauppa2
2009-11-14 17:18:38 install nvidia-190-modaliases <none> 190.42-0ubuntu1~karmic~nvidiavdpauppa2
2009-11-14 17:18:38 status half-installed nvidia-190-modaliases 190.42-0ubuntu1~karmic~nvidiavdpauppa2
2009-11-14 17:18:38 status unpacked nvidia-190-modaliases 190.42-0ubuntu1~karmic~nvidiavdpauppa2
2009-11-14 17:18:38 status unpacked nvidia-190-modaliases 190.42-0ubuntu1~karmic~nvidiavdpauppa2
2009-11-14 17:18:38 install nvidia-glx-190 <none> 190.42-0ubuntu1~karmic~nvidiavdpauppa2
2009-11-14 17:18:38 status half-installed nvidia-glx-190 190.42-0ubuntu1~karmic~nvidiavdpauppa2
2009-11-14 17:18:43 status triggers-pending desktop-file-utils 0.15-2ubuntu1
2009-11-14 17:18:43 status half-installed nvidia-glx-190 190.42-0ubuntu1~karmic~nvidiavdpauppa2
2009-11-14 17:18:43 status triggers-pending man-db 2.5.6-2
2009-11-14 17:18:43 status half-installed nvidia-glx-190 190.42-0ubuntu1~karmic~nvidiavdpauppa2
2009-11-14 17:18:44 status unpacked nvidia-glx-190 190.42-0ubuntu1~karmic~nvidiavdpauppa2
2009-11-14 17:18:44 status unpacked nvidia-glx-190 190.42-0ubuntu1~karmic~nvidiavdpauppa2
2009-11-14 17:18:44 install nvidia-settings-190 <none> 190.32-0ubuntu1~karmic~nvidiavdpauppa1
2009-11-14 17:18:44 status half-installed nvidia-settings-190 190.32-0ubuntu1~karmic~nvidiavdpauppa1
2009-11-14 17:18:44 status half-installed nvidia-settings-190 190.32-0ubuntu1~karmic~nvidiavdpauppa1
2009-11-14 17:18:44 status half-installed nvidia-settings-190 190.32-0ubuntu1~karmic~nvidiavdpauppa1
2009-11-14 17:18:44 status unpacked nvidia-settings-190 190.32-0ubuntu1~karmic~nvidiavdpauppa1
2009-11-14 17:18:44 status unpacked nvidia-settings-190 190.32-0ubuntu1~karmic~nvidiavdpauppa1
2009-11-14 17:18:44 trigproc desktop-file-utils 0.15-2ubuntu1 0.15-2ubuntu1
2009-11-14 17:18:44 status half-configured desktop-file-utils 0.15-2ubuntu1
2009-11-14 17:18:44 status installed desktop-file-utils 0.15-2ubuntu1
2009-11-14 17:18:44 trigproc man-db 2.5.6-2 2.5.6-2
2009-11-14 17:18:44 status half-configured man-db 2.5.6-2
2009-11-14 17:18:44 status installed man-db 2.5.6-2
2009-11-14 17:18:45 startup packages configure
2009-11-14 17:18:45 configure nvidia-190-libvdpau 190.42-0ubuntu1~karmic~nvidiavdpauppa2 190.42-0ubuntu1~karmic~nvidiavdpauppa2
2009-11-14 17:18:45 status unpacked nvidia-190-libvdpau 190.42-0ubuntu1~karmic~nvidiavdpauppa2
2009-11-14 17:18:45 status half-configured nvidia-190-libvdpau 190.42-0ubuntu1~karmic~nvidiavdpauppa2
2009-11-14 17:18:45 status installed nvidia-190-libvdpau 190.42-0ubuntu1~karmic~nvidiavdpauppa2
2009-11-14 17:18:45 status triggers-pending libc-bin 2.10.1-0ubuntu15
2009-11-14 17:18:45 configure nvidia-190-libvdpau-dev 190.42-0ubuntu1~karmic~nvidiavdpauppa2 190.42-0ubuntu1~karmic~nvidiavdpauppa2
2009-11-14 17:18:45 status unpacked nvidia-190-libvdpau-dev 190.42-0ubuntu1~karmic~nvidiavdpauppa2
2009-11-14 17:18:45 status half-configured nvidia-190-libvdpau-dev 190.42-0ubuntu1~karmic~nvidiavdpauppa2
2009-11-14 17:18:45 status installed nvidia-190-libvdpau-dev 190.42-0ubuntu1~karmic~nvidiavdpauppa2
2009-11-14 17:18:45 configure nvidia-190-modaliases 190.42-0ubuntu1~karmic~nvidiavdpauppa2 190.42-0ubuntu1~karmic~nvidiavdpauppa2
2009-11-14 17:18:45 status unpacked nvidia-190-modaliases 190.42-0ubuntu1~karmic~nvidiavdpauppa2
2009-11-14 17:18:45 status half-configured nvidia-190-modaliases 190.42-0ubuntu1~karmic~nvidiavdpauppa2
2009-11-14 17:18:45 status installed nvidia-190-modaliases 190.42-0ubuntu1~karmic~nvidiavdpauppa2
2009-11-14 17:18:45 configure nvidia-glx-190 190.42-0ubuntu1~karmic~nvidiavdpauppa2 190.42-0ubuntu1~karmic~nvidiavdpauppa2
2009-11-14 17:18:45 status unpacked nvidia-glx-190 190.42-0ubuntu1~karmic~nvidiavdpauppa2
2009-11-14 17:18:45 status half-configured nvidia-glx-190 190.42-0ubuntu1~karmic~nvidiavdpauppa2
2009-11-14 17:18:46 status installed nvidia-glx-190 190.42-0ubuntu1~karmic~nvidiavdpauppa2
2009-11-14 17:18:46 configure nvidia-settings-190 190.32-0ubuntu1~karmic~nvidiavdpauppa1 190.32-0ubuntu1~karmic~nvidiavdpauppa1
2009-11-14 17:18:46 status unpacked nvidia-settings-190 190.32-0ubuntu1~karmic~nvidiavdpauppa1
2009-11-14 17:18:46 status half-configured nvidia-settings-190 190.32-0ubuntu1~karmic~nvidiavdpauppa1
2009-11-14 17:18:46 status installed nvidia-settings-190 190.32-0ubuntu1~karmic~nvidiavdpauppa1
2009-11-14 17:18:46 trigproc libc-bin 2.10.1-0ubuntu15 2.10.1-0ubuntu15
2009-11-14 17:18:46 status half-configured libc-bin 2.10.1-0ubuntu15
2009-11-14 17:18:46 status installed libc-bin 2.10.1-0ubuntu15


---

### Post by TaxAlien on 2009-11-14
Oh and if you do what I wrote above you get Nvidia working but you can forget amarok et al because someone put a dependency like:

libxine1-bin:
 Depends: nvidia-185-libvdpau but it is not going to be installed

Is this the real bug in this whole glorious mess?

---

### Post by TaxAlien on 2009-11-14
> **TaxAlien said:**
> Oh and if you do what I wrote above you get Nvidia working but you can forget amarok et al because someone put a dependency like:

libxine1-bin:
 Depends: nvidia-185-libvdpau but it is not going to be installed

Is this the real bug in this whole glorious mess?

Actually, not quite so bad. It can be fixed too.

There appears to be two version of libxine stuff, the rotten one is 1.1.16.3-0ubuntu2.... whereas the good one is 1.1.16.3-0ubuntu4. For some reason synaptic insists the 0ubuntu2 version is newer than 0ubuntu4 (I am on AMD64).

If you select Package->Force Version you can circumvent this for those packages and then try to load the kdemultimedia-kio-plugins. Check everytime that you haven't missed anything because if you do it will uninstall 190 and replace it with 185 which I don't think works at all.

---

### Post by kb3lja on 2009-11-14
> **luinav said:**
> Hi all,

I had the same issue with a Silicon Integrated Systems card.

I booted in the recovery mode and moved xorg.conf to xorg.conf.old. Then rebooted again and the problem solved.

Just my two cents.

Regards,
Luis Miguel Navas
Moving the config file and rebooting worked.  I had flickerring login when I installed nvidia 185 over 96.  I removed the 185 under recovery mode and still had the issue.
When I moved the config file, the system booted normally.

---

### Post by bgiannes on 2009-11-14
oh man...  i can't get a shell, even in recovery mode :( 

if i try a fresh install will i just end up in the same place?

---

### Post by billykendall on 2009-11-14
ok so I have read through this entire thread and tried just about everything suggested here and I am still not able to log back into my Ubuntu Desktop and I am about to pull my hair out!!  I'm pretty sure this all happened as a result of installing Amarok through the Software Center.  I have no idea how to fix this one so...

Can anyone please try to help me get this resolved? I really don't wanna lose my current install because I had it setup so nicely.

Here is my scenario...Before I installed Amarok I was using Nvidia 190.42 drivers on Ubuntu 9.10 and everything was working great.  Now what exactly happened as a result of installing Amarok I do not know, but I can tell you that everything was working great prior to that install.  Now I get the blinking login command prompt.  Like I said before, I have tried everything in this thread but nothing is working for me. 

PLEASE HELP! :(

---

### Post by billykendall on 2009-11-15
ok so I kept at it (7 hours of trouble shooting) and FINALLY got it fixed!!  What I conclude is that when I installed Amarok from the new Ubuntu Software Center it replaced my nvidia 190 drivers with the nvidia 185 drivers and that is when the problem started somehow.  Upon my first reboot after the Amarok install I started getting the blinking login prompt.

What ended up working for me in the end was to remove the 185 drivers and reinstall the 190 drivers, but the xorg.conf file gave me a LOT of problems.  I tried using the .run package from nvidia.com and I let it build a new xorg.conf file for me but all I would get was a plain black screen. I ran apt-get to grab the 190 drivers from the Nvidia Vdpau Team PPA & then tried using some old backup xorg.conf files I have in /etc/X11 but that seemed to put me back into the blinking tty1 login prompt.  I tried replacing xorg.conf with xorg.conf.failsafe but I kept getting "Out of Range" errors from my monitor with that xorg setup.  I pretty much isolated it down to some sort of problem with my xorg.conf file but could not figure out how to work it out.  I finally stumbled across a command that ended up fixing it all for me!! ```
sudo nvidia-xconfig
``` that simple command built me a nice new WORKING xorg.conf file and got me back into my desktop!

:popcorn::popcorn::popcorn:

I'm happy again!

---

### Post by von Stalhein on 2009-11-15
> **fasmike said:**
> I was not on a network, so I had some trouble doing exactly what you said above, but your method did work, thanks!  This is what I did:


This made the flickering login problem go away and allowed me to get in and start using Ubuntu on my new machine.

> **lapdog said:**
> Similar update experience:  got flashing text login screen on tty1 with normal bootup--no way to log in since most keystrokes did not register.  tty2 - 6 had the same flashing.  tty7 was blank.  With either "recovery mode" option, got to login but startx gave "screen not found" error, among others.

With the guidance of other posts here, I am now writing from a working 9.10 system.  Yeah!  Since my network connection was working and I apparently needed the latest nVidia driver, I did the following:


Bloody beauty you blokes :p :p :p

I've spent nearly 3 days trying to sort this one problem - big thanks!!!

---

### Post by blue_bullet on 2009-11-15
> **golfdiesel said:**
> Now that they have found the bug, are they going to fix the livecd as well?

I guess I missed the answer to your question.  Is there anyone out there prepared to fix the unholy mess created by Canonical?  sudo fdisk -l shows 2 partitions not ending on cylinder boundaries for my internal hd and same for one partition on my exteral hd.  External hd is only used for weekly backups and a small ntfs partition used with virtualbox windows xp.  I can only boot to kernel 2.6.28-16.  File system cannot be mounted in 2.6.31-14 I suspect b/c of the partition problem.  I do not know how to fix the partition problem which I suspect was created during the upgrade process to 9.10. 
  
> rob@fargo:~$ sudo fdisk -l
[sudo] password for rob: 

Disk /dev/sda: 249 GB, 249999160320 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8         269     2096482    b  FAT32
/dev/sda3   *         270         294      192780   83  Linux
/dev/sda4             295       30394   241770217    f  Extended LBA
/dev/sda5             295         616     2578432   82  Linux swap
Warning: Partition 5 does not end on cylinder boundary.
/dev/sda6             617       30394   239183752   83  Linux
Warning: Partition 6 does not end on cylinder boundary.

Disk /dev/sdb: 750 GB, 750153761280 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb2               1       86050   691188592   83  Linux
/dev/sdb1           86051       91201   729861426    5  Extended
/dev/sdb5           86051       91201    41367375    7  HPFS/NTFS
Warning: Partition 5 does not end on cylinder boundary.


I cannot boot from the liveCD.  I downloaded another yesterday in case things had changed.  The liveCD leaves me with a screen full of flickering vertical bars where I would expect an opportunity to login.
 
I have perused many threads for 2 weeks now assuming answers would be forthcoming.  I am now completely confused and do not know whether to try a complete install of 9.04 or to move on to some other linux distribution.  I have used Ubuntu since 8.04 and have been quite happy.  This distribution is the worst I have experienced both in terms of problems and adequate responses to fixing them.       

I have been limping along w/o sound using the old kernel for 2 weeks now expecting some solutions to be forthcoming on this thread and others.  Nothing so far.  I guess we are seeing the downside of "free" from Ubuntu developers.  The silence and lack of response along with major articles chastizing the developers for this release (bad for linux) is not confidence inspiring.  Certainly not to would be converts from windows.

People are getting frustrated.  Flame away.

---

### Post by blue_bullet on 2009-11-15
A followup .I don't want to sound like sour grapes or whine a lot.  I am simply frustrated and confused.  Here's more to explain.

I installed (upgraded) 9.10 on my Dell Inspiron 1420 laptop with only one hitch.  My Sonos desktop controller no longer runs in wine.  It worked fine in 9.04.

I installed (upgraded) 9.10 on my Dell XPS 410 desktop with many hitches.  However, the Sonos desktop controller now runs in wine whereas it did NOT run on my desktop under 9.04. Now what is that all about?  Begin to see my confusion and frustration?

So when I answer the poll which you only get to answer once I told it I had major problems.  In fact I had a positive experience on the laptop and a very negative experience on the desktop.  Then we are advised that such polls are useless as there is a bias to those having problems in that those who install w/o a hitch are apt not to respond.  Then either conduct the poll differently or don't do it at all.  Come folks show a little competence. I will volunteer to the community to construct polls in the future that attempt to remove bias and also attempt to capture at least that one declined to participate in a poll.  That way you can present meaningful statistics.

---

### Post by mr_gourami on 2009-11-15
Still have issue.
i removed the nvidia card. I had installed 183 driver.
how do i fix?

I can access recovery mode and use a command line.

---

### Post by sarion on 2009-11-16
Great, I can use my system (with an ATI Radeon 2100) again! Thanks for the tips, everyone!

I added i915.modeset=0 in Grub, and got a terminal. Then I moved xorg.conf to xorg.conf.old and then rebooted. After that, Karmic was up and running! Then managed to install the proprietaty driver, and now everything works just fine! :-)

---

### Post by jstierman on 2009-11-16
Same problem.  Though mine may be my fault, since I had done the [downgrade to Intrepid xserver & xorg files to get an older ATI proprietary driver to work]("http://ubuntuforums.org/showthread.php?t=1252015").

Anyways, from root (recovery mode) I just copied my xorg.conf.bak (backup file I made before messing with stuff in 9.04) to xorg.conf

My working xorg.conf has code:
```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```Now I can boot to the desktop.  I have ATI x700 mobility.

---

### Post by Flymo on 2009-11-16
> **Jekshadow said:**
> .... seemed to boot fine, until it got to where the login screen should be showing. It flickered a lot, and only showed the command line login screen..

We got this on a new Athlon II X2 240 desktop using an MSI K9N6PGM2 MoBo.  Just a vanilla Karmic installation, never able to get to a login. :oops:

But.....  Xubuntu Karmic loaded fine, booted fast, and I'm using it now!

Go figure.... :confused:

Still, we rather like XFCE. 

All the best, Ben

---

### Post by bgiannes on 2009-11-16
i ended up installing mythbuntu,(which i would almost never do, but i couldn't get a shell!) and when i got to the gl drive bit i installed the opensource GL drivers; and all is well.

---

### Post by parkland on 2009-11-16
I think I have this issue.

The entire OS (9.10) seems buggy, laggy, disk errors, graphics defaulting or not showing desktop, and being a POS in general.

Is there a fix, or not? 

What a weird and serious issue!

---

### Post by alan_tam_sh on 2009-11-17
I have been using Ubuntu on my desktop since version 6.04 but none of the versions so far were so buggy then the 9.10.
Comes to nVidia card issue despite many attempts to solve/trouble shoot/uninstall this reinstall that, the nVidia graphic card driver simply don't work!

The problem seems here to stay for long times, I give up!

Ubuntu 9.10 Sucks!

---

### Post by parkland on 2009-11-17
> **alan_tam_sh said:**
> I have been using Ubuntu on my desktop since version 6.04 but none of the versions so far were so buggy then the 9.10.
Comes to nVidia card issue despite many attempts to solve/trouble shoot/uninstall this reinstall that, the nVidia graphic card driver simply don't work!

The problem seems here to stay for long times, I give up!

Ubuntu 9.10 Sucks!

Well, thats a little extreme!

Lets remember what kind of ground breaking changes and innovations are implemented in 9.10. This is not like programming a game of solitaire or something. 

While I am personally disappointed at the moment, and frustrated, and on my 5th night without watching movies in my living room, I am trying again. Maybe ext4 should have been an install OPTION, and not the install DEFAULT.

Dunno, but I sure hope I can get mine going tonight, or 9.04 might be going back on.

---

### Post by parkland on 2009-11-17
OK, 

I've got it running again, but theres all kinds of disk errors.
I see it failed to mount filesystem, failed "something" with swap partition, "inode" errors, stuff going into lost & found,

WTF!

This is with a fresh install, updated, no crashes, and nothing even done to it! The only thing I've done is installed ubuntu on a fresh wiped disk, which was just spinrited! (I then copied 400 700mb movies onto the disk)

What is wrong with EXT4, or is this something else? I fail to see what I've done to deserve this from the filesystem! Does it hate me? 

I don't know what else to try, it is currently running, but every 2nd reboot it has issues, and after playing one of my movies, firefox hangs, even the shutdown menu appears, but is empty, and then more filesystem damage!

---

### Post by alan_tam_sh on 2009-11-17
> **parkland said:**
> OK, 

I've got it running again, but theres all kinds of disk errors.
I see it failed to mount filesystem, failed "something" with swap partition, "inode" errors, stuff going into lost & found,

WTF!

This is with a fresh install, updated, no crashes, and nothing even done to it! The only thing I've done is installed ubuntu on a fresh wiped disk, which was just spinrited! (I then copied 400 700mb movies onto the disk)

What is wrong with EXT4, or is this something else? I fail to see what I've done to deserve this from the filesystem! Does it hate me? 

I don't know what else to try, it is currently running, but every 2nd reboot it has issues, and after playing one of my movies, firefox hangs, even the shutdown menu appears, but is empty, and then more filesystem damage!

Well, did you try going back to 9.04?
I actually tried a clean 9.04 installation guess what happen to me? I get the same blank flickering screen just like 9.10 at booting!! I am using nVidia geForce4 card btw, before i update my 9.04, my PC works so well and cool and happy with it. Now I am so regret upgrading it, where i will never get it back again. Worst i did not see if this bug has been reported!
So, guys i will try to resolve the problem one more time tonight after that if things dont improve then my last resource is to delete the entire partition and forget about Ubuntu. However this does not make me go back fall in love with MS..it just make me feel very disappointed with ubuntu for such a lousy release.

---

### Post by sauma on 2009-11-18
> **dodgy69 said:**
> I'm a newbie to Linux, and I had a hard time following the above instructions. I had the same problem but couldn't follow a lot of the technical stuff. If you're like me and you need a more "Linux for dummies" approach, here's how I got it to work, newbie-friendly style:

HOW TO UPGRADE YOUR NVIDIA DRIVER - For Linux dummies like me

1. Go to the NVIDIA site and download [this driver]("http://www.nvidia.com/object/linux_display_ia32_190.42.html") to your 'HOME' directory.
2. Go to your HOME directory and RIGHT CLICK on the driver package ("NVIDIA-Linux-x86-190.42-pkg1.run")
3. Select PROPERTIES. Select PERMISSIONS tab. MaKe sure first dropdown menu says "Read and Write". Check box that says "Allow executing file as program"
4. Reboot your system. At the boot menu, select 2.6.31 kernel - safe mode.
5. You'll come to a menu. Select "Continue boot" (or something like that)
6. A command line will prompt you for your login name and password. Enter them.
7. You'll come to a terminal line. Enter this:   sudo ./NVIDIA*.run
8. The NVIDIA install manager should run and update your driver. 
9. Reboot your system. The new kernel should work.


After three or four days of headaches and confusion, this is all I needed to do. I love you.

---

### Post by jcxaver on 2009-11-18
> **sauma said:**
> After three or four days of headaches and confusion, this is all I needed to do. I love you.

congratulation :)

It works not on my vaio, still the black flickering screen..

---

### Post by tomcatUK on 2009-11-18
I've just spent 4 days trying and finally succeeding getting both Ubuntu 9.0.4 desktop and server working. There was a common show stopper, a blank screen on both, but caused by a variety of different and sequence of causes. My desktop install was on an E system 1201 running an Intel Pentium Dual core T2370 - which had its own set of spicy complications. I had to trawl the forums to tick off each symptom/resolution listed below:

- For installation...editing the boot options in grub is a must.. F4 and F6 boot options are key in moving forward the install forward
- editing the boot command line to remove quiet and splash will give you a text narrative to trap where things are going wrong
- arriving at a command prompt "intranfms" means you have not managed to boot into ubuntu
( It is worth knowing the following: 
   F4.. "safe graphics" mode will help step round VGA concerns
   acpi ... relates to the card cooling fans
   EDD is a help for old bios working with larger the 32GB disks
   APIC = advanced programmable interupt controllers
LAPIC = Lower "interupt controllers" .. I left these alone )
- Setting noapic edd=on acpi=off during install is worth trying if you go straight to a blank screen
- if not left with an intranfms prompt, "ALT" and F2 may well give you a user name prompt ... startx or equivalent may well work, if it does you can work with the install options via the GUI by using the "Install" disk icon
- if dual booting, with XP, and you don't have a second partition, or not enough free space... taking a Windows "back up" and copying your files to a recovery media, then re-installing  XP choosing your partition size carefully will ceratinly simplify things. 

IF YOU GET THIS FAR YOU'VE WON ... but not finished. ( On booting via the GRUB menu things may well go pear shaped again ... "blank" screen ). The boot options and line edits need to be entered again using the "ESC" option when GRUB is moving into boot sequence.

The command line edits are the same as for install.

In my case, I was confronted with the boot stalling on "starting bluetooth ..". If faced with the same or similar service problems, "ALT" and "F2" should get you to your "user" promt and allow you to remove the offending service .. on the server edition I was able to install chkconfig to manage services, "sudo apt-get install chkconfig".. this was not available on the desktop version. For this I installed sysvinit-utils package to get access to "service" command to see what services where started on startup. I then installed/used "sudo update-rc.d -f  bluetooth" to remove the offending service.

If you don't get either renaming the rcX.d script name, changing the "S" prefix to a "K" may well work. 

Once removed from the boot process, you can work each service issue independently.

Editing /boot/grub/menu.lst allows you to imbed the noapic edd=on acpi=off and temporarily remove the quiet splash options from the kernel line.

On "sudo reboot"  - I was in business.

Sorry for the lengthy and imprecise explanation, but I'm brand new to linux and would have loved to have found all the above in one place.

What now ... I have wireless and display driver issues still to resolve and some mouse driver stuff... but having a stable bootable Ubuntu environment makes these straightforward.
  
Good luck

---

### Post by parkland on 2009-11-18
WOW, all I can say, is wow...

I have nothing but high respect for the programmers and contributors of the ubuntu project, but I'm starting to develop an opinion that this release is potentially too buggy for release.

Drivers not working out of the box is one thing, small little glitches are one thing, but data corruption, on a fresh install like mine, is IMHO not acceptable, even if it is free. 

Maybe they should switch to a 12 month release cycle, allowing longer testing & beta periods?

PS, I'm spewing these comments after returning from work, where all day long I work on windows computers, many of which the operating systems are corrupt, un-fixable, but yet no personal files are damaged. The fact that ubuntu is so much more stable than windows, and yet manages to pull this off, does not make me happy.

---

### Post by jcxaver on 2009-11-19
hello, maybe someone more experienced can help to solve flickering screen on sony vaio z31, please see bellow:

```
jc@jc-vaio:~$ hwinfo --gfxcard
09: PCI 02.0: 0300 VGA compatible controller (VGA)              
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_2a42
  Unique ID: _Znp.YnzOCluPhb6
  SysFS ID: /devices/pci0000:00/0000:00:02.0
  SysFS BusID: 0000:00:02.0
  Hardware Class: graphics card
  Model: "Intel Mobile 4 Series Chipset Integrated Graphics Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x2a42 "Mobile 4 Series Chipset Integrated Graphics Controller"
  SubVendor: pci 0x104d "Sony Corporation"
  SubDevice: pci 0x9025 
  Revision: 0x07
  Driver: "i915"
  Driver Modules: "drm"
  Memory Range: 0xe8400000-0xe87fffff (rw,non-prefetchable)
  Memory Range: 0xd0000000-0xdfffffff (rw,prefetchable)
  I/O Ports: 0x8130-0x8137 (rw)
  IRQ: 30 (45756 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00008086d00002A42sv0000104Dsd00009025bc03sc00i00"
  Driver Info #0:
    Driver Status: i915 is active
    Driver Activation Cmd: "modprobe i915"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

27: PCI 100.0: 0300 VGA compatible controller (VGA)
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10de_6e5
  Unique ID: VCu0.ZjUFH5GJEdE
  Parent ID: vSkL.KcfarPM+5y9
  SysFS ID: /devices/pci0000:00/0000:00:01.0/0000:01:00.0
  SysFS BusID: 0000:01:00.0
  Hardware Class: graphics card
  Model: "nVidia GeForce 9300M GS"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x06e5 "GeForce 9300M GS"
  SubVendor: pci 0x104d "Sony Corporation"
  SubDevice: pci 0x9025 
  Revision: 0xa1
  Memory Range: 0xe4000000-0xe4ffffff (rw,non-prefetchable,disabled)
  Memory Range: 0xc0000000-0xcfffffff (rw,prefetchable,disabled)
  Memory Range: 0xe2000000-0xe3ffffff (rw,non-prefetchable,disabled)
  I/O Ports: 0x7000-0x7fff (rw,disabled)
  IRQ: 10 (no events)
  Module Alias: "pci:v000010DEd000006E5sv0000104Dsd00009025bc03sc00i00"
  Driver Info #0:
    Driver Status: nvidiafb is not active
    Driver Activation Cmd: "modprobe nvidiafb"
  Driver Info #1:
    Driver Status: nvidia is not active
    Driver Activation Cmd: "modprobe nvidia"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #8 (PCI bridge)

Primary display adapter: #9
jc@jc-vaio:~$ ^C
jc@jc-vaio:~$ modprobe nvidiafb
WARNING: Error inserting i2c_algo_bit (/lib/modules/2.6.31-14-generic/kernel/drivers/i2c/algos/i2c-algo-bit.ko): Operation not permitted
WARNING: Error inserting fb_ddc (/lib/modules/2.6.31-14-generic/kernel/drivers/video/fb_ddc.ko): Operation not permitted
FATAL: Error inserting nvidiafb (/lib/modules/2.6.31-14-generic/kernel/drivers/video/nvidia/nvidiafb.ko): Operation not permitted
jc@jc-vaio:~$ modprobe nvidia
FATAL: Could not open '/lib/modules/2.6.31-14-generic/kernel/drivers/video/nvidia.ko': No such file or directory
jc@jc-vaio:~$ modprobe nv
FATAL: Module nv not found.
```


xorg.log with nvidia 173 driver and flickering screen installed:
```

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux jc-vaio 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686
Kernel command line: root=UUID=63ad37c2-4e28-422f-9dc2-e3eb88acb63f ro quiet splash vga=769 
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Thu Nov 19 15:50:14 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0:0:2:0) 8086:2a42:104d:9025 Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller rev 7, Mem @ 0xe8400000/4194304, 0xd0000000/268435456, I/O @ 0x00008130/8
(--) PCI: (0:1:0:0) 10de:06e5:104d:9025 nVidia Corporation G98 [GeForce 9300M GS] rev 161, Mem @ 0xe4000000/16777216, 0xc0000000/268435456, 0xe2000000/33554432, I/O @ 0x00007000/128
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  173.14.20  Thu Jun 25 19:49:59 PDT 2009
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  173.14.20  Thu Jun 25 19:28:52 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 00@00:02:0
(EE) No devices detected.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.1.log" for additional information.

 ddxSigGiveUp: Closing log
```



I need working nvidia card for hdmi output, to simply install Nvidia drivers , 173, 185, 190 helped not.

Ubuntu works without xorg.conf, or with xorg.conf for intel.

Thank you for reply

---

### Post by jc66 on 2009-11-19
jcxaver, look at my post in this thread #126.

Your symtons are the same as mine were, so what worked for me might fix your system too.

But, before you do that, you might want to install the package:

xserver-xorg-video-nv

and then make sure you have 'nv' set as the device in the xorg.conf file.

---

### Post by jcxaver on 2009-11-19
> **jc66 said:**
> jcxaver, look at my post in this thread #126.

Your symtons are the same as mine were, so what worked for me might fix your system too.

But, before you do that, you might want to install the package:

xserver-xorg-video-nv

and then make sure you have 'nv' set as the device in the xorg.conf file.

hello, checked xserver-xorg-video-nv, tried your suggestion from # 126 for 173 version of Nvidia driver, tried both, 

Section "Device"
..
	Driver	"nvidia"
EndSection

Section "Device"
..
	Driver	"nv"
EndSection

in xorg.conf

but the problem persists...

Best regards, jcxaver

---

### Post by coolgenes on 2009-11-19
This sounds really off the wall but I swear it's true.  I had a ATI4550 video card and couldn't get it to work in 9.04 with the ATI Catalyst driver. So I switched to another card, thought it was an nvidia but was a radeon 600 series, I navigated to the /usr/share/ati folder. With superuser permissions, enter the command "sh ./fglrx-uninstall.sh". rebooted.  

using synaptic removed x0rg-driver-fglrx X.Org X server -- ATI Radeon display driver 

again navigated to the /usr/share/ati folder. With superuser permissions, enter the command "sh ./fglrx-uninstall.sh". 
apt-get install nvidia-glx-180...

rebooted and everything worked great.

today I upgraded to 9.10 and now it doesn't work anymore.  I tried everything in this thread with nothing helping.  ATI doesn't support this card and the default vesa driver, while giving me gui, is 640x480 with no support for the display changer in Preferences.  Is it possible to get this radeon 600 working again? in xorg.conf I changed vesa to radeon and got up a little better resolution, still not max for these monitors.

Also can anyone recommend a decent nvidia card that I can use two monitors on in 9.10?  I'd rather upgrade my hardware at this point

---

### Post by dcollins on 2009-11-19
I am glad to see this thread finally made sticky, but I believe the title of this thread is misleading. lspci lists my graphics as VGA compatible controller: Intel Corporation 82946GZ/GL Integrated Graphics Controller (rev 02). I am not using any propritary drivers but have this problem too.

I am hitting this problem (twice now!) on the upgrade from kernel 2.6.31-14-generic to 2.6.31-15-generic. Once this problem occurs, I cannot boot even if I roll back to the 2.6.31-14-generic kernel!

I suspect this issue really has more to do with the new kernel breaking systems using disk encryption than with certain graphics controllers, though I can't prove it at this time. After reinstalling for the third time I will try putting the 2.6.31-14-generic kernel package on hold and cross my fingers that this issue gets resolved soon.

This showstopper is most unfortunate in the number of people it affects as well as its severity. As this thread is nearing 200 replies, perhaps it would be a good idea to post a fix *prominently* on the forum so people don't need to slog through all the posts to find a resolution.

My 2 cents, for what it's worth.

---

### Post by alan_tam_sh on 2009-11-20
> **alan_tam_sh said:**
> Well, did you try going back to 9.04?
I actually tried a clean 9.04 installation guess what happen to me? I get the same blank flickering screen just like 9.10 at booting!! I am using nVidia geForce4 card btw, before i update my 9.04, my PC works so well and cool and happy with it. Now I am so regret upgrading it, where i will never get it back again. Worst i did not see if this bug has been reported!
So, guys i will try to resolve the problem one more time tonight after that if things dont improve then my last resource is to delete the entire partition and forget about Ubuntu. However this does not make me go back fall in love with MS..it just make me feel very disappointed with ubuntu for such a lousy release.

THERE WAS NO IMPROVEMENTS OR WHATSOEVER AFTER MANY ATTEMPTS OMG!!
UBUNTU SIMPLY FAILS (NO MATTER WHAT I HAVE DONE) TO BOOT UP CORRECTLY ONLY FLICKERING ONCE I ACTIVATE THE PROPRIETARY nVIDIA DRIVER. I AM USING geFORCE4 CARD IF I WOULD TO KEEP MY UBUNTU RUNNING WHICH I HAVE BEEN USING AS MY PRIMARY PRODUCTIVE DESKTOP SINCE 6.04 I HAVE TO TURN IF OFF! NOW I ONLY RUNS MY MACHINE WITH VESA DRIVER OMG WITH THIS DRIVER THE DISPLAY QUALITY SUCKS! THERE IS NO FIX AVAILABLE ANYTIME SOON.... DO I HAVE CHOICE BUT TO SWITCH BACK TO MY WINDOWS???????

---

### Post by bummpr on 2009-11-20
The silence is deafening...

Is there any official or authoritative response to this serious situation???

Any guidance to the (tens, dozens, hundreds, or thousands of users) who have experienced critical problems with installation?  

What are they (we, me) to do...wait for an appropriate release, apply a fix, go back to prior release, install Win7 or take some other action?

---

### Post by von Stalhein on 2009-11-20
I'm not authoritative or knowledgeable, and I certainly share your frustration with many aspects of this release.

Nevertheless, aside from some dual-boot issues which I will eventually beat, I'm happy with the present setup.

In either the main kernel or recovery mode I had video issues.
I managed to get to a prompt(ctr+alt+F1) and followed the process below.

```
1. boot the thing.
2. Select the "recovery mode" with the later kernel: 2.6.31-14 or 2.6.31-15, whichever you want to use.
3. Login
4. Pray that ftp will work and you can download from nVidia's site--necessary step! don't skip!
5. ftp
    6. open download.nvidia.com
    7. for username, use: guest
    8. for password, just press <Enter>
    9. cd XFree86
    10. cd Linux-x86
    11. cd 190.42
    12. binary
    13. get NVIDIA-Linux-x86-190.42-pkg1.run
    and wait for it to download; don't panic if you see nothing on the screen - it's doin it!
    14. bye

15. chmod 777 NVIDIA*

16. sudo ./NVIDIA*.run

17. Follow instructions in nVidia installation. Remember to choose Yes when it asks if you want to replace current X config options.
18. reboot

```

I keep telling myself that I am in charge. Haven't reached belief stage yet :)

---

### Post by alan_tam_sh on 2009-11-21
> **von Stalhein said:**
> I'm not authoritative or knowledgeable, and I certainly share your frustration with many aspects of this release.

Nevertheless, aside from some dual-boot issues which I will eventually beat, I'm happy with the present setup.

In either the main kernel or recovery mode I had video issues.
I managed to get to a prompt(ctr+alt+F1) and followed the process below.

```
1. boot the thing.
2. Select the "recovery mode" with the later kernel: 2.6.31-14 or 2.6.31-15, whichever you want to use.
3. Login
4. Pray that ftp will work and you can download from nVidia's site--necessary step! don't skip!
5. ftp
    6. open download.nvidia.com
    7. for username, use: guest
    8. for password, just press <Enter>
    9. cd XFree86
    10. cd Linux-x86
    11. cd 190.42
    12. binary
    13. get NVIDIA-Linux-x86-190.42-pkg1.run
    and wait for it to download; don't panic if you see nothing on the screen - it's doin it!
    14. bye

15. chmod 777 NVIDIA*

16. sudo ./NVIDIA*.run

17. Follow instructions in nVidia installation. Remember to choose Yes when it asks if you want to replace current X config options.
18. reboot

```

I keep telling myself that I am in charge. Haven't reached belief stage yet :)

I certainly have tried what you mentioned above but no, it didn't work the bloodly flickering screen comes back right after activation of the nVidia driver! It was okay (of cause with the lousy display quality) after removing the driver replaced it with default VESA driver. Apparently 9.10 fails to provide support to the old graphic card as well let alone new cards. I totally disappointed with Ubuntu. Anyone who have used Ubuntu as primary OS t work will surely find themselves in trouble

---

### Post by von Stalhein on 2009-11-21
> **alan_tam_sh said:**
> I certainly have tried what you mentioned above but no, it didn't work the bloodly flickering screen comes back right after activation of the nVidia driver! It was okay (of cause with the lousy display quality) after removing the driver replaced it with default VESA driver. Apparently 9.10 fails to provide support to the old graphic card as well let alone new cards. I totally disappointed with Ubuntu. Anyone who have used Ubuntu as primary OS t work will surely find themselves in trouble

What's your hardware - what GPU?

---

### Post by dado112233 on 2009-11-21
it was working with nvida 190 driver up to today...i updated drivers and new nvidia 190 driver were there too...after restart there is nothing.
come on both ubuntu and nvidia...i had huge problems when i installed 9.10, after a lot of testing and trying it worked with nvidia 96 drivers then upgrade to 190 drivers was fine but today update to new 190 driver and nothing works...

how is that possible?

---

### Post by alan_tam_sh on 2009-11-22
> **von Stalhein said:**
> What's your hardware - what GPU?

I am using a desktop PC with following specs.
Pentium 4 CPU 3.06GHz
3.07GHz, 512 MB of RAM.
NVIDIA GeForce4 MX 440 with AGP8X 64MB GPU

dual boot with Windows XP P3.

btw the NVIDIA driver used was 96.43.14

---

### Post by von Stalhein on 2009-11-22
> **alan_tam_sh said:**
> I am using a desktop PC with following specs.
Pentium 4 CPU 3.06GHz
3.07GHz, 512 MB of RAM.
NVIDIA GeForce4 MX 440 with AGP8X 64MB GPU

dual boot with Windows XP P3.

btw the NVIDIA driver used was 96.43.14

Jingoes, aside from the GPU it's pretty similar to mine: -

P4 2.6, 4 G RAM, nVidia AGP 7600GS

I just can't get the dual boot to work atm :-(

Have you another GPU to swap in as a test? - not that you should need to mind!!!

---

### Post by jcxaver on 2009-11-22
see, linux sees nvidia graphics, but the correctly installed nvidia driver sees not the same graphics..


part of the xorg.log
```
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0:0:2:0) 8086:2a42:104d:9025 Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller rev 7, Mem @ 0xe8400000/4194304, 0xd0000000/268435456, I/O @ 0x00008130/8
(--) PCI: (0:1:0:0) 10de:06e5:104d:9025 nVidia Corporation G98 [GeForce 9300M GS] rev 161, Mem @ 0xe4000000/16777216, 0xc0000000/268435456, 0xe2000000/33554432, I/O @ 0x00007000/128
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  190.42  Tue Oct 20 20:55:08 PDT 2009
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  190.42  Tue Oct 20 20:26:00 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 00@00:02:0
(EE) No devices detected.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.1.log" for additional information.

 ddxSigGiveUp: Closin
```

---

### Post by JustAnotherBrick on 2009-11-22
For the flicker problem - just wanted to say that - as someone had tried successfully already - I went into the maintenance root prompt and moved my /etc/X11/xorg.conf to /etc/X11/xorg.conf.bk, basically ending up with no /etc/X11/xorg.conf  and rebooted. And that seemed to have magically solved all the problems. After that everything is working fine so far.

---

### Post by alh on 2009-11-22
Try entering 'nopat' in the bootup options in the grub screen. I had this problem with the latest version of mandriva and opensuse before changing the boot options in grub menu.list. This cured the problem. Did not seem to unduly effect the performence of the Nvidia driver. Apparently it is a problem with the new kernel and the nvidia drivers. This seems to be happening in all distros using the new kernel.
Maybe this will work for you.

---

### Post by jcxaver on 2009-11-23
> **JustAnotherBrick said:**
> For the flicker problem - just wanted to say that - as someone had tried successfully already - I went into the maintenance root prompt and moved my /etc/X11/xorg.conf to /etc/X11/xorg.conf.bk, basically ending up with no /etc/X11/xorg.conf  and rebooted. And that seemed to have magically solved all the problems. After that everything is working fine so far.

you had disabled a driver named in the xorg.conf

---

### Post by singedwings on 2009-11-23
jcxaver have you got two graphics cards?

```
(--) PCI:*(0:0:2:0) 8086:2a42:104d:9025 Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller rev 7, Mem @ 0xe8400000/4194304, 0xd0000000/268435456, I/O @ 0x00008130/8
(--) PCI: (0:1:0:0) 10de:06e5:104d:9025 nVidia Corporation G98 [GeForce 9300M GS] rev 161, Mem @ 0xe4000000/16777216, 0xc0000000/268435456, 0xe2000000/33554432, I/O @ 0x00007000/128

```

```
(II) Primary Device is: PCI 00@00:02:0
(EE) No devices detected.
```

If so try adding the busid for the nvidia card to xorg.conf, so you would have something like:

```
Section "Device"
Identifier "Configured Video Device"
Busid "PCI:1:0:0"
Driver "nvidia"
EndSection
```

---

### Post by jcxaver on 2009-11-23
yes, vaio z series has hybrid graphic card and switch to select one - intel, or nvidia card

when I tried nvidia settings, I allways had the switch in nvidia position

---

### Post by 2Flex on 2009-11-23
Hi,

I'm also new at Linux, in this case I have Karmic ;).
But I also have some blinking in X, its random.. I have the newest driver installed..
Could it be because of compz?

Best Regards

---

### Post by von Stalhein on 2009-11-24
> **jcxaver said:**
> yes, vaio z series has hybrid graphic card and switch to select one - intel, or nvidia card

when I tried nvidia settings, I allways had the switch in nvidia position

Yes, but did you try singedwings suggestion anyway to see if it made a difference?

Tweaking is a funny game you know :-)

---

### Post by wislon on 2009-11-24
> **JustAnotherBrick said:**
> For the flicker problem - just wanted to say that - as someone had tried successfully already - I went into the maintenance root prompt and moved my /etc/X11/xorg.conf to /etc/X11/xorg.conf.bk, basically ending up with no /etc/X11/xorg.conf  and rebooted. And that seemed to have magically solved all the problems. After that everything is working fine so far.

Thanks JustAnotherBrick, your solution worked for me.

I have an nvidia card as well. I just upgraded to '2.6.31-15-generic-pae' (apt told me there was an update, so I updated, silly me!). After a reboot into the new kernel, I got the same flickering problem.

I haven't tried to install the newest nvidia driver, but simply backing up and then clobbering the /etc/X11/xorg.conf and rebooting did the trick. It took a little longer to come up, but it looked like it was sorting some stuff out. Now the system runs perfectly again. And there's no xorg.conf, it hasn't replaced it or regenerated it, from what I can see.

I hope this helps someone!

---

### Post by sxe4ever on 2009-11-24
So, I've posted about this in a couple of other threads, but this one seems to be the largest and I'm not getting updates on the other ones......  I deleted the xorg.conf file as has been recommended in previous posts but when I did that, it worked fine with the newest update until I actually logged in.... Then the screen turned all VGAish (picture below)

[IMG]http://etcomeback.com/Hosting/CIMG0056.jpg[/IMG]

So.... I tried to delete some of my installed drivers/software, after doing so when I rebooted (with the newest update) it makes the noise like I'm at the login screen, but the screen is completely black.

The second to newest update is working great, and I'm currently on it.  Does anyone have any idea what could be going on or what I should install to get it working again??? Please & thanks for any info!!!

---

### Post by XanII on 2009-11-24
Soo... people upgraded to the latest 2.6.31-15-generic-pae and for some that managed to fix things earlier things fell apart again? 

Seems like i wont be touching that proprietary drivers settings for awhile. :( I simply dont have time to fight over this when my system again goes awol with the nvidia drivers activated.

---

### Post by XanII on 2009-11-24
Could someone please explain what happens when you choose to activate the proprietary drivers? or more importantly: if i wish to experiment by activating it, what is the best way to restore the system when everything goes to h*ll again and i end up with the horrenoud flashing prompt. last time i used a live cd on usb stick to get back up.

---

### Post by Subban on 2009-11-24
> **XanII said:**
> Soo... people upgraded to the latest 2.6.31-15-generic-pae and for some that managed to fix things earlier things fell apart again? 

Seems like i wont be touching that proprietary drivers settings for awhile. :( I simply dont have time to fight over this when my system again goes awol with the nvidia drivers activated.

I had previously installed the 190.42 driver downloaded from Nvidias site. Today after doing the update of courrse it was all broken again, a quick reboot to recovery prompt or what works for me is to just use ctrl+alt+F1-F5 until I get a prompt that doesn't flash (its entirely random and can take a few tries) then just re-run the nvidia installer. It only takes a couple of minutes, I would prefer not too, but its no big deal now I have it downloaded and sat in ~/

---

### Post by Benchamoneh on 2009-11-24
Just upgraded to 2.6.31-15 now and glad to see I'm not alone on this one. Hopefully that means a quicker resolution for the future. It's not that difficult to fix though and the answers are splattered all over this thread.

I'd take the advice of Subban and keep the latest nVidia driver somewhere on your system for reasons just like this. However if you're like me and have an encrypted /home then Ideally you'd want to keep it out of there as I couldn't access mine when logging on via the recovery terminal (I had to download it again via ftp).

---

### Post by jaylsi on 2009-11-24
> **XanII said:**
> Could someone please explain what happens when you choose to activate the proprietary drivers? or more importantly: if i wish to experiment by activating it, what is the best way to restore the system when everything goes to h*ll again and i end up with the horrenoud flashing prompt. last time i used a live cd on usb stick to get back up.

The quickest way is to reboot, select "Recovery Mode" (normally the second one in the boot prompt list), then go to command line mode with network support. From there, you can either 1) Remove /etc/X11/xorg.conf or 2) Download and rebuild the latest Nvidia driver.

To make things much easier, before you experiment activation, you should download the driver first.

Some people run Ubuntu without /etc/X11/xorg.conf. In doing so they basically are using a generic video driver without any fancy features. If you are okay with that, leave it that way and don't do the proprietary driver activation, then you should never see the flashing prompt again in future upgrades.

---

### Post by lapdog on 2009-11-24
> **dcollins said:**
> ...
I am hitting this problem (twice now!) on the upgrade from kernel 2.6.31-14-generic to 2.6.31-15-generic.
...
This showstopper is most unfortunate in the number of people it affects as well as its severity. As this thread is nearing 200 replies, perhaps it would be a good idea to post a fix *prominently* on the forum so people don't need to slog through all the posts to find a resolution.

My 2 cents, for what it's worth.

Same here--again.  I went into Update Manager and updated all the latest stuff today.  After it asked me to reboot I got the bootup flickering again. 

dcollins, I think your 2 cents is worth a lot.


> **Subban said:**
> I had previously installed the 190.42 driver downloaded from Nvidias site. Today after doing the update of course it was all broken again, a quick reboot to recovery prompt
...
then just re-run the nvidia installer. It only takes a couple of minutes, I would prefer not too, but its no big deal now I have it downloaded and sat in ~/

This was my solution too.  I reinstalled the 190.42 driver with the original:
```
sudo ./NVIDIA*.run
```
Fortunately I too left the driver in my home directory so I didn't have to download it again.

Subban, I respectfully disagree:  While it took me only a few minutes to try this solution, I think it is a *huge* deal at this point.  It's bad enough that a major upgrade makes one's system fail to boot, but for minor updates to include such a result is *absolutely unacceptable.*



And the other problem is just as bad:

> **bummpr said:**
> The silence is deafening...

Is there any official or authoritative response to this serious situation???

Any guidance to the (tens, dozens, hundreds, or thousands of users) who have experienced critical problems with installation?  

What are they (we, me) to do...wait for an appropriate release, apply a fix, go back to prior release, install Win7 or take some other action?


To be fair, I just reexamined the Upgrade Notes page at:

[https://help.ubuntu.com/community/KarmicUpgrades](https://help.ubuntu.com/community/KarmicUpgrades)

and found this snippet at the bottom:

> NVIDIA and ATI

People NVIDIA and ATI graphics cards have been seeing problems. Some people have remove the Ubuntu NVIDIA drivers and loaded the ones from nvidia.com. Alternatively, you can switch from using the 'nvidia' drivers to 'nv' drivers, editing /etc/X11/xorg.conf.

Bug report is here: [https://bugs.launchpad.net/ubuntu/+bug/464591](https://bugs.launchpad.net/ubuntu/+bug/464591)

Unfortunately this is poor "guidance," at best.  And the launchpad bug report that is noted?  It is for a bug reported on 2009-10-30 and the status is listed as "Won't Fix &#8594; Invalid."  See also comment #21 on that page for additional "blinks on reboot" issues:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/464591/comments/21](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/464591/comments/21)

The original bug for this issue seems to be:

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/441638](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/441638)

which has a status of "Fix Released," although now I suspect the gdm endlessly respawning is only part of the problem.  And, as has been noted (in this thread or another, I forget), this bug was reported back on 2009-10-03, nearly four weeks before Ubuntu 9.10 was released.


And what is the basis for this Poor Guidance and *absolutely unacceptable* upgrade/update behaviors?

Well, instead of using a lot of nasty adjectives and derisive nouns (and believe me, I'd like to!), I'm going to look more into the FreeBSD I have installed on an old computer and hope that Ubuntu will fix its serious errors and be proactive about such problems in the future.  In the meantime, I will not be accepting any upgrades/updates to Ubuntu until there is an official announcement of an official fix.

---

### Post by juliobahar on 2009-11-25
> **y.t said:**
> It works now, I did the following steps:

[LIST]
[*] Boot from the install disk into recovery mode
[*] download from nvidia.com the NVIDIA-Linux-*.run for your hardware and copy it to your PC (I did it with a second PC and transfered via scp)
[*] run the NVIDIA-Linux-*.run
[*] Follow the instructions
[*] reboot
[/LIST]

I had this same problem after karmic kernel upgrade to 2.6.31-15, with a NVIDIA graphic card.

This solved my problem immediately. But I had the NVidia 190.42 driver already downloaded on my harddisk so I logged in using 2.6.31-15 (recovery mode) and chose ROOT.

After that typed 
```
telinit 3
```
so as not to be root while reinstalling the NVIDIA 190.42 driver, then 
```
$ sudo ./NVIDIA*.run
```
and follow the instructions

---

### Post by sxe4ever on 2009-11-25
> **sxe4ever said:**
> So, I've posted about this in a couple of other threads, but this one seems to be the largest and I'm not getting updates on the other ones......  I deleted the xorg.conf file as has been recommended in previous posts but when I did that, it worked fine with the newest update until I actually logged in.... Then the screen turned all VGAish (picture below)

[IMG]http://etcomeback.com/Hosting/CIMG0056.jpg[/IMG]

So.... I tried to delete some of my installed drivers/software, after doing so when I rebooted (with the newest update) it makes the noise like I'm at the login screen, but the screen is completely black.

The second to newest update is working great, and I'm currently on it.  Does anyone have any idea what could be going on or what I should install to get it working again??? Please & thanks for any info!!!

Sorry to bump, but does anyone know what could be causing this???? Please & thank you!!!!

---

### Post by von Stalhein on 2009-11-25
> **jaylsi said:**
> ,<snip>

Some people run Ubuntu without /etc/X11/xorg.conf. In doing so they basically are using a generic video driver without any fancy features. If you are okay with that, leave it that way and don't do the proprietary driver activation, then you should never see the flashing prompt again in future upgrades.

I stand to be corrected, but I don't think there is actually a xorg.conf included in Karmic, or if there is, it contains nothing.

When I was having the video issues I read that somewhere but as I say IIRC,

I think it was something to do with both ATI and nVidia drivers being proprietary - perhaps a patent/copyright thing?

---

### Post by von Stalhein on 2009-11-25
> **sxe4ever said:**
> Sorry to bump, but does anyone know what could be causing this???? Please & thank you!!!!

Have you tried using the backup xorg.conf that usually resides in /etc/X11/xorg.conf.backup or the /etc/X11/xorg.conf.failsafe ?

---

### Post by otchie1 on 2009-11-25
Just another example of developers developing things just for their systems without much regard to anybody else. Guess that's just fallout from them being mostly anonymous.

---

### Post by captain_sensible on 2009-11-25
hi

let me say at the outset i'm a beginner , so if you think you have problems ........... 

I have been using Ubuntu jaunty jackel version for about a year on an elonex webbook laptop with that particular  installation fine and the graphics display no problem. i got a new update prompt for packages yesterday and to the new 9.10 version upgrade , which i made a big mistake in clicking  !

The upgrade proceeded but at the reboot stage i got a flickering xwindow GUI. So on bootup I choose from grub the recover option, fix broken package and then drop to comand line. 

i thought i might have completely mashed up the whole Liinux op,  but I had a mysql database and table previously installed so thought i would see after the botched upgrade  if the data had been preserved. At the command line i could log into the MySQL using mysql -u root -p and found that the databases and tables where still there  and  accessible using MySQL from command terminal  .

So it looks like its a display problem.

 On the previous Jaunty jackel I played around  from a command line using xrandr. So i just typed that in hoping 
for a list of options. The respose was can not open file.
I then logged in as root  and typed Xorg -configure 
and got fatal server error remove /tmp/.xo-lock which means  nothing to me. 


At least i can get to a none flickering terminal window , but I dont know where to start fixing the xwindow gui. 

I can connect to the internet and thought I would try :
 
apt-get install fluxbox from the terminal 

this worked. It installed , so next question how do I get this to run on the next boot up, so that at least I get (i hope) a simple gui window up ?  

 any pointers 

 much appreciated

---

### Post by tmfries on 2009-11-25
> **y.t said:**
> It works now, I did the following steps:

[LIST]
[*] Boot from the install disk into recovery mode
[*] download from nvidia.com the NVIDIA-Linux-*.run for your hardware and copy it to your PC (I did it with a second PC and transfered via scp)
[*] run the NVIDIA-Linux-*.run
[*] Follow the instructions
[*] reboot
[/LIST]


Great solution! Thanks. Worked like a champ for me. Luckily though I already had the NVIDIA drivers downloaded and in my home folder. A little info though... the drivers need to be run in runlevel 3. So when you are dropped to a root console type "telinit 3" then login with your normal user/pass and then sudo ./NVidia drivers.run

---

### Post by jaylsi on 2009-11-25
> **captain_sensible said:**
> hi

let me say at the outset i'm a beginner , so if you think you have problems ........... 

I have been using Ubuntu jaunty jackel version for about a year on an elonex webbook laptop with that particular  installation fine and the graphics display no problem. i got a new update prompt for packages yesterday and to the new 9.10 version upgrade , which i made a big mistake in clicking  !

The upgrade proceeded but at the reboot stage i got a flickering xwindow GUI. So on bootup I choose from grub the recover option, fix broken package and then drop to comand line. 

i thought i might have completely mashed up the whole Liinux op,  but I had a mysql database and table previously installed so thought i would see after the botched upgrade  if the data had been preserved. At the command line i could log into the MySQL using mysql -u root -p and found that the databases and tables where still there  and  accessible using MySQL from command terminal  .

So it looks like its a display problem.

 On the previous Jaunty jackel I played around  from a command line using xrandr. So i just typed that in hoping 
for a list of options. The respose was can not open file.
I then logged in as root  and typed Xorg -configure 
and got fatal server error remove /tmp/.xo-lock which means  nothing to me. 


At least i can get to a none flickering terminal window , but I dont know where to start fixing the xwindow gui. 

I can connect to the internet and thought I would try :
 
apt-get install fluxbox from the terminal 

this worked. It installed , so next question how do I get this to run on the next boot up, so that at least I get (i hope) a simple gui window up ?  

 any pointers 

 much appreciated
I am not sure to understand fully of your problem, but the quickest way to fix a flickering terminal is to go to recovery mode and rename /etc/X11/xorg.conf to a backup file, and reboot. Did you try that?

---

### Post by jaylsi on 2009-11-25
> **von Stalhein said:**
> I stand to be corrected, but I don't think there is actually a xorg.conf included in Karmic, or if there is, it contains nothing.

When I was having the video issues I read that somewhere but as I say IIRC,

I think it was something to do with both ATI and nVidia drivers being proprietary - perhaps a patent/copyright thing?

You are right that by default, xorg.conf is not created in 9.10, because it can work with almost all cards on basic display functions.  ATI and nVidia don't want their driver code to be GPL. So Linux can't distribute their binary drivers. Users often have to rebuild the driver when system updates cause dependence changes.

---

### Post by sxe4ever on 2009-11-25
> **von Stalhein said:**
> Have you tried using the backup xorg.conf that usually resides in /etc/X11/xorg.conf.backup or the /etc/X11/xorg.conf.failsafe ?

Yeah, I've actually had problems with my xorg.conf file in the past due to my video cards apparently not being supported by Ubuntu, so I actually back it up like once a month, but I have tried both of those files with no luck :-/

---

### Post by tibike on 2009-11-25
hello!
I ran across the 300+ post and i saw solutions like "install something then reboot"
But my case is blinking directly from the live Karmic CD (ubuntu-9.10.desktop-i386.iso from ubuntu.com). So there is no reboot possibility, i guess... 
Jaunty CD is cool, but I'd really like Karmic. Should i wait until some update and hope for a better .iso??

---

### Post by psycho5 on 2009-11-26
Ok I think the problem is the driver synaptic is buggy. When the new kernel was downloaded and installed along with nvidia-glx-190.42 ppau something for me, after reboot I knew that I wouldn't get X because currently I was using nvidia drivers from nvidia.com.


The crappy thing is, I tried to uninstall the driver by doing sudo sh NVIDIA* --uninstall from recovery mode of the new kernel because I got the flickering screen again. The uninstall doesn't work correctly I think... this is the uninstall log

```

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Thu Nov 26 20:08:15 2009
installer version: 1.0.7

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : true
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> You appear to be running in runlevel 1; this may cause problems.  For exampl
   e: some distributions that use devfs do not run the devfs daemon in runlevel
   1, making it difficult for `nvidia-installer` to correctly setup the kernel 
   module configuration files.  It is recommended that you quit installation no
   w and switch to runlevel 3 (`telinit 3`) before installing.
   
   Quit installation now? (select 'No' to continue installation) (Answer: No)
-> Parsing log file:
-> done.
-> Validating previous installation:
-> The previously installed file '/usr/lib/libcuda.so.190.42' has a different
   checksum (4013875169) than when it was installed (2063606468). 
   /usr/lib/libcuda.so.190.42 will not be uninstalled.
-> The previously installed file '/usr/lib/libGL.so.190.42' has a different
   checksum (2096745860) than when it was installed (12028714). 
   /usr/lib/libGL.so.190.42 will not be uninstalled.
-> The previously installed file '/usr/lib/libGLcore.so.190.42' has a different
   checksum (3512986921) than when it was installed (3817161217). 
   /usr/lib/libGLcore.so.190.42 will not be uninstalled.
-> The previously installed file '/usr/lib/libnvidia-tls.so.190.42' has a
   different checksum (3912779769) than when it was installed (351691719). 
   /usr/lib/libnvidia-tls.so.190.42 will not be uninstalled.
-> The previously installed file '/usr/lib/tls/libnvidia-tls.so.190.42' has a
   different checksum (3047729166) than when it was installed (2917724307). 
   /usr/lib/tls/libnvidia-tls.so.190.42 will not be uninstalled.
-> The previously installed file '/usr/lib/libvdpau.so.190.42' has a different
   checksum (1634306367) than when it was installed (240555900). 
   /usr/lib/libvdpau.so.190.42 will not be uninstalled.
-> The previously installed file '/usr/lib/libvdpau_trace.so.190.42' has a
   different checksum (2703300654) than when it was installed (2489557172). 
   /usr/lib/libvdpau_trace.so.190.42 will not be uninstalled.
-> The previously installed file '/usr/lib/libvdpau_nvidia.so.190.42' has a
   different checksum (2567229061) than when it was installed (3801241876). 
   /usr/lib/libvdpau_nvidia.so.190.42 will not be uninstalled.
-> The previously installed file '/usr/lib/libXvMCNVIDIA.so.190.42' has a
   different checksum (1585860875) than when it was installed (3561214553). 
   /usr/lib/libXvMCNVIDIA.so.190.42 will not be uninstalled.
-> The previously installed file
   '/usr/lib/xorg/modules/extensions/libglx.so.190.42' has a different checksum
   (498229394) than when it was installed (669782707). 
   /usr/lib/xorg/modules/extensions/libglx.so.190.42 will not be uninstalled.
-> The previously installed file '/usr/lib/xorg/modules/drivers/nvidia_drv.so'
   has a different checksum (1993173224) than when it was installed
   (809347286).  /usr/lib/xorg/modules/drivers/nvidia_drv.so will not be
   uninstalled.
-> The previously installed file '/usr/share/man/man1/nvidia-xconfig.1.gz' has
   a different checksum (1520601298) than when it was installed (1941609823). 
   /usr/share/man/man1/nvidia-xconfig.1.gz will not be uninstalled.
-> The previously installed symlink '/usr/lib/libcuda.so' has target
   'libcuda.so.190.42', but it was installed with target 'libcuda.so.1'. 
   /usr/lib/libcuda.so will not be uninstalled.
-> done.
WARNING: Your driver installation has been altered since it was initially
         installed; this may happen, for example, if you have since installed
         the NVIDIA driver through a mechanism other than nvidia-installer
         (such as your distribution's native package management system). 
         nvidia-installer will attempt to uninstall as best it can.  Please see
         the file '/var/log/nvidia-installer.log' for details.
-> Uninstalling NVIDIA Accelerated Graphics Driver for Linux-x86 (1.0-19042
   (190.42)):
-> Unable to restore symbolic link /usr/lib/libXvMCNVIDIA.so.1 ->
   libXvMCNVIDIA.so.190.42 (File exists).
-> Unable to restore symbolic link /usr/lib/libXvMCNVIDIA.so ->
   libXvMCNVIDIA.so.190.42 (File exists).
-> done.
-> Uninstallation of existing driver: NVIDIA Accelerated Graphics Driver for
   Linux-x86 (190.42) is complete.

```

It can't restore the links. I think because I just updated and rebooted, and X didn't run so the new driver from synaptic didn't load up? I don't know. If someone can figure out how to successfully uninstall the nvidia.com driver then you can just upgrade and reboot cause ubuntu will use the glx driver provided, am I right? Just thinking out loud here...

I know I can "fix" this by reinstalling the driver, but that still doesn't solve anything till the next update comes around, and this new driver from nvidia has the colors in all my videos inverted, all the time I have to run 

```

xvattr -a XV_HUE -v 0

```

to fix the inverted colors of the video. If anyone has successfully uninstalled the downloaded driver and reverted back, please tell how to do it. I've tried removing the driver, removing X, removing the glx, and reinstalling X and glx for nvidia but still flickering. So I know the uninstall of the downloaded nvidia driver is not working as it should. Its the only thing that makes sense to me. Its not allowing the driver from synaptic to load up because of some links it fails to restore.

---

### Post by deamon_knight on 2009-11-27
I've got an Idea of what is going on for Nvidia Users. I don't think its Nvidia's Drivers. It occurred to me that Proprietery drivers have never been enabled by default, and if they were broken, why would installing them from Nvidia directly solve the problem?

I believe that the"nv" drivers or a combination of the "nv" drivers and something else are the source of this problem.

My symptoms were: From a LiveCD or a fresh alt-install I would not get to a desktop or login, just a blank screen and my monitor's indicator LED would blink as though it was "out of range". (However, I would get the drum-login sound, this is interesting later) If I installed the nvidia drivers as some have suggested I could get to a desktop, but of course the next kernel update would break things.

So, I guessed that properly configuring X was the problem, as the "no desktop" was occurring BEFORE I would expect ANY proprietary drivers to be installed.

I don't know how to make an xorg.conf myself, and Ubuntu no longer generates one, but I had played around with Puppy Linux on some older systems. [http://puppylinux.org]("http://puppylinux.org") and I knew It generated a well annotated xorg.conf.

So I booted to A Puppy linux LiveCD, copied the contents of the xorg.conf it generates to my broken Karmic install. After this, I no longer got a blank screen but I did get the flashing text login prompt some have been reporting. Going back to Puppy, I looked at the xorg.conf and decided to change my display driver from "nv" to "vesa".

```

 Identifier     "Card0"
    Driver         "nv"
    VendorName     "nVidia Corporation"
    BoardName      "GeForce 7600 GS"
    Option         "NoLogo" "True"
	### Available Driver options are:-
    BusID          "PCI:1:0:0"

```

changed to

```

 Identifier     "Card0"
    Driver         "vesa"
    VendorName     "nVidia Corporation"
    BoardName      "GeForce 7600 GS"
    Option         "NoLogo" "True"
	### Available Driver options are:-
    BusID          "PCI:1:0:0"

```

After this change I was able to boot to GDM, login, and get to a desktop. (Although no Sound Now) From here I tried to install the Proprietary driver from Jockey and got an error about broken packages. Next I enabled the "Proposed" Repo, downloaded the updates and rebooted. After those updates I was able to enable the Proprietary Nvidia driver through Jockey. After a reboot, the correct driver is installed. However, I still don't have audio.

Here is the "default" xorg.conf that got me to a desktop.

```

#Special base config file used in Puppy Linux.

# **********************************************************************
# Module section -- this  section  is used to specify
# which dynamically loadable modules to load.
# **********************************************************************
#
Section "Module"

# This loads the DBE extension module.

    Load        "dbe"  	# Double buffer extension

# This loads the miscellaneous extensions module, and disables
# initialisation of the XFree86-DGA extension within that module.
    SubSection  "extmod"
      Option    "omit xfree86-dga"   # don't initialise the DGA extension
    EndSubSection

# This loads the font modules
    Load        "type1"
    Load        "freetype"

# This loads xtrap extension, used by xrandr
    Load       "xtrap"

# This loads the GLX module (if present)
    Load       "glx"

# This loads dri module (if present)
    Load       "dri"

EndSection

# **********************************************************************
# Files section.  This allows default font and rgb paths to be set
# **********************************************************************

Section "Files"

# The location of the RGB database.  Note, this is the name of the
# file minus the extension (like ".txt" or ".db").  There is normally
# no need to change the default.

    RgbPath	"/usr/X11R7/lib/X11/rgb"

# Multiple FontPath entries are allowed (which are concatenated together),
# as well as specifying multiple comma-separated entries in one FontPath
# command (or a combination of both methods)

    FontPath   "/usr/X11R7/lib/X11/fonts/misc/"
    FontPath   "/usr/X11R7/lib/X11/fonts/Type1/"
    FontPath   "/usr/X11R7/lib/X11/fonts/TTF/"

EndSection

# **********************************************************************
# Server flags section.
# **********************************************************************

Section "ServerFlags"

# Uncomment this to disable the <Crtl><Alt><Fn> VT switch sequence
# (where n is 1 through 12).  This allows clients to receive these key
# events.

#    Option "DontVTSwitch"

# Enables mode switching with xrandr
# There is a report that this can cause Xorg not to work on some
# video hardware, so default is commented-out...
# but i want to use it in xorgwizard so leave on...

    Option "RandR" "on"

EndSection

#everything past here is auto-generated by Puppy's Xorg Wizard...


Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option      "XkbRules" "xorg"
	Option      "XkbModel" "pc102"
	Option      "XkbLayout" "us" #xkeymap0
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "IMPS/2" #mouse0protocol
	Option	    "Device" "/dev/mouse"
	#Option      "Emulate3Buttons"
	#Option      "Emulate3Timeout" "50"
	Option      "ZAxisMapping" "4 5" #scrollwheel
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
	HorizSync    31.5-79
	VertRefresh  50-85
	#UseModes     "Modes0" #monitor0usemodes
	Option      "PreferredMode" "1280x1024"
	EndSection
	
Section "Modes"
	Identifier "Modes0"
	#modes0modeline0
EndSection

Section "Device"
	### Available Driver options are:-
	### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
	### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
	### [arg]: arg optional
	#Option     "SWcursor"           	# [<bool>]
	#Option     "HWcursor"           	# [<bool>]
	#Option     "NoAccel"            	# [<bool>]
	#Option     "ShadowFB"           	# [<bool>]
	#Option     "UseFBDev"           	# [<bool>]
	#Option     "Rotate"             	# [<str>]
	#Option     "VideoKey"           	# <i>
	#Option     "FlatPanel"          	# [<bool>]
	#Option     "FPDither"           	# [<bool>]
	#Option     "CrtcNumber"         	# <i>
	#Option     "FPScale"            	# [<bool>]
	#Option     "FPTweak"            	# <i>
	#Option     "DualHead"           	# [<bool>]
	Identifier  "Card0"
	Driver      "vesa" #card0driver
	VendorName  "nVidia Corporation"
	BoardName   "GeForce 7600 GS"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
    DefaultDepth 16
    Subsection "Display"
        Depth       16
        Modes       "1280x1024"
    EndSubsection
EndSection

#PuppyHardwareProfile=NVIDIA

```

The Steps from here were to login, Go to System>>Administration>>Software Sources. Select the pre-release (karmic-proposed) repos. Allow this to update your sources, then run "Update Manager" and download all updates. After that, reboot. If the reboot succeeds, you should be able to go to System>>Administration>>Hardware Drivers and choose the correct driver. Reboot to enable. As Always, YMMV, and I can't explain WHY it worked, but it worked for me. I have not examined much else so I may discover other things arte broken, but at least I can get to a desktop.

Now, I just need to get sound working........

---

### Post by alan_tam_sh on 2009-11-28
> **deamon_knight said:**
> I've got an Idea of what is going on for Nvidia Users. I don't think its Nvidia's Drivers. It occurred to me that Proprietery drivers have never been enabled by default, and if they were broken, why would installing them from Nvidia directly solve the problem?

I believe that the"nv" drivers or a combination of the "nv" drivers and something else are the source of this problem.

My symptoms were: From a LiveCD or a fresh alt-install I would not get to a desktop or login, just a blank screen and my monitor's indicator LED would blink as though it was "out of range". (However, I would get the drum-login sound, this is interesting later) If I installed the nvidia drivers as some have suggested I could get to a desktop, but of course the next kernel update would break things.

So, I guessed that properly configuring X was the problem, as the "no desktop" was occurring BEFORE I would expect ANY proprietary drivers to be installed.

I don't know how to make an xorg.conf myself, and Ubuntu no longer generates one, but I had played around with Puppy Linux on some older systems. [http://puppylinux.org]("http://puppylinux.org") and I knew It generated a well annotated xorg.conf.

So I booted to A Puppy linux LiveCD, copied the contents of the xorg.conf it generates to my broken Karmic install. After this, I no longer got a blank screen but I did get the flashing text login prompt some have been reporting. Going back to Puppy, I looked at the xorg.conf and decided to change my display driver from "nv" to "vesa".

```

 Identifier     "Card0"
    Driver         "nv"
    VendorName     "nVidia Corporation"
    BoardName      "GeForce 7600 GS"
    Option         "NoLogo" "True"
	### Available Driver options are:-
    BusID          "PCI:1:0:0"

```

changed to

```

 Identifier     "Card0"
    Driver         "vesa"
    VendorName     "nVidia Corporation"
    BoardName      "GeForce 7600 GS"
    Option         "NoLogo" "True"
	### Available Driver options are:-
    BusID          "PCI:1:0:0"

```

After this change I was able to boot to GDM, login, and get to a desktop. (Although no Sound Now) From here I tried to install the Proprietary driver from Jockey and got an error about broken packages. Next I enabled the "Proposed" Repo, downloaded the updates and rebooted. After those updates I was able to enable the Proprietary Nvidia driver through Jockey. After a reboot, the correct driver is installed. However, I still don't have audio.

Here is the "default" xorg.conf that got me to a desktop.

```

#Special base config file used in Puppy Linux.

# **********************************************************************
# Module section -- this  section  is used to specify
# which dynamically loadable modules to load.
# **********************************************************************
#
Section "Module"

# This loads the DBE extension module.

    Load        "dbe"  	# Double buffer extension

# This loads the miscellaneous extensions module, and disables
# initialisation of the XFree86-DGA extension within that module.
    SubSection  "extmod"
      Option    "omit xfree86-dga"   # don't initialise the DGA extension
    EndSubSection

# This loads the font modules
    Load        "type1"
    Load        "freetype"

# This loads xtrap extension, used by xrandr
    Load       "xtrap"

# This loads the GLX module (if present)
    Load       "glx"

# This loads dri module (if present)
    Load       "dri"

EndSection

# **********************************************************************
# Files section.  This allows default font and rgb paths to be set
# **********************************************************************

Section "Files"

# The location of the RGB database.  Note, this is the name of the
# file minus the extension (like ".txt" or ".db").  There is normally
# no need to change the default.

    RgbPath	"/usr/X11R7/lib/X11/rgb"

# Multiple FontPath entries are allowed (which are concatenated together),
# as well as specifying multiple comma-separated entries in one FontPath
# command (or a combination of both methods)

    FontPath   "/usr/X11R7/lib/X11/fonts/misc/"
    FontPath   "/usr/X11R7/lib/X11/fonts/Type1/"
    FontPath   "/usr/X11R7/lib/X11/fonts/TTF/"

EndSection

# **********************************************************************
# Server flags section.
# **********************************************************************

Section "ServerFlags"

# Uncomment this to disable the <Crtl><Alt><Fn> VT switch sequence
# (where n is 1 through 12).  This allows clients to receive these key
# events.

#    Option "DontVTSwitch"

# Enables mode switching with xrandr
# There is a report that this can cause Xorg not to work on some
# video hardware, so default is commented-out...
# but i want to use it in xorgwizard so leave on...

    Option "RandR" "on"

EndSection

#everything past here is auto-generated by Puppy's Xorg Wizard...


Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option      "XkbRules" "xorg"
	Option      "XkbModel" "pc102"
	Option      "XkbLayout" "us" #xkeymap0
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "IMPS/2" #mouse0protocol
	Option	    "Device" "/dev/mouse"
	#Option      "Emulate3Buttons"
	#Option      "Emulate3Timeout" "50"
	Option      "ZAxisMapping" "4 5" #scrollwheel
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
	HorizSync    31.5-79
	VertRefresh  50-85
	#UseModes     "Modes0" #monitor0usemodes
	Option      "PreferredMode" "1280x1024"
	EndSection
	
Section "Modes"
	Identifier "Modes0"
	#modes0modeline0
EndSection

Section "Device"
	### Available Driver options are:-
	### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
	### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
	### [arg]: arg optional
	#Option     "SWcursor"           	# [<bool>]
	#Option     "HWcursor"           	# [<bool>]
	#Option     "NoAccel"            	# [<bool>]
	#Option     "ShadowFB"           	# [<bool>]
	#Option     "UseFBDev"           	# [<bool>]
	#Option     "Rotate"             	# [<str>]
	#Option     "VideoKey"           	# <i>
	#Option     "FlatPanel"          	# [<bool>]
	#Option     "FPDither"           	# [<bool>]
	#Option     "CrtcNumber"         	# <i>
	#Option     "FPScale"            	# [<bool>]
	#Option     "FPTweak"            	# <i>
	#Option     "DualHead"           	# [<bool>]
	Identifier  "Card0"
	Driver      "vesa" #card0driver
	VendorName  "nVidia Corporation"
	BoardName   "GeForce 7600 GS"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
    DefaultDepth 16
    Subsection "Display"
        Depth       16
        Modes       "1280x1024"
    EndSubsection
EndSection

#PuppyHardwareProfile=NVIDIA

```

The Steps from here were to login, Go to System>>Administration>>Software Sources. Select the pre-release (karmic-proposed) repos. Allow this to update your sources, then run "Update Manager" and download all updates. After that, reboot. If the reboot succeeds, you should be able to go to System>>Administration>>Hardware Drivers and choose the correct driver. Reboot to enable. As Always, YMMV, and I can't explain WHY it worked, but it worked for me. I have not examined much else so I may discover other things arte broken, but at least I can get to a desktop.

Now, I just need to get sound working........


You have disabled your nvidia driver replace it with vesa.
of course your display may looks normal but you have lost your graphic card capabilities, can you still enable visual effects on your computer ?

---

### Post by BioVirtual on 2009-11-28
>  				 				**ATI & Nvidia: no X, just blinking on 2.6.31 (Karmic 9.10)** 			
 			 			 		   		 		 		I recentally upgraded to 9.10, and on doing so, when I rebooted, it had me enter my encryption passphrase, it seemed to boot fine, until it got to where the login screen should be showing. It flickered a lot, and only showed the command line login screen. Whenever it was flickering it would not let me type. Could this be a problem with GDM trying to start but cant? When I rebooted to the 2.6.18 kernel, it worked perfectly.


Follow up this:
*If you know where did you save the latest NVIDIA driver, pass step 6. Otherwise download it (step 6)
1- Restart you machine, After BIOS page repeatedly press Shift key. You will go to boot menu. 
2- Choose your Kernel (Most probably second option)
3- Choose root shell with networking
4- Type telinit 3
5- Log in with your account
6- wget [http://us.download.nvidia.com/XFree8...90.42-pkg2.run]("http://us.download.nvidia.com/XFree86/Linux-x86_64/190.42/NVIDIA-Linux-x86_64-190.42-pkg2.run") (Downloading the driver)
7- sudo sh ./NVIDIA-Linux-x86-190.42-pkg1.run
8- Follow driver installation steps
9- sudo reboot

I hope It helps.

---

### Post by deamon_knight on 2009-11-29
alan_tam_sh , Yes, You can enable desktop effects, as I only used the xorg.conf with the "vesa" driver to get Ubuntu 9.10 to boot to the desktop. From there everything works for me except sound. I could then Use "Hardware Drivers" to select the Nvidia Drivers and enable desktop effects. Downloading the drivers directly from Nvidia and installing from the command line works, but it breaks the next time a kernel update is released.

---

### Post by TGamel on 2009-11-29
I have been using Ubuntu for about three months with no problems, 9.10 even works great on my Acer 5050-3242 laptop with no problems. However, I just downloaded new updates to Ubuntu 9.10 per the update manager. It indicated that the machine needed to be restarted to activate updates, but the computer locks up every time. The update worked fine with no problems on my Acer laptop, however my Acer desktop will no longer boot, but becomes locked up as mentioned previously.
 

 I have re-booted the system more times than I can remember in order to try and get all the information hat I could. Any help with this boot problem will be appreciated.
 

 Here is what I see when I attempt to boot system:
 

 Grub loading please wait....
 Press 'ESC' to exit the menu (counts down from 2, 1 to 0)
 

 <then blank screen>
 

 Boot from (hd0,0) ext3 f4ed3c5e-1780-49fe-88b1-10353769ae53
 Starting up...
 

 Ubuntu logo
 

 Under logo in small letter says:
 

 One or more of the mounts listed in etc/fstab cannot be loaded.
 /:waiting for /dev/disk/by-uuid/f4ed3c5e-1780-49fe-88b1-10353769ae53
 (something I cannot read as it moves so fast)
 Press ESC to enter shell (if I hit 'Esc' at this point it does take me to a shell but I do not know what to do)
 

 <then blank screen>
 

 [COLOR=#ff0000]Boot from (hd0,0) ext3 f4ed3c5e-1780-49fe-88b1-10353769ae53[/COLOR]
 [COLOR=#ff0000]Starting up...[/COLOR]
 

 [COLOR=#ff0000]Ubuntu 9.10 todd-desktop tty1[/COLOR]
 

 [COLOR=#ff0000]todd-desktop login:[/COLOR]
 

 [COLOR=#000000]The text in red is flashing, when I try to enter text at the login prompt it does not work, not that I know what to do even if it would...[GRIN]... [/COLOR] 
 

 [COLOR=#000000]Now when the GRUB loader comes on I can hit ESC and load 9.10 under the older kernel and all works well, but this is kind of a pain in the backside to do every time I want to use Ubuntu. BTW I have already installed the NVIDIA 190.42 driver (at least Ubuntu says the driver is installed) and attempted a reboot but the same thing happens. I can use the system with the older kernel (2.6.28 but the new kernel (2.6.31) still will not work for me, get the same flickering and is locked up.[/COLOR]
 

 [COLOR=#000000]Here are my computer specs: AMD Aspire X3200[/COLOR]
 

 [COLOR=#000000]AMD Phenom x3 8400 triple-core processor 2.1 Ghz[/COLOR]
 [COLOR=#000000]4GB DDR2 memory[/COLOR]
 [COLOR=#000000]320GB SATA hardrive[/COLOR]
 [COLOR=#000000]SuperMulti double layer DVD+/-RW drive[/COLOR]
 [COLOR=#000000]Integrated NVIDIA GeForce 8200 graphics[/COLOR]
 [COLOR=#000000]Gigabit Ethernet[/COLOR]
 [COLOR=#000000]56k modem[/COLOR]
 

 [COLOR=#000000]BTW, I do have a CD of Ubuntu 9.10 from Canonical and I can boot the system with it and see the hard drive but I am not sure this will fix the problem. I have been reading many of the responses here and have tried a few suggestions with no luck. Any help would be appreciated.[/COLOR]
 

 [COLOR=#000000]Thanks,[/COLOR]
 

 [COLOR=#000000]Todd[/COLOR]

---

### Post by BioVirtual on 2009-11-29
Just follow the steps I mentioned, although you've already installed the driver. It won't hurt anything.

Let us know the result.

---

### Post by cubdukat on 2009-11-29
I have been fighting with NVidia drivers since at least 8.04, but this is the first time I haven't even gotten a low-res screen. 

I am truly confused at how people are saying that they're able to get things working with the NVidia drivers. I've tried installing them from both the restricted drivers repository and from NVidia's own binary package, but every time the results are still the same--a flashing terminal login screen that won't let me in. I've tried in both regular Ubuntu and Mythbuntu, but nothing seems to work.

Don't they both use the same allegedly "bulletproof" X manager?

The one thing I have noticed, however, is that there is no xorg.conf present in the system before install, and the one generated by nvidia-xconfig has no specific information about my display. Would I have to add that info manually, and if so, why would that not be detected on installation, if it was detected accurately on all previous versions?

Right now, I'm at the point where I'm about to wash my hands of both NVidia and Ubuntu. I have never had this many problems with a distro before. I don't think there's anything I'm missing, yet it still fails. As soon as I get home, I'll post the logs from a typical NVidia install. I have to reset the xorg.conf to default because it's currently doing the blinking terminal thing from a previous attempt.

---

### Post by cubdukat on 2009-11-29
Okay, I've gotten my system back. Here are my xorg log, the kernel log and my current xorg.conf file. The only difference between that and the old borked one is that the clean one says "nv" instead of "nvidia."

Oh, yeah, and the "nvidia-installer" log too...

I'm going to try adding the parameters of my monitor to the script to see if that helps.

---

### Post by alan_tam_sh on 2009-11-30
> **deamon_knight said:**
> alan_tam_sh , Yes, You can enable desktop effects, as I only used the xorg.conf with the "vesa" driver to get Ubuntu 9.10 to boot to the desktop. From there everything works for me except sound. I could then Use "Hardware Drivers" to select the Nvidia Drivers and enable desktop effects. Downloading the drivers directly from Nvidia and installing from the command line works, but it breaks the next time a kernel update is released.

hi thanks for your advice
I have since downloaded the software driver from nvidia.com and get it install as directed but very unfortunately the Hardware driver shows empty after I replacing "NVIDIA" with "vesa" driver in xorg.conf 
I have no idea what could possibly wrong? are you sure you can still activate the driver?

---

### Post by alan_tam_sh on 2009-11-30
> **cubdukat said:**
> I have been fighting with NVidia drivers since at least 8.04, but this is the first time I haven't even gotten a low-res screen. 

I am truly confused at how people are saying that they're able to get things working with the NVidia drivers. I've tried installing them from both the restricted drivers repository and from NVidia's own binary package, but every time the results are still the same--a flashing terminal login screen that won't let me in. I've tried in both regular Ubuntu and Mythbuntu, but nothing seems to work.

Don't they both use the same allegedly "bulletproof" X manager?

The one thing I have noticed, however, is that there is no xorg.conf present in the system before install, and the one generated by nvidia-xconfig has no specific information about my display. Would I have to add that info manually, and if so, why would that not be detected on installation, if it was detected accurately on all previous versions?

Right now, I'm at the point where I'm about to wash my hands of both NVidia and Ubuntu. I have never had this many problems with a distro before. I don't think there's anything I'm missing, yet it still fails. As soon as I get home, I'll post the logs from a typical NVidia install. I have to reset the xorg.conf to default because it's currently doing the blinking terminal thing from a previous attempt.

hi,
the display problem on your desktop indicate Ubuntu 9.10 have compatibility issue with the new nVidia proprietary drivers. This should not happen if Ubuntu developing team has tested the drivers before final release the 9.10.
To continue run Ubuntu you have to set default vesa driver of course you have to bear with the poor display quality otherwise you may try other OS. For me after my many fail attempts in resolving Ubuntu 9.10 nvidia issue I decided to give Win7 a chance. i love ubuntu very much but what have Ubuntu do to resolve the problem? Nothing at all after more that a month!! Now I feel sad for Ubuntu cos Win7 indeed a surprising good release that i have to admit there is something better out there... good luck Ubuntu good luck linux :-(
nevertheless, if the problem is eventually got resolve one day (but when??) i will still consider to go back to Ubuntu but I will not make it my primary OS....its just too risky.

---

### Post by nilgiri on 2009-11-30
My failure was caused by a bug in my motherboard.  I had maxed out the RAM during this process and after experiecning some issues in Jaunty as well, I removed it and all is well.  This is a bug I had seen before with this motherboard, but it didn't occur to me to try Koala without the extra RAM until I Jaunty failed to boot a couple times as well.

---

### Post by cubdukat on 2009-11-30
> **alan_tam_sh said:**
> hi,
the display problem on your desktop indicate Ubuntu 9.10 have compatibility issue with the new nVidia proprietary drivers. This should not happen if Ubuntu developing team has tested the drivers before final release the 9.10.
To continue run Ubuntu you have to set default vesa driver of course you have to bear with the poor display quality otherwise you may try other OS. For me after my many fail attempts in resolving Ubuntu 9.10 nvidia issue I decided to give Win7 a chance. i love ubuntu very much but what have Ubuntu do to resolve the problem? Nothing at all after more that a month!! Now I feel sad for Ubuntu cos Win7 indeed a surprising good release that i have to admit there is something better out there... good luck Ubuntu good luck linux :-(
nevertheless, if the problem is eventually got resolve one day (but when??) i will still consider to go back to Ubuntu but I will not make it my primary OS....its just too risky.

That's very disappointing to hear. I don't want to leave Ubuntu because I've worked with it for so long (and because Mythdora's too much of a pain to work with), but it appears that unless something is done with this pretty fast, I won't have much of a choice. 

Somehow, though, I have to wonder how much of this may be NVidia's fault. They've always seemed to be a thorn in the side of Linux for ages because of their refusal to release an open-source driver. I wish they'd explain what the hell is so top-secret that they can't reveal it to the public. 

At any rate, I believe that this will be my final go-round with both Ubuntu for a while, and Nvidia permanently. I never hear of ATI owners having this kind of problem. The last ATI card I had was the All-In-Wonder Radeon 8500DV, and I left them because they had horrible drivers in Windows (and no support in Linux), but it looks like it might be time for a changeI'll keep checking up on Ubuntu, though, and when they fix this problem, I'll be back, but until then...To misquote Christian Bale, "Me and Ubuntu are finished professionally" for the moment.

---

### Post by BioVirtual on 2009-11-30
Did you get your driver from this link (for 32bit)? Please make sure you are using the latest version:

[http://www.nvidia.com/object/linux_display_ia32_190.42.html](http://www.nvidia.com/object/linux_display_ia32_190.42.html)

---

### Post by benibuntu on 2009-11-30
I was having the same issue on nvidia 8600GT, with pae enabled after upgrading from 2.6.31-14 to -15.

I solved by uninstalling the pae version, going back to 2.6.31-14generic again and then reinstalling the 2.6.31-15generic-pae again.

In Jaunty (I used to run the server edition for 4GB+ RAM) the only video driver that worked after some effort was nvidia version 173 (not the default one by that time), as I was having the same blinking problem that time with the recommended one.

After uninstalling and installing back again the pae version, it stick with the 173 and as it's working, I probably won't fall the recommended 185 in Restricted Drivers (now Hardware Drivers).

---

### Post by alan_tam_sh on 2009-11-30
> **cubdukat said:**
> I have been fighting with NVidia drivers since at least 8.04, but this is the first time I haven't even gotten a low-res screen. 

I am truly confused at how people are saying that they're able to get things working with the NVidia drivers. I've tried installing them from both the restricted drivers repository and from NVidia's own binary package, but every time the results are still the same--a flashing terminal login screen that won't let me in. I've tried in both regular Ubuntu and Mythbuntu, but nothing seems to work.

Don't they both use the same allegedly "bulletproof" X manager?

The one thing I have noticed, however, is that there is no xorg.conf present in the system before install, and the one generated by nvidia-xconfig has no specific information about my display. Would I have to add that info manually, and if so, why would that not be detected on installation, if it was detected accurately on all previous versions?

Right now, I'm at the point where I'm about to wash my hands of both NVidia and Ubuntu. I have never had this many problems with a distro before. I don't think there's anything I'm missing, yet it still fails. As soon as I get home, I'll post the logs from a typical NVidia install. I have to reset the xorg.conf to default because it's currently doing the blinking terminal thing from a previous attempt.

due to my love and passion about Ubuntu, despite numerous attempt to leave ubuntu but no success, i decided to go back to 8.04 LTS. though it looks abit old fashion but it works very fine. I you don't mind the old fashion you may consider this option.

---

### Post by XanII on 2009-12-01
One thing i would like to know: if i activate nvidia proprietary drivers and everything goes to hell then the quickest way to 'restore' settings is to restore xorg.conf from a backup file or? 

Which also means that if i try out different drivers and they all fail and i get the flickering screen or similar then the best way out is to restore xorg.conf?

---

### Post by cubdukat on 2009-12-01
> **BioVirtual said:**
> Did you get your driver from this link (for 32bit)? Please make sure you are using the latest version:

[http://www.nvidia.com/object/linux_display_ia32_190.42.html](http://www.nvidia.com/object/linux_display_ia32_190.42.html)

If that's Nvidia's official site, yes. And I also got them from the restricted drivers menu on Ubuntu itself. Both yielded exactly the same results--a borked system.

---

### Post by huck416 on 2009-12-01
Hello,

Recently decided to upgrade from 8.10. Had reservations as I had read there were issues with ATI video cards. 

However, the upgrade to 9.04 (via adept version upgrade option) went smooth and sytem rebooted without difficulty. Everything appeared to be working including wireless networking.

Next day proceeded with upgrade to 9.10 via same method. Seemed to go smooth however system would not complete boot process. Stopped at black screen with single flashing cursor in top left corner; no disk activity either so ctrl-alt-del to reboot.

Selected "recovery" option and eventually was presented with a menu: resume normal boot, clean, etc. Chose the 'repair broken packages' option which went smooth however on reboot same results. Again into the 'recovery' option and this time selected 'resume normal boot'. Was eventually left at a login prompt. At times however there was garbage on the screen referring to an inability to mount drives (all network drives except the SWAP). Logged in and then sudo kdm start, voila, a functioning GUI with apparently all my files / programs intact.

Now I've gone through this thread and tried various solutions presented with no success. Other abnormalities include MySQL not loading correctly, still having to blacklist the bcm43xx driver to get my wireless to work, etc.

I tried installing xorg-driver-flgrx but when the desktop appeared it continually shut itself down and reported errors. When I removed (purged) xorg-driver-flgrx it worked again as before (loading only via the recovery option).

I find it very strange that I can get to a fully functional 9.10 desktop in a round-about way but cannot via a normal boot process.

My 2 cents.

EDIT - SOLVED - I deleted "splash" from the menu.lst line for the normal 31 kernel boot and now my system boots normally. Maybe it was hanging on trying to find a splash screen which I have never used and never had problems with before. But I'm not going to argue with sucess.

---

### Post by jaylsi on 2009-12-01
> **XanII said:**
> One thing i would like to know: if i activate nvidia proprietary drivers and everything goes to hell then the quickest way to 'restore' settings is to restore xorg.conf from a backup file or? 

Which also means that if i try out different drivers and they all fail and i get the flickering screen or similar then the best way out is to restore xorg.conf?

Yes. Before you play with video drivers, save a working /etc/X11/xorg.conf so that if anything goes wrong, restore it and reboot. Normally system automatically backs up xorg.conf, but you can get confused which one to pick when there are many backups.

For system upgrades, however, the previously working copy may not work with new kernel. In such case, you can remove xorg.conf, and start with default driver.

---

### Post by alan_tam_sh on 2009-12-02
> **jaylsi said:**
> Yes. Before you play with video drivers, save a working /etc/X11/xorg.conf so that if anything goes wrong, restore it and reboot. Normally system automatically backs up xorg.conf, but you can get confused which one to pick when there are many backups.

For system upgrades, however, the previously working copy may not work with new kernel. In such case, you can remove xorg.conf, and start with default driver.

This is how I get back my 9.04 up running with correct graphic driver activated after the disastrous 9.10 upgrade that fail me so badly.
My advice is you don't need to waste time to do clean installations for either 8.10, 9.04 or 9.10 or wahtsoever all these will not work if your graphic cards are not supported by default in 9.10.

Instead I choose to do a clean installation with 8.04 LTS, at this version all my hardwares are supported inclusive my ill fated geforce4 440MX nVIDIA graphic card.
Upon booting up with 8.04LTS i perform update until all available updates are done. I activate the graphic card driver from Hardware Driver to install the recommended driver, reboot. I got a very successful booting without problem. Now I got my system running Ubunutu 8.04 smoothly (looks very old fashion though).

Soon I got a prompt for upgrade to 8.10 from Update Manager. (*)I perform systems updates till i have no more updates available then i  proceed to perform 8.10 Upgrades. Once everything was done I reboot my system. I boot up my computer very smoothly without any problems. Now I am at Ubuntu 8.10. 

Again very soon I got a prompt for upgrade my system to 9.04 from Update Manager. I repeat (*) steps and reboot once all done.
This time i got a flickering screen at reboot just like the one i see when I upgrade to 9.10, nothing i can do here except hard reboot the system again. This time at the grub loader I choose "xfix Graphic card" option and reboot. System back to running fine this time, i got the X running well without problem. Then i proceed to perform update as usual. The last thing i do is to activate the graphic driver from Hardware Driver. After activated the driver as recommended and complete the installation, reboot. Well this time i managed to run my 9.04 without a problem with the geforce driver (96).
In total I spent about 6hrs to brings me upto here.

Of course the Update Manager will once again prompt me to upgrades to 9.10 .....but this i know is a trap that caught me so painfully before! I have learnt I will never do it again (until Ubuntu officially release a fix) otherwise I shall stop at 9.04 until my computer dies.

---

### Post by wnelson on 2009-12-02
I can get gdm to start by getting to the prompt loging in then su to root and executing gdm. Yet, if I try 'service gdm start' everything goes blank and then the cursor.

---

### Post by cubdukat on 2009-12-03
Think I may have just had an "a-ha!" moment here...

I was just googling Ubuntu and NVidia, and I stumbled upon something I think might help me. 

This is the link where I saw it:

[http://credentiality2.blogspot.com/2009/11/ubuntu-karmic-install-pae-kernel-breaks.html](http://credentiality2.blogspot.com/2009/11/ubuntu-karmic-install-pae-kernel-breaks.html)

I'm going to try this tonight and hopefully this will work, because if this is true, than I should expect these kind of issues in any distro that uses the PAE kernel, so dumping Karmic as I've planned to do would not solve the problem.

As they say, "better the devil you know..."

BTW, since the entire rationale behind PAE seems to be to open up the system to handling greater than 4GB, would this also happen in 64-bit, which if I understand it right, can already natively address greater than 4GB and shouldn't need PAE? I had thought 32-bit Linux could do that as well, but I guess I was wrong...

---

### Post by deamon_knight on 2009-12-04
Nvidia Drivers may be the problem on an upgrade, but as I posted, I was suffering this problem on a clean install. I have never seen the Proprietery Drivers loaded automatically, so whatever OpenSource drivers that are being used during the initial boot are the trouble. I suspect the 'nv" drivers aren't working right becuase of SOME underlying driver juggeling issues. Especially since installing the Nvidia drivers fixes this for people.

---

### Post by Jerubaal on 2009-12-04
[ATI Radeon 9600]

The clean install works with no problems at all.

The upgrade (different partition) doesn't:
1. It will boot in sort-of-properly, but after maybe a minute, goes to a black screen with flashing cursor. Works normally in the meantime.

2.i. Having noticed somewhere here about 9.10 behaving after pressing 'ESC' to go into some recovery mode, I tried that, and all was indeed well: but not a route for my computer-phobic wife to take.
2.ii. Next, I tried changing xorg.conf to use the 'vesa' driver, as suggested above. This booted ok, but still went to the black screen as before.
2.iii. Abandoning hope, I backed up everything I could think of & pasted it back into the clean install of 9.10 :P

:KS I now have a wife-friendly version of 9.10 :KS
(along with a host of other backup partitions I have lost track of :-({|= )

---

### Post by sxe4ever on 2009-12-04
Fighting all urges to do a clean install as I don't want to have to set everything back up the way that I prefer.  I have two 512MB ATI Mobility Radeon HD 3870 video cards.  I haven't been able to get video drivers to work on my laptop ever, so I've just been using the basic video driver without enhanced anything, even prior to this install.  I went to AMD's website to download the most recent drivers.  The installation goes through fine.  When I rebooted into either the newest build or the second to newest build they both have black screens.  The second to newest has never had sound for myself so I'm not sure if it's actually getting to the login screen, but I know the newest one is because I hear the little Ubuntu noise.  I deleted xorg.conf and tried again.  Got a blinking screen that wouldn't go to the main login screen (text based or GUI) on the newest build, and on the second to newest went to a black screen still.  After I uninstalled the driver, the newest build goes to a black screen, and the second to newest runs fine with basic drivers.  Any ideas here???? Please & thanks for any info.  Please let me know if anything else is needed!

---

### Post by sxe4ever on 2009-12-05
> **sxe4ever said:**
> Fighting all urges to do a clean install as I don't want to have to set everything back up the way that I prefer.  I have two 512MB ATI Mobility Radeon HD 3870 video cards.  I haven't been able to get video drivers to work on my laptop ever, so I've just been using the basic video driver without enhanced anything, even prior to this install.  I went to AMD's website to download the most recent drivers.  The installation goes through fine.  When I rebooted into either the newest build or the second to newest build they both have black screens.  The second to newest has never had sound for myself so I'm not sure if it's actually getting to the login screen, but I know the newest one is because I hear the little Ubuntu noise.  I deleted xorg.conf and tried again.  Got a blinking screen that wouldn't go to the main login screen (text based or GUI) on the newest build, and on the second to newest went to a black screen still.  After I uninstalled the driver, the newest build goes to a black screen, and the second to newest runs fine with basic drivers.  Any ideas here???? Please & thanks for any info.  Please let me know if anything else is needed!

I updated Linux with the newest updates that were available yesterday, but still having issues getting my computer to work.

If I try to create an Xorg.conf with Xorg -configure still no sound on the latest build and I'm back to my original problem, where I get the login screen (which looks fine) but it doesn't have any users or any ability to actually login.  If I use a backup Xorg that used to work it goes to the login screen, makes the noise, but still no option to login.

If I change nothing (still have a working xorg.conf from previously loaded) and just boot into the third newest build instead of the newest, everything works fine except for the sound which when I scroll over my output it states "Dummy Output"

My three newest builds are 2.6.31-16, 2.6.31-14, and 2.6.28-16.  Any help would be greatly appreciated!!!!

---

### Post by ktechman on 2009-12-05
Here is the solution for my Toshiba (A305-S6864) laptop with the "Mobility Radeon HD 3400 Series' VGA controller. 

First I purged all fglrx drivers by this method found in the ubuntu wiki

```
sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
  sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
  sudo apt-get install xserver-xorg-video-ati
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg
```

Then I deleted /etc/X11/xorg.conf, then rebooted my computer to make sure everything was cleaned up. I then installed the proprietary drivers from the repositories (if you open up Synaptic Package Manager and do a search for FGLRX you will see Xorg-Driver-FGLRX. This is what I installed. If you do not have a xorg.conf that is fine, the aticonfig commands will create it for you) . After I installed these drivers but BEFORE I rebooted my system I typed the following into the terminal.

```
sudo aticonfig --initial -f
   sudo aticonfig --acpi-services=off
```
This is directly quoted from this post

[http://ubuntuforums.org/showthread.php?t=1315199]("http://ubuntuforums.org/showthread.php?t=1315199")
 By: Lubberick
This worked the first time without a fuss.


Ktechman

---

### Post by DustofDust on 2009-12-05
i also posted there a solution

[http://ubuntuforums.org/showpost.php?p=8201026&postcount=23](http://ubuntuforums.org/showpost.php?p=8201026&postcount=23)

btw. the bug report [https://bugs.launchpad.net/ubuntu/+bug/464591](https://bugs.launchpad.net/ubuntu/+bug/464591) has some new infos which may help too.

---

### Post by ddeo on 2009-12-06
> **fasmike said:**
> I was not on a network, so I had some trouble doing exactly what you said above, but your method did work, thanks!  This is what I did:

[LIST=1]
[*]Use a different computer to download the NVIDIA-Linux-*.run for my new laptop
[*]Copy that new driver to a USB drive
[*]Boot to recovery mode on the new laptop [(had to look this up)]("https://wiki.ubuntu.com/RecoveryMode"):
[INDENT]Hit ESC just after your Bios loads when (in theory) you see the "Grub loading blah blah"  (it was WAY too fast to see it on my machine)[/INDENT]
[INDENT]A menu will come up with boot options, select the one that ends in (recovery mode)[/INDENT]
[INDENT]You are dropped at the root@yournmachine:~# prompt[/INDENT]
[*]Plug my USB drive into the laptop (after a few seconds I saw some stuff scroll by the screen)
[*]Mount the USB drive [(had to look this one up):]("http://help.ubuntu.com/community/Mount/USB")
[INDENT]Find the drive with the command: sudo fdisk -l  (mine was /dev/sdb1)[/INDENT]
[INDENT]Create a directory to mount it as: sudo mkdir /media/external [/INDENT]
[INDENT]Mount the drive:  sudo mount -t vfat /dev/sdb1 /media/external -o uid=1000,gid=100,utf8,dmask-027/fmask=137[/INDENT]
[INDENT]NOTE: if your USB is not FAT## you need a different -t option[/INDENT]
[*]Copied the new driver to my home directory (may not have been necessary)
[*]execute the NVIDIA-Linux-*.run file
[INDENT]I had to change permissions on the file before I could run it: chmod 777 NVIDIA*[/INDENT]
[INDENT]Ran the file with: ./NVIDIA*.run[/INDENT]
[*]Follow the instructions
[*]Reboot
[/LIST]

This made the flickering login problem go away and allowed me to get in and start using Ubuntu on my new machine.

I had a similar problem.  I ran the ubuntu 9.10 upgrade from my ubuntu desktop and when I rebooted I could log in but my gui was all messed up and then it crashed.  I followed your instructions and this worked perfectly for me.  THanks!  The only wrinkle was that I booted in recovery mode and when I ran the installer it gave me a warning...

```
You appear to be running in runlevel 1; this may cause problems. For example: some distributions that use devfs do not run the devfs daemon in runlevel 1, making it difficult for 'nvidia-installer' to correctly setup the kernel module configuration files. It is recommended that you quit installation now and switch to runlevel 3 ('telinit 3') before installing.
```

so i chose YES to exit the installer and at the command prompt typed

```
telinit 3
```

It then asked me to log in and then I ran the installer again and there was no warning and it installed...

On my first reboot the graphics were messed up again and my laptop rebooted automatically.  I then booting again and everything seems to be working correctly!  Thanks!  I'll report back if I notice anything unusual..

Ddeo

---

### Post by cubdukat on 2009-12-06
> **cubdukat said:**
> Think I may have just had an "a-ha!" moment here...

I was just googling Ubuntu and NVidia, and I stumbled upon something I think might help me. 

This is the link where I saw it:

[http://credentiality2.blogspot.com/2009/11/ubuntu-karmic-install-pae-kernel-breaks.html](http://credentiality2.blogspot.com/2009/11/ubuntu-karmic-install-pae-kernel-breaks.html)

I'm going to try this tonight and hopefully this will work, because if this is true, than I should expect these kind of issues in any distro that uses the PAE kernel, so dumping Karmic as I've planned to do would not solve the problem.

As they say, "better the devil you know..."

BTW, since the entire rationale behind PAE seems to be to open up the system to handling greater than 4GB, would this also happen in 64-bit, which if I understand it right, can already natively address greater than 4GB and shouldn't need PAE? I had thought 32-bit Linux could do that as well, but I guess I was wrong...

Well, just like every other problem I've had installing this monstrosity, this didn't work either. So now I'm going to do a clean install, update everything afterwards and uncheck the PAE kernel, since that seems to be the root of the problem. I also intend to download and install the 64-bit version of Mythbuntu and/or regular Ubuntu, since there is no PAE kernel. 

Failing that, I'm just going to swear off Linux on my main system for a while since it's just too much hassle.

---

### Post by Neondog on 2009-12-06
Have you seen [this]("http://www.howtoforge.com/enabling-compiz-fusion-on-an-ubuntu-9.10-desktop-nvidia-geforce-fx-5200")?

---

### Post by mcunix on 2009-12-06
Very similar problem. Upgraded from 9.04 to 9.10. Ran just fine until update to 2.26.31-16 and blooey - can't even boot to LiveCD.

Can boot to an XP CD tho. 

Running ARECA 1210 RAID5 on 3 partitions:
- ubuntu
- xp
- huge 3TB data

---

### Post by Clancy_s on 2009-12-06
> **DustofDust said:**
> sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon xorg-driver-fglrx
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
dpkg-reconfigure xserver-xorg
sudo apt-get install xserver-xorg-video-mach64

last line or radeon or fglrx depending which generation of card you have.

I don't quite follow the last line there: do I use the radeon or fglrx in place of the *mach64* in the last line or do I add another line with the radeon or fglrx and if that's the case what's the syntax?  :confused:

Exactly what should the commands be if I want to use radeon?

---

### Post by cubdukat on 2009-12-07
> **Neondog said:**
> Have you seen [this]("http://www.howtoforge.com/enabling-compiz-fusion-on-an-ubuntu-9.10-desktop-nvidia-geforce-fx-5200")?

Yes I have, but it does not work. But as luck would have it, my theory about the 64-bit version not having those issues was correct. I installed the 64-bit version of Mythbuntu, and it seems to be cooperating quite nicely. 

I finally have the binary drivers up and working!

Which leads me to believe that the problem lies either with NVidia's drivers or the PAE kernel, or both.

---

### Post by DustofDust on 2009-12-07
> **Clancy_s said:**
> I don't quite follow the last line there: do I use the radeon or fglrx in place of the *mach64* in the last line or do I add another line with the radeon or fglrx and if that's the case what's the syntax?  :confused:

Exactly what should the commands be if I want to use radeon?

if you have a radeon just drop my last line with mach64 and use instead the following

sudo apt-get install xserver-xorg-video-radeon

if you want to use the closed source drivers and you have a newer card which is supported by ati then it is 

sudo apt-get install xserver-xorg-video-fglrx

[http://wiki.x.org/wiki/Projects/Drivers](http://wiki.x.org/wiki/Projects/Drivers)
for a bigger view about what is going on

---

### Post by ddeo on 2009-12-07
> **ddeo said:**
> 
On my first reboot the graphics were messed up again and my laptop rebooted automatically.  I then booting again and everything seems to be working correctly!  Thanks!  I'll report back if I notice anything unusual..

Hi, to clarify, I should have mentioned which graphics card I have.  It is a GeForce 8400M GT

Now that I have been using the computer for a while I am noticing little video glitches.  Ofter when moving the mouse around on the screen.  It is hard explain...

I know there is nothing wrong with the hardware because I don't have any problems on the Windows side of this dual boot.

Can anyone tell me if there is anything I can try to fix this?  Again, I installed the latest driver using the method described earlier in this thread by [fasmike]("http://ubuntuforums.org/showthread.php?p=8198141#post8198141").

Thanks, Ddeo

---

### Post by cubdukat on 2009-12-07
> **cubdukat said:**
> Yes I have, but it does not work. But as luck would have it, my theory about the 64-bit version not having those issues was correct. I installed the 64-bit version of Mythbuntu, and it seems to be cooperating quite nicely. 

I finally have the binary drivers up and working!

Which leads me to believe that the problem lies either with NVidia's drivers or the PAE kernel, or both.

An update...

IT WORKS!!!!!

I now have perfectly-accelerated, VDPAU-powered Nvidia graphics!

Guess there really is something to running a 64-bit distro...

I just wish I had thought of it sooner...

---

### Post by XanII on 2009-12-07
Whew. what a relief. the latest update offered finaly fixes this. 

I was already with bootable USB-stick in hand ready to attempt fixing of the mess again, but no. this time 185 nvidia drivers that the system recomends works. no hassles no blinking no nothing. 

I am so happy to have my windows key+e zoom compiz function back again. ;)

---

### Post by Carthorse on 2009-12-07
I can't even get the live cd to work. Same prob as others here, blinking if booting into low graphics or 'out of range' if booting normally. Don't think I'll be hitting the 'install' option. Thats the 64bit, my 32 bit works fine. If I were braver, I'd install and hope for the best but I have a nicely working system so it'll have to wait until I'm bored and have a full day or two to play :-) Not afraid of the cli or vi!
Sadly, I've not the capacity to do a massive download of an iso image, so that's out.

---

### Post by Clancy_s on 2009-12-08
> **DustofDust said:**
> if you have a radeon just drop my last line with mach64 and use instead the following

sudo apt-get install xserver-xorg-video-radeon

if you want to use the closed source drivers and you have a newer card which is supported by ati then it is 

sudo apt-get install xserver-xorg-video-fglrx

[http://wiki.x.org/wiki/Projects/Drivers](http://wiki.x.org/wiki/Projects/Drivers)
for a bigger view about what is going on

Thanks for the clarification and the link: looking for something with that information was on my todo list for next weekend.  Theoretically fglrx supports my card (mobility radeon HD2600, M700), in practice no-one seems to have gotten it to work.  I'll try your approach, if that fails I plan on switching to a testing kernel and radeon drivers which support 3D.

---

### Post by Carthorse on 2009-12-08
Just tried (out of interest) to boot live cd 32bit. Same prob. It suggests a problem with the video driver 'nv' and my integrated graphics, nVidia 7025/n630. My working install was done on my previous motherboard  on an AGP GeForce 5200, with the Ubuntu advised nVidia driver activated afterward. No way to log on means that option, from a live cd, means no solution? I'm ordering a PCIe 8400GS. The integrated graphics was only ever going to be a stop-gap but it looks like I'm pushed to go for add-on much sooner than I'd have liked, if I want 64bit.

---

### Post by chessmani on 2009-12-09
Indeed, everything seems to be solved with the latest upgrades.

---

### Post by Carthorse on 2009-12-11
Posting from live cd. Seems the on-board graphics was the problem (for me, at least) as I installed the PCIe card and everything looks to be working so far.

---

### Post by mpp123 on 2009-12-11
I too have experienced the blinking screen installing Karmic 9.10 xAMD64:

AMD x2 - 5400
4 G Ram
Asus M2N SLI mb
nVidia GEForce 8500 GT video
300 GB SATA drive

This was a clean install to a 65 GB ext4 partition using Karmic 9.10 ISO burned to CDR

Install went clean, but, on first reboot, blinking ascii text to screen:

usplash: setting mode 1152x864 failed
             using mode 1024x768

[5.57598] ACPI I/O resource nForce2-Smbus [0x4C00-0x4C3F] conflicts with ACPI region
               SM00 [0x4C00-0x4C05]
[5.576042] nForce2-Smbus 0000:00:01:1 Error probing SMB1
Ubuntu 91.0 Ubuntu-desktop tty1
Ubuntu-desktop login:

I was able to enter the username, but the password never took as the screen was continuously blinking.

I booted from the Live CD, logged in using my username/password and was able to download the nVidia-Linux*.run file from nVidia. The drivers installed, and when I rebooted, the same error as above came back up.

I cleaned the partition (zero'd the bits), created a new 65 GB ext3 partition and installed Intrepid 8.10 xAMD64. The install went well and the GUI booted perfect. I downloaded and installed the latest nVidia Linux drivers. 

Since then, I have upgraded to 9.04 and will not go any further.

I hope this info helps...

Regards,
Michael

---

### Post by Cindarh on 2009-12-13
I'm new to this OS. I downloaded 9.10 and was attempting to run it from the cd (Trial). It show some stuff on the screen but after a few seconds my monitor shows, "no signal" and goes into standby. I would really like to start using Linux but I'm not having any luck from the get go. Anyone have any ideas? I've tried some things people have mentioned regarding my ATI card, but they were giving me advice for a completely different version of this OS. I would like some help pertaining to 9.10.
 
System:
P4 2.8
4GB RAM
160GB SATA HDD (2x80GB running RAID)
ATI HD3650 GPU
currently using XP PRO
SB XFI X-treme gamer
intel d875pbz mobo
 
Thanks for any information you guys can provide.

---

### Post by mammalien on 2009-12-16
I have a similar problem. When I rebooted after one of the kernel updates, (2.6.31-15 I think) I got a nice little box telling me that ubuntu could not detect my video card. with the option to reboot to console from the trouble shooting dialogues that followed i found that X was working fine with the Nvidia drivers if I start x with

sudo service kdm restart

I have tried with both the repository vddpau and the package straight from NVIDIA but It will not boot straight to X

Has this got something to do with the boot up maybe doing too many things at once?, I noticed that fsck now runs in the background

---

### Post by sxe4ever on 2009-12-16
> **ktechman said:**
> Here is the solution for my Toshiba (A305-S6864) laptop with the "Mobility Radeon HD 3400 Series' VGA controller. 

First I purged all fglrx drivers by this method found in the ubuntu wiki

```
sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
  sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
  sudo apt-get install xserver-xorg-video-ati
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg
```Then I deleted /etc/X11/xorg.conf, then rebooted my computer to make sure everything was cleaned up. I then installed the proprietary drivers from the repositories (if you open up Synaptic Package Manager and do a search for FGLRX you will see Xorg-Driver-FGLRX. This is what I installed. If you do not have a xorg.conf that is fine, the aticonfig commands will create it for you) . After I installed these drivers but BEFORE I rebooted my system I typed the following into the terminal.

```
sudo aticonfig --initial -f
   sudo aticonfig --acpi-services=off
```This is directly quoted from this post

[http://ubuntuforums.org/showthread.php?t=1315199](http://ubuntuforums.org/showthread.php?t=1315199)
 By: Lubberick
This worked the first time without a fuss.


Ktechman

I did everything in the first step as described using the recovery mode for the latest build.  I then dropped to the 3rd newest build for the part that required Synaptic Package Manager.  When I installed xorg-driver-fglrx it said that it was removing some nvidia-glx drivers which seemed alright as I'm using ATI video cards.  The installation went through fine, and I adjusted the aticonfig appropriately.

I booted into the newest build of 2.6.31-16 and just got a black screen.  I did hear the login noise however, so apparently it did load completely, I just don't have any video.  Booted into the third newest build of 2.6.28-16  and was still getting a black screen.  The sound has never worked on this build, but I didn't hear a login noise.

Deleted xorg.conf file using the recovery mode of the newest build and booted into the newest build again.  Black screen still with the login noise.  When I went into the third newest build, it worked fine but still no sound.

There were a bunch of updates though that were available, so I installed those.  Requested for a restart, so I restarted into the newest build.  It said "glrx (8.660)........fail!" "nvidia (185.18.36)......done" at one point, but then it just freezes on enabling laptop mode....  Rebooted, checked to make sure that xorg.conf was not present and it's not, rebooted and tried the third build again without changing anything, and it worked fine, again with no sound though.

---

### Post by sxe4ever on 2009-12-16
> **sxe4ever said:**
> I did everything in the first step as described using the recovery mode for the latest build.  I then dropped to the 3rd newest build for the part that required Synaptic Package Manager.  When I installed xorg-driver-fglrx it said that it was removing some nvidia-glx drivers which seemed alright as I'm using ATI video cards.  The installation went through fine, and I adjusted the aticonfig appropriately.

I booted into the newest build of 2.6.31-16 and just got a black screen.  I did hear the login noise however, so apparently it did load completely, I just don't have any video.  Booted into the third newest build of 2.6.28-16  and was still getting a black screen.  The sound has never worked on this build, but I didn't hear a login noise.

Deleted xorg.conf file using the recovery mode of the newest build and booted into the newest build again.  Black screen still with the login noise.  When I went into the third newest build, it worked fine but still no sound.

There were a bunch of updates though that were available, so I installed those.  Requested for a restart, so I restarted into the newest build.  It said "glrx (8.660)........fail!" "nvidia (185.18.36)......done" at one point, but then it just freezes on enabling laptop mode....  Rebooted, checked to make sure that xorg.conf was not present and it's not, rebooted and tried the third build again without changing anything, and it worked fine, again with no sound though.

Tried to reinstall the fglrx driver, did the aticonfig again and rebooted into the newest build, still only sound and black screen.  Third newest build, froze on enabling laptop mode telling me that nvidia was done again and that ati failed again.  Rebooted into the third build again (without changing anything) and just got a black screen with no sound. Deleted xorg.conf.  Rebooted into newest build - black screen with sound.  Third newest build - works fine but with no sound yet again

---

### Post by JoCkEr7 on 2009-12-17
Thank you so much

---

### Post by alan_tam_sh on 2009-12-19
Due to bitter 9.10 upgrading experience with serious failures on my geForce4 MX440 card for more than 2 months ago, I am retract back and still holding on the 9.04.
Is the Ubuntu 9.10 graphic cards support problem particular the card i mentioned here solve now?
Can anyone be do kind to give some lights on this before i jump into upgrading again? thank you

---

### Post by golfdiesel on 2009-12-21
Is there allready an updated live cd/DVD which works normally?
Both with a Nvidia and a ATI videocard the screen keeps blinking.

---

### Post by Specologic on 2009-12-24
Hello,

My conclusion it that there is a problem with Nvidia driver and Compiz. I would like to resolve this problem, I like Compiz but dammm.... the blinking is just so frequent. I had Karmic installed with the blinking problem, than I downgraded to Jaunty and the problem maintained. First I tried the version 185 or 180 drivers of Nvidia but the problem didn't vanish and than I tried the last Nvidia drivers 190.54 and the problem maintained.. If I remove Compiz the problem gets fixed, there is no blinking. But I like the effects of Compiz :x, hope there will be a solution. I'm loving Ubuntu and I'm a new guy at Linux but this problem dammmm :x.
My graphic card is GeForce 7600 Go and I have tried the 32bits and 64bits Systems..

Best Regards

---

### Post by golfdiesel on 2009-12-25
It seems that Ubuntu doesn't care about the users. The current live dvd still has the problem. 
Ubuntu lost a user...

---

### Post by Beastlicker on 2009-12-27
Hey. I don't even get the chance to install ubuntu due to the flashing. I get to the cd boot up screen, and choose "Try ubuntu without any changes" After that, the glowing logo comes up, then once that is finished, a terminal shell comes up and flashes with some errors, and sometimes "ubuntu@ubuntu$". I can get into the try ubuntu option using safe graphics, but will installing it cause the flashing?

P.S, I was able to install ubuntu before with my old video card, I was just doing a new install.

System:

2 gb RAM
3.06 ghz processor
nvidia geforce 9800 gt
500 gb hdd, 160 gb hdd
x64 machine.

Currently running windows 7 home premium.

---

### Post by Hrodnovar on 2009-12-27
Same flashing on and off with ATI HD 4200.  Makes all versions of Ubuntu unusable.  The screen won't stay viewable long enough to download current drivers from ATI or anything.  

I really like Ubuntu but it just does not work with this hardware.  Video, ATI HD 4200, is on the MOBO.

Model #: p6230y
Product #: NY549AA-ABA
Serial #: MXX9390G9R
Software Build #: 94NAv6PrA2
Service ID #: 103-009
PCBRAND: Pavilion

:confused:

---

### Post by yyg on 2009-12-29
I am working on solving this same issue using fasmike's great instructions.  I am losing power to my keyboard after going into recovery mode.  I felt that it should probably be put in a new thread, so if you think you can help.  Head over [here]("http://ubuntuforums.org/showthread.php?p=8577507#post8577507").

---

### Post by John Pizzapone on 2009-12-30
I had a similar problem : I couldn't boot from the live-cd (blinking on a command prompt).

Then I tried an installation from the alternate CD, the installation process went fine but same symptoms appeared on first boot.

Then I rememered that the same live CD used to work on the same machine, so I tried to guess what could have changed since, and I found : the DVI output used ! When I plugged my screen on the other DVI output of my Geforce 6800, it all worked !!

Hope this helps

---

### Post by pritcharded on 2009-12-30
My PC is Dell 390 Intel Core 2 duo with 4Gb memory, ATI FireGL V7200 graphics card. It has Vista, 8.04 and 9.10 installed.
Selecting 9.10 from cold causes "entering power save" to appear every time (on a black screen). Meanwhile the PC seems to be progressing to the log in screen.
If I select either 8.04 or Vista, both boot normally and both run without fault. If I run either for a short period and then reboot to 9.10, nearly every time it too boots normally (almost) and runs flawlessly. 
The "almost" refers to the fact that after 8.04 or Vista closes, Grub2 appears to hang for a period before starting to interrogating the discs.
Once 9.10 is running the graphics are very good, indeed the whole system is markedly nicer to use than 8.04.
It seems to me that Grub2 must be failing to install something that fires up the graphics card, but if the machine has been running 8.04 successfully the graphics card retains sufficient memory for a short period to correctly fire up again under 9.10.
As I get further than most of the posts here, examining this one in detail might throw up the solution to the whole thread. If someone expert can hold my hand on this , I'm happy to try to chase this down.

Ted

---

### Post by Freedom Sky on 2010-01-01
Hello everyone. Forgive me if I'm typing with errors. I'm from Russia and the first time in this forum. I use translation software Dicter, to roughly understand what is at stake. I can not run version 9.10. On screen the message "Out of Range". Perhaps the reason my computer. I installed nVidia 7600 GS 256. And, please, help as and where you can get the software for Ubuntu. I even set the screen can not change. Thanks in advance. Alexey (Or call me Alex, if you are more familiar).
 
PS If possible, please contact me by ICQ (426486264). Maybe because you help me more. And I'm looking for new friends.:) By the way, Happy New Year! :)))

---

### Post by alan_tam_sh on 2010-01-02
> **Beastlicker said:**
> Hey. I don't even get the chance to install ubuntu due to the flashing. I get to the cd boot up screen, and choose "Try ubuntu without any changes" After that, the glowing logo comes up, then once that is finished, a terminal shell comes up and flashes with some errors, and sometimes "ubuntu@ubuntu$". I can get into the try ubuntu option using safe graphics, but will installing it cause the flashing?

P.S, I was able to install ubuntu before with my old video card, I was just doing a new install.

System:

2 gb RAM
3.06 ghz processor
nvidia geforce 9800 gt
500 gb hdd, 160 gb hdd
x64 machine.

Currently running windows 7 home premium.


delete the xorg.conf then reboot before that pls copy xorg.conf to xorg.conf.backup just in case you need it back later.
btw are you running Linux kernel 2.6.31.16? for me i am running this linux kernel without any problem though i do encountered similar blinking problem but now i am okay everything are just great.

---

### Post by alan_tam_sh on 2010-01-02
> **Freedom Sky said:**
> Hello everyone. Forgive me if I'm typing with errors. I'm from Russia and the first time in this forum. I use translation software Dicter, to roughly understand what is at stake. I can not run version 9.10. On screen the message "Out of Range". Perhaps the reason my computer. I installed nVidia 7600 GS 256. And, please, help as and where you can get the software for Ubuntu. I even set the screen can not change. Thanks in advance. Alexey (Or call me Alex, if you are more familiar).
 
PS If possible, please contact me by ICQ (426486264). Maybe because you help me more. And I'm looking for new friends.:) By the way, Happy New Year! :)))

Did you installed the nVidia software directly from the System->Hardware Drivers? You should not face much problem if you install thre recommended driver from there but beofre that please check if your Linux Kernel version, i advice you to install Linux Kernel 2.6.31.16 if you are not.

---

### Post by joy23 on 2010-01-02
> **JBAlaska said:**
> Your Nvidia drivers have to be recompiled (installed) for the new kernel. Go to the Nvidia site, print the instructions (as you have to do this from a CLI), and follow the directions. you should be ok after the final restart of your X server.


I have the problem like there's no flickering just bkank black screen after installing nvidia driver.
any suggestions for this?](*,)](*,):shock:
can't go anywhere i really need help.
I could start X-server did as said for installing nvidia driver.
Can u all suggest any guide from where i could learn more about commands:confused:

Running intel core2duo 
nvidia 9500 GT
2gb ram

am using win XP on c: drive 
and karmic on k:

---

### Post by freackout on 2010-01-02
> **Jekshadow said:**
> I recentally upgraded to 9.10, and on doing so, when I rebooted, it had me enter my encryption passphrase, it seemed to boot fine, until it got to where the login screen should be showing. It flickered a lot, and only showed the command line login screen. Whenever it was flickering it would not let me type. Could this be a problem with GDM trying to start but cant? When I rebooted to the 2.6.18 kernel, it worked perfectly.

your new setup ie you changed the setup for your xorg.conf ie useually better idea to back it up... ie mv xorg.conf toanother.bak.
if you do this in with mint 8 as i had once the initialisation of trying to set it up again ok your using ati but i was using nvidia on another box and it dosn't like the name xorg.conf.backup or was it .bak, because it tried to rename the next or even empty xorg.conf file to the backup, get the drift. ok its all feasable. however on my ati system i simply as it seamed a good idea at the time.... did the following
sudo apt-get remove --purge xserver-xorg
sudo apt-get install xserver-xorg
and it detected and setup all my xorg.conf for me ok easy init...reboot or even just startx. if yo struggling look at the basics all yo settings will stay same ie icons on desktop ect..

---

### Post by freackout on 2010-01-02
> **macogw said:**
> Can you folks file bugs using "ubuntu-bug xserver-xorg" ?

yup i did 
sudo apt-get remove --purge xserver-xorg
sudo apt-get install xserver-xorg
startx
and guess what .... brilliant.....alls fine now, same icons nothing lost lovely.

i even tried removing the actual desktop before that, but i did not have to as that was not the problem......

---

### Post by Aceshigh8330 on 2010-01-04
> **freackout said:**
> yup i did 
sudo apt-get remove --purge xserver-xorg
sudo apt-get install xserver-xorg
startx
and guess what .... brilliant.....alls fine now, same icons nothing lost lovely.

i even tried removing the actual desktop before that, but i did not have to as that was not the problem......
This worked great for me as well with one exception.

I am a novice to Linux but Google has helped me make it through this ordeal along with a bit of inspiration and careful thought. I've run some other versions of Ubuntu but never really had to do anything with the command line.

As with most everyone I am sure the flicker made it completely impossible to type in a password. 

I used a recommendation to use the recovery kernel by pressing esc during boot and typing the command:
sudo passwd username 
and enter a new password that was shorter than my original password. This enabled me to get to the point I could run the above quoted commands.

However after I tried to startx the system would not start so I rebooted. Now I am getting a line that stated that the system could not update the ICEauthoriy file
/home/user/.ICEauthority and nautilus failed to load anything beyond a background image.

I ended up coming across some permissions pages on google and figured that the reason nautilus was failing to load is because I choose to encrypt my home directory during installation and I had just changed my password to the letter "a" to get past the flicker and fix the graphics bug. Sure enough using alt+f6 and logging into my account with the password "a" and re-running the sudo passwd username command I was able to change it back to the originally installed encrypted password. I attempted a reboot and the OS booted fully. Hooray!!! 

Hopefully this can help someone else that stumbles into this hairy situation.

---

### Post by grauniadangel on 2010-01-06
Hi,

I can log in but only using a text page - is there a correct command to install the Ubuntu splash screen again ?

Thanks


John

---

### Post by teejcee on 2010-01-06
Sort of "off-topic" but has anyone else noticed that the title of this thread keeps changing to......

> Re: Ubuntu will not boot successfully with 2.6.31 kernel, but fine with 2.6.28 kernel....and then back again???

---

### Post by awwong on 2010-01-06
> **awwong said:**
> I have the same issue with the Live CD - slow burned and md5 checked.

My system is a Dell XPS 3.0 GHz, 2.0 GB RAM, nVidia GeForce 7600 GS.Replying to myself... weird, but what I discovered as a Live Cd fix is also weird...

I never thought that changing my old monitor - a ViewSonic PF790 Color Monitor (CRT) - with a new NEC MultiSync EA231WMi monitor (LCD) would get rid of the flashing, no loading X problem with the Live CD, but it has!  

Now Karmic boots on my old Dell as well... go figure... this is not a viable solution for most because of the expense, but my poor old monitor has just about had it.

My system specs:
Dell XPS Pentium 4 3.0 GHz [hyperthreaded]
2.0 GB RAM
AGP nvidia Geforce 7600GS
new NEC MultiSync EA231WMi LCD monitor

---

### Post by genux05 on 2010-01-07
Not sure is this helps, but I had a similar problem in that the nvidia graphics memory allocation from the ACER BIOS was saying to use the 0xb0000000 - 0xbfffffff (BAR 15 and BAR 1 errors happened because this is where the system ram is).  So I had to alter the arch/x86/pci/i386.c file, well more of a hack / test to make it to work, but looking into doing a more permanent hack that will do the memory allocation dynamically. 

In essence, the hack is.
```

if ((r->start >= 0xc0000000) && (r->end <= 0xcfffffff)) {
	dev_info(&dev->dev,                              
		  " not allocating resource 0xc - 0xcf %pR\n",
		  r);                                         
	/*                                                   
		stop any resources gaining the 0xc0000000 - 0xcfffffff
		region, the linux kernel will re-place them.          
	*/                                                            
	r->flags = 0;                                                 
}                                                                     

/* where the nvidia is going and replace in the above region */
if ((r->start == 0xb0000000) && (r->end == 0xbfffffff)) {      
	r->start = 0xc0000000;                                 
	r->end = 0xcfffffff;                                   
}  
``` 

I have put more details about the [BAR 15 - BAR 1 nvidia graphics card problem on here]("http://www.codingfriends.com/index.php/2010/01/07/bar-15-bar-1-no-parent-nvidia-graphics-card-does-not-work/")

---

### Post by mungo63 on 2010-01-08
I think this is the same problem I have. My 9.04 system was working fine.  Then  I upgraded from 9.04 to 9.10, and now there is an issue with the nvidia driver.  I can't get the Ubuntu gui to come up.  I did manage to get it up in a low-res mode somehow, but it won't let me install the driver.  I've read up on the issues in the 9.10 release notes/bug reports, but it is not clear to me how to solve the problem.  One solution was to comment some lines in /etc/modprobe.d/lrm-video file, but I don't see that file in my system. Any ideas to resolve this would be appreciated.

---

### Post by 1993 on 2010-01-09
I had a similar problem on my laptop with Nvidia graphics. I killed the X server (cntrl alt backspace) and did a safe login (I forget the exact name of the option but it's with window manager, not a terminal). From then on everything worked. On my desktop I had a similar problem with ATI graphics (HD2400) and I did a safe boot, followed by a safe login session (again I forget the exact terms). I don't remember the exact sequence and with older versions of Ubuntu I sometimes have had to repeat the process 2 or three times especially after changing the video drivers to get the right sequence.

I also noticed that using KDE gave fewer problems than Gnome and at one point with jaunty I could only use KDE until I made some unknown change and things worked again.
The key seems to me to be to get any correct display in any mode with the driver you want to use and then for me it keeps working even after reboots and resolution changes etc.


I

---

### Post by pritcharded on 2010-01-09
> **John Pizzapone said:**
> I had a similar problem : I couldn't boot from the live-cd (blinking on a command prompt).

Then I tried an installation from the alternate CD, the installation process went fine but same symptoms appeared on first boot.

Then I rememered that the same live CD used to work on the same machine, so I tried to guess what could have changed since, and I found : the DVI output used ! When I plugged my screen on the other DVI output of my Geforce 6800, it all worked !!

Hope this helps

> **pritcharded said:**
> My PC is Dell 390 Intel Core 2 duo with 4Gb memory, ATI FireGL V7200 graphics card. It has Vista, 8.04 and 9.10 installed.
Selecting 9.10 from cold causes "entering power save" to appear every time (on a black screen). Meanwhile the PC seems to be progressing to the log in screen.
If I select either 8.04 or Vista, both boot normally and both run without fault. If I run either for a short period and then reboot to 9.10, nearly every time it too boots normally (almost) and runs flawlessly. 
The "almost" refers to the fact that after 8.04 or Vista closes, Grub2 appears to hang for a period before starting to interrogating the discs.
Once 9.10 is running the graphics are very good, indeed the whole system is markedly nicer to use than 8.04.
It seems to me that Grub2 must be failing to install something that fires up the graphics card, but if the machine has been running 8.04 successfully the graphics card retains sufficient memory for a short period to correctly fire up again under 9.10.
As I get further than most of the posts here, examining this one in detail might throw up the solution to the whole thread. If someone expert can hold my hand on this , I'm happy to try to chase this down.

Ted

Many thanks, many thanks to John Pizzapone. I swapped DVI outlets and as was the case for John, all my problems instantly disappeared! Clearly there is a flaw in the script that controls the graphics card.

I couldn't get 9.04 to work either and gave up on it (blank screen blinking similar to most of the posts on this thread). I dumped 9.04 and can't check but I suspect my problem with it was due to the same cause.

I also have had my problem listed on Launchpad so I will put in a bug report.

Ted

---

### Post by bonixavier on 2010-01-10
Hi everyone!

I`m a total linux noob and I`m experiencing the same problem. I downloaded the NVIDIA driver and have it stored in two places: a cd and the c: (windows) partition. The problem I have is that I don`t know how to access the file from the prompt line (using recovery mode). I tried to reach the dev/sda1 (which is the c: name) and the cd, but I don`t know how to get there from the prompt. What commands should I type?

Another possibility would be (and that`s what I`m trying to do) using the Live CD to try to transfer the file to my hard drive, but I don`t seem to be able to get the clearance necessary. I attempted to login using my Ubuntu login from the Live CD, but to no success. What should I do?

I have no Flash Drives to store the file, only cds and dvds. Sorry for such a noob question.

Edit: Nevermind. I was able to run it by running a sudo mount /dev/sda1 /mnt/cdrom/ (a directory I had created), then I ran sudo sh ./NVIDIA-Linux-x86-190.53-pkg1.run and it is now working. I remembered to unmount what I had mounted, although I don't know if that was really necessary.

---

### Post by britseye on 2010-01-14
> **freackout said:**
> yup i did 
sudo apt-get remove --purge xserver-xorg
sudo apt-get install xserver-xorg
startx
and guess what .... brilliant.....alls fine now, same icons nothing lost lovely.

i even tried removing the actual desktop before that, but i did not have to as that was not the problem......
The approach of uninstalling and installing X worked for me also. This makes me think the whole issue is nothing to do with particular drivers, since my 'video card' is SiS. I had done the torrent download of 9.10-alternate over an evil slow connection, with many shutdowns en route, verified its checksum, and installed it without errors. Then when the install restarted I got a lot of flash-by text and eventually a command prompt. So following the lead, I uninstalled X:

sudo apt-get remove --purge xserver-xorg

Then tried to reinstall, when it told me to put the CD in the drive. I never made a CD, so I mounted the ISO with

sudo mount -o loop ~/Desktop/ubuntu-9.10-alternate-i386.iso /media/cdrom0

Then the reinstall of X worked:

sudo apt-get install xserver-xorg
startx

and BINGO! - back in business.

So it would seem that the upgrade procedure is not doing the same thing as apt-get install xserver-xorg.

---

### Post by sxe4ever on 2010-01-16
When I tried uninstalling and reinstalling 'X' like it's listed above the same thing happens.... I get a black screen, but the login music plays so I know it's loading but still can't get any kind of video unless I use a previous build, and then it works fine but just no sound at all.... Any help???

---

### Post by sxe4ever on 2010-01-16
I was about to give up and just reinstall Ubuntu, so I burned an install disc, threw it in, rebooted and hit the install option and it eventually just went to a blank screen after giving me the black & white Ubuntu symbol....

I then tried to run Ubuntu without making any changes to the computer and I got the black & white symbol again, and then went to a black screen again, it eventually gave me the sound like it's logging in but it just stays as a black screen as it does with the current install I have....

Any ideas as to what I should do here????

EDIT: It does load up with safe graphics

EDIT AGAIN: I was able to install completely using the safe graphics mode.  When I put on the restricted ATI drivers it gives me the same issues as before with the black screen but with the login noise.  I couldn't figure out how to remove the ATI drivers and was lazy so just reinstalled it, and it's been working fine since using the safe graphics.....

---

### Post by Handssolow on 2010-01-22
I started another similar thread today before I'd seen this one.

I wasn't able to get any of the three live CDs of 9.10 to load without ending up with a flickering screen (Ubuntu, Xubuntu and Ubuntu UNR). I think I'd be unable to enter anything in the flashing command line. Looks like I've just burnt three useless live CDs.

[http://ubuntuforums.org/showthread.php?t=1387899](http://ubuntuforums.org/showthread.php?t=1387899)


Edit: While the screen was flashing I was eventually able to stop this with sudo stop gdm suggesting a video driver with latest kernel issue.

---

### Post by gbrent on 2010-01-30
I updated 9.04 to 9.10 and then did the following: 

sudo apt-get remove --purge xserver-xorg
sudo apt-get install xserver-xorg

which failed with the message:

"E: Couldn't find package xserver.xorg"

I have been searching the forums to no avail. Any suggestions? 

Thanks Glen

---

### Post by sxe4ever on 2010-01-30
> **gbrent said:**
> I updated 9.04 to 9.10 and then did the following: 

sudo apt-get remove --purge xserver-xorg
sudo apt-get install xserver-xorg

which failed with the message:

"E: Couldn't find package xserver.xorg"

I have been searching the forums to no avail. Any suggestions? 

Thanks Glen

Just taking a guess..... do you have an internet connection and access to it when you're running this?

---

### Post by gbrent on 2010-01-30
Seems that this installation has gone from bad to worse. You are probably right that the 9.10 boots without the network connection working. It is now not completing the boot and hanging up with the message:

* could not access PID file for nmbd

I have to hit CTRL-ALT-DEL to get it out of it.  There are other failures also.  It does boot from the CD and will run, but not from the updated installation. I expect that I'll have to do a clean installation. 

Thanks.

---

### Post by lupadagit on 2010-02-02
> **Regele IONESCU said:**
> I did it!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!:D

Here is what I did:

**I simply removed 1Gb of 3Gb of RAM**. The installation, boot and start went all fine!!! No need to do anytrick with USB flash drive or ftp downloads. It simply works.

I have an Acer Aspire 9423wsmi.


After installing and successfully running Ubuntu 9.10 for a few times I reinserted the 1Gb RAM and still works fine!!!! So, it is a matter of OS install only.


Thanks man, i did it too. I followed your trick. I removed 2 G of my 4 G memory in ASUS F8 v series. It installed completely. I'm online with it now.

I will return the 2 G memory, and expect it to work, as you reported. Thanks again. I've been trying to install 9.10 since yesterday, with no joy, until I tried your trick. Kudos to Ubuntu Community!

---

### Post by sxe4ever on 2010-02-02
> **lupadagit said:**
> Thanks man, i did it too. I followed your trick. I removed 2 G of my 4 G memory in ASUS F8 v series. It installed completely. I'm online with it now.

I will return the 2 G memory, and expect it to work, as you reported. Thanks again. I've been trying to install 9.10 since yesterday, with no joy, until I tried your trick. Kudos to Ubuntu Community!

That doesn't make any sense. Why would this work??? I'm not doubting that it does work, I'm just wondering if anyone knows why this works??? LOL

---

### Post by Kibblesnbits on 2010-02-02
Wanted to report that this same problem was encountered on an Acer Aspire One 751h with the Intel GMA 500 graphics chipset.

---

### Post by Bobhuber on 2010-02-13
If you do a Kernel upgrade and have previously installed Nvidia's driver you need to reinstall the driver for the new Kernel. The instructions are on there website along with the most recent driver.

---

### Post by steve723 on 2010-02-17
I have a similar problem.  I am using Virtualbox version 3.1.4r57640 (The latest version as of yesterday0.  I get the following error message: **Ubuntu is running in low-graphics mode**

The following error was encontered.  You may need to update your configuration to solve this.

(EE) Failed to load module "vboxvideo" (module does not exist, 0)
(EE) No drivers available.

Anybody have any ideas?

Ubuntu runs after I click ok and select "run in low graphics mode for this session only.  It looks terrible in low graphics mode.

---

### Post by XEyedBear on 2010-02-17
> **Bobhuber said:**
> If you do a Kernel upgrade and have previously installed Nvidia's driver you need to reinstall the driver for the new Kernel. The instructions are on there website along with the most recent driver.

I have just installed the latest nvidia driver from nvidia's site for my old Rina TNT2 card and immediately get the flashing command prompt after starting gdm. In other words I think I have just "reinstall the driver for the new kernel".

So what do I do now to recover from this mess? the screen flashes too quickly for me to have any hope of entering a password.

---

### Post by von Stalhein on 2010-02-18
> **XEyedBear said:**
> I have just installed the latest nvidia driver from nvidia's site for my old Rina TNT2 card and immediately get the flashing command prompt after starting gdm. In other words I think I have just "reinstall the driver for the new kernel".

So what do I do now to recover from this mess? the screen flashes too quickly for me to have any hope of entering a password.

See if this is any assistance:
[http://ubuntuforums.org/showpost.php?p=8356996&postcount=204](http://ubuntuforums.org/showpost.php?p=8356996&postcount=204)

---

### Post by ultratek on 2010-02-18
does not the alpha 3 include already a more up to date release of the ati drivers than the ones released 2/17/2010

---

### Post by tomthumb99 on 2010-02-20
Just ran a command level prompt  'apt-get update' (using recovery menu) and it installed the 2.6.31-19 kernel/OS boots and now goes in X win for me. I have a Pavillion AMD 64-dual with Nvidia 7600GT. Prior to today, the 2.6.31-17  would boot and go into back screen (ie: think stuck on disk or memory fault).

------ bad log  2.6.31-17-----
Feb 16 06:58:00 amd64linx kernel: [   17.520036] hda_codec: Unknown model for ALC888, trying auto-probe from BIOS...
Feb 16 06:58:00 amd64linx kernel: [   17.560116] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:10.1/input/input5
Feb 16 06:58:01 amd64linx kernel: [   19.779965] ppdev: user-space parallel port driver
Feb 16 06:58:02 amd64linx kernel: [   20.448723] usplash:387 freeing invalid memtype ffffffffe0000000-fffffffff0000000
Feb 16 06:59:03 amd64linx kernel: [   81.520043] Clocksource tsc unstable (delta = -266594648 ns)
Feb 16 07:01:04 amd64linx kernel: Kernel logging (proc) stopped.
-----------------

Odd about the 31-17 upgrade was that the initial 2.6.31-16 kernel/OS boot was very clean, had no issues with it a all.  The 'apt-get upgrade' got me to the initial bad or untested/non-robust 31-17.  ('apt-get upgrade'- most dangerous command in OS - never know what you get!)

Ubuntu cannot release untested SW, everybody looking for an alternative from MS.  Better to go slow and stable, rather than fast and crash. This is the time to shine (not sink).

---

### Post by kevinlw on 2010-02-24
Greetings,

I'm testing out Karmic Koala and was sucessful on my first install using WUBI. My system updating got corrupted so I used Wubi to uninstall n reinstall Koala again.  subsequently, I get "Input not supported" dancing around my screen when Koala goes to the login screen.  I have ATI Radeon Xpress 200 series card n driver inside my PC running XP pro.

Do I need to reformat the Ubuntu target drive?

thanks & regards,
kev

---

### Post by Pegasuss on 2010-03-10
I have another Teeth Nashing problem:

1. 13+ Hrs ago (@17:00Hrs GMT) I got an Update notification (running Ubuntu 9.10) for My Nvidia Graphics Drivers (Geforce FX 5500).

2. After downloading/Installing Updates I powered off My Computer to work on another Build.

3. On rebooting this Computer I find that My Graphics are All Stuffed Up, the best display I can get is 640X480 & Ubuntu has My Monitor(ACER 17"TFT) as 'UNKNOWN'.

Also:
A. when I try to make changes to the resolution the window flicks for Maximised to Minimised when I click on any point on the screen.

B. Also, my toolbar has got a life of it's own, click on 'System' & My Browser Opens.

I would consider doing a New Install, but I am worried that the same thing will happen again when I do the Updates?

Help!!! Please!

---

### Post by haroonrn on 2010-03-10
Hi All.

Just purchased a new Compaq laptop. downloaded the latest Ubuntu studio alternate install iso image from internet. burnt it to a DVD. verified the installer, sucssfully.
Installation was through without any problem. however after complete installation when laptop is rebooted the loader freezes. and i m unable to boot into the ubuntu studio.

reinstalled 3 times still same behavior. 
can someone guide me? 
thanks in advance

- HP Compaq CQ40-616TU
4Gb Ram, T6600 C2D, 320Gb SATA harddisk. Intel GM45 (4500MHD) chipset.

---

### Post by Pegasuss on 2010-03-11
Addendum

I uninstalled the Nvidia Drivers, & tried to install the drivers from the Nvidia Site (found link in previous post in this thread), all this did was make it Imposssible for Me to Login on Reboot (My Usename & Password were rejected/no found)!

So, I bit the Bullet & Reinstalled Ubuntu!

On reinstall, I checked the Resolution on My Monitor Menu & found that it was now 800x600 (a little better).

I installed all the upgrades (accept the Nvidia one).

So, back to the same problem as I started with? How to get My Graphics Res back Up to an Acceptable Setting of  at least 1024x768?

---

### Post by Pegasuss on 2010-03-11
Addendum 2:

A Resolution (no Pun Intended).

I realised (to late to save 2% of my Docs & etc), that all I needed to do was 'Remove' the 'Nvidia ver 173' drivers & 'Activate' the old 'ver 96' drivers!:oops:

Now I have My system looking as I like it, All I have to do is re-install all My old Dos Games & the backup of My Docs!:)\\:D/;)

---

### Post by pd71sat on 2010-03-19
> **freackout said:**
> yup i did 
sudo apt-get remove --purge xserver-xorg
sudo apt-get install xserver-xorg
startx
and guess what .... brilliant.....alls fine now, same icons nothing lost lovely.

i even tried removing the actual desktop before that, but i did not have to as that was not the problem......

Thanks guys this works perfectly for me now. 

I did not follow the recommended upgrade path to 9.04 first, but went straight from 8.04 LTS to 9.10. I simply installed into the previous 8.04 LTS partitions without formatting. 

Worked ok all along until last night when I did the latest update that brought in kernel "2.6.31-20-generic". After that I could not get the Desktop, and it kept booting straight to command mode. Followed some other instructions on the forum to remove and re-install the xorg-video-radeon, and other drivers and reconfigure Xorg all to no avail. After those instructions I would get the Xserver staring up and giving a Desktop but could not get mouse or keyboard input to function. Could only hit the power-off switch to shutdown. Now with re-install of "xserver-xorg" I am happy as a pig in mud as all is back to normal again :D

---

### Post by roberts73543 on 2010-03-22
Hi
I also got the same message that ya'll have received tho mine wasn't until I finally got my Ubuntu machine to accept a wireless card so that I could get it on the network. Now my errors came after I had done the update through update manager and had to do a reboot, I got basically the same reactions as described in this thread and finally got it to the window asking me to make a choose ummm I'm REAL NEW here and wasn't sure but made the correct chose, but getting a shutdown message that I'm not sure abt it reads as fallow:

Ubuntu 9.10 doug-desktop tty1
doug-desktoplogin:[712.219370] System halt 

I went to my bootstrap log, once I got back onto the system unit  to see if I could figure it out and what I seen was there was 5 things not installed and they are:

awk
libc6
libpam-modules 
coreutils
lzma 
Sorry in advance if too long of a thread

---

### Post by jeff-free174 on 2010-03-23
Hi I have had the same problems, I believe it is in the final stages of update where the updater shows a list of 'non community supported software' I have noticed that the NVideo drivers are included in this list and as such are removed giving the blank screen, or in my case a monitor flag showing 'unsupported input'.

I removed 2.10 and reinstalled 2.09 and then the nvideo drivers and now all is OK.
But still unable to 'protect' the NVideo drivers from removal during update to 9.10

---

### Post by ravisunny2 on 2010-05-03
[FONT=Verdana]I had installed ubuntu 9.10 on my C2D. It worked fine for some days.[/FONT]
[FONT=Verdana]This was a **fresh install**, not an upgrade. I did **not** apply any update either.[/FONT]
[FONT=Verdana]Of late, I am getting the flashing screen :[/FONT]
[FONT=Verdana]
usplash: Setting mode 1152x864 failed
usplash: Using mode 1024x768

....[/FONT]
[FONT=Verdana] [/FONT]
[FONT=Verdana]Is there a logical fix that does not require trial & error ?[/FONT]

---

### Post by tfleonard on 2010-05-04
Same problem here with 2.6.31.14 and Ubuntu 9.10 on a Dell 2650.  
I booted 2.6.31 in recovery mode and then updated the kernel to 2.6.31.20.  Nvidia drivers do not work but vga does and I can boot the machine.  Keyboard works by touch pad does not.

---

### Post by tomski on 2010-05-06
same problem with upgrade to lucid seems like my xorg.conf has been deleted for some reason & now all i see in the logs is somethin about ecid being wrong!!!!!!!!!!!!!!!!!!!!!!!!!!

im considering installing pirated win7 as every upgrade of ubuntu i do results in major problems

---

### Post by sboutwell on 2010-05-08
I also have been a LONG time fan of Ubuntu... But I can say after the last 3 upgrades.. I'm also considering trying something else.  The stability after the UPGRADE has NEVER worked.  I got bit with the INTEL Driver issue on a box, I got BIT with the ATI Driver on another box, and got hammered with the NVIDIA issue.   

Now after this lastest upgrade, I'm going to have to do a FRESH install on my Laptop YET AGAIN.  

MUCH worse record at this point than Microsoft.  I'm WANTING to be a FAN and BELIEVE but you HAVE to Provide stability and get off this BLEEDING EDGE Mentality that since we are LINUX users we can put up with this and just REINSTALL.

Sorry for Venting but I have better things I could be doing rather than REBUILDING systems ever 6 months.  Don't release until you have a STABLE PLATFORM.

---

### Post by Sketches on 2010-05-09
I have an Ati card and have a more extreme problem than most. There is no screen.
No command prompt no login no loading screen just black. Every 2nd boot or so it will flash white once and thats about it.

If i can't access terminal is there any way to fix this?

---

### Post by jrop on 2010-05-11
> **sboutwell said:**
> I also have been a LONG time fan of Ubuntu... But I can say after the last 3 upgrades.. I'm also considering trying something else.  The stability after the UPGRADE has NEVER worked.  I got bit with the INTEL Driver issue on a box, I got BIT with the ATI Driver on another box, and got hammered with the NVIDIA issue.   

Now after this lastest upgrade, I'm going to have to do a FRESH install on my Laptop YET AGAIN.  

MUCH worse record at this point than Microsoft.  I'm WANTING to be a FAN and BELIEVE but you HAVE to Provide stability and get off this BLEEDING EDGE Mentality that since we are LINUX users we can put up with this and just REINSTALL.

Sorry for Venting but I have better things I could be doing rather than REBUILDING systems ever 6 months.  Don't release until you have a STABLE PLATFORM.

I'm having a different issue, but when I saw this post, I couldn't agree more.  In fact, I feel like repeating my favorite part of the above post: "*...I have better things I could be doing rather than REBUILDING systems ever 6 months.  Don't release until you have a STABLE PLATFORM.*"

---

### Post by ravisunny2 on 2010-05-14
> **ravisunny2 said:**
> [FONT=Verdana]I had installed ubuntu 9.10 on my C2D. It worked fine for some days.[/FONT]
[FONT=Verdana]This was a **fresh install**, not an upgrade. I did **not** apply any update either.[/FONT]
[FONT=Verdana]Of late, I am getting the flashing screen :[/FONT]
 
[FONT=Verdana]usplash: Setting mode 1152x864 failed[/FONT]
[FONT=Verdana]usplash: Using mode 1024x768[/FONT]
 
[FONT=Verdana]....[/FONT]
 
[FONT=Verdana]Is there a logical fix that does not require trial & error ?[/FONT]
 
Solved the issue by **updating** the nvidia driver.

---

