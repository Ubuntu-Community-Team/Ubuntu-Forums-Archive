---
title: "P3 450MHz&amp;32MB RAM - Freezes while unpacking nic-extra-modules"
date: 2005-08-14
forum: Hardware &amp; Laptops
---

### Post by Aubs on 2005-08-14
I'm kind of new to Linux, have used it on and off before, but keen to get into it more.

This is what I get when carrying out a server install (the most basic, right?):
[list=1]
[*]boot: Server <ENTER>
[*][!!] Low memory - Entering low memory mode - This system has relatively little free memory, so it will install in low memory mode. Among other things, this means that the installation will proceed in English. You should set up swap space as soon as possible. <CONTINUE>
[*][!]  Cgiise language - English <ENTER>
[*][!] Select a keyboard layout - British English <ENTER>
[*]Detecting hardware to find CD-ROM drives
[*]Scanning CD-ROM
[*]Loading additional components. Runs through many
[*]Does the following loop 12 times:
[list=a]
[*]Retrieving nic-extra-modules-2.6.10-5-386-di
[*]Unpacking nic-extra-modules-2.6.10-5-386-di
[*]Screen briefly goes blue with black stripe at bottom and cursor bottom left
[*]Screen briefly goes black with cursor at bottom left
[/list] 
[*]loop stops and sticks on the black screen with the cursor a the bottom left
[*]The Cd drive runs for a bit longer, say 30/40seconds then stops
[/list] 

I have tried numerous ways of installing (e.g. pci=noacpi, noapic, nolapic) with server/linux etc

I'm running a Gateway Solo P3 450MHz with 32MB RAM (well, it says 640KB System RAM & 31MB extended RAM)

I know it says it needs 32MB RAM, but is there any way at all of getting it installed? - the help (F1 at start of install) actually says it needs 28MB RAM.

They sent me 10CD's to give to friends, but if I can't install it on this laptop, I'm sure they will not be able to either!

I have used a different distro (redhat) and that installs completely, however, on booting, just before it gets to the login page, the screen goes completely white. I think this may have something to do with the screen settings that I used.

Anyway, I have created a 512MB swap space and set up the different drives (home, root, boot, var, tmp, usr, sawp etc), but ubuntu still doesn't work...

Any help greatly appreciated.

Aubs

---

### Post by gmc on 2005-08-14
[QUOTE=Aubs]I'm kind of new to Linux, have used it on and off before, but keen to get into it more.

This is what I get when carrying out a server install (the most basic, right?):
[list=1]
[*]boot: Server <ENTER>
[*][!!] Low memory - Entering low memory mode - This system has relatively little free memory, so it will install in low memory mode. Among other things, this means that the installation will proceed in English. You should set up swap space as soon as possible. <CONTINUE>
[*][!]  Cgiise language - English <ENTER>
[*][!] Select a keyboard layout - British English <ENTER>
[*]Detecting hardware to find CD-ROM drives
[*]Scanning CD-ROM
[*]Loading additional components. Runs through many
[*]Does the following loop 12 times:
[list=a]
[*]Retrieving nic-extra-modules-2.6.10-5-386-di
[*]Unpacking nic-extra-modules-2.6.10-5-386-di
[*]Screen briefly goes blue with black stripe at bottom and cursor bottom left
[*]Screen briefly goes black with cursor at bottom left
[/list] 
[*]loop stops and sticks on the black screen with the cursor a the bottom left
[*]The Cd drive runs for a bit longer, say 30/40seconds then stops
[/list] 

I have tried numerous ways of installing (e.g. pci=noacpi, noapic, nolapic) with server/linux etc

I'm running a Gateway Solo P3 450MHz with 32MB RAM (well, it says 640KB System RAM & 31MB extended RAM)

I know it says it needs 32MB RAM, but is there any way at all of getting it installed? - the help (F1 at start of install) actually says it needs 28MB RAM.

They sent me 10CD's to give to friends, but if I can't install it on this laptop, I'm sure they will not be able to either!

I have used a different distro (redhat) and that installs completely, however, on booting, just before it gets to the login page, the screen goes completely white. I think this may have something to do with the screen settings that I used.

Anyway, I have created a 512MB swap space and set up the different drives (home, root, boot, var, tmp, usr, sawp etc), but ubuntu still doesn't work...

Any help greatly appreciated.

Aubs[/QUOTE]
 You might be able to install Ubuntu with 32M of ram if you can create and activate the swap partition. I'm thinking that if you can get as far as partitioning the drive and create the swap partition, you should be able to switch to the alternate console (press f2) and issue the command 'swapon /dev/hdXX' (replacing hdXX with the drive/partition you created for swap).

You absolutely want to install as a "server" and pick and choose what packages to install, rather than let the install try and install the full gnome/desktop options. With 32M of ram, you'll probably find that even the most basic X11/desktop will be very slow. The smallest system I tried to install Ubuntu on had 64M of ram and it was pretty painful but it did work.

G.

---

### Post by blastus on 2005-08-14
Even if you managed to get it installed I think it would perform like crap and would constantly thrash the hard drive. And if you plan on running any serious server side stuff like Apache HTTP, Tomcat, JBoss, Mysql, Oracle or whatever they will grind your machine to a halt (that is even if you were able to install them in the first place.) Even if you just want to use it as a file or mail server or whatever I think you'd want more than 32Mb. 

My suggestion, go and see if you can find some cheap 2 x 256Mb chips and boost the RAM to 512Mb. I have an old P2 350Mhz machine with 512Mb of RAM and have never regretted putting in the extra memory. You need more RAM!

---

### Post by Aubs on 2005-08-14
GMC,
I don't think I can even get to the partitioning bit you mention... I'm not too bothered about speed as it's just a learning tool.

Blastus,
I don't particularly want to run much software on the install, I simply want to get into Linux and learn how it works. Unfortunately, I can't install it on my desktop for various reasons (one of which is financial!) and so getting more RAM for the laptop, isn't an option.


Thanks for your help guys, hopefully someone will be able to tell me why it fails on the unpacking of the module.

---

### Post by gmc on 2005-08-15
[QUOTE=Aubs]GMC,
I don't think I can even get to the partitioning bit you mention... I'm not too bothered about speed as it's just a learning tool.[/QUOTE]

I have an old Dell Laptop with 128M of ram, however to simulate 32M of ram I typed "server mem=32M". This forces linux to think I've only got 32M. I tried to install Ubuntu (Warty) and ran into the same problem you did. It appears the install goes into a loop trying to free up enough memory to continue the install.

I then tried 'server mem=32M debian-installer/framebuffer=false debian-installer/probe/usb=false hw-detect/start_pcmcia=false netcfg/disable_dhcp=true'. This effectively frees up a little more memory for the installer, by telling the installer not to load drivers for framebuffer video, nor try to detect usb/pcmcia and don't try and get an ip address from a local router. This seems to get a little further.

I felt that I was close to getting it, so I tried the above again, this time when the system appeared to go into the loop (CD access stopped). I pressed ALT-F2, pressed enter to get the console. Issuing a 'ps aux', to see what was running, I noticed that syslog was already running, so I 'kill -9 <pid>' of syslog, and then typed 'exit' to get out of the console. The CDROM started up again, but again, it appears there was insufficient memory for the installer to continue. Thought the screen kept flashing between blank and a message telling me "Loading additional modules" and trying to decompress nic-extra-modules-2.6.10-5-386-di.

Then it hit me! If the default server option was loading every module under the sun and causing the insufficient memory loop, perhaps server-expert might work. So I tried the following 'server-expert mem=32M debian-installer/framebuffer=false debian-installer/probe/usb=false hw-detect/start_pcmcia=false netcfg/disable_dhcp=true'. Then I, ALT-F2 over to the console, and use ps and kill to kill the syslog process, and then exit and ALT-F1 back to the install menu and began working my way down the list of options.

After several hours of choosing different configuration options and loading only the modules that my laptop requires to see the harddrive and CDROM, I came very close to getting Ubuntu to install but failed.

It occurs to me, can you boot the LiveCD in textmode only. You might be able to use that to create your swap partition. Unfortunately without a swap partition there's no way Ubuntu is going to install with only 32M of ram. Sorry I tried.

G.

---

### Post by peacemake on 2005-10-12
I have successfully installed ubuntu 5.10 on a laptop with 233Mhz P1 and 32Megs of ram. (Dell Latitude CP M233XT) When the installation was about to loop, I typed "swapon /dev/hda1" on console 2 and it went smooth after that. Just to let you all know. :)

-Nico

Edit: Oh, I -did- create the swap partition beforehand with a debian installer. 256Mbs. (If it's of any importance)

---

### Post by UCW181 on 2005-10-28
I have successfully installed Ubuntu 5.04 on an old laptop. Celeron processor with 32MB ram. Problem is... it's sooooo slow that you can't do anything much with the machine. I also encountered the nic-extra-modules loop when I started installing it on my laptop but was fixed when I did a "swapon /dev/hda2" on terminal 2. having a swap drive ready before installation is the key to a 32MB installation.

---

