---
title: "How to: Create a Live USB"
date: 2009-06-21
forum: Installation &amp; Upgrades
---

### Post by vegetarianshrimp on 2009-06-21
[COLOR="Indigo"][SIZE="4"]*This guide is outdated. For up-to-date information on creating a Live USB, go to [Install Ubuntu from a USB stick - Community Documentation]("https://help.ubuntu.com/community/Installation/FromUSBStick")*[/SIZE][/COLOR]

[COLOR="Gray"][SIZE=3]If you need to install Ubuntu on a computer without a CD drive (e.g. a netbook) or you want your OS on a USB drive so you can take it anywhere, then you want to create a [Live USB]("http://en.wikipedia.org/wiki/Live_USB"):[/SIZE]

**PLEASE READ ALL INSTRUCTIONS CAREFULLY BEFORE DOING _ANYTHING_**
[B][SIZE=3][COLOR=Orange]
Method 1: Linux[/COLOR] UNetbootin[/SIZE]

[/B] 1. Insert your** [COLOR=Blue]_[USB flash drive]("http://en.wikipedia.org/wiki/USB_flash_drive")_[/COLOR]** (1GB should be enough, although less may work too, I just haven't tested it with less)

2. Go to Applications>**Add/Remove** 

3. Search for **UNetbootin**. If it is there **Install** it, if not, try Method 3.

4. Open UNetbootin (Applications>System Tools>UNetbootin)

5. In the UNetbootin window, there will be a drop-down menu "==Select Distribution=="
Select **Ubuntu**

6. There will also be one called "==Select Version=="
Select **9.04_Live** for the latest version of Ubuntu: 9.04 Intrepid Ibex, or **8.04_Live **for 8.04 Hardy Heron LTS (Long Term Support)

7. In the bottom left corner of the window, there will be another drop down menu. It will either say "Hard Disk" or "USB Drive". You want it to say **USB Drive**

8. Click **OK**

12. Wait for everything to finish. While you are waiting, **DO NOT CLOSE UNETBOOTIN WINDOW, OR UNPLUG YOUR USB DRIVE**

14. On the same or different computer, plug in your USB Drive, and restart. Right at the beginning of the boot, press F12 (may be different) repeatedly, select USB Drive with the arrown keys and spacebar, and Ubuntu will boot from USB drive.[B][SIZE=3][COLOR=Orange]


Method 2: Windows[/COLOR] UNetbootin

[/SIZE] [/B] 1. Insert your** [COLOR=Blue]_[USB flash drive]("http://en.wikipedia.org/wiki/USB_flash_drive")_[/COLOR]** (1GB should be enough, although less may work too, I just haven't tested it with less)

2. Go to [COLOR=Blue]_**[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)**_[/COLOR]

3. Click on **Download (for Windows)**

4. Install the .exe

5. Open Unetbootin.

6. In the UNetbootin window, there will be a drop-down menu "==Select Distribution=="
Select **Ubuntu**

7. There will also be one called "==Select Version=="
Select **9.04_Live** for the latest version of Ubuntu: 9.04 Intrepid Ibex, or **8.04_Live **for 8.04 Hardy Heron LTS (Long Term Support)

8. In the bottom left corner of the window, there will be another drop down menu. It will either say "Hard Disk" or "USB Drive". You want it to say **USB Drive**

9. Click **OK**

10. Wait for everything to finish. While you are waiting, **DO NOT CLOSE THE UNETBOOTIN WINDOW OR UNPLUG YOUR USB DRIVE**

11. On the same ordifferent computer, plug in your USB Drive, and restart. Right at the beginning of the boot, press F12 (may be different) repeatedly, select USB Drive with the arrown keys and spacebar, and Ubuntu will boot from USB drive.



**[SIZE=3][COLOR=Orange]Method 3: Linux[/COLOR] UNR image (.img)[/SIZE]**
[B]
Note: [/B]This only works with [Ubuntu Netbook Remix]("http://www.canonical.com/projects/ubuntu/unr") (UNR) 9.04**, **not the Desktop Edition, and not 8.04 LTS. No worries though, you can get a regular desktop in UNR.

1. Insert your** [COLOR=Blue]_[USB flash drive]("http://en.wikipedia.org/wiki/USB_flash_drive")_[/COLOR]** (1GB should be enough, although less may work too, I just haven't tested it with less)

2. Download the Ubuntu Netbook Remix image [here]("http://releases.ubuntu.com/9.04/ubuntu-9.04-netbook-remix-i386.img"). **Save** to **Desktop**

3. Download USB Imagewriter [here]("http://packages.ubuntu.com/jaunty/all/usb-imagewriter/download"). 

4. **Open** with GDebi Package installer. 

5. Click **Instal**l.

6. When it is installed, press **Alt-F2**, type in "imagewriter", and press enter.

7. In ImageWriter, select the UNR image that's on the Desktop for "Write Image:" and select your plugged-in USB drive in "to:".

8. Click **Write to Device**.

9. Wait for everything to finish. While you are waiting, [B]DO NOT CLOSE THE IMAGEWRITER WINDOW, OR UNPLUG YOUR USB DRIVE

[/B]10. On the same or different computer, plug in your USB Drive, and restart. Right at the beginning of the boot, press F12 (may be different) repeatedly, select USB Drive with the arrow keys and spacebar, and Ubuntu will boot from USB drive.

[SIZE=3]That's all the methods I know of. If you have any more, please post! 

Thanks,
-vegetarianshrimp
[/SIZE][/COLOR]

---

### Post by presence1960 on 2009-06-21
[COLOR="Red"]Method 4[/COLOR]

[COLOR="Black"]From Ubuntu 9.04- Go System > Administration > USB Startup Disk Creator. Really simple just follow the prompts.[/COLOR]

---

### Post by vegetarianshrimp on 2009-06-21
> **presence1960 said:**
> [COLOR=Red]Method 4[/COLOR]

[COLOR=Black]From Ubuntu 9.04- Go System > Administration > USB Startup Disk Creator. Really simple just follow the prompts.[/COLOR]
Oh yeah, I forgot about that! :) thanks

---

### Post by Mighty_Joe on 2009-06-22
[Install Ubuntu from a USB stick - Community Documentation ]("https://help.ubuntu.com/community/Installation/FromUSBStick") contains valuable troubleshooting information.
[LiveUsbPendrivePersistent]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent")includes instructions to make a USB Live CD install persistent (so one can save settings and files).
My preference is to install Ubuntu to the flash drive.  It's faster than the Live CD, though it takes more disk space(2Gb+ compared to ~700).  I used these [install instuctions]("http://beastie.cs.ua.edu/cs150/usb-install.html") and [configuration instructions]("http://beastie.cs.ua.edu/cs150/configuration.html") (the configuration includes steps to improve performance and hopefully prevent flash memory wear and tear).

---

### Post by vegetarianshrimp on 2009-06-22
> **Mighty_Joe said:**
> [Install Ubuntu from a USB stick - Community Documentation ]("https://help.ubuntu.com/community/Installation/FromUSBStick") contains valuable troubleshooting information.
[LiveUsbPendrivePersistent]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent")includes instructions to make a USB Live CD install persistent (so one can save settings and files).
My preference is to install Ubuntu to the flash drive.  It's faster than the Live CD, though it takes more disk space(2Gb+ compared to ~700).  I used these [install instuctions]("beastie.cs.ua.edu/cs150/") and [configuration instructions]("http://beastie.cs.ua.edu/cs150/configuration.html") (the configuration includes steps to improve performance and hopefully prevent flash memory wear and tear).
Thanks!

---

### Post by Alxl on 2009-06-28
I am an average computer user trying to use Linux for the first time (using Windows now).

 No problem downloading Ubuntu to a USB stick (using Method 2: Windows Unetbootin above). But when I try to reboot from the stick I get this error:
SYSLINUX 3.72 2008-09-25 EBIOS  ...
Unknown keyword in configuration file: MD5SUM
Could not find kernel image:  linux  

I followed all specified steps in Method 2 except for   ‘4. Install the .exe’ since don’t know how to do this (unetbootin-windows-356.exe is on desktop and I ran it and it downloaded and installed Ubuntu on the USB stick).

I also tried  ‘Method 3: Linux UNR image (.img)’ but could’t do ‘4. Open with GDebi Package installer’  since it says : “Sorry but your system is not (yet) supported...’ when I try to download GDebi Package.

Any help appreciated

---

### Post by vegetarianshrimp on 2009-06-28
> **Alxl said:**
> I am an average computer user trying to use Linux for the first time (using Windows now).

 No problem downloading Ubuntu to a USB stick (using Method 2: Windows Unetbootin above). But when I try to reboot from the stick I get this error:
SYSLINUX 3.72 2008-09-25 EBIOS  ...
Unknown keyword in configuration file: MD5SUM
Could not find kernel image:  linux  

I followed all specified steps in Method 2 except for   ‘4. Install the .exe’ since don’t know how to do this (unetbootin-windows-356.exe is on desktop and I ran it and it downloaded and installed Ubuntu on the USB stick).

I also tried  ‘Method 3: Linux UNR image (.img)’ but could’t do ‘4. Open with GDebi Package installer’  since it says : “Sorry but your system is not (yet) supported...’ when I try to download GDebi Package.

Any help appreciated
Hmm...I don't know what the problem is with the LiveUSB, but but if your computer has a CD dirve, you can try using a LiveCD instead of a LiveUSB to try out and install Ubuntu.
You can request a free Ubuntu CD from Canonical [here]("https://shipit.ubuntu.com/"), or you can buy one [here]("http://www.ubuntu.com/GetUbuntu/purchase").
You can also download the .iso and burn it to your own CD [here]("http://www.ubuntu.com/getubuntu/download").

Alternatavely, if your computer does not have a CD drive or if you find this easier, you can try [Wubi]("http://wubi-installer.org/"). It installs Ubuntu as a program in Windows. You can boot Ubuntu or Windows at startsup, and if you don't like Ubuntu, you can remove it in Windows just by removing [Wubi]("http://wubi-installer.org/").

---

### Post by Alxl on 2009-06-28
Thanks. 
I did some reading and it appears that there is a problem  with the syslinux.cfg file. Some additional info about this problem :

 [http://syslinux.zytor.com/wiki/index.php/SYSLINUX](http://syslinux.zytor.com/wiki/index.php/SYSLINUX)

[http://www.pendrivelinux.com/error-could-not-find-kernel-image-linux/](http://www.pendrivelinux.com/error-could-not-find-kernel-image-linux/) 
  
I have the syslinux.cfg  file in the USB but cannot open it to see its content. It is only 432 bytes! . 

If I cannot put it on a USB, I’ll try your suggestions. Computer has a CD drive bu my small laptop does not.  And then I'll have to see if I can transfer the info from the CD to the stick

---

### Post by vegetarianshrimp on 2009-07-01
> **Alxl said:**
> Thanks. 
I did some reading and it appears that there is a problem  with the syslinux.cfg file. Some additional info about this problem :

 [http://syslinux.zytor.com/wiki/index.php/SYSLINUX](http://syslinux.zytor.com/wiki/index.php/SYSLINUX)

[http://www.pendrivelinux.com/error-could-not-find-kernel-image-linux/](http://www.pendrivelinux.com/error-could-not-find-kernel-image-linux/) 
  
I have the syslinux.cfg  file in the USB but cannot open it to see its content. It is only 432 bytes! . 

If I cannot put it on a USB, I&#8217;ll try your suggestions. Computer has a CD drive bu my small laptop does not.  And then I'll have to see if I can transfer the info from the CD to the stick
Hope it all works out! Post here if you have any questions.

---

### Post by Alxl on 2009-07-19
Hi,
it's been awhile.
I looked around and decided to download and install a program called 'Portable Ubuntu Remix' .  It is relatively new and apparently not well known.

The program is installed in Windows and one can get to Ubuntu without having to reboot.
For the time being this is what I need. It comes with Hardy but most likely can also be upgraded - 

And it is a free program listed on SourceForge  ( [http://sourceforge.net/](http://sourceforge.net/) )

---

### Post by vegetarianshrimp on 2009-07-19
> **Alxl said:**
> Hi,
it's been awhile.
I looked around and decided to download and install a program called 'Portable Ubuntu Remix' .  It is relatively new and apparently not well known.

The program is installed in Windows and one can get to Ubuntu without having to reboot.
For the time being this is what I need. It comes with Hardy but most likely can also be upgraded - 

And it is a free program listed on SourceForge  ( [http://sourceforge.net/](http://sourceforge.net/) )
Glad you found what you need!

---

### Post by stlsaint on 2009-07-19
question vegshrimp....so im running ubuntu ultimate 2.2...wihtout going thru and testing myslef do you know if the startup disk method from inside ubuntu will make me a ubuntu ultimate bootable usb or will it make a jaunty 9.04 disk thats not ultimate? just asking as i am on my windows partition now and havent gotten to test this methog within my ubuntu partition yet!?!? WHAT AM I STILL DOING ON WINDWOS!?!?!? i know.....

---

### Post by vegetarianshrimp on 2009-07-19
Hmm. I don't know, because I don't use Ubuntu Ultimate, and I don't know how the Live USB Creator works. My suggestion, you download the Ultimate ISO, and instead of using it with the Live USB creator, download UNetbootin, choose the ISO option instead of the "distro from a list" option: [http://unetbootin.sourceforge.net/#other](http://unetbootin.sourceforge.net/#other)

---

### Post by stlsaint on 2009-07-19
yea i have the iso and ultimate is based off jaunty 9.04 so maybe...but thanks i will try your method...also with it being ultimate you think 2gbs will be enough?!?!? my iso is 1.98 so pushing it but.......

---

### Post by vegetarianshrimp on 2009-07-19
> **stlsaint said:**
> yea i have the iso and ultimate is based off jaunty 9.04 so maybe...but thanks i will try your method...also with it being ultimate you think 2gbs will be enough?!?!? my iso is 1.98 so pushing it but.......
I don't think  it will be enough. One, I think (not know), that the ISO is more compressed than what actually turns into the LiveUSB. Two, USB Drive companys tend to cheat a little. My memorex 2GB USB drive is actually 1.8GB. Try, but if it doesn't work, get a bigger USB drive, or install regular Ubuntu, install the Ubuntu Ultimate packages, and then change your repositories to Ubuntu Ultimate's.

---

### Post by max11 on 2009-07-20
thank for posting this ... very helpful

---

### Post by vegetarianshrimp on 2009-07-20
> **max11 said:**
> thank for posting this ... very helpful
No Problem!

---

### Post by pakki on 2009-07-20
Hey there this is my 1st psot at this forum.
I am a totally newbee but thing is that I downloaded 'Live USB Creator' application you just browse the ubuntu image & the process begins & you get urself a totally bootable linux of any distribution.
Now the problem is that being a live session user you can't make the USB remember what changes you had made. I mean after a reboot you need to reinstall each application & whatsoever. 
Now came across 'U904p' application which has some kindoff casper-rw 1gb partition in which the developers claim that you can save changes to ubuntu even in live session. However I wasn't being able to boot my USb through this application ( which I need a solution for), it gives me some I/O error after ubuntu 9.04 slider vanishes!!
So plz tell me how can I make a Persistent ubuntu via USB!!

Thnx in advance

---

### Post by macintard on 2009-07-20
Has ANYONE ever made a persistent liveusb Ubuntu install with unetbootin? Right now I'm running Fedora 11 and run into the same problem as with Ubuntu, there is no persistence whatsoever. Ubuntu seems easiest to create the persistence with a single casper-rw file so I want to try that. 

I can run Unetbootin from Windows too with wine but also can with a binary linux version. Either way works. BTW, can that windows install of u904.exe work in DOSBOX? It had issues in WINE, apparantly some kind of error making the flash drive bootable. Thanks!

PS How do you know you have persistence? Would it show 4GB free space or is your stuff simply there the next time you reboot?

---

### Post by vegetarianshrimp on 2009-07-20
@pakki and macintard

The one time I was able to have a regular (non Live) linux installation on a USB drive, I had 2 USB drives. One Live, one empty.  I installed it on the empty one using the install from the Live. I did this with Linux Mint, and there were some things that got messed up. I don't know whether it will work with Ubuntu.

---

### Post by macintard on 2009-07-20
> **vegetarianshrimp said:**
> @pakki and macintard

The one time I was able to have a regular (non Live) linux installation on a USB drive, I had 2 USB drives. One Live, one empty.  I installed it on the empty one using the install from the Live. I did this with Linux Mint, and there were some things that got messed up. I don't know whether it will work with Ubuntu.

Oh well, thanks anyhow. I'll keep researching and stuff.

---

### Post by Mighty_Joe on 2009-07-21
> **macintard said:**
> Has ANYONE ever made a persistent liveusb Ubuntu install with unetbootin? 

I don't think unetbootin can create a persistent install.  There is nothing about it in the [documentation]("http://unetbootin.sourceforge.net/")

---

### Post by vegetarianshrimp on 2009-07-21
> **Mighty_Joe said:**
> I don't think unetbootin can create a persistent install.  There is nothing about it in the [documentation]("http://unetbootin.sourceforge.net/")
I don't think it can either.

---

### Post by nemein on 2009-07-24
I just started looking at this (figure moving a USB thumb drive is easier than hauling the USB DVD/CD around ;)) and something occurred to me.  Is it possible to create an "all-in-one" iso selector bootable drive?  What I mean is I'm currently creating a 9.04 32-bit server USB drive as an initial test.  What would be nice is some way of loading all the isos (v8 v. v9, desktop v. server, 32 v. 64) on the same USB drive and then to be able to select which OS I want to boot and/or install.  I suspect this is not possible and I'll end up w/ a few different USB drives, but I figured I'd ask.

TIA

---

### Post by Mighty_Joe on 2009-07-24
> **nemein said:**
> Is it possible to create an "all-in-one" iso selector bootable drive?  

It may be.  [this guy]("http://www.justlinux.com/forum/showthread.php?threadid=150078") claims success.  I've seen others propose the idea on this forum but have not seen anyone follow through.

---

### Post by JohnFH on 2009-07-24
> **nemein said:**
> I just started looking at this (figure moving a USB thumb drive is easier than hauling the USB DVD/CD around ;)) and something occurred to me.  Is it possible to create an "all-in-one" iso selector bootable drive?  What I mean is I'm currently creating a 9.04 32-bit server USB drive as an initial test.  What would be nice is some way of loading all the isos (v8 v. v9, desktop v. server, 32 v. 64) on the same USB drive and then to be able to select which OS I want to boot and/or install.  I suspect this is not possible and I'll end up w/ a few different USB drives, but I figured I'd ask.

TIA

If it's just different versions of Ubuntu you want to select from then that's relatively easy as you only need to deal with grub bootloader, but if you want to select from other distros as well, then that's when it becomes a bit more complicated as you need to support other bootloaders - syslinux, etc.

Grub4Dos (don't be mislead by the name) apparently supports the option to boot directly from any chosen iso bootable image.  I tried it and had some limited success.

---

### Post by vegetarianshrimp on 2009-07-25
I've heard it works, but have now idea how to do it. :)

---

### Post by Mighty_Joe on 2009-07-26
> **JohnFH said:**
> 
Grub4Dos (don't be mislead by the name) apparently supports the option to boot directly from any chosen iso bootable image.  I tried it and had some limited success.

I took a couple of hours to mess with Grub4Dos and couldn't get it to work :confused:

---

### Post by vegetarianshrimp on 2009-07-26
> **Mighty_Joe said:**
> I took a couple of hours to mess with Grub4Dos and couldn't get it to work :confused:
Oh, well.

---

### Post by Mighty_Joe on 2009-07-27
> **Mighty_Joe said:**
> I took a couple of hours to mess with Grub4Dos and couldn't get it to work :confused:

I spent a couple more hours with Grub4Dos and managed to get it to boot the Ubuntu Live CD ISO.  Ii tried Puppy and CrunchBang and could not get them to work.
It turns out the Grub4Dos ISO feature is experimental AND doesn't work with most ISOs:
> The majority of Linux based CD images will also fail to work with Grub4dos ISO emulation. Linux distributions require kernel and initrd files to be specified, as soon as these files are loaded the protected mode kernel driver(s) take control and the virtual CD will no longer be accessible. If any other files are required from the CD/DVD they will be missing, resulting in boot error(s).
[Grub4Dos guide: Booting from .ISO Images]("http://diddy.boot-land.net/grub4dos/files/map.htm#hd32")
There is a list of ISO's that have worked along with the menu.lst entry used [here]("http://www.boot-land.net/forums/index.php?showtopic=5041").

---

### Post by vegetarianshrimp on 2009-07-28
> **Mighty_Joe said:**
> I spent a couple more hours with Grub4Dos and managed to get it to boot the Ubuntu Live CD ISO.  Ii tried Puppy and CrunchBang and could not get them to work.
It turns out the Grub4Dos ISO feature is experimental AND doesn't work with most ISOs:

[Grub4Dos guide: Booting from .ISO Images]("http://diddy.boot-land.net/grub4dos/files/map.htm#hd32")
There is a list of ISO's that have worked along with the menu.lst entry used [here]("http://www.boot-land.net/forums/index.php?showtopic=5041").
Thanks for the info!

---

### Post by macintard on 2009-07-29
I figured something out... You download and install Unetbootin, the Xubuntu, or Kunbuntu, or Ubuntu ISO.. then, you download the .exe install file for that distro off pendrivelinux.com and unarchive it with WINE...go to the folder and look inside the fixit.bat and makeboot.bat and figure out the corresponding commands in linux. Not hard at all. I might write a tutorial tomorrow. Then, you copy whatever casper-rw file you want... 2GB, 3GB or 4GB and copy it to your flash, and then type 7z e 4GB-casper-rw.zip for example and wait forever for that thing to unzip...then when you reboot you might have persistence...worked in Linux Mint. Yeah, was trying everything and figured it out by the time I got to that one... It's based of Ubuntu should it should work with all the other ubuntuish stuff... You might try copying stuff to your hdd off it, then install gparted and destroy the partition on the usb, then create a FAT32, format it FAT32, and then when it is done change the flag to boot...then you're good to go to do what I said previously...best of luck and let me know if it works.

---

### Post by vegetarianshrimp on 2009-07-30
> 
I figured something out... You download and install Unetbootin, the Xubuntu, or Kunbuntu, or Ubuntu ISO.. then, you download the .exe install file for that distro off pendrivelinux.com and unarchive it with WINE...go to the folder and look inside the fixit.bat and makeboot.bat and figure out the corresponding commands in linux. Not hard at all. I might write a tutorial tomorrow. Then, you copy whatever casper-rw file you want... 2GB, 3GB or 4GB and copy it to your flash, and then type 7z e 4GB-casper-rw.zip for example and wait forever for that thing to unzip...then when you reboot you might have persistence...worked in Linux Mint. Yeah, was trying everything and figured it out by the time I got to that one... It's based of Ubuntu should it should work with all the other ubuntuish stuff... You might try copying stuff to your hdd off it, then install gparted and destroy the partition on the usb, then create a FAT32, format it FAT32, and then when it is done change the flag to boot...then you're good to go to do what I said previously...best of luck and let me know if it works.

Thanks! Maybe you should start a new thread?

---

### Post by macintard on 2009-07-30
Ok sure thing. I'll do that. Good idea!

---

### Post by Teh H4rRy on 2009-08-19
When using the windows method for creating a USB live drive with unetbootin, will it remember any changes i make so i can use it from computer to computer without changing keyboard settings, time zone, and other settings?

---

### Post by Mighty_Joe on 2009-08-19
> **Teh H4rRy said:**
> When using the windows method for creating a USB live drive with unetbootin, will it remember any changes i make so i can use it from computer to computer without changing keyboard settings, time zone, and other settings?

To my knowledge, unetbootin does not create a persistent USB install (look on page 2 of this topic), so the answer is "no".

---

### Post by Teh H4rRy on 2009-08-19
> **Mighty_Joe said:**
> To my knowledge, unetbootin does not create a persistent USB install (look on page 2 of this topic), so the answer is "no".

Okay thanks, I am using a Unetbootin-ed drive now, The first drive a made was with the Ubuntu 9.10 wizard, reserving a lot of space for presistance, it didnt work...Ill try again when i am at my desktop PC, using a lil netbook ATM

Any reason why it didnt work?

---

### Post by Mighty_Joe on 2009-08-20
> **Teh H4rRy said:**
> 
Any reason why it didnt work?

I take it that the "it" you refer to is the USB Creator on the Live CD. As I indicated in [your other post]("http://ubuntuforums.org/showthread.php?t=1242539"), I ran into several known bugs with the USB Creator.  I know [this bug]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/321544") does not cause an error, but persistence will just plain not work.  Did you try to make your persistence file larger than 2Gb?

---

### Post by Teh H4rRy on 2009-08-20
> **Mighty_Joe said:**
> I take it that the "it" you refer to is the USB Creator on the Live CD. As I indicated in [your other post]("http://ubuntuforums.org/showthread.php?t=1242539"), I ran into several known bugs with the USB Creator.  I know [this bug]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/321544") does not cause an error, but persistence will just plain not work.  Did you try to make your persistence file larger than 2Gb?

I did, I set it to use the rest of the drive, 3GB Is that too much then?

---

### Post by Mighty_Joe on 2009-08-20
> **Teh H4rRy said:**
> I did, I set it to use the rest of the drive, 3GB Is that too much then?

According to the bug I linked earlier and my experience, yes. Note that this bug is a problem with the way USB Creator uses the dd command, not with persistence in general.  [PenDriveLinux]("http://www.pendrivelinux.com/usb-kubuntu-904-persistent-install-windows/") has a 3Gb casper-rw file you could download and try.

---

### Post by russu52 on 2009-08-26
> **Mighty_Joe said:**
> According to the bug I linked earlier and my experience, yes. Note that this bug is a problem with the way USB Creator uses the dd command, not with persistence in general.  [PenDriveLinux]("http://www.pendrivelinux.com/usb-kubuntu-904-persistent-install-windows/") has a 3Gb casper-rw file you could download and try.

i used the pendrivelinux method with a 3gb casper-rw file and works well. it is handy if you are using the same thumb drive on different pc's. but if you are going to use only one pc, then i suggest installing ubuntu direclty on the pen drive (need at least an 8gb drive). it boots well and fully featured.

---

### Post by Mighty_Joe on 2009-08-27
> **russu52 said:**
> it is handy if you are using the same thumb drive on different pc's. but if you are going to use only one pc, then i suggest installing ubuntu direclty on the pen drive 

I've used my USB drive with a full install on several PC's without a problem.  [this guy]("http://ubuntuforums.org/showpost.php?p=7756588&postcount=9") says it used to be a problem but isn't anymore.

---

### Post by Mike1971 on 2009-11-04
Hi Guys,

I want to create a USB stick with Ubuntu 9.10 on it as a full installation. I went into the USB creater when running the live CD and the slider max's out at 4GB but my key is 8GB.  Is this normal? Also is there a way to remove the screan at the begining offering me to install Ubuntu and just boot direct instead? It's like the live CD but on a USB key but my settings are saved. I want to run it as a full installation and get used to it before installing to my hard drive and make sure everything on my laptop works properly.

Thanks

---

### Post by Mighty_Joe on 2009-11-05
> **Mike1971 said:**
> the slider max's out at 4GB but my key is 8GB.  Is this normal? 


The maximum file size on a FAT32 volume is 4 GB

> **Mike1971 said:**
> 
I want to run it as a full installation and get used to it before installing to my hard drive and make sure everything on my laptop works properly.


If you want a full install, go through the normal install process and select your USB drive as the destination.  Make sure in the final step of the installer to select to install GRUB to the USB drive.  If you look on the first page of this topic, I've linked to some detailed instructions on installing and optimizing Ubuntu on a flash drive.

---

### Post by Mike1971 on 2009-11-06
Thanks finally I decided to dual boot instead ( I had the realestate on the drive) and I'm pleased with the results. Configuration was easy and everything on my laptop seems to work great (except for chess in 3d mode??? I have compiz and cube enabled). Most of all I find Ubuntu boots way faster than Vista. Only problem is that I read (after I installed) that the default file system in 9.10 is maybe unstable with files over 512MB (EXT4 I think) and should have opted for EXT3 instead. Anyway thanks for the help I will check for this in the appropriate thread.

---

### Post by NO_oB on 2009-11-19
> **presence1960 said:**
> [COLOR="Red"]Method 4[/COLOR]

[COLOR="Black"]From Ubuntu 9.04- Go System > Administration > USB Startup Disk Creator. Really simple just follow the prompts.[/COLOR]

P::what is the name of the program in synaptics?
R::usb-creator

---

### Post by presence1960 on 2009-11-19
> **NO_oB said:**
> P::what is the name of the program in synaptics?
R::usb-creator

see the attached pic

---

### Post by acodring on 2009-11-20
> **Mighty_Joe said:**
> The maximum file size on a FAT32 volume is 4 GB
If you want a full install, go through the normal install process and select your USB drive as the destination.

I'm trying to boot a Zotac IONITX as a mythtv frontend from an 8GB USB stick. The Zotac machine has no HDD and no optical drive.

Using another machine in the house I've tried installing the O/S directly to the USB stick from the Mythbuntu 9.10 CD (as suggested above). Unfortunately when I get to the partitioning page it doesn't include the USB stick as an option. I tried on two different machines.

Before that I tried the LiveCD on USB methods and it boots once OK but on reboot the machine no longer recognizes the USB stick as bootable.

Any tips related to either approach appreciated. In the meantime I'll get back to googling...

---

### Post by Mighty_Joe on 2009-11-23
> **acodring said:**
> I get to the partitioning page it doesn't include the USB stick as an option. I tried on two different machines.

Have you tried a different USB drive?  Did the OS recognize the disk and mount it when you plugged it in?  I've seen some reports that the partitioner isn't recognizing USB drives, but I've installed Ubuntu 9.10 to a couple of drives and have not had any problems.
Another thing you can try is to boot up the live CD and use the partitioner (Gparted) outside the installer.  Click on System->Administration->Gparted.  Select your USB drive in the upper right-hand corner, click on Device->Create Partition Table.  Create a new partition table (this will destroy any existing partitions and data) and partition the drive.  I have enough RAM to run without swap (2GB), so I just create one big ext3 partition.

> **acodring said:**
> 
Before that I tried the LiveCD on USB methods and it boots once OK but on reboot the machine no longer recognizes the USB stick as bootable.

That's not unusual. I've had several Live USB drives just stop working.  A full install is your best bet if you want to do anything other than testing.

---

### Post by acodring on 2009-11-23
Thanks for chipping in with your thoughts!

> **Mighty_Joe said:**
> Have you tried a different USB drive?  
It turns out it was a pure bonehead issue. It's one of those tiny USB drives with no insertion keying and I had put it in upside down...

Once it was in the right way it was recognized and I was able to start the full install process. Unfortunately it kept failing at 43% done. I tried another copy of a LiveCD (also switched to 64bit instead of i386) and that worked.

The flash drive then worked great for a couple reboots and then stopped working - it hung with "GRUB' on the screen and wouldn't respond to any keyboard input.

I then booted back into the LiveCD on the other machine (I am really impressed how well the LiveCD worked on my MacBook!), re-installed MBR ([http://www.pendrivelinux.com/install-a-new-mbr-to-your-usb-flash-device/](http://www.pendrivelinux.com/install-a-new-mbr-to-your-usb-flash-device/)) and reinstalled GRUB2 ([http://linuxers.org/howto/how-recover-grub2-ubuntu-910-karmic-koala](http://linuxers.org/howto/how-recover-grub2-ubuntu-910-karmic-koala)) and it's worked fine for a couple reboots again.

Now that it's working and updated I want to figure out how to back it up! It must be something involving 'dd' but I can't find explicit instructions or examples using Linux. There's lots of help on copying .img files TO a flash drive, but nothing so far on how to copy one off of a working drive. I did find this Windows tool: [http://www.ghacks.net/2008/07/03/backup-and-restore-usb-images/](http://www.ghacks.net/2008/07/03/backup-and-restore-usb-images/)

Then if I'm feeling REALLY crazy I'll start looking into how to run two USB flash drives with RAID...

---

### Post by phillw on 2009-11-23
You could always get one of these to play with [http://shop.canonical.com/product_info.php?products_id=577&osCsid=0c2c450b2eec50ead3c2004767939d37](http://shop.canonical.com/product_info.php?products_id=577&osCsid=0c2c450b2eec50ead3c2004767939d37)

And Ubuntu gets few pennies / cents out of the profits for running costs :D

The logo is worth it, never mind the 4GB and the 9.10 install part of it :p

Can't wait to get my hands on the one I've recently ordered.

Regards,

Phill.

---

