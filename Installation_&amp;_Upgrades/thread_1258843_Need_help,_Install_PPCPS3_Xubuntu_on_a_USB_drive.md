---
title: "Need help, Install PPC/PS3 Xubuntu on a USB drive"
date: 2009-09-05
forum: Installation &amp; Upgrades
---

### Post by dv-design on 2009-09-05
Hello Everyone,

Id like to be able to run Xubuntu (or any full featured version of a gui based linux) on my PS3, but heres the catch...i want to run it off a live CD or off a usb drive (2GB).

My need for doing it this way is that the internal hdd is currently being used and id like to be able to run linux externally, read a ext3 partition on the internal hdd, and send its contents over wireless network to my pc.

I tried running xubuntu live cd on ps3, but the screen goes black and it just sits there. I get the kboot prompt and type 'live'. When i do this it just goes to a black screen and sits forever.

Im running the ps3 to a 19" Samsung LCD tv via hdmi. The tv can handle 720p. Do i maybe have to select a resolution for the live disk, maybe im just not seeing it?

Any help would be great, the problem with making a installed linux on the pen drive is that its the ppc/ps3 version of xubuntu...so i cant exactly boot to the cd from a computer and install it to the usb drive.

---

### Post by phillw on 2009-09-05
There is a wiki here .....

[https://help.ubuntu.com/community/PlayStation_3](https://help.ubuntu.com/community/PlayStation_3)

and a thread on the subject is here .....

[http://ubuntuforums.org/showthread.php?t=316047](http://ubuntuforums.org/showthread.php?t=316047)


Hope that helps

Phill.

---

### Post by dv-design on 2009-09-05
Thanks fr the ffort man, but no it didnt really help. Your first link is general instructions and is outdated.

The second link didnt go anywhere :(

Looking to be able to run a livecd (boot and run linux off the cd) or a way to install linux to a usb drive and run it from the usb drive...the purpose of both ideas is the hard drive has a ext3 partition i want to be able to read but not wipe out.

---

### Post by stlsaint on 2009-09-05
you may want to retry that second link again...i checked and it works.

---

### Post by dv-design on 2009-09-07
For anyone interested, the key to doing this is when the partioner comes up during the installation process.

When your at the aprtioner, and it askes you if you want guided format/partion, select manual.

Here you will be presented with a list of storgae devices, look for the usb drive and you can select that and partion it however you like. Make sure that at least one partion is '/' and bootable, this will make the root install on that partion and make it bootable.

Xubuntu installed fine on a 2Gb stick, leaving just enough space for it to function. The major issue was that Xubuntu required extra configuring and installation to have samba/windows networking and sharing capabilty, and at 2Gb i didnt have the space, no how, nor patience to do this.

I successfully installed Ubuntu on a 8gb stick, using 2gb as a swap space. This gives me plenty of room to manipulate and tinker, plus ubuntu on the pse works out the box with wireless and connecting to windows networks.

My guess is a 4Gb stick should be the minimum usb drive to install on. Preformance off the 8gb with 2gb swap was the same as on an internal installation. Unfortunatly the ps3's limiting factor is ram not anything else.

---

### Post by Xureus on 2009-09-17
Hi, I have installed Ubuntu 7.10 desktop for PS3 onto my 4GB Usb stick but now I can't get the PS3 to boot from it.

I have no linux partion set in PS3 Game OS. I partitioned the usb drive on the ubuntu installer like u said. The usb drive should be bootable and contain the root. I've partitioned the usb stick like this:

[U][[IMG]http://img36.imageshack.us/img36/926/ubuntu0000.jpg[/IMG]]("http://img36.imageshack.us/i/ubuntu0000.jpg/")
[/U]
However the bootloader coming with Ubuntu fails to find root fs, Petitboot & pdaXrom-ng freeze on trying to boot (but they do on almost anything, only pdaXrom-ng's own distro works with his bootloader).

How did you do it, dv-design?

Would you enlighten me, please?


PS:  I've installed 7.10 because my PS3 doesn't want to boot the installer for 9.04. It fails after I type install on kboot. It says booting systems and then freezes.

---

### Post by Xureus on 2009-09-18
I've finally done it, in case other people wonder how to do it:

Stuff you will need:
- PS3
- Ubuntu (ubuntu-7.10-desktop-powerpc+ps3.iso)
- Bootloader (included in afore mentioned iso)
- USB stick
- IMGBurn or other cd burning software that features burning of images
- Time

Steps:
1) Burn "ubuntu-7.10-desktop-powerpc+ps3.iso" to a CD-R (save image to disc). I used IMGBurn for this.
2) Copy the bootloader (otheros.bld) to your USB stick and install it on the PS3 by using the function in the XMB.
3) Insert the burned CD-R, boot into Other OS and wait for the kboot prompt.
4) Type in "install" (or "install video=ps3fb:mode:0" if you have an SD monitor).
5) Choose your settings (Timezone, Keyboard type etc).
6) Choose manual partitioning, delete all existing partitions on you usb stick. Create 2 new partitions: The first you give much space, choose "ext3" as file system and "/" as mount point. The second you give the remaining space, choose "swap" as the file system, moint point will be grayed out.
7) Choose additional settings (login information).
8) Reboot when prompted.
9) KBoot will come up and say that there was no default root fs found. Insert "sh" to access the shell.  Then insert kboot while being in shell. You will be in kboot again. Hit enter. Kboot will boot the kernel and Ubuntu will start.
10) Be happy if all went well!

That's how I made it work. I hope it works for others as well.

---

### Post by arawas on 2009-12-22
To Xureus,
Did the step# 2 (2) Copy the bootloader (otheros.bld) to your USB stick and install it on the PS3 by using the function in the XMB.) format the PS3 HDD or it was intact and can you now access the data on the PS3 HDD from UBUNTU ?

---

