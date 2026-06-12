---
title: "Nvidia GTX 660, unable to install Ubuntu"
date: 2013-12-25
forum: Hardware
---

### Post by Bachey on 2013-12-25
Hi!

I am unable to install ubuntu on my new pc. When I insert the CD, the it loads for a while, but then the screen goes blank forever. I have a feeling it's the video card. model: nvidia GTX 660. Please help me out of this matter!

PS: Merry Christmas! :)

---

### Post by oldfred on 2013-12-25
If it is just nVidia and not dual video nomodeset should work. If dual video you may be using the Intel chip and need different boot parameters.

If UEFI booting with Windows 8 pre-installed you need to follow the grub boot instructions that are shown after the install. Or just use e on grub menu, scroll to linux line and replace quiet splash with nomodeset.

 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

      
 Backup efi partition and Windows partition before Install of Ubuntu.
Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Bachey on 2013-12-27
> **oldfred said:**
> If it is just nVidia and not dual video nomodeset should work. If dual video you may be using the Intel chip and need different boot parameters.

If UEFI booting with Windows 8 pre-installed you need to follow the grub boot instructions that are shown after the install. Or just use e on grub menu, scroll to linux line and replace quiet splash with nomodeset.

 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

      
 Backup efi partition and Windows partition before Install of Ubuntu.
Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Thank you man! You helped me a lot! BUT, the system still does not work. I could now install ubuntu on my bare hard drive. It is done. And after the installation is complete it leads me to a black screen. Then I just restarted and CTRL+F1 and in console
```
sudo apt-get --purge remove nouveau
``` so now the system can boot, but without hardware acceleration and low resolution. If I install the prop. drivers in system settings, then the booting does not work again. Is it possible to fix this?

---

### Post by oldfred on 2013-12-27
Does nomodeset get you into low resolution, still?
Or does recovery mode, second option in grub menu work?

Which version of Ubuntu? Some need the headers installed first to get nVidia correctly installed into kernel.
       sudo apt-get install linux-headers-generic

    

It should have suggested the correct nVidia as an option, but may show old ones also. Which driver did you install.
 cat /sys/module/nvidia/version 

And have you used nvidia X server settings to configure system? Mine is in Administration, but I have the old menu system.

---

### Post by Bachey on 2013-12-27
13.10 - headers are already installed.
I installed version 331 and when I boot it shows a black screen with a messagebox in the middle saying xserver failed to check the setting and a few options with radio buttons. Everytime I reboot, it drops me automatically to console (like when I press CTRL+F1). I'm getting confused... Does that mean my pc is not compatible with ubuntu?

---

### Post by oldfred on 2013-12-27
Do not know specifics of your model nVidia card. I have a much older one that still works. 9600GT. And I thought only some of the older drivers had issues with the very newest nVidia cards.

While not your exact model it seems to have both older & newer and higher end and lower end or brackets your model. I think this is just with the open source driver.
[http://www.phoronix.com/scan.php?page=article&item=nvidia_9geforce_opencl&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_9geforce_opencl&num=1)

Both open & closed source drivers.
[http://www.phoronix.com/scan.php?page=article&item=amd_nvidia_15way&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_nvidia_15way&num=1)

---

### Post by Bachey on 2013-12-27
I had a GT 430 earlier, and didn't experience any problem with it... Looks like it's the newer cards that make the struggling.

---

### Post by Bachey on 2013-12-27
I could boot with failsafex, low graphics mode and nvidia driver installed. Now I can open nvidia xserver settings, and it does not look how it should. And my resolution should be 1920x1080... [IMG]http://kepfeltoltes.hu/131228/why_www.kepfeltoltes.hu_.png[/IMG]

---

### Post by oldfred on 2013-12-27
Please attach screenshots. You can use the paperclip icon in the advanced editor.

This is my screen. It looks like your nVidia is not really working?

---

### Post by Bachey on 2013-12-28
Nope, my nVidia is REALLY working! I installed elementary OS now and everything is fully functioning! YAY!

---

