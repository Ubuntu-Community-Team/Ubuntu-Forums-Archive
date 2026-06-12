---
title: "Is this a faulty motherboard problem?"
date: 2014-01-27
forum: Hardware
---

### Post by geomcd1949 on 2014-01-27
Built my first computer: Intel i-4770, asrock z87 extreme4 motherboard, 128 gb Vertex SSD, 16 GB RAM.

It won't boot. I tried with a fresh hard drive, a hard drive with a working OS, and also tried to reinstall Ubuntu 12.04 LTS.

On each startup, I go into the UEFI, set the boot order, and wait. When  it is set to boot from a hard drive, it asks which OS (Ubuntu, Ubuntu  safe mode, or memory test). When I select Ubuntu, it appears to start to  boot, then I get an interminable flashing horizontal line (like an  underscore) in the left hand corner of the monitor.

When I try to reinstall Ubuntu from a disc in the optical drive, it  begins the process by showint the logo in the middle of the bottom of  the screen, then just stops and does nothing.

When I put in (only) a working hard drive from another computer, it asks  what I want to boot, appears ready to statrt, and then the flashing  underscore is all I get.

I've taken the machine apart completely and carefully re-assembled it, using static-electricity protection. 

I'm wondering if this is a motherboard problem, or whether there is some  thing I don't know about that I haven't done. Thanks very much.

~George

---

### Post by grahammechanical on 2014-01-27
If you boot with the fresh hard drive without an OS on it, how far does the boot process get? The motherboard boot system (UEFI) should run some Power On System Tests (POST) and then it should look for an operating system to load at which point it should give an error message saying that it could not find an operating system. That would be a good indicator that the motherboard is working.

Does it get that far? Can you go into the boot system UEFI and set the boot priority for the optical drvie to be first and the hard disk to be second?

I think that you could have problems if you try to load Ubuntu that was set up on another machine. The Linux kernel will have modules for that other machine and not for the new motherboard.

I suggest that you decide to use the fresh hard drive and stay with that setup and then describe the problems that you are getting.

When you try to run the Ubuntu live session try this

1) At the first purple screen (with the two icons, keyboard and human) press Enter
2) At the Language screen select the language and press Enter. English is the default language.
3) At the Try Ubuntu - Install Ubuntu screen press F6
4) A menu will appear at the bottom right of the screen. Select nomodeset and press Enter.
5) Press Esc to get back to the Try - Install Screen and the select Try Ubuntu and press Enter.

Does the Ubuntu Live session load? You may need to try a combination of those F6 options. We can install Ubuntu form that Try - Install screen or from the live session desktop.

Regards.

---

### Post by oldfred on 2014-01-27
If booting in UEFI mode you do not get accessibility screen with tiny icons, but have to manually edit grub to add nomodeset. Just like after install having to edit it.  Use e on grub menu, scroll to linux line, replace quiet splash with nomodeset. If you have installed an only have Ubuntu you may not get grub menu unless you hold shift key, or some UEFI use escape key to get grub menu.

What video do you have? nomodeset works for nVidia, but others may need different settings.

 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

Also some motherboards may need settings changed from defaults.
This was posted on an older Asrock.

 So to people with an Asrock Z77 Extreme4 motherboard: if you install Ubuntu, make sure the drives you are installing from and to are not connected to the Asmedia SATA ports!

---

### Post by geomcd1949 on 2014-01-28
Was able to install 12.04 LTS from disk. Thanks for the help.

~George

---

