---
title: "Anybody got suspend to work on a Dell 8100 ?"
date: 2006-06-20
forum: Hardware &amp; Laptops
---

### Post by declanmullen on 2006-06-20
After hibernating via clicking on gnome's hibernate button, resume does not work for my Ubuntu 6.06 on a Dell Inspiron 8100 (with ATI graphics).  I'm using the reiser filesystem. I've got 384MB ram, with a 500MB swap partition.

Is there anything in particular one needs to do to get either suspend to ram or suspend to disk to work for this type of laptop ?

Eg is there anything in particular that needs to be set in "/etc/default/acpi-support" or "/etc/X11/xorg.conf" ? Or do I need to configure where on the disk the system hibernates to ?

I haven't changed xorg.conf since the OS was installed and it defines the video card as:

 Section "Device"
  Identifier "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
  Driver "ati"
  BusID "PCI:1:0:0"
 EndSection

I have attached my current acpi-support file.

Regards,
Declan

---

### Post by declanmullen on 2006-06-28
Any suggestions ?

---

### Post by declanmullen on 2006-08-13
Anybody ?

---

### Post by Emerzen on 2006-08-14
By way of a bump, I'm having problems w/ a  Dell Dim 8400 w/ ATI graphics.  I've got the Radeon proprietary drivers installed.  It will go to standby w/o a hitch, but when I go to resume I cannot get my backlight to come on.  I've read several posts, but nothing seems to make a difference?

---

### Post by declanmullen on 2006-08-15
With my i8100, suspend closes down the system as expected, but waking up involves a bit of disk activity followed by nothing and a blank screen. I've experimented with the "/etc/default/acpi-support" options, but with no success.

BTW, I am not using the proprietary ATI driver.

A while back I was running Mepis 3.1 on this system, and suspend worked about half the time.

Having a notebook that will not suspend correctly is a pain :(

Ironically when I was looking for a notebook, I specifically chose a Dell over other brands because I assumed that Dell's large market presence would result in good Linux support. This seems to be the case with some of the other Dell models, but looks like I was unlucky to choose the i8100.

---

### Post by Emerzen on 2006-08-15
I've been searching and it may be a problem w/ GNOME power manager.  Does anyone who uses an alternative desktop (Kubuntu, etc...) have this problem?  (Problem being a failure of monitor to turn on after standby->resume.)  

Here's one possibility:
[http://www.gnome.org/projects/gnome-power-manager/packages.html](http://www.gnome.org/projects/gnome-power-manager/packages.html)

Or it may be a problem w/ the kernel, which is addressed in this post:
[http://www.kernel.org/git/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob;hb=HEAD;f=Documentation/power/video.txt](http://www.kernel.org/git/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob;hb=HEAD;f=Documentation/power/video.txt)

Has anyone tried changing acpi_sleep=mem -> acpi_sleep=s3_bios?  (Or any of the other hacks mentioned?)

I'm at work and won't have access to my box until later to try these myself.

---

### Post by declanmullen on 2006-08-16
:) Good news! Disabling DRI seems to have fixed suspend. Since then the system has woken from suspend correctly. I haven't tried hibernate yet.

The system is a Dell Inspiron 8100 with ATI graphics, running Ubuntu 6.06 with the latest updates and the GNU ATI driver. 

DRI was disabled by commenting out the DRI entries from "/etc/X11/xorg.conf". Ie 
[INDENT]Section "Module"
[INDENT]        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
[/INDENT]#       Load    "dri"
        [INDENT]Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"[/INDENT]
EndSection

#Section "DRI"
#       Mode    0666
#EndSection[/INDENT]

:(  Update:
Subsequent testing revealed that the system often does not resume correctly from a suspend. In these cases, resume starts with some disk activity, but then the system hangs with the screen remaining blank.

---

### Post by Emerzen on 2006-08-16
Declan,

sounds promising, I'm going to try it when I went get home.

---

### Post by Emerzen on 2006-08-16
When you say GNU ATI driver, does that refer to the one released by ATI or the one in the repositories?  I guess I'm confused because I thought the ATI released drivers were proprietary?

---

### Post by Richo on 2006-08-20
GNU ATI driver would have to be the opensource one and not the ATI company one.

I have a Dell 8100 with nVidia card and the suspend/hivernate currently work great ... here is the story.

I originally installed Ubuntu Dapper Beta 4 and upgraded via repsitories, and installed mountains of crap. The suspend/hibernation was broken, only boot 2 out 3 times, sometime the graphics went all reddish and had to be rebooted.

I shrunk the partition and install a dual boot with a fresh 6.06.1 install. This worked great until I installed ndiswrapper for my wifi card, then suspend/hibernate broke. I couldn't see to fix this so I changed to a card with a native linux driver and suspend/resume work fine.

I haven't installed the proprietory nVidea driver yet, but have suspicions that may cause problems.

---

### Post by declanmullen on 2006-08-21
> When you say GNU ATI driver, does that refer to the one released by ATI or the one in the repositories?

Yes, I'm using the ATI opensource driver that is in the ubuntu repositories and was installed by default.

---

### Post by declanmullen on 2006-08-21
> Good news! Disabling DRI seems to have fixed suspend.

Subsequent attempts to suspend and wake have had mixed results. Sometimes the system wakes correctly, and sometimes there's a bit of disk activity but then system locks up and the screen remains black. 

I'll keep experimenting.

---

### Post by segalion on 2006-08-21
Maybe with a new DSDT file suspend can work. It fix my compaq armada 1750 acpi support.

The instructions are:

1. download specific dsdt file at [http://acpi.sourceforge.net/dsdt/view.php?manufacturer=Dell](http://acpi.sourceforge.net/dsdt/view.php?manufacturer=Dell)
(maybe you have to compile the file with instructions in acpi.sourceforge.net, if you dont have the DSDT.aml bin file)

2. Install DSDT file in kernel in initrd image following instructions in [http://gaugusch.at/kernel.shtml](http://gaugusch.at/kernel.shtml)
I´ve done it in dapper with the script [http://gaugusch.at/acpi-dsdt-initrd-patches/initrd-add-dsdt](http://gaugusch.at/acpi-dsdt-initrd-patches/initrd-add-dsdt)

3. reboot and see if kernel has loaded new custom DSDT with 
#dmesg|grep DSDT

---

### Post by declanmullen on 2006-08-22
> Maybe with a new DSDT file suspend can work.

Thanks for the suggestion. I tried the DELL custom DSDT file that was available. But that hasn't fixed the wake/resume problem. 

I'll try suspend2 next.

---

### Post by declanmullen on 2006-08-23
I havge found these suspend2 packages provide good working hibernation: 
[http://dagobah.ucc.asn.au/dapper-kernels/]("http://dagobah.ucc.asn.au/dapper-kernels/")

Though they have introduced some issues that I have yet to fix. 
Eg 
- Wifi no longer works.
- CPU speed adjustment doesn't work.
- Unloading of sound module "snd_maestro3" didn't work.

I'll let you know how i go.

---

### Post by declanmullen on 2006-08-27
> **declanmullen said:**
> I havge found these suspend2 packages provide good working hibernation: 
[http://dagobah.ucc.asn.au/dapper-kernels/]("http://dagobah.ucc.asn.au/dapper-kernels/")

Though they have introduced some issues that I have yet to fix. 
Eg 
- Wifi no longer works.
- CPU speed adjustment doesn't work.
- Unloading of sound module "snd_maestro3" didn't work.

I'll let you know how i go.

Wifi is now fixed. :) 
The solution: My system used to run a 386 kernel (version 2.6.15-26-46) and its associated restricted-modules (ie linux-restricted-modules-2.6.15-26-386). The restricted-modules package was required because it provided the wifi's drivers (ie madwifi). I installed Bernard's 686 suspend2 kernel without realising that it wouldn't work with the 386 restricted-modules package. Installing the 686 version (ie linux-restricted-modules-2.6.15-26-686) has solved the issue.

CPU speed issue:
Something in the suspend2 package is trying to manipulate the CPU's speed and it is generating the following "dmesg" "cpufreq: change failed with new_state 1 and result 0" entries. However Ubuntu's attempt's to control the speed are still working.

Unload sound module "snd_maestro3" issue:
The suspend2's metapackage includes "hibernate" that by default lists "snd_maestro3" as a module that must be unloaded during hibernation, ie it is in "/etc/hibernate/blacklisted-modules". My current work around has been to comment "snd_maestro3" out of that file, so no attempt to unload it is made. 

Bernard's [http://dagobah.ucc.asn.au/dapper-kernels/]("http://dagobah.ucc.asn.au/dapper-kernels/") suspend2 meta package is turning out to be excellent. Many thanks Bernard.

BTW, I've still got X's DRI capability disabled, see [http://www.ubuntuforums.org/showpost.php?p=1385579&postcount=7]("http://www.ubuntuforums.org/showpost.php?p=1385579&postcount=7")

---

### Post by eurgain on 2006-12-06
> **declanmullen said:**
> Any suggestions ?

Yes, but you're not going to like it...

Install SUSE 10.2 instead.

The Dell I8x00 series are real buggers when it comes to suspend/resume.  However, SUSE has just worked since 10.0 (and Fedora does too).  However, I have really tried and tried with Ubuntu (curom kernels, ACPI patches replacement DSDTs, the dreaded postvga - you name it!), but to no avail.

These laptops have badly broken BIOSes.  SUSE and FC must have some nifty kernel patch.  (For SUSE < 10.0, you can get it to work with a replacement DSDT, but even this does not fix Ubuntu.)

This is some annoyance! My Inspiron is now my only machine that does not use Ubuntu.  Even my Dell Latitude X1 laptop works with Edgy (and Dapper before) without hesitation.

A

---

