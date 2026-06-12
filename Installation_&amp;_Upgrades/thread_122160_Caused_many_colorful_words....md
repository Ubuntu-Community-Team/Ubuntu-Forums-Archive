---
title: "Caused many colorful words..."
date: 2006-01-26
forum: Installation &amp; Upgrades
---

### Post by thepocketdrummer on 2006-01-26
Well, I tried to install this over a copy of windows. The process of shrinking the Windows partition actually killed windows, forcing me to reformat entirely. I took this opportunity to try to install Ubuntu on a clean system. I reformatted... started the installation... then after all was done, it took me to the login screen. I thought I was home free. I was wrong. Just like the Live CD problem, it just sits at a tan screen with a mouse. Nothing else is on the screen. There is no GUI of any sort, just this tan screen. Several hours later and here I am... back on windows.

What is causing this issue and how do I fix it?

Also, what is the proper way to "shrink" the Windows Partition without destroying the OS?

Specs as follows:
Athlon 64 3700+ (san diego core)
Foxconn Winfast NF4UK8AA Motherboard
1024MB PC3200 RAM (2x 512MB)
eVGA 7800GT CO 256MB
Audigy 2 ZS

---

### Post by adwait on 2006-01-26
A proper way to shrink the partition would be to use a specialised software such as partition magic or something.

Anyway, as for your display issues, there is a problem with your display drivers. Press Alt + Ctrl + F1 to get to the console screen. Login there with your usual username and password. And try running
```
sudo dpkg-reconfigure xserver-xorg
```

This could help.....but it may not. Search for Linux drivers for your graphics card.

---

### Post by RavenOfOdin on 2006-01-26
[QUOTE=adwait]A proper way to shrink the partition would be to use a specialised software such as partition magic or something.
[/QUOTE]

[QUOTE=https://wiki.ubuntu.com/forum/installation/Partitioning?highlight=%28partitioning%29]
The ubuntu installer's partitioner is one of the safest ways to partition a hard disk. This is not an excuse for not making backups of your important files.
[/quote]

You can go either way drummer, given posts on this forum and the relative safety of a backup system, I don't think the installer would screw you over. Not to mention, you can do better than Partition Magic. :p

---

### Post by towsonu2003 on 2006-01-26
[QUOTE=adwait]A proper way to shrink the partition would be to use a specialised software such as partition magic or something.
[/QUOTE]
I used R.I.P. (a live cd) to shrink my ntfs. It uses a recent version of ntfstools that can (more or less) safely shrink the damn thing. But you'll need to read about how to use ntfstools from the command line. It's relatively easy (I was a newbie when I did that, with my first ever linux installation, and I didn't screw it). 

this is the web site for RIP [http://www.tux.org/pub/people/kent-robotti/looplinux/rip/](http://www.tux.org/pub/people/kent-robotti/looplinux/rip/)
and this is some very good info on ntfsresize: [http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html](http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html)

make sure you run the anti-fragmentation thingy under windows a couple of times [edit]in safe mode[/edit] beforehand (and do **backups**). You'll be able to see about how much you can shrink it from the graphical thing it shows. 

after that, still using RIP, you can also partition your drive... here is the man page of fdisk which may be helpful: [http://linuxcommand.org/man_pages/fdisk8.html](http://linuxcommand.org/man_pages/fdisk8.html) (see also my PS3 below)
while using fdisk, follow the insructions provided within the thingy. 
two ext3 partitions (one for / of at least 5GB and one for /home) will be useful. 

RIP is all command-line though. the command "shutdown" will turn the computer off ;)

PS. Although you're a newbie, stuff like RIP and Slackware (another distro) are helpful during the linux-learning-period... If you have a test machine, you may wanna try this stuff on it first. And if you have plenty of time, you could start with slackware and go down (ok now I'm going awfully offtopic!!)

PS2. Instead of shrinking, I would use a live cd to partition the drive for 4 partitions: ntfs (windows) fat (transfer files between Operating Systems), 2x ext3 (one for / and one for /home) . then go ahead and install windows to the available ntfs. than install ubuntu (or some other distro) and voila, you have a dual boot from scratch. 

PS3. Take a look at this link: [http://www.bitbenderforums.com/vb22/showthread.php?postid=311808](http://www.bitbenderforums.com/vb22/showthread.php?postid=311808)
It is for slackware, but it is perfect for seeing how fdisk works with screenshots.

---

### Post by mcduck on 2006-01-27
I have used Ubuntu's installer to shrink NTFS partitions many times, and it has never failed. I just defrag the partition in Windows safe mode first.

Honestly, I find programs like Partition Magick quite useless in Linux world. We have tools like gparted and qparted for managing partitions, and 'dd' command handles copying partitions, whatever the filesystem is..

If you anyway use such a program, you should not make new partitions with it, just use it for resizing and let Ubuntu's installer create it's own partitions.

Anyway, this might be a helpful link. It's a complete guide to setting upa dual-boot with Ubuntu and Windows, including lots of screenshots from the installation (and partitioning wtih Ubuntu installer): [http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

---

### Post by hobbit1983 on 2006-01-27
The latest release of knoppix Live CD contains an application called QTParted that is a nice GUI that uses NTFS resize under the covers to allow you to resize NTFS partions without the need for defragmenting the partition.

My dad has used this successfully to (non destructivly) resize his NTFS partition to make room for Ubuntu.  It all seemed to work fine for him.

I really would suggest it

---

### Post by thepocketdrummer on 2006-01-27
[QUOTE=adwait]A proper way to shrink the partition would be to use a specialised software such as partition magic or something.

Anyway, as for your display issues, there is a problem with your display drivers. Press Alt + Ctrl + F1 to get to the console screen. Login there with your usual username and password. And try running
```
sudo dpkg-reconfigure xserver-xorg
```

This could help.....but it may not. Search for Linux drivers for your graphics card.[/QUOTE]

How can I get the drivers though? I don't have an a GUI of any sort once Ubuntu starts. I found Linux drivers for my card though. How would I go about installing those?
(I don't have a CD-Burner)

---

### Post by codejunkie on 2006-01-28
[QUOTE=thepocketdrummer]How can I get the drivers though? I don't have an a GUI of any sort once Ubuntu starts. I found Linux drivers for my card though. How would I go about installing those?
(I don't have a CD-Burner)[/QUOTE]
try this press ctrl+alt+f1 this should drop you to a console from here run ```
sudo nano /etc/X11/xorg.conf
``` this will open a console based text editor scroll down until you find a section called "Device" 
this will be your video card look for the Driver line
it will look something like
```
Driver          "nv"
```
change it to 
```
Driver          "vesa"
```
if "vesa" is already listed change it to "nv" the reason for trying this is some nvidia card modles will work with one and not the other so you have to tinker a bit to get them working. to save the file press ctrl+x and y now restart the computer by entering ```
reboot
``` and press enter.
this should get you into a gui where you can install the official nvidia driver if this doesn't work let me know and i'll try and help you line this out.

---

### Post by thepocketdrummer on 2006-01-28
Well, I installed Kubuntu (with a little trouble) and instead of a Tan screen, I get a really distorted blue-ish screen. I tried pressing ctrl+alt+F1 and nothing happened. Any suggestions?

---

### Post by thepocketdrummer on 2006-01-28
Ok, I booted Kubuntu in recovery mode which allowed me to type in

```
sudo nano /etc/x11/xorg.conf
```

This just took me to a blank screen.
:cry:

---

### Post by Jason_25 on 2006-01-28
I think it's because your graphics are so new, that the xorg "nv" driver is having trouble.  Try changing the "driver" section in your xorg file from nv to vesa.  Then ctrl-alt-backspace.  If that works, you can then go about installing the propietary nvidia driver.

---

### Post by thepocketdrummer on 2006-01-28
I'm having trouble getting the Driver part to even show up. I get into an area to type things in, but there isn't a list of anything.

---

### Post by thepocketdrummer on 2006-01-28
ok, now I tried typing

sudo nano

by itself. Took me to the same blank nano editor (I'm guessing thats the name). I can't, for the life of me, get to xorg.conf. I have no clue how to use this editor. I don't think I've ever been so frustrated with anything in my whole life.

Does anyone know how to get Grub to make Windows my default? Or, if I never get this to work, how do I remove Grub so it just boots strait to Windows without bothering me?

---

### Post by codejunkie on 2006-01-28
[QUOTE=thepocketdrummer]Ok, I booted Kubuntu in recovery mode which allowed me to type in

```
sudo nano /etc/x11/xorg.conf
```

This just took me to a blank screen.
:cry:[/QUOTE]
the reason it didn't work is linux is case sensitive and you used a lower case X it should be X11 not x11.

---

### Post by thepocketdrummer on 2006-01-28
You were right about the lower-case x. \\:D/ 

Well, I'm in Kubuntu now, but I'm not sure how to install these drivers.

This is the website for the drivers.
[http://www.nvidia.com/object/linux_display_amd64_1.0-8178.html](http://www.nvidia.com/object/linux_display_amd64_1.0-8178.html)

It says, > Type "sh NVIDIA-Linux-x86_64-1.0-8178-pkg2.run" to install the driver but I don't know where I'm supposed to type it.

Also, I realized that pressing ctrl+alt+F1 while in Kubuntu is a bad Idea :-k

---

### Post by Jason_25 on 2006-01-28
Actually it's not a bad idea.  Ctrl-alt-F7 will take you back to the gui.

Make sure you remove your restricted modules before trying to compile.  Also, install build-essential and gcc-3.4 base in synaptic.  CD to the directory of the installer, then type:
CC=gcc-3.4
export CC
sudo sh NVIDIA-Linux-x86_64-1.0-8178-pkg2.run

and follow the instructions.

When (if) you get all that done, change the driver section in the xorg file from vesa to nvidia.

---

### Post by thepocketdrummer on 2006-01-28
ok, i found Konsole and typed what it said into it, but it says it must be run as root. What does that mean?

---

### Post by thepocketdrummer on 2006-01-28
[QUOTE=Jason_25]
Make sure you remove your restricted modules before trying to compile.  Also, install build-essential and gcc-3.4 base in synaptic.  CD to the directory of the installer, then type:
CC=gcc-3.4
export CC
sudo sh NVIDIA-Linux-x86_64-1.0-8178-pkg2.run[/QUOTE]

You lost me at that part. (I've never used linux before, I'm as green as they get)

---

### Post by towsonu2003 on 2006-01-28
> **Jason_25]Ctrl-alt-F7 will take you back to the gui.
[/QUOTE]
just wanted to add "in normal conditions" here. in my computer, it doesn't eheheh (it takes me back to a "colorful" (sic) screen hihih). 
offtopic notes: 
1. patience is gold in linux
2. me too lazy to fix my own drivers  said:**
> to run as root
you need to do ```
sudo somecommandyouwant
``` and enter your password. don't do it if what you have is not from a very very very trusted source (nvidia's own site is a trusted source for most people)...

---

### Post by Jason_25 on 2006-01-28
[QUOTE=thepocketdrummer]You lost me at that part. (I've never used linux before, I'm as green as they get)[/QUOTE]

Go into synaptic and search for "restricted".  Look down the list a ways and find the restricted modules package for your kernel version.  There should only be one installed by default.  Now remove it.  Now search for "build-essential" and "gcc-3.4".  Install these and whatever packages they say they need.

Now, if you downloaded the nvidia installer to your desktop, open a terminal and type:

cd Desktop
CC=gcc-3.4
export CC
sudo sh NVIDIA-Linux-x86_64-1.0-8178-pkg2.run

Good luck and ask if you have questions.

---

### Post by thepocketdrummer on 2006-01-28
What/where is synaptic?

(this is borderline embarrassing)

---

### Post by thepocketdrummer on 2006-01-28
Is Adept a Kubuntu version of synaptic? I opened that and did a filter for restricted and came up with a bunch of modules. Should I delete these?

---

### Post by codejunkie on 2006-01-28
[QUOTE=thepocketdrummer]ok, i found Konsole and typed what it said into it, but it says it must be run as root. What does that mean?[/QUOTE]
if your installing the nvidia driver from [www.nvidia.com](www.nvidia.com) you need to do a couple of things first make sure to follow these in order
you can just open up konsole and copy and paste these in there
1|```
sudo apt-get update
```
2|```
sudo apt-get dist-upgrade
```
let it download and install all updates avaliable then reboot
3|open up konsole again and copy an paste this in there
```

sudo apt-get install linux-headers-`uname -r` build-essential gcc-3.4

```
4|```
sudo apt-get remove --purge nvidia*
```
5|place the nvidia driver in your home directory then press ctrl+alt+F1
now 
6|```
sudo /etc/init.d/kdm stop
```
7|```
sudo -s
```
8|```
export CC=gcc-3.4
```
9|```
sh NVIDIA
``` hit the tab key and it should fill in the rest of that long file name for you press enter and it will start the driver installer follow the prompts and when it finishes run 
sudo nano /etc/X11/xorg.conf againg and change the driver from "vesa"
to "nvidia" and reboot and that should do it.

---

### Post by thepocketdrummer on 2006-01-28
ok, when I typed
```
sudo killall -9 gdm
```
it says no process was killed

I did the rest anyway, and when I did
> sh NVIDIA
and pressed tab, the installation started, but it said that X server was still running and could not install.

---

### Post by codejunkie on 2006-01-28
[QUOTE=thepocketdrummer]ok, when I typed
```
sudo killall -9 gdm
```
it says no process was killed

I did the rest anyway, and when I did

and pressed tab, the installation started, but it said that X server was still running and could not install.[/QUOTE]
do you know what your using for a login manager gdm or kdm or what's the screen look like where you enter your username and pasword when you first login?

---

### Post by thepocketdrummer on 2006-01-28
Its the one that installs with Kubuntu. I'm not really sure what it is.

---

### Post by codejunkie on 2006-01-28
[QUOTE=thepocketdrummer]Its the one that installs with Kubuntu. I'm not really sure what it is.[/QUOTE]
ok it's kdm instead of running sudo killall -9 kdm & sudo killall -9 gdm you'll need to use ```
sudo /etc/init.d/kdm stop
``` to kill the display manager
i'll edit the steps in my other post to make it right and just start with number 5 and it should work this time sorry for the confusion.

---

### Post by towsonu2003 on 2006-01-28
after hitting alt+ctrl+f1 try ```
sudo /etc/init.d/kdm stop
``` which will / should stop (kill) kdm.

PS. I need to type even faster

---

### Post by thepocketdrummer on 2006-01-28
ok, I started at 5 and did it that way. The new command worked, but typing ```
sudo -s
```
seems to do nothing. Same with the Export one.

it still says the X server thing...

---

### Post by thepocketdrummer on 2006-01-28
does the fact that its the 64-bit version change anything?

---

### Post by Jason_25 on 2006-01-28
Did you press ctrl-alt-f2 (or 1-4 doesn't matter) and then
sudo /etc/init.d/kdm stop

If that was successful the xserver should definitely be stopped.
Then run the installer.

I am running 81.78 on 64-bit 5.10 right now.

---

### Post by thepocketdrummer on 2006-01-28
I tried again and it stopped it. The installation started, then stopped saying something about the kernel not matching and a different compiler that the one used to compile the driver... I'm not really sure.

What am I doing wrong?

---

### Post by Jason_25 on 2006-01-28
You're almost there.

you need to do 

CC=gcc-3.4
export CC

Before you run the installer.

---

### Post by thepocketdrummer on 2006-01-28
Ok, basically it says that no precompiled kernel interface was found. It asks if I'd like it to try to make one, I say yes. Then it tells me that it couldn't, the gcc-version-check failed, and that the compiler used to compile the kernel was gcc 3.4; the current compiler is gcc 4.0.

I'm not sure what any of that means, but hopefully it helps.

---

### Post by Jason_25 on 2006-01-28
Follow my last post and you should be all set.

Choose yes to configuring the kernel interface, assuming you have the restricted modules for your kernel already uninstalled.

---

### Post by thepocketdrummer on 2006-01-28
I don't think they're uninstalled. Could you walk me through that?

---

### Post by Jason_25 on 2006-01-28
Search for restricted in synaptic.  Scroll down until you find the restricted modules for your kernel.  It should have it's green square to the left filled in.  Right-click it and choose "mark for uninstallation" then hit apply.

---

### Post by thepocketdrummer on 2006-01-29
Ok, I searched restricted with Adept and found only one restricted one installed. Its called linux-restricted-modules-common

The description is "Non-free Linux 2.6.12 modules helper script"

Should I uninstall it?

---

### Post by thepocketdrummer on 2006-01-29
YYEEESSS!!!!! It worked!

I went ahead and uninstalled that one, and that was it!

\\:D/ THANK YOU!!!! \\:D/

---

