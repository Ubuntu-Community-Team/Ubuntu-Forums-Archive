---
title: "Cannot get NVIDIA driver working with Geforce GT 730"
date: 2015-12-27
forum: Hardware
---

### Post by joe-crofts04 on 2015-12-27
Hello all,

I have recently built a desktop computer, but am having severe trouble installing the NVIDIA driver for my GeForce GT 720 Graphics card. I have attempted to install the driver through the Additional Drivers tool; the official Ubuntu repository (installing nvidia-current); the NVIDIA website; the xorg-edgers repository and the graphics-drivers repository - all to no avail.

The computer has been setup to dual boot with Windows 7 - which works absolutely fine with the graphics card. When booting into Xubuntu, I have to use the "nomodeset" parameter in the GRUB menu, which leaves me with 640x480 video only. If the NVIDIA drivers are installed, or I don't use nomodeset, then I only get a black screen.

If anyone has any suggestions then I would very much appreciate the help - I'm at my wit's end! My version of Xubuntu is 15.10 x64.

Specs:
[LIST]
[*]Intel i5-4460 @ 3.20GHz 
[*]Gigabyte H81M-H motherboard 
[*]MSI NVIDIA GeForce GT 730 
[*]8GB RAM 
[/LIST]

---

### Post by SeijiSensei on 2015-12-27
I stick to LTS versions.  On my 14.04 system, I'm using nvidia-346 with my GTX 750 which is in the repository.  Works fine.

---

### Post by tokyobadger on 2015-12-27
I think the first thing you need to do is remove all installs of nvidia-drivers and related packages
```
sudo apt-get purge nvidia*
```
remove all the ppa's you added to try to resolve this issue eg
```
sudo ppa-purge xorg-edgers
```
remove the current xorg.conf (if you have one)
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.2015-12-28
```
You should now have a clean slate, so add the [Graphics Drivers Team ppa]("https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa")
```
sudo add-apt-repository ppa:graphics-drivers/ppa
```
Update the system
```
sudo apt-get update
```
Make sure you have the latest source and headers
```
sudo apt-get install linux-source linux-headers-generic
```
Install either nvidia-355 or nvidia-358 - I'm using 358, but there is a warning on the PPA page that 358 reportedly crashes Steam and they advise 355 - decide for yourself
```
sudo apt-get install nvidia-35x nvidia-settings
```
For setting the resolution in /etc/default grub [there are 2 suggested solutions at this page]("http://www.randomlinuxstuff.tk/2013/05/fix-ubuntu-boot-screen-after-installing.html") - I use the first (linked one) on my desktop with GTX680 - this box was originally installed with Ubuntu 13.04 x64 and has been updated through various versions to 16.04 x64. On another partition I have Ubuntu 15.10 x64, Mint 17.03 x64, elementaryOS 0.3.2 x64 all using the same solution.

A couple of additional ideas:

[Your CPU has Intel HD 4600 graphics built in](http://ark.intel.com/products/80817/Intel-Core-i5-4460-Processor-6M-Cache-up-to-3_40-GHz) have you disabled it in the BIOS?

[Several nvidia users had success with this method](http://ubuntuforums.org/showthread.php?t=2263316&page=4) - personally I would not do the manual install of the drivers as the package manager is unaware of them meaning that at every kernel update you need to purge and reinstall; post 32 adds the ppa approach to the OP's solution. My own take is that it is not an issue of the Ubuntu/ppa packaged drivers, but more the need to blacklist nouveau that is the reason for success

Though it shouldn't be necessary you might want to run
```
sudo nvidia-xconfig
```
Further options for nvidia-xconfig can be found with man nvidia-xconfig

---

### Post by joe-crofts04 on 2015-12-28
Thanks for taking time to answer my query tokyobadger. I have followed your instructions, but unfortunately I am still greeted with a black screen at startup. More specifically, a message from fsck displays, then a text-only login screen is displayed for a few seconds before disappearing. I have also disabled the CPU's integrated graphics in the BIOS.

If it helps, I installed the nvidia-355 driver, then ran nvidia-xconfig, which generated a new xconf file. After this, I rebooted.

---

### Post by tokyobadger on 2015-12-28
Can you share /var/log/Xorg.0.log and /etc/default/grub via [the pastebin](http://paste.ubuntu.com/) - separate links

---

### Post by joe-crofts04 on 2015-12-28
/etc/default/grub: [http://paste.ubuntu.com/14241575/](http://paste.ubuntu.com/14241575/)
/var/log/Xorg.0.log: [http://paste.ubuntu.com/14241580/](http://paste.ubuntu.com/14241580/)

---

### Post by tokyobadger on 2015-12-28
**EDIT:** You might have to take a few extra steps before the ones above because of the manual install of the drivers from Nvidia's download site:

1. Boot into recovery mode (at the grub screen select the advanced options for Ubuntu and you'll see an expanded menu with the Recovery option)

2. Run the following (XXX being the version number you installed)
```
sudo sh NVIDIA-Linux-x86_64-XXX.run --uninstall
```
3. Redo the steps in the earlier post to remove and reinstall the drivers from the PPA

4. Edit as indicated below

You'll need to edit /etc/default/grub at Lines 11 and 25 (use sudo nano)
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```
```
GRUB_GFXMODE=1920x1080
```
After editing you'll need to
```
sudo update-grub2
```
5. Reboot

Your xorg log looks fine - you appear to be connecting on the second connection DFP1 instead of DFP0 but that shouldn't matter. The DPI looks very high
```
[    14.490] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080 
[    14.526] (--) NVIDIA(0): DPI set to (1219, 914); computed from "UseEdidDpi" X config
```
Is it a 4K monitor?

---

### Post by joe-crofts04 on 2015-12-29
I don't think I was clear enough before, my bad - I installed the drivers from the PPA, but then ran nvidia-xconfig after installation, to see if that would help fix my problem. I'll try your other steps and get back to you though. And no - it's not a 4K monitor.

---

### Post by tokyobadger on 2015-12-29
[quote="joe-crofts04"]I have attempted to install the driver through the Additional Drivers  tool; the official Ubuntu repository (installing nvidia-current); **the  NVIDIA website**; the xorg-edgers repository and the graphics-drivers  repository - all to no avail.[/quote]
If you did install the drivers by downloading + making executable + executing the script, and you have not run the uninstaller, you will need to do that before trying to install from PPA. The Nvidia installer script is not recognized by apt so using apt to try and clean out previous nvidia driver installs will catch anything from the official Ubuntu repositories and 3rd party PPAs but not from the manually invoked Nvidia installer script.

If you've already run the uninstaller, then ignore and move to editing /etc/default/grub

I commented on the DPI because my equivalent line in /var/log/Xorg.0.log has the DPI at (101, 101) that's why the high numbers surprised me, but my monitor is pretty old

---

### Post by joe-crofts04 on 2015-12-29
It worked! Thank you so much for helping me out mate, you've been bloody brilliant. I just have one more question: will I have to do anything if I get a kernel update, or does the driver take care of itself once it's installed?

---

### Post by tokyobadger on 2015-12-29
Great to hear you've cracked it. Hopefully you'll be able to help others with their issues in the future - marking the thread as solved already potentially helps so thanks. To answer your question (warning a long version and a short version):

**Long**
Because the package manager (apt) is aware of the driver install from the PPA, if there is a kernel update (or any other package with interdependency eg xorg-server) any updates to nvidia-driver are automatically taken care of.

With the install script from Nvidia's website you bypass apt and will have to know when to update the drivers eg you run an update / upgrade through the GUI, automatically click yes to continue without analysing all packages to be updated, reboot to black screen, you'd have to know which logs to look at and how to fix the issue.

That's why I'd always advise installing software via the package manager. 

**Short**
Long answer short, you're good to go.

Now you can finally get to enjoy the new machine in Ubuntu, have fun!

---

### Post by joe-crofts04 on 2015-12-30
Thanks again!

---

