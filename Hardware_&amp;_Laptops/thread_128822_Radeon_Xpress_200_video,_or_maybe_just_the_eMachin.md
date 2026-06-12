---
title: "Radeon Xpress 200 video, or maybe just the eMachine"
date: 2006-02-12
forum: Hardware &amp; Laptops
---

### Post by 09dgc on 2006-02-12
Ok, so I got my Ubuntu install to work, thanks to tseliot's help.  Now, however,  when I choose Ubuntu from Grub Loader it boots up, then my screen goes black.     I've got an MSI 7145-RS480M motherboard, with integrated Radeon Xpress 200 graphics, and I'm not sure that ATI had any drivers that are going to make my display work.  Are there any possible solutions to this problem?  Thanks.

---

### Post by tseliot on 2006-02-12
[QUOTE=09dgc]So, I took a look at this thread [http://www.ubuntuforums.org/showthread.php?t=98698&highlight=radeon+xpress+200](http://www.ubuntuforums.org/showthread.php?t=98698&highlight=radeon+xpress+200)
and found that other people have experienced problems with  the ATI Radeon Xpress 200 onboard video/ATI RS480 chipset, though their problems come after installation.  I can't even get Ubuntu to install on my eMachines T6520, in 64 bit or 32, and I've tried numerous other distros that all hang.  During the installs, IRQ 185 misbehaves, but can't be disabled.  There's also a lot of documentation about eMachines in general disliking Linux, and lots of people have been forced to bootstrap, but I can't find any info on the T65-- line.  For reference:
[http://www.emachines.com/support/product_support.html?cat=Desktops&subcat=T-Series&model=T6520](http://www.emachines.com/support/product_support.html?cat=Desktops&subcat=T-Series&model=T6520)  Does anyone have any thoughts?  Sorry if I didn't explain myself adequately or include enough information, I'm new at this.  Just let me know what I should do to make my problem more clear, and thanks for your time.[/QUOTE]
My father has the same motherboard (it's a Compaq PC) but I've never had any problems as far as the installation is concerned.

Anyhow I think this trick might work for you:
follow this guide of mine:
[http://ubuntuforums.org/showthread.php?t=75281]("http://ubuntuforums.org/showthread.php?t=75281")
Get to the following part of the guide:
[QUOTE=tseliot]UBUNTU 32BIT SECTION

This trick doesn't work for everyone (it depends on your hardware). For this reason I suggest you to try it on an Ubuntu Livecd


1) 

a) If you haven't installed Ubuntu 32 bit yet...[/QUOTE]

And use this boot option: noapic acpi=noirq

In other words you will need to type this at boot:
```
linux noapic acpi=noirq
```

NOTE: you will pass that boot option to the Install CD instead of the Livecd(which my guide refers to). In this way the boot option should prevent the installer from freezing.

Another thing: Upgrade your BIOS if you can.

---

### Post by 09dgc on 2006-02-12
Thanks for your reply.  I made some progress, but not a lot.  By booting with the comand line code you gave me, I was able to get to the normal Ubuntu install screen.  Everything was going well until it came time to parition the drive so I could dual boot.  I set up the parition to be the minimum posible size, hit continue, it was accepted without any problems, and then the install crashed.  I let it sit for over an hour before I gave up on it.  Then really bizarre things happened.  I couldn't turn off my machine with the power down button.  Every time I turned the comp off, it would boot up again without me even touching it.  When it did boot again, the screen read "no signal."  I had to actually pull out the power cord to get it to turn off.  When I plugged it back in, the display worked, Windows ran checkdisk and then booted normally.  I went to check my   disk and it wasn't partitioned any differently than before I had used the Ubuntu  disk.  On a potentially related note, though I'm not sure, I was using the 64 bit install disk.  Thanks for your help, I may hold off on another attempt until I have more time, but I'll be sure to let you know if it works.

---

### Post by tseliot on 2006-02-12
[QUOTE=09dgc]Thanks for your reply.  I made some progress, but not a lot.  By booting with the comand line code you gave me, I was able to get to the normal Ubuntu install screen.  Everything was going well until it came time to parition the drive so I could dual boot.  I set up the parition to be the minimum posible size, hit continue, it was accepted without any problems, and then the install crashed.  I let it sit for over an hour before I gave up on it.  Then really bizarre things happened.  I couldn't turn off my machine with the power down button.  Every time I turned the comp off, it would boot up again without me even touching it.  When it did boot again, the screen read "no signal."  I had to actually pull out the power cord to get it to turn off.  When I plugged it back in, the display worked, Windows ran checkdisk and then booted normally.  I went to check my   disk and it wasn't partitioned any differently than before I had used the Ubuntu  disk.  On a potentially related note, though I'm not sure, I was using the 64 bit install disk.  Thanks for your help, I may hold off on another attempt until I have more time, but I'll be sure to let you know if it works.[/QUOTE]
A friend of mine had the same problem yesterday. He was trying to resize his windows partition but the installer hanged (Ubuntu's, Fedora's, etc.).

He had to defrag his Windows partition and try the Ubuntu installer again and everything worked. Please try it (and of course don't forget to use that boot option).

I hope it helps.

It's not a kernel incompatibility as that chipset is supported by kernel 2.6.12 (which Ubuntu uses by default) or higher.

---

### Post by 09dgc on 2006-02-12
Bump

---

### Post by 09dgc on 2006-03-05
Bump

---

### Post by 09dgc on 2006-03-11
Bump

---

### Post by brucehohl on 2006-03-18
Bump, Bump, Bump ... does this mean you are still having trouble?

Did you defrag as noted above?

You may also need to do the following from Windows:
Accessories > System Tools > Command Prompt
chkdsk /f

Then follow the instructions, that is, the command will run at next boot.
So reboot the computer to Windows so the command runs.
Afterwards you can try again to install Ubuntu.

---

