---
title: "installation destroyed mbr"
date: 2009-08-04
forum: Installation &amp; Upgrades
---

### Post by jeanlucmalet on 2009-08-04
Hi,
I'm not a regular ubuntu user, I just tested the 9.04 and well I find it impressive:KS! however for a friend I wanted to install it on a usbdrive in order to avoid having something changed on her drive (MacOSX user)
so I made the install, selected /dev/sdb1 as /.... well everything went fine and it copied the files.... :popcorn:
BUT
at the end it was impossible to boot neither on MacOSX nor the usbdrive:(
it seems that grub got installed on /dev/sda mbr (then overwriting the macosX mbr) and that no bootloader got installed on /dev/sdb....

I don't like grub because it require to be installed on mbr, but I find more dangerous to have no prompt asking the user where the bootloader shall be installed....

I've done several install with other distro more "geek" oriented, using lilo on first sector of partition, and it did worked everytime.... it's the first time that I'm getting such error

---

### Post by presence1960 on 2009-08-05
GRUB is not required to be installed on MBR. When you get to the Ready to install window (see attached screen shot) you should have clicked the advanced button and chose sdb as the location to install GRUB. If no location is selected it defaults to sda which is the MBR of the first hard disk, which is where practically all OSs put their bootloader unless specified otherwise by the user. You can choose to install GRUB to partitions and they are listed in that menu (sda1, sda2, sdb1, sdb2, etc) You can restore GRUB to MBR of USB drive and after that is completed set BIOS to boot from CD, USB or Removable, then sda. This will only bring up GRUB if the external USB is plugged in when you boot.

Restore GRUB:
> 1. Boot your computer up with Ubuntu CD with USB drive plugged in.
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd1)", to install GRUB to MBR of sdb
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
Now change the boot order in BIOS.

The next step I can't advise because I know zippo about Macs. You need to restore Mac's bootloader to sda. Unplug the USB when you restore Mac's bootloader. When this is done, then when the USB is unplugged Mac's bootloader will take over.

This method will allow Mac to be unscathed and still allow you to boot Ubuntu from GRUB when the USB is plugged in at boot.

Just be aware your assumption that GRUB must be installed to MBR is erroneous. I run Ubuntu Jaunty, Sabayon 4.1, Mint 5 & Win 7 RC. Jaunty's GRUB is installed to MBR but Mint's and Sabayon's are installed to their respective partitions not MBR. Sabayon is on a separate disk from the other OSs. I chainload Mint & Sabayon off of Jaunty's GRUB.

I am sorry your friends machine got messed up, but it is fixable. I say this all the time on here : before one tries to install a new OS one should really spend time studying and reading documentation of what it is they are about to do and become familiar with what it is they are going to do **_BEFORE_** actually attempting to do it. I found out about that advanced button on the Ready to install window by reading beforehand.

---

### Post by jeanlucmalet on 2009-08-06
Well, sorry to not have RTFM before installing.... however I'm not unfamiliar with linux, and this is the first time that during an install I've to click to advanced somewhere for such critical feature such as the bootloader... :(
such behaviour will just drive users from ubuntu. why don't you do like Microsoft or Apple and just destroy everything assuming that you're the only OS that shall be on the computer (well this is almost what you do when displaying the install partition, hopefully this is so brainless that the user seek for the small button)? 
well I just find that this small button on a summary screen isn't welcome... looking for solution (at the end the system had to be completely reinstalled after format) I saw lot of post asking for help for such case.... most of them ended with lines like "I will never install ever again a linux on my mac".... :(

---

### Post by Mark Phelps on 2009-08-06
I'll probably get flamed for saying this, but I basically agree with your concerns.  Linux (in general) and Ubuntu (specifically) is going through a time when a greater and greater part of the community is composed of nontechnical folks (at least, when compared to the CLI-or-nothing perspective of the hardcore Linux users).

I'm not saying this to be insulting, quite the opposite.  I'm saying that installation processes need to be revamped to PREVENT folks from accidentally doing damage to their machines. I agree that to expect someone unfamiliar with Ubuntu to click another option to prevent from overwriting the MBR on a machine that already has another OS installed is not realistic.  A more reasonable behavior would have been to (1) detect the presence of the other OS, (2) determine which drives COULD hold the modified MBR, and (3) display a warning to the user that using the default will overwrite the exiting MBR, and (4) offer a selection list of other places to write the MBR.

Yeah, I know that most probably, many people wouldn't read the warning -- but at least they would get one and be told that they need to make a choice. 

Also, as a side-effect, if the installer overwrites an existing MBR, it should (1) automatically make a backup of that MBR, and (2) provide an option (as part of the boot menu) of restoring that MBR from backup.  The second would help out lots of folks who install dual-boot to experiment with Ubuntu and later, want to get their previous system back, including the original MBR.

But, these are just my opinions.

---

### Post by jeanlucmalet on 2009-08-06
in fact a better solution would have been to display a screen like the partition selection one that display several possibilities with some text and default option.... like this no way to shoot into the foot without notice....
in fact I thought that grub add to be installed into mbr (which I find a stupid solution... mbr shall never be touched!) but seems not, so a good way is to display thing and I totally agree :
> I'm saying that installation processes need to be revamped to PREVENT folks from accidentally doing damage to their machines
because saying to someone that have some linux experience that he had to RTFM..... lol what shall we say to a linux beginner?

---

### Post by presence1960 on 2009-08-06
My statement wasn't meant to be interpreted as RTFM. Undertaking  an operation such as installing an OS, especially one which the user is totally foreign or just a little green to, should be researched prior to trying to install. As a matter of fact most people are not versed in installing OSs because their machines come with the OS preinstalled. Most of those have a recovery disk and/or recovery partition. Using a recovery disk/partition really does not qualify as installing an OS because all the partitioning, formatting, installing of drivers, etc is done by the recovery process. The user has to make no choices other than whether to start the process or not.

Now if you have ever installed from an OEM or install disk you know what I am talking about. you must make all those decisions about partitioning, formatting, where to install etc.

Unfortunately most computer users today have  not the faintest idea of how to truly install an OS.

Given the above facts is why I say one must read & study what they are about to do and become at least somewhat familiar with exactly what it is they are trying to do before they attempt to do it.

Or they could have asked for help on here before the install. 

My comment wasn't meant to be a smug RTFM reply, rather it was meant as a good suggestion for someone rather unfamiliar with the Ubuntu (or any other OS for that matter) install process. That is why we have a whole section of documentation on things to read when switching from another OS. Like everything else in life you will only get out of this what you put into it.

What really baffles me is why you are arguing about this when maybe you should be restoring GRUB to MBR of the USB drive and finding out how to restore Mac's bootloader to that sda drive! After all isn't a working computer what you want or would you rather be right than happy?

---

### Post by presence1960 on 2009-08-06
> **Mark Phelps said:**
> I'll probably get flamed for saying this, but I basically agree with your concerns.  Linux (in general) and Ubuntu (specifically) is going through a time when a greater and greater part of the community is composed of nontechnical folks (at least, when compared to the CLI-or-nothing perspective of the hardcore Linux users).

I'm not saying this to be insulting, quite the opposite.  I'm saying that installation processes need to be revamped to PREVENT folks from accidentally doing damage to their machines. I agree that to expect someone unfamiliar with Ubuntu to click another option to prevent from overwriting the MBR on a machine that already has another OS installed is not realistic.  A more reasonable behavior would have been to (1) detect the presence of the other OS, (2) determine which drives COULD hold the modified MBR, and (3) display a warning to the user that using the default will overwrite the exiting MBR, and (4) offer a selection list of other places to write the MBR.

Yeah, I know that most probably, many people wouldn't read the warning -- but at least they would get one and be told that they need to make a choice. 

Also, as a side-effect, if the installer overwrites an existing MBR, it should (1) automatically make a backup of that MBR, and (2) provide an option (as part of the boot menu) of restoring that MBR from backup.  The second would help out lots of folks who install dual-boot to experiment with Ubuntu and later, want to get their previous system back, including the original MBR.

But, these are just my opinions.

I won't flame you for that. Actually your points have merit. But from my perspective I really don't care if another person uses Ubuntu or any other OS for that matter. I know how to install it. I will gladly try to help others who want to give Ubuntu a try without any expectation in return. Like I said your points have merit but they don't bother me enough to voice my opinion about them. I messed up badly on my first attempt at installing Ubuntu. I picked the wrong install option and wiped my windows partition. Luckily I had my data backed up. I blamed Ubuntu at first because I was so mad. But after I reinstalled Windows from an OEM disk I started reading what I decided I didn't need to read the first time. Everything I needed to know about the install was there for me. Armed with the plan of how I was going to install Ubuntu as a dual boot I was a success the second time. The reason for my success was knowledge gained from reading community documentation and I was prepared that second time around.

It is human nature to push blame away from or outside of oneself rather than to accept responsibility for oneself. That is called projection. We all do it. Ubuntu didn't mess up the install, it only does what the user tells it to do.

---

### Post by jeanlucmalet on 2009-08-07
sorry if my reply looked harsh... it wasn't meant to be.
the problem with macosX is that I couldn't find any way to restore the mbr (well all google answer that I tried only lead to the same result : a beautifull icon with a question mark on it.... ) in fact the macosX install disk has never been thought with in mind that someone could try to install something else than macOSX (like windows the uniq thinking way is that macOSX is the WORLD) so in fact when you destroy the mbr, the only way to have it restaured is to destroy the partition and reinstall everything... (unlike windows where you can use linux to retore the mbr...)
this was just a suggestion for making the installer more user friendly, and more, more safe (I wouldn't like to hold a gun without safety and shoot me in the foot) is to display an additional screen like the partition installation menu, for bootloader installation location selection :popcorn:

something like :
> 
bootloader install selection
the bootloader is a small program that allow you to select among all os available on the system. it can be installed into the first sector of the disk (called MBR) and shared among all systems installed, or be installed into the system partition and then be system private
* install in primary disk MBR
* install in UBUNTU partition
* install elsewhere
if install elsewhere is selected then an advanced selection screen will be displayed for advanced users

---

### Post by davidshere on 2009-08-07
> **jeanlucmalet said:**
> Hi,
It seems that grub got installed on /dev/sda mbr (then overwriting the macosX mbr) and that no bootloader got installed on /dev/sdb....

Exact same thing just happened to me.  I have a Dell laptop provided by my employer.  I wanted to install Ubuntu 904 on a 4GB USB drive I have.  I've done this before about three times on a different laptop, and didn't have any problems.  

This time, grub was installed on the laptop HD.  Not necessarily a problem -- I can still dual boot -- unless you also take into consideration that the grub configuration files are on the USB.  So now my laptop won't do anything without this USB stick.  I hope I don't try to wash it in the clothes washer, again.

I do beleive that next time I'll do the smart(er?) option -- create the USB as a live "CD" instead of a straight install.  Lesson learned.  Installing an OS on a flash drive, using the laptop as little more than a "host" or "bridge" between the CD and the flash drive, seems to me to be an advanced operation, and warrants an "advanced" button.  I'm by no means green to Ubuntu; I've installed it what seems like hundreds of times.  I think I've even made this exact mistake before.

In the meantime, will a "fixmbr" with the windows installation CD fix me?

---

### Post by jeanlucmalet on 2009-08-07
well doing a usb as a live cd (using syslinux) didn't worked for me, and anyway I wanted to be able to update de distribution (gcompris on the liveCD segfault). CDROMS is something of the past, some relic that scratch, is slow, never work when expecting... flash rocks! :popcorn:

---

### Post by presence1960 on 2009-08-07
> **jeanlucmalet said:**
> sorry if my reply looked harsh... it wasn't meant to be.
the problem with macosX is that I couldn't find any way to restore the mbr (well all google answer that I tried only lead to the same result : a beautifull icon with a question mark on it.... ) in fact the macosX install disk has never been thought with in mind that someone could try to install something else than macOSX (like windows the uniq thinking way is that macOSX is the WORLD) so in fact when you destroy the mbr, the only way to have it restaured is to destroy the partition and reinstall everything... (unlike windows where you can use linux to retore the mbr...)
this was just a suggestion for making the installer more user friendly, and more, more safe (I wouldn't like to hold a gun without safety and shoot me in the foot) is to display an additional screen like the partition installation menu, for bootloader installation location selection :popcorn:

something like :
if install elsewhere is selected then an advanced selection screen will be displayed for advanced users

No problem. I just want your machine working.

---

### Post by jeanlucmalet on 2009-08-10
using my new knowledge I tried to re-install ubuntu on a USBdrive,
sadely I discovered something really annoying : 
# fdisk -l  /dev/sdb

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 16.0 GB, 16070475776 bytes
255 heads, 63 sectors/track, 1953 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1954    15693823+  ee  GPT


looking what GPT is, I found on wikipedia that GPT partion table aren't bootable by BIOS.... but it seems that GPT is backward compatible with mbr... maybe 
/dev/sdb1               1        1954    15693823+  ee  GPT
shall be
/dev/sdb1    *           1        1954    15693823+  ee  GPT
(ie marked active?)

as well I'm not sure but is it possible to boot such drive using a PC or a MAC?

in any case, I can install ubuntu on the usbkey, with grub on first sector of partion, but still can't boot on it....

---

### Post by presence1960 on 2009-08-10
> **jeanlucmalet said:**
> using my new knowledge I tried to re-install ubuntu on a USBdrive,
sadely I discovered something really annoying : 
# fdisk -l  /dev/sdb

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 16.0 GB, 16070475776 bytes
255 heads, 63 sectors/track, 1953 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1954    15693823+  ee  GPT


looking what GPT is, I found on wikipedia that GPT partion table aren't bootable by BIOS.... but it seems that GPT is backward compatible with mbr... maybe 
/dev/sdb1               1        1954    15693823+  ee  GPT
shall be
/dev/sdb1    *           1        1954    15693823+  ee  GPT
(ie marked active?)

as well I'm not sure but is it possible to boot such drive using a PC or a MAC?

in any case, I can install ubuntu on the usbkey, with grub on first sector of partion, but still can't boot on it....

You have to format the usb to a filesystem such as ext 3 or ext 4 to install ubuntu on there and have it boot. if you are making a bootable USB in place of the live CD use [unetbootin]("http://unetbootin.sourceforge.net") after formatting the USB as FAT 32.

---

### Post by jeanlucmalet on 2009-08-12
> **presence1960 said:**
> You have to format the usb to a filesystem such as ext 3 or ext 4 to install ubuntu on there and have it boot. if you are making a bootable USB in place of the live CD use [unetbootin]("http://unetbootin.sourceforge.net") after formatting the USB as FAT 32.

thanks for the hint... however it seems that grub, unlike lilo, don't boot on usbdrive... :(
I've tried several things like :
- create a regular PC partition table
- make the GID partition bootable
- install grub on usb drive mbr
- install grub on usb drive partion

all time the system is installed on an ext4 FS....
nothing happens, nor on Macbook or Dell laptop....

by the past I successfully booted such devices using lilo... it was amazingly easy, just have to use /dev/disk/by-uuid/* entries.... 

I prefer not to use unetbootin, because it rely on livecd mecanism
anyway some day ubuntu will have to support usb install...
that's amazing that you can install XP  on a usb drive (allthough it awfully slow) and that you can't do the same on ubuntu (other distro that use lilo can do it)
I'm not used to grub... but such limitation will not make me more grub friendly

---

### Post by presence1960 on 2009-08-12
> **jeanlucmalet said:**
> thanks for the hint... however it seems that grub, unlike lilo, don't boot on usbdrive... :(
I've tried several things like :
- create a regular PC partition table
- make the GID partition bootable
- install grub on usb drive mbr
- install grub on usb drive partion

all time the system is installed on an ext4 FS....
nothing happens, nor on Macbook or Dell laptop....

by the past I successfully booted such devices using lilo... it was amazingly easy, just have to use /dev/disk/by-uuid/* entries.... 

I prefer not to use unetbootin, because it rely on livecd mecanism
anyway some day ubuntu will have to support usb install...
that's amazing that you can install XP  on a usb drive (allthough it awfully slow) and that you can't do the same on ubuntu (other distro that use lilo can do it)
I'm not used to grub... but such limitation will not make me more grub friendly

You must have something wrong because GRUB does boot on a USB drive. many Ubuntu users have their Ubuntu install on a USB drive. Don't take my word for it, search these forums.

---

### Post by presence1960 on 2009-08-13
read this: [http://en.wikipedia.org/wiki/GNU_GRUB](http://en.wikipedia.org/wiki/GNU_GRUB)

more specifically :

Installation

A key feature of GRUB is that it can be installed without being attached to an operating system; however, it needs a copy of a Linux image for such an installation. Working as a stand alone system it is virtually a mini system in its own right and able to boot all the installed major operating systems by chain loading, as described above.

Unlike LILO, there is no need to reinstall GRUB to the MBR or a partition after a change to the configuration file.

In Linux, the "grub-install" command is used to install stage1 to either the MBR or a partition. GRUB's configuration file, stage2 (usually), and other files must be in a usable partition. If these files or the partition become unavailable, stage1 will drop the user to the command line interface.

The name and disk location of the GRUB configuration file varies from system to system; for example, in Debian GNU/Linux and openSUSE the file is stored in /boot/grub/menu.lst while Fedora and Gentoo Linux uses /boot/grub/grub.conf. Fedora also provides a symbolic link from /etc/grub.conf to /boot/grub/grub.conf for FHS compatibility reasons.

**Instead of being installed on the system's hard disk, GRUB can be installed on removable media such as an optical drive (bios access, and el-torito), floppy disk or USB flash drive in order to bring up a system which may not have or cannot boot from its own disk.**

---

### Post by jeanlucmalet on 2009-08-14
well... I'll only say that theory is theory, I'm one of the people that believe only what they see....
I've to test more with grub but at this time writing nothing happens... install after install.... on pc or mac... with mbr based partition or GUID partition... when booting on usb there is only a black screen, no activity on the card reader... 
however, unetbootin works on pc at least, the lilo based usb boot of the sorecerer box I use is working on pc at least.... the only one that I can't make work is ubuntu with grub.... I performed grub-install by hand... according to what is said on wikipedia I shall at least have a prompt... :confused:

---

### Post by jeanlucmalet on 2009-08-14
I've not tested [http://ubuntuforums.org/showthread.php?t=1065670&highlight=usb+boot](http://ubuntuforums.org/showthread.php?t=1065670&highlight=usb+boot) yet

---

### Post by presence1960 on 2009-08-14
> **jeanlucmalet said:**
> well... I'll only say that theory is theory, I'm one of the people that believe only what they see....
I've to test more with grub but at this time writing nothing happens... install after install.... on pc or mac... with mbr based partition or GUID partition... when booting on usb there is only a black screen, no activity on the card reader... 
however, unetbootin works on pc at least, the lilo based usb boot of the sorecerer box I use is working on pc at least.... the only one that I can't make work is ubuntu with grub.... I performed grub-install by hand... according to what is said on wikipedia I shall at least have a prompt... :confused:
 sorry but that is no theory. Either you are doing something incorrectly or you have a hardware/software issue. Just because you can't seem to get it to work does not mean it isn't able to be done. Well let me rephrase, for you it is theory. But the fact remains that GRUB will boot off an USB drive, ask the many on here who are doing it. Why don't you do a search of the forum, maybe you can find how others have done it.

---

### Post by presence1960 on 2009-08-14
> **jeanlucmalet said:**
> I've not tested [http://ubuntuforums.org/showthread.php?t=1065670&highlight=usb+boot](http://ubuntuforums.org/showthread.php?t=1065670&highlight=usb+boot) yet

That is how you should install it, what have you been doing if you weren't doing this? That's probably why it isn't working for you.

---

### Post by mostafa178 on 2009-08-14
When you boot you get an icon with a question mark on it?
I might be able to help here because I seemed to have the same problem with my MacBook.

I can't remember exactly how I did it but here's what I do remember:

1. Boot from the OS X install disc and hold "C" while booting so you can boot in to the DVD.
2. Open terminal
3. Run fdisk
4. If you read the output, you'll see many commands. What I did was type in "fdisk -i" which initializes the disk with a new MBR

I can't remember anything past that. BUT if you to plan on doing this, do it with caution as I can't 100% remember it, and I'm not going to go through that experience again, it almost gave me a heart attack :P

---

### Post by lamontg on 2009-09-03
I found this thread after using bootcamp to install Ubuntu onto a bootcamp "windows" partition and nuked the Mac MBR.  In this case Ubuntu is running on sda3:

> 
lamont@trimix:~$ df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3            104827064   2227544  97274568   3% /
People who have done the "guided install" first option which resizes sda3 will probably have / mounted on /dev/sda4.

For me, with Ubuntu on /dev/sda3 on my Mac, I believe I need to do this:

> 
                             1. Boot your computer up with Ubuntu CD with USB drive plugged in.
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,2)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0,2)", to install GRUB to MBR of sdb
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
This is subtley different in step #6 in that I install onto the partition (hd0,2) which is grub-speak for /dev/sda3 instead of doing "setup (hd0)" which installs on the MBR on /dev/sda.  For people who have installed ubuntu on /dev/sda4 then you would probably do (hd0,3) in both steps #5 and #6 -- in any case you should use the results of step #4 in steps #5 and #6.

That should have given me the grub bootloader in my ubuntu partition in addition to the MBR, but now I need to head in to work to get the Mac install disks in order to try to replace the MBR with the Mac one.  I believe this should work though.

For the instructions in this thread, I believe you need to determine if grub thinks the USB key is (hd0) or (hd1) and do "setup (hdX)" in order to install on the MBR of the USB key -- if you get it wrong you'll simply install grub onto the MBR of the laptop drive again.

(And I've been using Unix since 1989, been doing IT since 1987, been doing Unix SA work since 1995 and from 2001-2006 I was a senior unix SA at Amazon.com and managed 30,000 linux servers and I still made this mistake....   oops...  ENOCAFFIENE...  mental note not to mess around with bootloaders before noon...).

---

### Post by lamontg on 2009-09-03
> **mostafa178 said:**
> When you boot you get an icon with a question mark on it?
I might be able to help here because I seemed to have the same problem with my MacBook.

I can't remember exactly how I did it but here's what I do remember:

1. Boot from the OS X install disc and hold "C" while booting so you can boot in to the DVD.
2. Open terminal
3. Run fdisk
4. If you read the output, you'll see many commands. What I did was type in "fdisk -i" which initializes the disk with a new MBR

I can't remember anything past that. BUT if you to plan on doing this, do it with caution as I can't 100% remember it, and I'm not going to go through that experience again, it almost gave me a heart attack :P

uhm, i think you want fdisk -u and not fdisk -i

---

