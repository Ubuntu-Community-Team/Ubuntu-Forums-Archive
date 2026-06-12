---
title: "haswell laptop - can't boot livecd"
date: 2013-07-19
forum: Hardware
---

### Post by leespa on 2013-07-19
Hi All,

New laptop: 

Toshiba Satellite P50 model number: P50-A-01E
Intel Core i7-4700MQ
Intel HD4600 + NVIDIA GeForce GT 740M with Optimus
Windows 8 pre-installed
full specs here: [http://www.futureshop.ca/en-CA/product/toshiba-toshiba-satellite-p50-15-6-laptop-grey-intel-core-i7-4700mq-1tb-hdd-16gb-ram-windows-8-p50-a-01e/10257006.aspx?path=fe546a5d55286b6dafacb1c98bc38826en02&SearchPageIndex=1](http://www.futureshop.ca/en-CA/product/toshiba-toshiba-satellite-p50-15-6-laptop-grey-intel-core-i7-4700mq-1tb-hdd-16gb-ram-windows-8-p50-a-01e/10257006.aspx?path=fe546a5d55286b6dafacb1c98bc38826en02&SearchPageIndex=1)

BIOS settings: Secure Boot Disabled, Boot Mode UEFI

I can NOT get an Xubuntu 12.04, Xubuntu 12.04.2 Alternate, Xubuntu 13.04, Ubuntu 13.04 AND Xubuntu-saucy-13.10 (all amd64) past the intial bootloader / choose install or try ubuntu stage.

Have modified all kinds of grub loader options such as: nomodeset, acpi=off, nomodeset acpi=off, acpi_osi=Linux acpi_backlight=vendor, i915.i915_enable_rc6=1, etc. NONE HAVE WORKED.

I keep getting stuck at a BLANK screen immediately choosing boot options. CTL+ALT+Fx does nothing...changing brightness does nothing, etc.

ANY help would be greatly appreciated. Also tried booting off of VGA and HDMI...no dice.

---

### Post by oldfred on 2013-07-20
You have the very newest hardware which probably needs the newest version of Ubuntu. 
Are you able to control which video mode you boot with from UEFI/BIOS? That would narrow down the possible boot options needed.
Some also only boot in BIOS mode even though they should boot in UEFI mode. Each writes system info differently and UEFI may not be doing it correctly. Do you have the latest UEFI/BIOS version from vendor?

Another user with an early Intel posted this:
 The problem was caused by another technology by Intel called the Integrated Network Interface Controller (NIC) that was conflicting with my USB controller that prevented my LiveUSB from working
Some BIOS
turn off discrete graphics
turn off "os optimus detection"

---

### Post by leespa on 2013-07-20
@oldfred - thanks for the reply.

Control video = NO. The Optimus setup is 'muxless' as I understand it so no way to specify this and/or change anything to do with video. I have a slightly older laptop with HD4000 setup same issue, but I got Xubuntu 12.04 installed no issues.

It seems when I boot in 'CSM Boot' versus 'UEFI Boot' it completely ignores all USB, HDD and then tries to boot PXE off the NIC for some unknown reason.

I will try turning the NIC off -AND/OR- updating the BIOS if available and report back.

THANK YOU

---

### Post by leespa on 2013-07-31
Turned NIC off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.

Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.

Thanks all.

---

### Post by oldfred on 2013-07-31
Glad you got it working. :)

---

### Post by sroutier on 2013-08-17
Hey, I am looking to get myself that laptop. Can you give me your impressions? Are all devices (sound, nic, wifi) working? Is the battery life good with Linux? Any special incantations required?
Thanks.

---

### Post by leespa on 2013-08-18
@sroutier - it's fast and everything works well on it using 13.10. 

It is not of the same build quality, feature-set of a more expensive Enterprise grade laptop of course, but for $1000 you get a lot of cutting edge hardware.

---

### Post by don-kozm0 on 2013-08-21
> **leespa said:**
> Turned NIC off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.

Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.

Thanks all.


I also have a Thosbiba P50 model laptop. Once I got it I immediately swapped the HDD to a SSD and tried to install Ubuntu. After following your hints I managed to boot the Ubuntu Install from my USB drive and managed to install Ubuntu to my SSD. But when the Installation of Ubuntu is done and I reboot in order to boot Ubuntu from the SSD I get this message "Reboot and select proper boot drive or insert boot media in selected boot device and press a key."

The settings in BIOS is like you did, Secure Boot Off, EFI Boot ON, and NIC turned Off.


This is really frustrating, as the BIOS detects the SSD, and Ubuntu finds the SSD during installation and writes the OS to it, but I cannot boot the OS from the SSD once the installation is done :/

Anything you experienced? Any hints on what to to do?

---

### Post by leespa on 2013-08-21
@don-kozm0 - only thing I can think of is that bootloader didn't get installed properly or to right media. I had seen grub get installed to USB in older Ubuntu installs. OS installation went good and then unit wouldn't boot like you described.

On this unit's HDD I had to futz around with getting MBR fixed, but that is mainly due to the fact that the existing Win8 partitions weren't 100% wiped before installing Win7 and then Ubuntu. Company IT folks installed Win7 and then I took it from there...

---

### Post by don-kozm0 on 2013-08-21
> **leespa said:**
> @don-kozm0 - only thing I can think of is that bootloader didn't get installed properly or to right media. I had seen grub get installed to USB in older Ubuntu installs. OS installation went good and then unit wouldn't boot like you described.

On this unit's HDD I had to futz around with getting MBR fixed, but that is mainly due to the fact that the existing Win8 partitions weren't 100% wiped before installing Win7 and then Ubuntu. Company IT folks installed Win7 and then I took it from there...


Hmm, I noticed one difference though in my setup. You said in another post I found on the forum, that after you had installed Ubuntu, you then switched NIC back on again, where as mine is still sett to OFF. I don't know if this has anything to do with it, but I will try that once I get home from work just to check.


Really strange if the bootloader has not been installed on the right drive. I have always installed Ubuntu from a memory stick in the past, and never have I experienced anything wrong with booting up the OS from the HDD/SSD. But you did nothing more than format the hdd, turn secure boot off, nic off, and efi boot on, install win 7 first, and then ubuntu, and it just worked? Nothing more?

---

### Post by leespa on 2013-08-21
I'd give the boot-repair option mentioned here a whirl. [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Dealing with the new EFI machines appears to be greasy at best. I think issue you may be facing is to get the machine to recognize your Ubuntu install in UEFI mode.

---

### Post by oldfred on 2013-08-21
If you installed to a totally blank drive, did you install in UEFI mode with gpt partitioning or in BIOS mode which could be either gpt or MBR(msdos). Windows only boots from gpt with UEFI, but Ubuntu boots either UEFI or BIOS with gpt. Both Windows & Ubuntu only boot in BIOS mode from MBR.

Boot-Repair's BootInfo shows all the details and often can fix issues. But with UEFI you usually have to go back into UEFI menu to choose what to boot and what is standard option.

---

### Post by don-kozm0 on 2013-08-21
I found out what was wrong. As this is my first install on a machine with UEFI, I had not thought about creating a EFI partition, therefor I could not boot Ubuntu from the drive. Created the EFI partition and now it works ;)

Anyway, thanks for the help and input :)

---

### Post by don-kozm0 on 2013-08-22
> **oldfred said:**
> If you installed to a totally blank drive, did you install in UEFI mode with gpt partitioning or in BIOS mode which could be either gpt or MBR(msdos). Windows only boots from gpt with UEFI, but Ubuntu boots either UEFI or BIOS with gpt. Both Windows & Ubuntu only boot in BIOS mode from MBR.

Boot-Repair's BootInfo shows all the details and often can fix issues. But with UEFI you usually have to go back into UEFI menu to choose what to boot and what is standard option.


And now it wont boot from the disk again. God damn UEFI. Arrrrgh. Tried Boot Repair from a memory stick, it booted like it should, loaded and then crashed after a while. Back to square one. 

To answer your question I had to install Ubuntu in UEFI mode, the laptop refuses to boot anything in Legacy mode :(

In fear of sounding like a total noob here, do I actually have to have a efi partition created by Windows before I even try to Install Ubuntu to get Ubuntu to boot correctly? What I mean is, is the EFI partition that Ubuntu creates uncapable of booting correctly? Seems that way to me. Because the only difference between me and leespa is that he installed windows 7 first(which I assume then creates a efi partition) and then installed Ubuntu afterwards.

---

### Post by don-kozm0 on 2013-08-22
Just installed 13.04 from scratch, and now it boots correctly again. No logic in this(at least I dont see it). We will just have to see how long it works this time....

---

### Post by don-kozm0 on 2013-12-16
Disabling the onboard LAN in the BIOS settings does "fix" the boot issue when trying to install any Linux distro it seems, but then you obviously are left with a machine that has no useful Ethernetport, and you can only use WLAN. Has anyone made any progress here as to enable the onboard LAN and still get a working computer? There seems to be a BIOS update available now for the p50 on Toshibas website. Anyone had a go with that update yet?

What I have done as a workaround is to buy a USB->Ethernet adapter. However then I only get 100mbit instad of gigabit, and it is also unpractical to run around with an adapter instad of just using the built in LAN port.

---

### Post by leespa on 2013-12-16
1) install OS off of USB with LAN disabled.
2) shutdown, go back into BIOS and re-enable LAN
3) carry on

---

### Post by don-kozm0 on 2013-12-16
> **leespa said:**
> 1) install OS off of USB with LAN disabled.
2) shutdown, go back into BIOS and re-enable LAN
3) carry on

I wish it was that simple. I have tried that. If I do that(ENABLE the LAN card after the installation of Ubuntu), then the pc tries to pixie(PXE) boot through the LAN card instead of booting from the SSD(and yes I have checked the boot order and the SSD is set to boot first), and if I go back into the BIOS again to disable NIC once more in order to get the computer to at least boot back up again, then the switching on and off(enabling/disabling) off the LAN card in the BIOS somehow confuses/corrupts the GRUB-loader and it doesnt see the efi partition any more, and the computer will not boot, and then I either have to use "boot-repair-disk" or reinstall Ubuntu from scratch again :(

---

### Post by leespa on 2013-12-16
I had to run fixparts on the drive as well, however, this is due to the fact that person who installed Win 7 (corp laptop) didn't completely nuke the Win 8 partitions.  [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

If you start with a completely fresh SSD and let Ubuntu choose installs you are still running into these issues?

---

### Post by don-kozm0 on 2013-12-16
> **leespa said:**
> I had to run fixparts on the drive as well, however, this is due to the fact that person who installed Win 7 (corp laptop) didn't completely nuke the Win 8 partitions.  [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

If you start with a completely fresh SSD and let Ubuntu choose installs you are still running into these issues?

Yes. If i start with a completely fresh SSD and install Ubuntu from scratch, I can install and boot Ubuntu as long as NIC is disabled, but once I enable NIC again it just wont boot of the SSD, and the grub loader gets messed up.

---

### Post by don-kozm0 on 2013-12-17
FINALLY I got it to work the way I want it to, but I had to "trick" the computer a bit to get it to work. I will explain more in detail below.


Up until now it has been my understanding(and also my experience in practice) that you cannot install any Linux OS on this computer in Legacy(CSM) boot mode. Every time I have tried that in the past, the screen just turns black when for example booting the install from a memory stick and nothing happens. Therefore I have been stuck with UEFI boot mode, which also involves killing the onboard LAN in order to get the installer to launch, but at least you can install any Linux distro this way. Loosing the onboard LAN was no longer an option for me, so a couple of days a go I bought a USB->Ethernet adapter. That workaround did the job, but is not very practical, and since the onboard LAN card is also a gigabit card I really would like that to work.


So what I did to make it all work was this:
Yesterday, for the first time in months, I tried installing Ubuntu in Legacy Mode again. I went into the BIOS, set the settings to CSM, enabled the onboard LAN card, saved the changes and rebooted with a USB pen drive with Ubuntu 13.10 on it. Instead of choosing install Ubuntu from the pen drive, I instead chose to do a live session, because I knew that booting into a live session in Legacy Mode would work. From that live session I then installed Ubuntu, rebooted, and voila, everything works. The OS boots up in Legacy Mode, no problems at all, and best of all, now the onboard LAN works too. 

I am not saying this will work for everybody, as my experience with this Thoshiba model is that it is quite "unpredictable", but it might be worth a shot for other people to at least try. Now I am a happy camper again :)

---

### Post by fernando21 on 2014-04-21
Looking for a definitive and easy way to install ubuntu 14.04 in a PC with Windows 8.1 installed, I finally decide to write a little resume of what I have done:

INSTALLING UBUNTU 14.04 WITH WINDOWS 8.1 IN TOSHIBA SATELITE P50
1. Make one partition from Windows 8.1 in the hard disk of 2GB. This one will be for swap partition.
2. Make another partition from Windows of the size you want.
3. Download the iso image from ubuntu.com (64-bits)
4. Use a good program to burn the image into a USB pen drive ([http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) could be one, but it hasn't been used in this tutorial).
IMPORTANT NOTE: The desire option is to make it from ubuntu but not with the utility provided, else from the command line with (more info [http://askubuntu.com/questions/59551/how-to-burn-a-iso-to-a-usb-device):](http://askubuntu.com/questions/59551/how-to-burn-a-iso-to-a-usb-device):)
 sudo umount /dev/sd[1 letter][optionally 1 number]
 sudo dd bs=4M if=[ur .iso] of=/dev/sd[that 1 letter]
 Example:
 sudo dd bs=4M if=windows7.iso of=/dev/sdc
5. Disable the windows Fast Startup feature ([http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html))
6. In Windows 8.1 go to Configuration/Shut down and holding the SHIFT key press Restart.
7. When you get the new menu, select Troubleshoot/UEFI Firmware Settings
8. In the BIOS disable: Fast boot and Secure Boot, save changes and exit.
9. Insert the USB drive
10. In Windows 8.1 go to Configuration/Shut down and holding the SHIFT key press Restart.
11. When you get the new menu, select  EFI USB Drive or similar
12. The PC must be initiated from the USB and there you could be choose Install Ubuntu.
13. If the Windows 8,1 OS is not recognised select Other options instead of erase.
14. For the next steps you can follow this tutorial in spanish or go to step 15: [http://www.ubuntu-guia.com/2012/04/como-instalar-ubuntu.html](http://www.ubuntu-guia.com/2012/04/como-instalar-ubuntu.html)
15. Select the partition for Ubuntu files, press change and select ext4 and mount in "/".
16. Select the partition for Ubuntu swap (2GB) and press change and select swap.
17. Select the whole Hard Drive for installing the whole Ubuntu OS ("/dev/sda" in last dropdown menu) and press Install.

I recomend to read this article for possible troubles in booting:
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)
For installing boot-repair (since its not available in 14.04) make this:
   sudo add-apt-repository ppa:yannubuntu/boot-repair
 sudo sh -c "sed -i 's/trusty/saucy/g' /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list"
 sudo apt-get update
 sudo apt-get install -y boot-repair
 sudo boot-repair

 
For those who have installed the ubuntu in no EFI mode, here you can find a help:
[https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode](https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode)

---

