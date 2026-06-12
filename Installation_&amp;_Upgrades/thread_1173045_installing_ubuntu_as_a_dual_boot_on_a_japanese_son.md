---
title: "installing ubuntu as a dual boot on a japanese sony VAIO FS21-B laptop ?"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by bjaz on 2009-05-29
hello all

my wife has a japanese sony VAIO FS21-B laptop, currently running a french version of windows XP with many proprietary driver issues.
we would love to run an ubuntu desktop version on this laptop, first as a dual boot version, then eventually as a full on ubuntu laptop, as we've had enough of windows, and the version owned (french) doesn't really work, usb support etc... the solution after contacting sony is to order a japanese windows (the original japanese computer came with no windows CD to reinstall but a sony VAIO back up partition which i deleted when installing the french windows XP)

from what i've been reading this is quite complex. Would anyone know if this is possible on this specific machine ( a japanese model FS 21 -B, with 256MB RAM, a 1.40 GhZ intel celeron processor and 30 Gigs of free disk space), and if so, with what version of ubuntu ?


the only version i have downloaded is a version of of ubuntu studio that i plan on using myself on a mac laptop.  I tried placing this inside the drive and was told the CPU was i-686

if it's possible to install a version, how would this be done to avoid damaging the windows partition which was already quite painful to install ?
if i was sure it would work (ie USB, PCMI card support, display, sound etc) I guess i could take the plunge and go ubuntu all the way, and forget windows.
but how can we be sure without trying. apparently others have run into problems with VAIOs, and this one is japanese which could possibily lead to further issues like it did with the windows version

sorry for the rather broad nature of this demand, but i'm really not finding my way around the many tutorials, which feature different laptops and versions. I am a total newbie and it is a pretty frightening experience, though the motivation is high to finally get this laptop working for her

thanks in advance for your help

ben

---

### Post by Mr, Bean on 2009-05-29
[SIZE=3]hello,

Installing ubuntu is quite easy, especially with the newer versions like 9.04. i am currently running ubuntu as a dual-boot with win-XP and the ubuntu installation was quick and easy.

1. First go to the [ubuntu website]("http://www.ubuntu.com/getubuntu/download") and Download the ISO image for your Laptop, then burn it to a CD.

2.Reboot your laptop with the cd in the drive it, then follow the instructions.
[/SIZE]

---

### Post by themusicalduck on 2009-05-29
As your wife's laptop has fairly low specs it might be worth installing xubuntu, which is a lighter version of Ubuntu. I think the minimum specs for normal Ubuntu is 384mb of ram, but xubuntu should work fine.

You need to get the i386 version, it sounds like the studio version you tried probably was 64bit and the laptop is 32bit, hence it couldn't boot.

Best thing to do first is to boot up the CD and select Try Xubuntu without any changes to your computer. This will run the OS off the CD itself. It'll be pretty slow, but you can check that it'll work properly.

Another way of installing xubuntu without having to do anything too permanent is by using the WUBI installer. Put the CD into the drive while running Windows and run the autorun. It should let you install xubuntu alongside windows as a dual-boot, and it'll put an entry into the add/remove list in windows from where it can be uninstalled again.

I'm writing all this assuming that xubuntu works in the same way as ubuntu since I've only actually used ubuntu myself.. hopefully if I'm wrong and it's a bit different then someone will post here and correct me.

If you decide you want to install it permanently and need more help then just post here and someone will help.

---

### Post by bjaz on 2009-05-29
that's great, i'm going to download xubuntu straight away and look into it.

i'll see how it goes

thanks again

ben

---

### Post by bjaz on 2009-05-30
hello again
the install worked ( i finally installed it using the WUBI installer).

however it is incredibly slow, to the point that opening an application takes more than 30 seconds.
is there anything that can be done or is this due to 256mb of RAM being simply not enough to run xubuntu ?

thanks

ben

---

### Post by themusicalduck on 2009-05-30
It shouldn't be that slow. 256mb should be ok for xubuntu. It might be down to a missing driver or a driver not working properly. I can't really help much there but someone hopefully can.

---

### Post by bjaz on 2009-05-30
hi and thanks. the slowness is fixed. I managed to find an old compatible DDR ram from another dead laptop and now at 500mb things are really fast, it's fantastic. I love it, because this computer is alive again, functionnal.sound doesn't seem to be working but i haven't looked into it properly.

some issues, i'm trying to install the updates and configure things, yet the disk is full.
which is a little odd since the install was on a 33Gig partition.  
i get the following error message : the upgrade needs a total of 92.3M free space on disk '/'
Please free at least an additionnal 92.3M of disk space on '/'

i guess the install partition must have ended up to small or something, orthat '/' doesn't exist hence the problem. how can i either increase '/' 's size or specify a correct path in which to download the updates and language packs ?

thanks again

ben

---

### Post by kruegger on 2009-05-30
You may use gparted or testdisk to redimension your root directory (/). If I get it right you still keep the french Xp installed. This could be swallowing the hard disk space and you may have to reduce the Xp partition. 

Gparted can give you graphical information about the partitions in your disk and then you can decide from that point.
This program comes with Ubuntu cd Live. I guess it can be installed in Xubuntu by typing

sudo aptitude install gparted

If you want to know if a certain package is in your current Ubuntu distro and you know its name

sudo aptitude search gparted

This will list packages with similar name.

Anyway, next time you install a Linux distro, choose manual partitioning which is quite similar to Gparted.

good luck and enjoy!

---

### Post by themusicalduck on 2009-05-30
I'm not sure if that suggestion will work because it was done with a wubi install and I think wubi creates a virtual disk on the NTFS partition rather than creating a new one?

How much space did you assign to xubuntu when you installed it?

/ basically refers to the root of the install. It's equivalent to the windows c drive.

---

### Post by bjaz on 2009-05-31
i forgot to specify that I actually removed the WUBI install and did one from the live CD directly, by booting into it. I've been reading up a little and found a suggestion to download GParted and boot into that, then increase the size of the partition as it's really full.

i've have quite a few crashes when trying to install updates, but i'm hoping they're all related to the root partition being full.

what's really promising is that apart from sound, drivers seem to be working fine, USB etc
got the box online via a PCMIA wifi card.

i'll look into the size issue see if this fixes things a little

many thanks for your help

ben

---

### Post by themusicalduck on 2009-05-31
Ah right, that should help then.

As for sound, click on the volume icon at the top right, then click on Select controls and have a fiddle with that, check all the volume controls are up. I think it starts up with the master all the way down.

Good luck with it.

---

### Post by bjaz on 2009-05-31
hello again.
the partition resizing worked, however i'm still stuck with the updates and language support options.
i don't know if this is due to the fact that the VAIO is Japanese or not, but whern i try to update and install the language packs, i get

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

i don't really know where to go from here, if i type sudo dpkg --configure -a in a terminal i get a series of options that i'm don't understand enough to "correct the problem"

the internet is working, though i have to manually input the connection data when i boot, and i'm on the computer now, but i really need Japanese support (IME) so my wife can use it
.
i also tried installing vlc and get the same error message. tired checing if sound was working, on you tube, a dvd, an aiff file, an mp3 but for all of this i need to download and install codecs and i get stuck with the same error message

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

when i open a terminal window and type this i get

dpkg: unknown option --configue

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !

which doesn't really help

sorry if this is sliding beyond the topics covered here, i'm just in no position to know if this is due to the actual install on this machine or not

ben

---

### Post by kruegger on 2009-05-31
Why are you installing manually?

Isn't there Synaptic in Xubuntu?

In command line:

sudo aptitude update

sudo aptitude install any_package.

To look for a language

System> Administration/Manager> Language Support.

If you have Xubuntu, do it like that.

---

### Post by bjaz on 2009-06-01
that's what I was trying to do, using the graphical interface, but for a reason or another (maybe because it didn't work when the root partition was too small), the graphical interface doesn't work and i get these error messages i printed.

i'm trying to install the languages automatically from the graphic menus but get this.
apparently anything i try to install, updates, language support, codecs, vlc end up with the same error message 

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

i'm a little lost on what to do next.

i'll try the command line you posted, see if it fixes things

thanks

ben

---

### Post by bjaz on 2009-06-01
ok, i'm still stuck, here are the results :

:~$ sudo aptitude update
[sudo] password for xxx: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Sources
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: Couldn't rebuild package cache
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

~$ sudo aptitude install any_package
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

---

### Post by kruegger on 2009-06-01
> **bjaz said:**
> hello again.
the partition resizing worked, however i'm still stuck with the updates and language support options.
i don't know if this is due to the fact that the VAIO is Japanese or not, but whern i try to update and install the language packs, i get

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

i don't really know where to go from here, if i type sudo dpkg --configure -a in a terminal i get a series of options that i'm don't understand enough to "correct the problem"

the internet is working, though i have to manually input the connection data when i boot, and i'm on the computer now, but i really need Japanese support (IME) so my wife can use it
.
i also tried installing vlc and get the same error message. tired checing if sound was working, on you tube, a dvd, an aiff file, an mp3 but for all of this i need to download and install codecs and i get stuck with the same error message

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

[SIZE="4"][COLOR="YellowGreen"]when i open a terminal window and type this i get

dpkg: unknown option --configue[/COLOR][/SIZE]

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !

which doesn't really help

sorry if this is sliding beyond the topics covered here, i'm just in no position to know if this is due to the actual install on this machine or not

ben


You have typed the command wrong

sudo dpkg --configure -a

Post the outcome of it but I suggest you open another thread. 

Your problem is that update can't be done on Xubuntu Jaunty Jackalope in a Vaio laptop. Be as specific as you can. Order and data.
This way someone else will be able to help.


PS: When I wrote this command:

sudo aptitude install any_package

I meant {any_package} to be a known program. You must know the program/package you want to install.
Do not take it literally. You don't use this for the update matter. Dpkg problem must be cleared first.

Good luck

---

### Post by bjaz on 2009-06-02
ah ok, i thought it was a generic command !

will do, thanks again for your help

b

---

