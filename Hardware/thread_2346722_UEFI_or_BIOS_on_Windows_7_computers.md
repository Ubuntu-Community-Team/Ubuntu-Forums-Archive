---
title: "UEFI or BIOS on Windows 7 computers"
date: 2016-12-17
forum: Hardware
---

### Post by t0p on 2016-12-17
I bought a HP laptop with Windows 8.1... and it had the awful UEFI on it, and I can't dual-install it with Ubuntu.  Result: spending time getting rid of viruses and malware.

If I bought an older, refurbished laptop loaded with Windows 7, would it come with the good old BIOS to enable a dual-install?  Is UEFI just for Windows 8 and over?  Or do some machines with Windows 7 have the blasted UEFI?

I've tried umpteen approaches to getting Ubuntu to sit next to my Win 8.1 and I'm sick of it. My old laptop (now unfortunately housebound due to a broken monitor and keyboard) runs Win 7 and Ubuntu with no problem.  So what do you think: Will a laptop preinstalled Windows 7 come with a friendly BIOS?  Or might it be UEFI?

---

### Post by sudodus on 2016-12-18
I have bought refurbished computers and I have helped friends buy such computers with Windows 7 as well as with Windows 10 installed in BIOS mode. That company installs in BIOS mode by default, so it is possible. (It might be difficult to buy Windows 7 now.)

You should tell the company (that you might buy from) that you want Windows installed in BIOS mode (and *check* that they will do it for you, before you buy it, and *specify* BIOS in the order).

---

### Post by yancek on 2016-12-18
>  Is UEFI just for Windows 8 and over?

Computer with windows 8 and newer which are pre-installed are almost always UEFI.  Older windows are almost always NOT UEFI so if you bought a computer with windows 7, it probably will be the older MBR.  Where I live, it is pretty easy to get a system from a local computer shop with win 7, you might check that.  If you are buying online, I'm sure they will indicate which OS.

Dual booting windows/Ubuntu UEFI is explained in detail at the link below.  

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2016-12-18
We have seen just a few Windows 7 systems with UEFI. 
Usually vendor started trying out his new UEFI just before UEFI was required with Windows 8. Windows 8 or later also required UEFI secure boot where Windows 7 if UEFI cannot use Secure boot.
Some users also install Windows 7 in UEFI on newer hardware, but DVD is BIOS only. It has to be copied to flash drive & files moved to make it UEFI bootable.

HP does not make it easy to install other systems, but we have seen many dual boot UEFI HP systems. What model is yours?
HP uses description as part of UEFI boot which is not allowed per UEFI spec. But there are many work arounds, depending on if dual boot or Ubuntu only.

       [http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook](http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook)
Some HP will not boot a flash drive that is gpt partitioned. Some only boot from the USB2 port not USB3 ports.
[http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260](http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260)
HP Check if Customized UEFI settings available like this  HP ProBook 4340
[https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216](https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216)
HP Envy 700-430QE desktop used bcdedit to dual boot
[http://ubuntuforums.org/showthread.php?t=2260681](http://ubuntuforums.org/showthread.php?t=2260681)
Boot Ubuntu 14.04 LTS 64-bits on external hdd - HP Envy 17 w/Windows 8.1 Details
[http://ubuntuforums.org/showthread.php?t=2256244](http://ubuntuforums.org/showthread.php?t=2256244)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)
It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
Envy M6 Change boot order sudo efibootmgr -o 2,1 post #23
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)

Boot-Repair now has an option "use standard efi file" to eliminate the manual copying of files.

 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

