---
title: "No GUI after installation"
date: 2010-11-11
forum: Hardware
---

### Post by Bob_I on 2010-11-11
I have searched the forums and can't seem to find an answer to this.  I have a brand new Acer Aspire-7741 laptop with an Intel processor, 3gb main memory and 250gb on the hard disk.  It came with Windows-7.  I want it to dual boot with Ubuntu.  I used a live CD of 10.10 Meerkat, i386, 32bit.  It booted up fine.  I used Gparted to repartition the hdd, with partitions for "/" and "/home" and "swap", then installed the OS.  Everything went fine until I rebooted after the install.  I selected "Ubuntu" from the Grub menu and the boot-up proceeded from the command line instead of the Gnome GUI.  I have no idea of how to get from such a command line to the GUI.  Can anyone help?

---

### Post by Quackers on 2010-11-11
Does "startx" bring up the desktop? Or ctrl+alt+F7 after login?

---

### Post by oldfred on 2010-11-11
Several versions of commands to start gui.

startx
or 
now preferred
sudo service gdm start
sudo /etc/init.d/gdm restart
sudo start gdm

But even though it worked with liveCD, many are having issues with video drivers. You do not mention what video card/chip you have.

On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed Nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

---

### Post by Bob_I on 2010-11-11
Thank you oldfred, but none of your suggestions worked.  "startx" yielded a blank screen and a hung computer, as did all the other options you listed.  I do not know what the video chip is, as "lspci" goes by so fast I can only read the last few lines.  The CPU is an Intel chip, and I suspect that the video chip is of the same manufacture.  The live CD can make it work just fine, but the installation can't.  Bummer.
   Bob_I

---

### Post by oldfred on 2010-11-12
this will list just the video:

 lspci -nn|grep VGA

From  my portable:
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)

---

### Post by Bob_I on 2010-11-12
OK, thanks again.  The command reveals: VGA Compatible controller [0300] Intel Corp. core processor integrated graphics controller 8086-0046 - rev 02.

This is pretty much what I suspected from visiting the Acer web site.

I have a feeling that there is some module that is not working properly, but why it should work fine from the CD and not from the installation, I cannot understand.  Do you think that doing an "apt-get update" would help?

---

### Post by oldfred on 2010-11-12
You are not the only one where liveCD works but install does not. 

Did you try the other settings to put on grub boot line?

Sometimes other  BIOS settings may be an issue:

[https://wiki.ubuntu.com/X/Troubleshooting/Nouveau](https://wiki.ubuntu.com/X/Troubleshooting/Nouveau)
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line

---

### Post by Bob_I on 2010-11-12
I have tried all the above suggestions to no avail.  Interestingly, trying to edit grub does not work either. Hitting "e" at the grub menu does get to the editing screen, but changes made do not hold nor seem to function after the "cntrl-x".

I have the feeling that the "vga16fb" module is the culprit, but trying to blacklist it by editing the grub menu does not work.  I will try to get the system working from the CD and see if I can edit the grub file from there.
   Bob_I

---

### Post by oldfred on 2010-11-12
Editing grub with the e as you boot is a one time thing. If permanent changes are required you have to edit:
/etc/default/grub - the file containing GRUB 2 menu settings.

And if you know what to blacklist

Examples - not necessarily recommended but you can try.
 sudo nano /etc/modprobe.d/blacklist.conf
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist rivatv

Count of video drivers
dpkg -l|grep xserver-xorg-video|wc -l
List of drivers
dpkg -l|grep xserver-xorg-video

---

### Post by Bob_I on 2010-11-12
Ok.  I will have to try those things later or tomorrow.  Bob_I

---

### Post by Bob_I on 2010-11-13
The latest results in this saga:  The machine will boot to the GUI if I chose the second option in the Grub menu, "Restart in safe mode".  I suspected something wrong with the machine, so on one reboot, I tried the memory test option.  This came up, but immediately failed, going to a black screen. I am assuming that the memory check routine will work in a machine with a 64 bit processor.  If that assumption is wrong, please inform me. I am going to attempt a system restore from the restore disks that I made after first turning on the machine.  If I can get it restored, fine, but either way I am going to return the machine for a refund.
   BTW. Win-7 came with the machine, and in my impression, it is horrendous bloat-ware, little better than XP.
   Bob_I

---

### Post by Bob_I on 2010-11-15
The problem turns out to be a hardware one.  The machine failed a memory test, so it is on it's way back to the people I bought it from.

Just as an aside, the machine came with Win-7 on it.  I made the recovery disks (5 DVDs!) as directed, but when I re-installed Win-7, it wouldn't boot up.  Evidently the "recovery" disks were unable to restore the MBR or whatever is in it's place.  XP could do this with ease.  Talk about bloat-ware!!!

---

