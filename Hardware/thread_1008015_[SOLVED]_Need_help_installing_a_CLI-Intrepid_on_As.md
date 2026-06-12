---
title: "[SOLVED] Need help installing a CLI-Intrepid on Asus EEE PC 1000H via USB pendrive"
date: 2008-12-11
forum: Hardware
---

### Post by lardandweed on 2008-12-11
Hi! I've been on this for three days and i just can't get the installation to work. I think i'm quite close though. :P Here's what i need to do...
[B]
install a [COLOR=Red]command-line version of ubuntu[/COLOR] on my eeepc 1000H using a [COLOR=Red]USB pendrive[/COLOR], through the [COLOR=Red]local files contained within the Intrepid alternate CD iso[/COLOR]. [/B]

why so specific?
1) I want CLI-only ubuntu because I feel like seriously diving into linux (i think i'll learn the most by throwing myself in the deep end =p)
2) USB pendrive because the eeepc has no cd-rom drive and i don't want to spend $100+ on an external drive (hardware is costly in my country) when i have a bunch of pendrives ready at my disposal
3) I have to use the files local to the iso because the ubuntu-installer does not include the eee ethernet drivers, so i cannot download the necessary files through the repositories. This means that the minimal-CD-iso is out for me

Yup! that said, i've been tampering around with many different configurations to my setup files, but to no avail. I get different levels of success though. Just an idea of what i've tried


[B]method 1) Using UNetbootin to create my bootable-pendrive installer
[/B]If i do this in ubuntu, i can only boot with default options. All other options on the Unetbootin boot menu don't work. I selected help and it strangely booted (i presume it was the default boot) No CLI install means no go.

If i used UNetbootin in WinXP, the option to install a CLI-ubuntu works via the boot menu, but now, instead of detecting CDROM, the installer tries to detect network hardware. Meaning i can only install by downloading components from the repositories, which won't work on the EEE PC (see earlier point about having no ethernet drivers)


**method 2) In WinXP, use syslinux to make the drive bootable. Then throw in the required files in various combinations,** (i.e. extract iso and rename isolinux folder and isolinux.cfg to syslinux and syslinux/extract only install and isolinux and then dump iso into drive/etc)

Not useful at all. Somehow, a winxp-syslinuxed boot menu turns out quite warped. There is no option to boot via cli or cli-expert at all. Pressing F4 & F6 does nothing. I managed to get a boot: prompt via Help+F3, then i typed cli, but it says "Could not find kernel image: cli"


This is turning out a little long, so i'll proceed to the best configuration i've got. 
**best method) In linux, use syslinux to make the drive bootable and extract the contents of the iso into the USB drive** 
1) partition using fdisk
2) syslinux to make drive bootable
3) extract contents of iso[INDENT]*mount -o loop /path/to/iso /media/cdrom0
*cp -r /media/cdrom0/* /path/to/usb
(i get the notice that some symbolic links cannot be copied because FAT doesn't support them. More on this later)
[/INDENT]4) doing the isolinux>syslinux adjustments

Now, i can boot into a cli-install at the boot menu using F4. And it give me the option to detect cdrom instead of network, which is great as well! But of course, since eee pc has no cdrom, it can't detect anything. So i use this:[INDENT]*mkdir /cdrom /dev/cdroms
*cd /dev/cdroms
*ln -s ../sdb1 /cdrom0
*mount -t vfat /dev/cdrom/cdrom0 /cdrom
[/INDENT]And my cdrom is now detected, but then now it seems that the installer can't read data from installation files in cdrom or something like that. So i tried looking through the debug log to see what i can glean from it. I found out that "cdrom/dists/stable/release doesn't exists" via the system log. It turns out that on the iso, /dists/stable/ is a symbolic link(recall earlier point about symb-links) to /dists/intrepid/. So what i did was to create /dists/stable/ and /dists/unstable/ and copy all the files over from /dists/intrepid/ (there is another symbolic link and i made the adjustments just in case)

and with this, the installer is able to carry on loading the required components! yaay! alls swell up till "install the base system", whereupon i get a "debootstrap error - failed to determine the codename for the release". This is still beyond me at this point and i'm still trying to find out what's causing it. Not sure if the intermediary fixes would have broke anything to begin with =/

additionally, as i was looking through the debug log, i noticed these:[INDENT]*DEBUG: resolver (libc6-udeb): package doesn't exist (ignored)
*DEBUG: resolver (libc6): package doesn't exist (ignored) 
*DEBUG: resolver (libnewtx0.52): package doesn't exist (ignored) 
*DEBUG: resolver (efi-modules): package doesn't exist (ignored)
[/INDENT]I notice they either seem to occur quite consistently, i believe it's when the installer shifts between menu and submenus. Just hazzarding a guess. Could they be the main problem?

Well, this is a horrendously long post. I appreciate it if you have followed me all the way through. I thought I'd try to be as elaborate as i can to help with the troubleshooting process, but if you think certain sections can be shaved off, do let me know and i'll make the necessary adjustments! thx

---

### Post by snowpine on 2008-12-11
Hi there, I've been following your eee troubles with interest. Sorry the alternate CD suggestion didn't work. :(

The only other lead I can think of is this: The Debian eee project has a tiny netinstall equivalent to the Ubuntu mini.iso. This 16mb installer includes the wired and wireless drivers for all of the eee models (well, supposedly... I can only verify that it worked on my 900ha). Maybe if you post over there, someone can explain which drivers are needed and whether or not it's possible to do the same with Ubuntu. [http://wiki.debian.org/DebianEeePC/HowTo/Install](http://wiki.debian.org/DebianEeePC/HowTo/Install)

It's a long shot but I know you are looking for a learning experience. :)

---

### Post by lardandweed on 2008-12-11
Hihi!

You might have seen this on the eee user forums but, well, i've solved the problem by using Intrepid Live to create a bootable USB with the alternate-iso. Now it all runs like it should \\:D/


Btw, i realised you use crunchbang linux too?

---

### Post by snowpine on 2008-12-11
Yeah man, love the CrunchBang!

Glad you got it working. :)

---

### Post by chuchi2k2 on 2009-02-03
Hi guys. I follow lardandweed's steps to install Ubuntu Alternate 8.04.2 on my Samsung NC10 (similar to eee 1000h). All with identical results:

"debootstrap error - failed to determine the codename for the release". 

Of course, i'd previously mount the usb, and for me changed the name of two files in the USB:

nic-restricted-firmware-2.6.24-23-generic-di_2.6.24.16-23.56_i38
to
nic-restricted-firmware-2.6.24-23-generic-di_2.6.24.16-23.56_i388.udeb

and

nic-restricted-modules-2.6.24-23-generic-di_2.6.24.16-23.56_i386
to
nic-restricted-modules-2.6.24-23-generic-di_2.6.24.16-23.56_i386.udeb

because the installer stops at loading modules if these two files have not changed the names.

Finally at the "Install base system" stage, the installer stop with error: "debootstrap error - failed to determine the codename for the release". 

I'd try with Intrepid Live and USBCreator with Hardy-Alternate ISO but unlucky with the same error.

Suggests?

---

