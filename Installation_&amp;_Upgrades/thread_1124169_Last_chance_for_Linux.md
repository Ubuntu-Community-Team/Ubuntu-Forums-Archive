---
title: "Last chance for Linux"
date: 2009-04-13
forum: Installation &amp; Upgrades
---

### Post by noelc on 2009-04-13
Wel,

I,ve tried numerous times to run Ubuntu to no avail. I have sucessfuly downloaded and burnt to CD. I thought I,d sucessfully installed it this time but when it reboots I get,

Grub loading please wait then Error 21 and then nothing. I had to log onto my work laptop to post here.

Help please

---

### Post by bruno9779 on 2009-04-13
I had a similar problem.

have a look at this:

[http://ubuntuforums.org/showthread.php?t=668864](http://ubuntuforums.org/showthread.php?t=668864)

---

### Post by Walter Melon on 2009-04-13
> **noelc said:**
> Wel,

I,ve tried numerous times to run Ubuntu to no avail. I have sucessfuly downloaded and burnt to CD. I thought I,d sucessfully installed it this time but when it reboots I get,

Grub loading please wait then Error 21 and then nothing. I had to log onto my work laptop to post here.

Help please

This thread might help you out. 
[http://ubuntuforums.org/showthread.php?t=62717](http://ubuntuforums.org/showthread.php?t=62717)

---

### Post by noelc on 2009-04-13
> **Walter Melon said:**
> This thread might help you out. 
[http://ubuntuforums.org/showthread.php?t=62717](http://ubuntuforums.org/showthread.php?t=62717)

GUys,

Thanks for the links but none helped,

I trying to reinstall Linux again to see if that works.

I did try to manually partion but kept getting an error message "no root files"

I,ve goolge grub 21 error seeking a solution but seems theres no easy to understand solution to this error?

---

### Post by sahabcse on 2009-04-13
For fixing the grub follow below url

[http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html](http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html)
[http://sahabm.blogspot.com/2009/01/grub-fix-windows.html](http://sahabm.blogspot.com/2009/01/grub-fix-windows.html)

---

### Post by frankjeffries on 2009-04-13
> **noelc said:**
> Wel,

I,ve tried numerous times to run Ubuntu to no avail. I have sucessfuly downloaded and burnt to CD. I thought I,d sucessfully installed it this time but when it reboots I get,

Grub loading please wait then Error 21 and then nothing. I had to log onto my work laptop to post here.

Help pleaseWhy do you download and burn to cd just buy a Linux based magazine and install the system that it has on Free disk.

---

### Post by Mark Phelps on 2009-04-13
> **frankjeffries said:**
> Why do you download and burn to cd just buy a Linux based magazine and install the system that it has on Free disk.

And why exactly do you thing THIS would work??

The "system" he gets on the free disk is most probably nothing more than a copy of the 32-bit installer that he would get through the download.

At least, that's been my experience using the "Free CDs".

---

### Post by theozzlives on 2009-04-13
> **noelc said:**
> GUys,

Thanks for the links but none helped,

I trying to reinstall Linux again to see if that works.

I did try to manually partion but kept getting an error message "no root files"

I,ve goolge grub 21 error seeking a solution but seems theres no easy to understand solution to this error?

you mean root partition, you have to assign a partition as root (/) mount point when you set it up.

---

### Post by noelc on 2009-04-13
Finaly got Ubuntu loaded and works fine (looks like an easy system to use once navigation sorted). Unfortuantely when I reboot the computer it loads Ubuntu straight away. I wanted a dual boot IE: the ability to choose XP or Ubuntu.

Can anyone suggest how I can now set it up to do this?

---

### Post by SuperSonic4 on 2009-04-13
You can usually press Esc during boot up to give you the grub menu

---

### Post by Walter Melon on 2009-04-13
> **SuperSonic4 said:**
> You can usually press Esc during boot up to give you the grub menu
you can also edit /boot/grub/menu.lst to have the menu always shown.  

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```

if you don't want the menu take the pound sign out of the "#hiddenmenu".  To have the menu, leave the sign there.

---

### Post by noelc on 2009-04-13
> **Walter Melon said:**
> you can also edit /boot/grub/menu.lst to have the menu always shown.  

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```

if you don't want the menu take the pound sign out of the "#hiddenmenu".  To have the menu, leave the sign there.

Ok Thanks,

I,m totally new to this so how/where do I perfrom these edits?

---

### Post by Walter Melon on 2009-04-14
> **noelc said:**
> Ok Thanks,

I,m totally new to this so how/where do I perfrom these edits?

type
```
sudo gedit /boot/grub/menu.lst
``` in a terminal. 
if you don't know where it is: applications->accessories->terminal.  it'll then prompt you for the password.  it won't show any symbols or characters but its still typing.  

the sudo grants you temporary administrator rights and gedit opens up a text editor.  after it opens up, just find the aforementioned lines and edit them.  

(if you want to see what the file looks like without the possibility of accidentally messing it up, type the command in without the 'sudo'.  but then you won't be able to save it.)

---

### Post by noelc on 2009-04-14
Well I tried pressing escape on boot up and was given 4 choices 2 for Ubuntu and two for Unduntu recovery? None for Windows XP.

I tried "Sudo" via accessories terminal entered passowrd and got a blank text editor??

Any ideas on what I,m doing wrong please help as I do want to be able to switch between systems until I,m familiar with Linux?.

Plese help.

Thanks

---

### Post by rtom on 2009-04-14
I guess during the install process you told Ubuntu to use the whole disk, so Win Xp isn't there anymore. Could you give us an output for the command ```
fdisk -l
``` in terminal?

---

### Post by noelc on 2009-04-14
> **rtom said:**
> I guess during the install process you told Ubuntu to use the whole disk, so Win Xp isn't there anymore. Could you give us an output for the command ```
fdisk -l
``` in terminal?

Ok I typed fdisk -1 and got the following?

noel@noel-desktop:~$ sudo fdisk -1
[sudo] password for noel: 
fdisk: invalid option -- '1'

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
noel@noel-desktop:~$

---

### Post by noelc on 2009-04-14
Got it?

k /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6589b897

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18701   150215751   83  Linux
/dev/sda2           18702       19457     6072570    5  Extended
/dev/sda5           18702       19457     6072538+  82  Linux swap / Solaris
noel@noel-desktop:~$ fdisk -l

---

### Post by rtom on 2009-04-14
> **noelc said:**
> 
noel@noel-desktop:~$ sudo fdisk -1

Not fdisk -1 but fdisk -l, like list.

Yes, the NTFS partition is missing.

So first boot a LiveCD and start gparted, make a partition for Win (NTFS, about 10 Gb), Linux (ext3, also ~10 Gb), keep the swap partition. Then you have to install Windows into the first partition, then Linux into the second one. You can do this by selecting the "select partitions by hand" section during installing Ubuntu.

---

### Post by noelc on 2009-04-14
> **rtom said:**
> Not fdisk -1 but fdisk -l, like list.

Yes, the NTFS partition is missing.

So first boot a LiveCD and start gparted, make a partition for Win (NTFS, about 10 Gb), Linux (ext3, also ~10 Gb), keep the swap partition. Then you have to install Windows into the first partition, then Linux into the second one. You can do this by selecting the "select partitions by hand" section during installing Ubuntu.

OK Thanks, Can I assume then that all my programs loaded in XP are a;so gone?

---

### Post by rtom on 2009-04-14
> **noelc said:**
> OK Thanks, Can I assume then that all my programs loaded in XP are a;so gone?

Unfortunately yes. You may try some unformat software, but I never tested any. To avoid loosing personal data I always keep the OS on different partitions (I also have dual-boot), I personally prefer having the /home directory on the third partition, this way all personal settings and data will be safe.

---

### Post by noelc on 2009-04-14
> **rtom said:**
> Unfortunately yes. You may try some unformat software, but I never tested any. To avoid loosing personal data I always keep the OS on different partitions (I also have dual-boot), I personally prefer having the /home directory on the third partition, this way all personal settings and data will be safe.

Not to worry I had backed up all my data to an external hard drive while I muck around with this one which I will be completely reformatting it anyway and useing it as storeage. I will be purchasing a new desktop shortly and in order to save money am thinking about not purchasing any Windows operating system software and operating totally of Linux.

I,m getting the impression not many people run Linux solo? Given I,m completely new is this a good idea. I cant find any reasonable Linux navigation tutorials?

---

### Post by fballem on 2009-04-14
> **noelc said:**
> Not to worry I had backed up all my data to an external hard drive while I muck around with this one which I will be completely reformatting it anyway and useing it as storeage. I will be purchasing a new desktop shortly and in order to save money am thinking about not purchasing any Windows operating system software and operating totally of Linux.

I'm getting the impression not many people run Linux solo? Given I,m completely new is this a good idea. I cant find any reasonable Linux navigation tutorials?

Actually, I have been running ubuntu solo for about a year now. My observation is that dual-boot is an option that works well for most people, but there can be significant issues as well.

There are two main reasons that I've seen where people will dual boot - either they play a lot of games or there is a specific application that will only run in Windows.

I'm not a gamer, and there are two applications that I haven't found good replacements for - Visio and Enterprise Architect. I do have access to a separate Windows machine where necessary, so I don't need to dual-boot. I've been really happy with ubuntu.

You may want to browse some of the entries in [http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326) (the Absolute beginners section) for some suggestions as to where to find tutorials. I also found Moving to Ubuntu Linux by Marcel Gagné (Addison-Wesley, ISBN: 0-321-42722-X) to be very useful. This was written for ubuntu 6.06. The general concepts are still valid. You may want to browse Amazon.com for other introductory books on ubuntu.

There are many flavours of Linux - each using it's own distribution. The major differences (there are many minor variations) seems to be in the packaging tool and in the Windows system.

The following is based on my observations and opinion. It is not a complete list, but hopefully will be a place to start:

The two major packaging systems in Linux seem to be .deb (used by Debian, ubuntu, and lots of others) and .rpm (used by Fedora, OpenSUSE, and lots of others). Each have strengths and weaknesses, both are very good.

The two major windows systems in Linux seem to be GNOME (used by ubuntu, Fedora, and lots of others) and KDE (used by Kubuntu, OpenSUSE, and lots of others). There are other significant windows systems, such as XFCE which have specific purposes (XFCE uses significantly less graphics resources).

I first started with ubuntu and got comfortable with .deb and GNOME. I tried Fedora (particularly after the ubuntu decision to not include OpenOffice 3.0 in ubuntu 8.10) but I could not get comfortable with the .rpm packaging system. I also tried Kubuntu and OpenSUSE, but could not get comfortable with KDE. Many people have strong opinions about which distribution is the 'best', but, for the most part, it boils down to personal opinion - what works for you!

Be prepared for a learning curve - no matter which distribution you choose, Linux is not Windows. The challenge is that many things work in a similar fashion, but because you've been using Windows, you may be used to doing something in a specific way. Linux will do the same thing, but slightly differently. I have found the forums to be incredibly useful when I'm stuck on something. Be patient with yourself and with Linux - there is a learning curve!

There may be some items, particularly media, that you cannot play out of the box. You may want to look at [http://www.medibuntu.org](http://www.medibuntu.org) to see if there is a codec there that will do the job. If not, then [http://www.fluendo.com](http://www.fluendo.com) has commercial codecs at a reasonable cost that seem to work very well. For example, Windows Media Lossless formats can be played using a fluendo provided codec.

Some of the things that I really like about Linux (after having gone through the learning curve):

- Installation. Assuming that I've made a good backup of my data, I can re-install everything and have the machine working the way that I want in a matter of a few hours. I keep careful notes of my installation, but the biggest factor is the use of repositories. The majority of the programs that I use are found in the repositories, so there is no hunting around the internet for drivers and programs and updates. It takes me a couple of days to create a polished Windows installation from scratch.

- Virtual desktops. I use GNOME and in the lower right-hand corner, there are small boxes that represent virtual desktops. I can select one of these to work with, open a program full-screen, then select another and open a different program. It took me a bit to get used to, but now that I am, I really miss it when I have to go back to a Windows machine.

Hope this has been useful, and have fun!

---

### Post by Sef on 2009-04-14
> There are two main reasons that I've seen where people will dual boot - either they play a lot of games or there is a specific application that will only run in Windows.

Or they are fairly new to GNU/Linux and are trying it out.

---

### Post by Chudilo on 2009-04-14
as far as not being ble to play certain types of media is concerned, get VLC and you should be covered for just about everything.

---

### Post by pbpersson on 2009-04-14
> **noelc said:**
> Not to worry I had backed up all my data to an external hard drive while I muck around with this one which I will be completely reformatting it anyway and useing it as storeage. 

I,m getting the impression not many people run Linux solo? Given I,m completely new is this a good idea. I cant find any reasonable Linux navigation tutorials?

1.  You backed up all your data before you started playing with the install disk?  COOL!  It seems you are wiser than many poeple.  ;)

2.  Unless you are a nuclear physicist or designing a space shuttle or a professional graphics designer or a gamer you should be able to do everything in Ubuntu.  However, there is a learning curve.

To start, go to System--->Help and Support and read the basic topics.  Then if you have any questions, let us know.

This is a newbie friendly place :)

None of us were born with this knowledge  ;)

---

### Post by fballem on 2009-04-14
> **Chudilo said:**
> as far as not being ble to play certain types of media is concerned, get VLC and you should be covered for just about everything.

I agree that VLC covers most formats - I'm just not sure that Windows Media Lossless is included.

I use Fluendo because it uses GStreamer, and is therefore more accessible to other programs than VLC. It also does support reading Windows Media Lossless format, unlike medibuntu.

I use VLC for playing DVDs and ISOs. I use Medibuntu because Fluendo will read, but will not write to formats such as MP3. It's fairly common for me to burn my CDs in flac (open source lossless) then run Sound-converter to create MP3 files from the flac files. The MP3 files can then be loaded into my MP3 player using Gnomad2.

I would be interested in knowing if VLC covers Windows Media Lossless format, although I will continue to use the Fluendo product because of the flexibility.

Hope this helps,

---

