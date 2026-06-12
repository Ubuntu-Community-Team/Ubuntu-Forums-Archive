---
title: "Another total newbie."
date: 2009-06-26
forum: Installation &amp; Upgrades
---

### Post by thefunks on 2009-06-26
Okay, so I have two problems. 

1. Upgrades on Desktop - I burned the ubuntu iso to disk yesterday and installed it on my desktop, which had no problems until I upgraded it with the suggested updates it had found. Then upon restarting ubuntu failed to boot and after it fails it gives me options of the version to use. The old one still works fine, but the updated one won't boot, even in recovery mode.

2. Initial Installation on Laptop - I tried installing ubuntu on my acer laptop from the same cd and sometimes it completes the installation, reboots and then goes through the checking of the installation and then gets stuck at 0% on "Installing System" (which comes after the "Checking Installation" goes all the way through to 128%). I am always forced to shut the computer down to get it off that screen, (it was stuck there at 0% for 7 and a half hours overnight). I always have to uninstall ubuntu from inside of windows in order to try the installation again. Sometimes it gets stuck at the same place, other times it gets stuck before the apparently successful installation and reboot on what it calls "Creating Virtual Discs."

Thanks much to anyone who can help me out.

---

### Post by raymondh on 2009-06-26
Hello thefunks,

_DESKTOP_

Can you download the bootinfoscript

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Then in terminal, type

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a results.txt file (saved to your desktop) which you can post back.  Remember to highlight and wrap the file in codes (#) to make reading easier.  The bootinfoscript will give you/us a clearer picture of your desktop set-up.

Also, what are the ERRORS?


_LAPTOP_

kindly explain

*I always have to uninstall ubuntu from **inside of windows** in order to try the installation again*

Is this a WUBI install or are you using windows to delete the partition, etc?

A little reference link for browsing

[http://www.linux-on-laptops.com/acer.html](http://www.linux-on-laptops.com/acer.html)

I am assuming that you have checked the integrity and hash of the install disc.

---

### Post by TravisEvans on 2009-06-26
Hi I am extremely new to this and am looking for help.
Yes I do have an ATI graphics card its a radeon something with 256 ram and 256 bit
anyway I'm trying to do this Mythbox setup and I can't get anywhere, all i get is a black screen with an outlined Grey beveled rectangle and thats it. If i hit a lot on the arrow keys i then get a different outline and i can move a box up and down to make a choice. But i see no text at all with anything. so if i hit escape and then chose the lower option i finally get the desktop. I get the same thing when i try to configure it like i need to. and I tried disabling all the theams to see if some odd default would work but no luck. here is a log file that i was able to make, again i just want to record tv with this computer and then watch it here and there. I have it coming in from an intenna and I know it all went to digital but with this same cord i can plug it into a tv in my room and watch tv just fine, an old crt tv, the antenna is really really big on top of our house and i live in the city so...

here can anybody just help me i don't even know how to create a new thread in this thing or a post. I have never used forms really ever.
I'm 19 I've been puttzing with computers for a long time and i have built six for firends and family.

man this is odd I hope that error log made it on here as an attachment.

Ok well I hope i can get help here and there I am just gonna post this everywhere and hope i can get some help set up.

Travis Evans

and my error log text is too big so...

It says to put this link somewhere?
[http://mythbuntu.pastebin.com/f3633a24](http://mythbuntu.pastebin.com/f3633a24)
Yeah this link works it show you my comp set up if you can read all that code!

---

### Post by thefunks on 2009-06-26
Thanks for the reply. 

For the laptop, yes I was talking about a wubi install. The reason I'm upgrading to ubuntu in the first place is because windows and other viruses have screwed up my computer in various ways, and I've screwed it up also by handling them improperly. I'm on the verge of bringing it to somebody to look at. At the present moment I'm not even able to get the wubi install to run in windows. This is probably more a problem with the laptop than the ubuntu disc. I haven't checked the integrity and hash of the install disc but I did use it to install ubuntu successfully on my desktop. I did use a high write speed (way higher than 4x) when burning the iso to disc. How do I check the integrity and hash of the install disc?

Desktop: 

Unfortunately I wasn't able to understand what was meant by this sentence: "Remember to highlight and wrap the file in codes (#) to make reading easier." So reading probably won't be easier. Sorry. I'm very new like I said. But here's what I came up with in the hard to read version:

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /boot.ini /ntldr 
                       /NTDETECT.COM /wubildr.mbr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x33b633b5

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   160,071,659   160,071,597   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: UUID="eda31ff5-f486-4e03-b8fe-cbd367127c1a" TYPE="ext3" 
/dev/sda1: UUID="01C6A31BCC31D460" LABEL="Hard Drive" TYPE="ntfs" 

=============================== "mount" output: ===============================

/host/ubuntu/disks/root.disk on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
/dev/sda1 on /host type fuseblk (rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
/host/ubuntu/disks/boot on /boot type none (rw,bind)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/thefunks/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=thefunks)


==================== sda1/ubuntu/disks/boot/grub/menu.lst: ====================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=01C6A31BCC31D460 loop=/ubuntu/disks/root.disk ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-13-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=01C6A31BCC31D460 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=01C6A31BCC31D460 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=01C6A31BCC31D460 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=01C6A31BCC31D460 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
root        ()/ubuntu/disks
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
chainloader    +1


======================== sda1/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
    find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
    configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
    fallback 2
    find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
    configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
    fallback 3
    find --set-root --ignore-floppies /menu.lst
    configfile /menu.lst

title find /boot/grub/menu.lst
    fallback 4
    find --set-root --ignore-floppies /boot/grub/menu.lst
    configfile /boot/grub/menu.lst

title find /grub/menu.lst
    fallback 5
    find --set-root --ignore-floppies /grub/menu.lst
    configfile /grub/menu.lst

title commandline
    commandline

title reboot
    reboot

title halt
    halt

================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 

================================== sda1Wubi: ==================================

Operating System: "Ubuntu 9.04"

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  11.4GB: ubuntu/disks/boot/grub/menu.lst
  15.1GB: ubuntu/disks/boot/initrd.img-2.6.28-11-generic
  15.5GB: ubuntu/disks/boot/initrd.img-2.6.28-13-generic
  11.2GB: ubuntu/disks/boot/vmlinuz-2.6.28-11-generic
    .0GB: ubuntu/disks/boot/vmlinuz-2.6.28-13-generic

---

### Post by Bucky Ball on 2009-06-26
Is your laptop a 64bit and the desktop 32bit by any chance? You will require the appropriate ISO if so.

---

### Post by thefunks on 2009-06-26
I think that's correct (desktop 32bit, laptop 64bit) but my iso is for 32bit which should be universally compatible, right?

---

### Post by Bucky Ball on 2009-06-26
*** thefunks: I would definitely try the 64bit on the laptop and see if that makes a difference.
*** Travis: 

> **TravisEvans said:**
> Hi I am extremely new to this and am looking for help.

Hi Travis and welcome. You should keep reading this thread and post one specific to your own issue using a descriptive title and as much helpful info you can think of about the hardware/problem/Ubuntu you are using.

> **TravisEvans said:**
> i don't even know how to create a new thread in this thing or a post.

Upper left of the forum screen at this thread, you will see a 'location line':

> **[Ubuntu Forums]("http://ubuntuforums.org/index.php")**      > [The Ubuntu Forum Community]("http://ubuntuforums.org/forumdisplay.php?f=130")       >[Main Support Categories]("http://ubuntuforums.org/forumdisplay.php?f=327")       > [Installation & Upgrades]("http://ubuntuforums.org/forumdisplay.php?f=333")       > [[ubuntu] Another total newbie.]("http://ubuntuforums.org/showthread.php?p=7521238#post7521238")Click on the part I have in bold, choose the appropriate forum for your issue, click on that and in a big box to the top left of the screen you will see, 'New Thread'.

Get into it.

---

### Post by thefunks on 2009-06-26
Okay so I restored my system on my laptop to where it was about two weeks ago before it got a nasty virus and I'm having less trouble with it now; in windows anyway.

The laptop is an Acer Travelmate 4500. I can't seem to find out for certain whether its 32 bit or 64 bit but I am assuming that since I can't find reference to a distinction that it is 32 bit.

Using the same CD as before, my system simply will not open the wubi.exe file. I've reburned it at a slower pace at around 4X and also tried to mount the iso to its own drive using winmount and then loading it from there, but it also does not load from there. So I know it's not the CD writing since in the second instance I wasn't even using a CD but instead a virtual drive.


Right now I'm attempting to download the 32 bit version of 8.04 instead of 9.04, and hopefully that will make some difference.

---

### Post by thefunks on 2009-06-26
Alright so that worked (by the way, the requirements on the ubuntu download page are not totally accurate, you don't actually need to burn a cd; just download winmount for free and you can mount the iso file as if it were being read by a disc drive - for those who don't have disc-writing capabilities). So the 32bit version of 8.04 worked on my laptop while 9.04 did not.

---

### Post by raymondh on 2009-06-26
Catching up on this thread ...

Glad you have the laptop going =D>

Now to the desktop ...

Do you remember the errors when you try to boot into the new kernel 2.6.28-13?  

Kindly share how you installed ubuntu and the steps you took to upgrade to the new kernel.

I am seeing WUBI on sda1...

---

### Post by thefunks on 2009-06-27
Desktop:

The error when trying to boot into the new kernel is: 

Error 13: Invalid or unsupported executable format

The steps I took to install and upgrade were:

1. Downloaded ISO from ubuntu.com 32bit version 9.04
2. Burn ISO to CD-rom
3. Boot computer in windows xp
4. Insert CD-Rom and Select the second option - install from within windows
5. Computer restarts, installation occurs following instructions on screen
6. System reboots, User chooses to boot in ubuntu at option prompt
7. Ubuntu works great, User starts firefox and surfs web which is apparently automatically connected
8. User notices a window behind firefox on the upper left hand corner of the desktop, it's a long list of updates presumably just retrieved from the web, so user selects the download updates or install updates button, whichever it was.
9. Updates install, system reboot, User chooses to boot in ubuntu at option prompt, Error 13: Unidentified or unsupported executable format

Laptop:

My laptop connects to the internet via wireless networks using an internal wireless card, but currently I am having no luck getting the wireless card to work. It's only drivers are windows drivers, which end in .sys and not .inf. ubuntu apparently is able to identify the hardware as a wireless card, but I can't figure out where to get the linux drivers if there are any. I've seen this discussed a bunch elsewhere and so I'm going to go peruse all that before I get too much more into detail about it here.

Thanks a bunch for all the help!

---

### Post by Bucky Ball on 2009-06-27
Plug an ethenet cable into the laptop and boot up. Get online that way and you will probably get the drivers for wireless card and the wireless connection setup automatically. (Ubuntu will recognise the card, tell you there are Restricted Third Party drivers available for it and ask you if you would like to use them).

Also, you can type this in a terminal:

```
lspci
```

Somewhere near the bottom in there, you will find the make and model of your wireless card. :)

---

### Post by thefunks on 2009-06-27
Very helpful, thanks. Too tired to try it tonight but I will work on it tomorrow first thing. Really liking the OS so far. Way more user friendly than Windows. Better support too haha

---

### Post by thefunks on 2009-06-27
> **Bucky Ball said:**
> Plug an ethenet cable into the laptop and boot up. Get online that way and you will probably get the drivers for wireless card and the wireless connection setup automatically. (Ubuntu will recognise the card, tell you there are Restricted Third Party drivers available for it and ask you if you would like to use them).

Also, you can type this in a terminal:

```
lspci
```Somewhere near the bottom in there, you will find the make and model of your wireless card. :)

Actually plugging into the router directly does is not working to connect my laptop to the internet. The desktop is connected that way, so it's not the router's problem and I've tried all available ports and they all work with the desktop but not with the laptop. The only option I get when I left click the network manager is Manual Network Configuration. I think my wired network device is disabled because I can't get a wired connection in windows either, though I can get a wireless connection in windows.

Info gathered from the terminal: 

02:02.0 Ethernet controller: Broadcom Corporation BCM 4401 100Base-T (rev 01)
02:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

---

### Post by thefunks on 2009-06-27
Alright, I posted something about the laptop in the wireless section and it ended up taking me quite a while and I have a bunch of new information so I figured I'd post it here as well just in case:

 				 				**Intel PRO/Wireless---Ubuntu 8.04----Acer Travelmate 4500 Laptop** 			
 			 			 		   		 		 		**This post is based on the HOWTO post a Wireless issue (ticket). It's been filled in like a worksheet.**             


**1 ) Machine Brand and Model (PC/Laptop)**: 

Acer Travelmate 4500 Series Model ZL1

**2 ) Wireless Brand, Model and Wireless Chipset:** 

Intel Corporation PRO/Wireless 2200BG Network Connection
[B]
3 ) check interface:[/B]
[B]
Not sure what I'm checking here :

lo no wireless extensions.

eth0 no wireless extensions

eth1 radio off ESSID:" "
Mode: Managed Frequency: 2.462 GHz Access Point: 00:22:3F:84:2C:14
Bit Rate: 0 kb/s Tx-Power=off Sensitivity=8/0 
Retry Limit:7 RTS thr:eek:ff Fragment thr:eek:ff
Power Management:eek:ff
Link Quality:0 SIgnal level:0 Noise Level:0
Rx invalid nwid:0 Rx invalid crypt:1 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

4 ) Check for modules:[/B]

[FONT=monospace]Can't find one for the wireless card.

[/FONT]**5 ) Kernel boot messages**e

eth1: no IPv6 routers present
eth1: link becomes ready
NET: registered protocol family 17
ieee80211_crypt: registered algorithm 'TKIP'
ipw2200: Failed to send RSN_Capabilities: Command timed out.
ipw2200: Failed to send SSID: Command timed out.
eth1: no IPv6 routers present
ipw2200: Failed to send CARD_DISABLE: Command timed out.
ADDRCONF (NETDEV_UP): eth1: link is not ready
ADDRCONF (NETDEV_UP): eth0: link is not ready
ADDRCONF (NETDEV_UP): eth1: link is not ready
ADDRCONF (NETDEV_UP): eth1: link is not ready
ADDRCONF (NETDEV_UP): eth1: link is not ready

**6 ) Network configuration**
*-network:0
description: ethernet interface
product: BCM4401 100Base-T
vendor: Broadcom Corporation
physical id: 2
bus info: pci@0000:02:02.0
logical name: eth0
version: 01
serial: 00:c0:9f:61:70:2d
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clcok: 33MHz
capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s

*-network:1 DISABLED
description: Wireless Interface
product: PRO/Wireless 2200BG Network Connection
vendor: Intel Corporation
physical id: 4
bus info: pci@0000:02:04.0
logical name: eth1
version: 05
serial: 00:0e:35:67:d6:05
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off

**7 ) Scan for networks:**
[FONT=monospace]
lo    Interface doesn't support scanning.
eth0  Interface doesn't support scanning.
eth1  No scan results

[/FONT]**8 ) Ubuntu Version: **

Ubuntu 8.04.2

**9 ) Kernel/architecture (including 32 vs. 64 bit): **

2.6.24-23-generic i686

**10 ) Restarting the network:**

listening on lpf/eth0 several times but never on eth1, which would be the wireless card.

No DHCPOFFERS recieved.
No working leases in persistent database - sleeping.
grep: /etc/resolv.conf: No such file or directory


----------------------------------------------------------------------------------------------------------

So normally in Windows my wireless card works but my wired device does not. It's probably disabled or something and I just don't know how to enable it. The wireless card is definitely disabled in Ubuntu. I try to physically turn it on via the button in front of the laptop, but it does not respond when I am in Ubuntu (though it does in windows - it lights up when it is enabled and glows with a red backlight).

When I visit the network manager in Ubuntu the only option a left click allows is "Manual Network Configuration." From the wireless part of this window it looks like the wireless card is picking up networks around here with various signal strengths but won't connect to them; even though to my knowledge the wireless network card is currently disabled (no glowing backlight like in windows) and it shouldn't be able to detect those networks at all.


Thanks in advance for any help :smile:

---

### Post by raymondh on 2009-06-27
_LAPTOP_

Some members have resorted to using ndiswrapper.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

_DESKTOP_

WUBI install

1.  Defrag c:\ubuntu  just to make sure the kernel and initrd are not fragmented.

2.  You could un-install and re-install the offending/bad Kernel and see if it solves that issue.  To do that, you could access synaptic package manager (system then admin) > status > installed > browse for the offending kernel (linux generic .... ) > mark for removal _ensuring that you have marked the offending kernel_ > apply.  Close synaptic.  To re-install, you can use update manager again. 

My thoughts on remove/re-install revolve around a 'bad download'.  It could also be a md5sum mismatch.

In the meantime, I am glad you have the old kernel to use.  You can set ubuntu to default to the old kernel until you get the newer kernel fixed.  Easiest way is to use startupmanager (which you can install thru synaptic and once done, can access thru system > admin) and set default kernel from there.

Good luck.

---

### Post by Bucky Ball on 2009-06-27
Yea, you need the drivers to get the Broadcom card up. A simple, 'follow your nose' process now, if you are online via ethernet cable!

Can't really help myself, but you might look into why you can't get online with a cable either. That is strange. The cable is plugged in when you switch the machine on?

The other possibility is working out how to get the Broadcom B43 drivers on another machine and transfer them on over and update from the device (cd, usb dongle, whatever). This might get you going:

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

* Update: Don't use ndiswrapper! This is much easier if it works. If it doesn't, then consider it, but this driver is specifically designed and reverse-engineered for the Broadcom cards. :)

You might, *might*, be able to install the drivers from the installation disk you already have (not sure if they are included on there, don't think they are) by running this:

**```
sudo apt-get install b43-fwcutter
```**
[B]
... from this page:

[http://linuxwireless.org/en/users/Drivers/b43#firmware](http://linuxwireless.org/en/users/Drivers/b43#firmware)

[/B]PS: Broadcom cards are a known nightmare which is one of the reasons this driver exists. Having said that, it might not work for your card.

---

### Post by thefunks on 2009-06-27
Yeah, I dunno. that second laptop solution is just way way way over my head. There are so many steps and I don't understand any single one of them so there's just no chance I could do it all right. 

I got the ndiswrapper to work though, thanks for that! Laptop running ubuntu 8.04 without problems and with a wireless connection ~ FINALLY. I was about to give up.

---

### Post by presence1960 on 2009-06-27
From raymondhenson: 2. You could un-install and re-install the offending/bad Kernel and see if it solves that issue. To do that, you could access synaptic package manager (system then admin) > status > installed > browse for the offending kernel (linux generic .... ) > mark for removal ensuring that you have marked the offending kernel > apply. Close synaptic. To re-install, you can use update manager again.

My thoughts on remove/re-install revolve around a 'bad download'. It could also be a md5sum mismatch.

That is a very logical idea to test out. Since your old kernel works it isn't GRUB or your Ubuntu filesystem. if it were neither kernel would boot. I would mark the new kernel for compete removal. This will remove it from cache. if you simply uninstall it the download will still be in your cache and will be used again to reinstall. Mark for complete removal then use update manager to redownload & install. Hopefully it was a corrupted download. it can't hurt to try.

---

