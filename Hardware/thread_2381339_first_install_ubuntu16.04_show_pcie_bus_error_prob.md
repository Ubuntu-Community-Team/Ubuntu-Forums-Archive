---
title: "first install ubuntu16.04 show pcie bus error problem and pci=noaer can't work"
date: 2017-12-29
forum: Hardware
---

### Post by glados.ai on 2017-12-29
environment: i7-7700k, gtx1050ti, sm961(samsung nvme pcie3x4), ASUS prime Z270A, WD hard 1T), system WIN10, sandisk USB3.0

i use ultralso make a ubuntu16.04 USB flash disk uefi boot. I close the secure boot(only unload key PK) and fast boot. And when i choose install ubuntu, it shows PCIE bus error. I remove the gtx1050ti from motherboard. and problem still.
I try to close XMP and Intel rapid store. but the problem still. 
I try to add "pci=noaer" or "nomodeset", also can't install. But it does't show pci error, it only shows "BusyBOX V1.22.1............Unable to find a medium containing a live file system" 

detail :
(first)
PCIE bus error: severity=corrected , type=p
device [8086:a294] error status/mask=000
[0] receive error (first)
nouveau 0000:01:00.0: priv:HUB0: 00d054 00000007 (1e408216)
nouveau 0000:01:00.0: DRM: failed to create kernel channel, -22
busybox v1.22.1 ...................Unable to find a medium containing a live file system
And in command, i use lspci, show"...... 8086:a294 [0604] PCI-PCI bridge......." 

(second, add"pci=noaer")
nouveau 0000:01:00.0: priv:HUB0: 00d054 00000007 (1e408216)
nouveau 0000:01:00.0: DRM: failed to create kernel channel, -22
busybox v1.22.1 ...................Unable to find a medium containing a live file system
And in command, i use lspci, show"...... 8086:a294 [0604] PCI-PCI bridge......."

[add"pci=nomsi"]
e1000e 0000:00:1f.6 (unintialized):Failed to initialize MSI interrupt. Falling back to legacy interrupts.
nouveau 0000:01:00.0: priv:HUB0: 00d054 00000007 (1e408216)
nouveau 0000:01:00.0: DRM: failed to create kernel channel, -22   

[add nomodeset]
[COLOR=#000000]pcieport 0000:00:1c.4: PCIE bus error: severity = corrected, type=physical layer, id =00e4(receiver ID)[/COLOR]
[COLOR=#000000][COLOR=#000000]device [8086:a294] error status/mask=000000041/00002000
[0]receiver error
[6]bad TLP
usb 2-4 :device not accpeting address 2, error -62
[/COLOR][/COLOR][COLOR=#000000][COLOR=#000000]usb 2-4 :device not accpeting address 3, error -62
[/COLOR][/COLOR][COLOR=#000000][COLOR=#000000]usb 2-4 :device not accpeting address 4, error -71
[/COLOR][/COLOR][COLOR=#000000][COLOR=#000000]usb 2-4 :device not accpeting address 5, error -71
usb usb2-port4: unable to enumerate usb device

[/COLOR][/COLOR]
(third, remove gtx1050ti)
PCIE bus error: severity=corrected , type=p
device [8086:a294] error status/mask=000
[0] receive error (first)
busybox v1.22.1 ...................Unable to find a medium containing a live file system

(forth, remove gtx,and add "pci=noaer)
busybox v1.22.1 ...................Unable to find a medium containing a live file system

(fifth, rufus make ubuntu17.10,uefi's MBR)
same problem above

so what should i do?very thank your help!

---

### Post by oldfred on 2017-12-29
If you have nVidia video you need nomodeset until you can install the driver from the repository. You probably have to add the ppa to get the very newest driver for nVidia with Ubuntu.

You may need other settings in Asus' UEFI. 
My older Asus Z97 need lots of UEFI settings.

 Asus Prime Z270-A  Ethernet patch
[https://ubuntuforums.org/showthread.php?t=2351572](https://ubuntuforums.org/showthread.php?t=2351572)
Asus Z97 Motherboard Change UEFI from Windows (secure boot only) to other OS
[http://ubuntuforums.org/showthread.php?t=2298896](http://ubuntuforums.org/showthread.php?t=2298896)
Asus z97 screenshots:
[http://ubuntuforums.org/showthread.php?t=2258575&page=297](http://ubuntuforums.org/showthread.php?t=2258575&page=297)
Minor problems with using an ASUS Z97-A Motherboard
[http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard](http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard)
[http://askubuntu.com/questions/554735/good-z97-motherboard-for-ubuntu](http://askubuntu.com/questions/554735/good-z97-motherboard-for-ubuntu) 

      
 # Shows standard repository versions, which is the same as
System Settings, Software & Updates icon, Additional drivers tab
ubuntu-drivers devices 
   [https://askubuntu.com/questions/813676/installing-ubuntu-mate-with-dual-boot-option-on-windows-10-usb-booting-not-hap/814413#814413](https://askubuntu.com/questions/813676/installing-ubuntu-mate-with-dual-boot-option-on-windows-10-usb-booting-not-hap/814413#814413)
[https://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers](https://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 
   # should show newest versions available in addition
ubuntu-drivers devices

---

### Post by glados.ai on 2018-01-01
Very thank you for your help!

I try the method add nomodset &#65306;choose install ubuntu and press E to edit, 
and edit: linux  /casper/vmlinuz.efi  file=/cdrom/pressed/ubuntu.seed boot=casper only-ubiquity quiet splash nomodest

but show that:
pcieport 0000:00:1c.4: PCIE bus error: severity = corrected, type=physical layer, id =00e4(receiver ID)
[COLOR=#000000]device [8086:a294] error status/mask=000000041/00002000
[0]receiver error
[6]bad TLP
usb 2-4 :device not accpeting address 2, error -62
[/COLOR][COLOR=#000000]usb 2-4 :device not accpeting address 3, error -62
[/COLOR][COLOR=#000000]usb 2-4 :device not accpeting address 4, error -71
[/COLOR][COLOR=#000000]usb 2-4 :device not accpeting address 5, error -71
usb usb2-port4: unable to enumerate usb device


another question I don't know how to open a terminal, and I only see command-line like this: grub> [/COLOR]

---

### Post by oldfred on 2018-01-01
You are at a grub terminal, which only has a few limited commands that can be used to manually boot a broken system. But if from installer, it is either settings in Asus' UEFI or bad ISO or flash drive issue. 
Many with NVMe drives have needed the firmware updated. And you need to make sure you have newest UEFI from Asus.

Most new UEFI require you to turn on allow USB boot. And generally better to have UEFI Secure Boot off. You will need it off to be able to install nVidia driver once installed anyway. But you still want to boot in UEFI mode not Legacy/BIOS/CSM mode

Did you compare your UEFI with my older screen shots, I expect it is very similar.

       Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Check that ISO is correct.

 [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) 
Flash drive tests

 pendrive speed tests USB2 & USB3 various brands - user sudodus
[http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085](http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085)
Includes links to speed tests and lists some that do not work well.
[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

---

### Post by glados.ai on 2018-01-02
very thank you for your help again!!
Finally,  I success to install ubuntu. 
I change to 
(1)use an usb2.0 disk flash instead of usb3.0,
(2) open CSM(legacy and uefi),
(3) close rapd(open ACHI) 

Unbelievable!!!usb3.0 have a bad compatibility. nvida card and nvme have a good compatibility.

---

### Post by oldfred on 2018-01-02
Have seen others that had to use USB2, some were just able to use different USB3.
Perhaps an UEFI update would help?

Glad you got it installed. :)

If install is working, then you can change thread to solved.
And if future issues, then start a new thread with that issue in title.

---

