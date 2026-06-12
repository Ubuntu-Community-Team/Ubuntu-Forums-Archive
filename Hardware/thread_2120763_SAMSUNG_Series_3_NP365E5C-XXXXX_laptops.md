---
title: "SAMSUNG Series 3 NP365E5C-XXXXX laptops"
date: 2013-02-27
forum: Hardware
---

### Post by Rebelli0us on 2013-02-27
These have AMD A-Series Trinity APUs, dual-core or quad. Mine is Series 3 NP365E5C-S01US A8-4500M with Radeon HD 7640G.

I have success:

Windows 8 (preinstalled) worked fine. I kept it long enough to update the BIOS, then deleted it. W8 had some kind of GPT partition, I had to use gparted to obliterate it.

Windows 7 (both Pro & Enterprise) works fine, but has intermittent suspend failure. I plan to delete it soon. I will post my driver install procedure later, for anybody interested.

Ubuntu 12.10, worked fine, though I had a hard time navigating the OS’s UI.

Linux Mint 14 MATE, everything works, Suspend/Resume S3 very reliable. Touchpad mouse is fully supported, including 2-figer scrolling.

I have not encountered the so-called “brick” BIOS bug that makes these laptops inoperable. In BIOS "boot" options I disabled "secure boot", and in Advanced tab disabled “Fast BIOS Mode”. In “OS mode selection” I have “UEFI and legacy”, but “CSM” worked too.

BIOS Version	: P05ABF
Date		: 01/29/2013

For me the best news is that all 4 USB ports are bootable (USB 2.0 **and 3.0**). That means you can boot any OS from a UHS-I flash drive at 80+ MB/sec and have as many **portable OS** sticks as you want. Nice security feature too in case your laptop gets stolen.

Problems so far:

-- In Power Options, I have “When power button is pressed” set to “Suspend” but it shuts down instead.

-- Some of the Fn shortcuts don’t work properly.  Display Brightness Fn+F2/F3 and sound volume adjustment Fn+F7/F8 mess up the keyboard stack and you basically have to reboot. I think it has something to do with Windows/Linux differences in Key_Up/Key_Down event handling. F1, F11, F12 don’t work either, generate some nasty key codes and you have to reboot. Fn+F5 enable/disable touchpad **works**, I wish there was a way to auto-disable touchpad when an external mouse is connected.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=231958&stc=1&d=1361984305[/IMG]



BTW, on startup F10 brings up the boot menu (undocumented), but does not list all available boot devices.

Color temperature of the LCD display is way off to the cool side, but problem solved (see attached)
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=231959&stc=1&d=1361984305[/IMG]


More soon. . .

---

### Post by Rebelli0us on 2013-02-27
WebCam SC-13HDL12639P works fine in Linux too. Capturing video in VLC and Skype video-phone:popcorn:  

Skype is v4.1 that installs from Synaptic.

---

### Post by slooksterpsv on 2013-02-27
I want to install Ubuntu so you got rid of the GPT partitions? Won't Ubuntu install in a GPT partition setting if so can't I install it and will Grub work with it?

I don't care for Windows 8, but will need to backup my stuff, but I need Windows 8 to do some other things. I guess this is a test of my Linux skills here soon, but I'll need to make some new threads and ask some questions.

1. I'd rather us GPT if I can have multiple parition tables
2. I'd like to keep Windows 8 installed without having to reinstall it.
3. Do I need to repair windows 8 once I disable secure boot, use UEFI and Legacy, and disable FAST BIOS mode (last shouldn't change much)?
4. Will grub work with GPT, UEFI, etc.?
5. Should I wait for Ubuntu 13.04

---

### Post by Rebelli0us on 2013-02-27
> **slooksterpsv said:**
> I want to install Ubuntu so you got rid of the GPT partitions? Won't Ubuntu install in a GPT partition setting if so can't I install it and will Grub work with it?

I don't care for Windows 8, but will need to backup my stuff, but I need Windows 8 to do some other things. I guess this is a test of my Linux skills here soon, but I'll need to make some new threads and ask some questions.

1. I'd rather us GPT if I can have multiple parition tables
2. I'd like to keep Windows 8 installed without having to reinstall it.
3. Do I need to repair windows 8 once I disable secure boot, use UEFI and Legacy, and disable FAST BIOS mode (last shouldn't change much)?
4. Will grub work with GPT, UEFI, etc.?
5. Should I wait for Ubuntu 13.04

$256 ?!  Is that US $ or the Australian stuff? I paid $399usd for mine at newegg but it’s a quad.

After I deleted W8 I tried W7, it was the W7 installer that complained about GPT (w7 would not install). So I used gparted to create a new partition table, and w7 installed fine after that.

If you need w8 keep it as is, you can boot any other OS from USB flash drives. Or you can run Windows as a virtual machine.

---

### Post by oldfred on 2013-02-27
Grub/Ubuntu work with gpt partitions in either UEFI or BIOS mode. I have only BIOS and have used gpt partitions on a couple of drives since 10.04.

But if you install Ubuntu in BIOS/Legacy/CSM mode you have to go into UEFI/BIOS and change boot mode to/from UEFI for how system is installed. For easy dual boot both need to be in same mode either UEFI or BIOS.

       You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

    
       Booting the Ubuntu installer in UEFI mode from a USB disk on certain Samsung laptops (530U3C, NP700Z5C) may trigger a firmware bug that renders the machine unbootable. Users are advised to use caution when installing on Samsung laptops and ensure that they are configured for legacy BIOS mode, not UEFI mode. (1040557) 

            The current state of UEFI and Linux = Feb 1, 2013 - Matthew Garrett
Samsung, Lenovo & Toshiba UEFI issues
[http://mjg59.dreamwidth.org/22028.html](http://mjg59.dreamwidth.org/22028.html)
Matthew Garrett's Blog
[http://mjg59.dreamwidth.org/](http://mjg59.dreamwidth.org/)       
 UEFI boot live-usb bricks SAMSUNG 530U3C,np700z5c laptop - fix released
[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557)
[http://www.h-online.com/open/news/item/Booting-Linux-using-UEFI-can-brick-Samsung-laptops-1793958.html](http://www.h-online.com/open/news/item/Booting-Linux-using-UEFI-can-brick-Samsung-laptops-1793958.html)
The problem also appears to affect Ubuntu 12.10 and other Samsung models. The Ubuntu bug report includes posts from users reporting that the problem also affects 300E5C, NP700Z5C, NP700Z7C and NP900X4C series laptops.


Installs that seem to have worked.
       
 Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)

---

### Post by Rebelli0us on 2013-03-03
After using the Samsung NP365E5C-S01US for a few days I can say it **is** Linux compatible. 

I settled on Linux Mint MATE 13 (based on Ubuntu 12.04 Precise Pangolin) and fixed the Fn shortcut problem (above) as follows:

Open “Preferences” > “Keyboard Shortcuts”. **Disable** “Volume Up”, “Volume Down” and “Volume Mute” (click on shortcut and press backspace).

Replace these with your own: In “Keyboard Shortcuts” create 2 new shortcuts:
Volume UP = amixer set Master 4+ and assign to Winkey+Up
Volume DN = amixer set Master 4-  and assign to Winkey+Down

Display Brightness Fn+F2/F3 works!

Fn+F4/F5 also work: Touchpad on/off & LCD/external monitor

Fn+F11/F12 don’t work but you can assign Fn+F11 to whatever command you want in “Keyboard Shortcuts” (keycode = XF86Launch3). 



The power button problem is still unresolved:

“Power Management Preferences” in “General” tab, “When the power button is pressed” **if set to “Suspend” setting is ignored and machine shuts down instead**! It is dangerous, if you accidentally press the power button it will destroy your session.


And a screenshot
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=239726[/IMG]

---

### Post by slooksterpsv on 2013-03-04
I was able to successfully dual-boot Windows 8 and Ubuntu without having to use restore disks, restore to factory defaults, or delete any partitions. I just shrinked my Windows one, and made 60GB avail for Ubuntu. I'm running 12.10 with Cinnamon using AMD drivers directly from AMD. It's awesome. =D

---

### Post by Rebelli0us on 2013-03-05
Good, I assume you're booting with Grub?  I noticed that Samsung has 4 or 5 partitions in there (what are they for?). I have no use for W8 so I cleaned out the entire disk. But as you can see from my desktop I run several OSes simultaneously without need for separate partitions.

---

### Post by oldfred on 2013-03-05
UEFI requires an efi partition to boot from. That replaces the MBR and allows many systems to boot from one efi. It is like having many MBRs so systems so not conflict. That is assuming UEFI is correctly implemented even with secure boot. But many UEFI do not seem to be correct and add code to only boot Windows.

Windows also has to have a unformatted reserved partition just before its main install. That is a scratch area somewhat like how Windows used the space after the MBR but before the first partition in MBR partitioning for DRM, hidden serial numbers and other data it wanted to hide.

       Windows Recommended UEFI-Based Disk-Partition Configurations
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx")

Ubuntu will boot from gpt partitioned drive in BIOS or UEFI partitioning. My sysem is BIOS only and I have used gpt on two drives and a couple of flash drives.
      
 GPT Advantages (older but still valid)  srs5694 post #@:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

But Windows will only boot from gpt partitioned drives with UEFI.

---

### Post by Rebelli0us on 2013-03-17
While suspended this laptop uses about 1% per hour of battery charge so we need hibernation, which is disabled by default in Ubuntu 12.04/Mint 13, so I had to enable it. Google search shows how to do it, it requires some tinkering, and to enable/create a swap partition. Hibernation works **VERY** well on this machine.


The next item is disabling the Touchpad when an external mouse is inserted. Two steps:

Create &#8220;/etc/udev/rules.d/72-touchpad.rules&#8221;.

```
# /etc/udev/rules.d/72-touchpad.rules
#   
# Enables/Disables SynPS/2 Synaptics TouchPad upon external mouse detection.
# Works on insertion/removal of external mouse and on resume from suspend or hibernation.
# Note $USER variable

ACTION=="add", SUBSYSTEM=="input", KERNEL=="mouse[0-9]", ENV{DISPLAY}=":0", ENV{XAUTHORITY}="/home/$USER/.Xauthority", ENV{ID_CLASS}="mouse", ENV{REMOVE_CMD}="/usr/bin/synclient TouchpadOff=0", RUN+="/usr/bin/synclient TouchpadOff=1"


```


Create &#8220;/usr/local/bin/toggle-touchpad.sh&#8221; and add it to your Startup Applications:

```
#!/bin/bash

# /usr/local/bin/toggle-touchpad.sh

# PURPOSE:
# Disables the TouchPad if a second (external) mouse is available, otherwise enables the TouchPad.

# INSTRUCTIONS:
# If laptop has a Fn+ shortcut key to enable/disable the TouchPad, it should be left in the
# enabled state otherwise this script will be ineffective.


if [ `ls -d /dev/input/mouse* | wc -l` -gt 1 ]; then
	# disable touchpad if more than one mouse is available
	/usr/bin/synclient TouchpadOff=1
else
	# enable touchpad if only one mouse is available
	/usr/bin/synclient TouchpadOff=0
fi

```

---

### Post by Rebelli0us on 2013-03-17
Webcam (1280x1024) works well for Skype and capturing video & photos. Cheese works but guvcview (GTK+ UVC Viewer) has more video options, but it seems to have a bug in the video display window. So I start it with a script instead:


```
#!/bin/bash

guvcview --size=1280x1024 &				# Set max webcam resolution (keeps defaulting to 640x480)

sleep 2

wmctrl -r GUVCVideo -e 0,720,0,640,512	# IMPORTANT, resize video window to 1/2 of max res (1280x1024)

wmctrl -r GUVCViewer -e 0,0,0,-1,-1		# Just move to corner

wmctrl -a GUVCViewer					# Activate

```

---

