---
title: "Ubuntu broken: nVidia 5600"
date: 2005-08-06
forum: Hardware &amp; Laptops
---

### Post by blastus on 2005-08-06
I'm new to Linux. I've used Fedora Core a little but not much. I thought I would try Ubuntu so I downloaded it on 56K dialup. I've used Fedora Core 3 and it installs and loads just fine on this machine. Ubuntu, however, is broken.

I have an nVidia GeForce FX5600 256MB video card and a PCI Lucent WinModem. Ubuntu installed with errors and refused to launch X-Server when rebooted. I get a nice terminal window instead. Anyway I don't know what to do. I know that soft modems have pretty much no support under Linux so I don't expect to get the Lucent WinModem to work but it would be nice to at least get a GUI working. But I need Internet access to download stuff...like an nVidia driver or something. So this leaves me pretty much screwed I think because I can't use apt or Synaptic or whatever it is to download and install anything. No GUI and no Internet access--I'm off to a good start. :roll: Is it possible for me to get X-Server working on this machine with no Internet access?

I also have a PCI Soundblaster Audigy card which I've read on these forums is a problem with Ubuntu. But if I could just get the X-Server working...and what is the password for root?

---

### Post by neilbain on 2005-08-06
OK... Root password first.  In Ubuntu it is the same as your log-on password.  So at the terminal, to run a command as root you would proceed the command with 'sudo'.  i.e. $>sudo some_command  On pressing enter you will be prompted for your password prior to the command being run.

Onto X...

The place to start is the xorg.conf file.  I use the vim text editor but you can use whatever you prefer.  Do...

$>cd /etc/X11        [Note. Linix is case sensitive]
$>sudu cp xorg.conf xorg.conf.bak    [make a backup of the file before any changes]
$>sudo vim xorg.conf         [Enter your password when promted]

At this point you should have the contents of xorg.conf displayed.

Check...  Driver should equal "nv"  [this is the ubuntu driver which at a later date you may wish to change to the latest nvidia driver but let's not complecate things now  :? ]

Comment out, using a # at the beginning of the line, Load GLX and Load DRI.  [To enter insert mode in vim press 'insert', and press 'esc' to exit the insert mode.]

Save the file.  In vim use (without the quotes) ':save xorg.conf' then ':q'

Now start X with $>startx

Let us know if that worked.... if not, we'll dig deeper.

Neil

---

### Post by Sephiriz on 2005-08-06
And in regard to the sound card, I have one as well, and I can attest to the fact that it is difficult to set it up, but at this point there are so many topics and solutions in these forums on how to use your particular soundcard that I don't think there will be much of any problem.  It will take some time, thats about it.

One thing I've learned from Debian, or maybe just Linux in general, is that there is nearly always a solution :)

---

### Post by blastus on 2005-08-06
[QUOTE=neilbain]OK... Root password first.  In Ubuntu it is the same as your log-on password.  So at the terminal, to run a command as root you would proceed the command with 'sudo'.  i.e. $>sudo some_command  On pressing enter you will be prompted for your password prior to the command being run.[/QUOTE]

I see. That makes perfect sense. But this means that any user can modify the system as if they were root no?

This explains why I needed to type "sudo shutdown -r now" to reboot. I'm familiar with a couple of commands such as cat, cd, pwd, ls, mkdir, rmdir, mv, cp, rm (I think it's rm), mount, fdisk and shutdown but I'm TOTALLY LOST with configuration. 

> 
Onto X...

The place to start is the xorg.conf file.  I use the vim text editor but you can use whatever you prefer.  Do...

$>cd /etc/X11        [Note. Linix is case sensitive]
$>sudu cp xorg.conf xorg.conf.bak    [make a backup of the file before any changes]
$>sudo vim xorg.conf         [Enter your password when promted]

At this point you should have the contents of xorg.conf displayed.

Check...  Driver should equal "nv"  [this is the ubuntu driver which at a later date you may wish to change to the latest nvidia driver but let's not complecate things now  :? ]

Comment out, using a # at the beginning of the line, Load GLX and Load DRI.  [To enter insert mode in vim press 'insert', and press 'esc' to exit the insert mode.]

Save the file.  In vim use (without the quotes) ':save xorg.conf' then ':q'

Now start X with $>startx

Let us know if that worked.... if not, we'll dig deeper.

Neil

This file, /etc/X11/xorg.conf does not exist on my machine. I even did a "cat /etc/X11/xorg.conf" and an "ls" to list the contents of /etc/X11 of and xorg.conf does not exist.

When I installed Ubuntu I just pressed Enter for the basic setup. Everytime I boot up I'm shown a terminal window that says that the X server could not be started. When I select "Yes" to diagnose it shows another terminal window with this message:

"GDM: XServer not found: /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
Error: Command could not be executed
Please install the X Server or edit /etc/gdm/gdm.conf to point to the right place."

Also, these two terminal windows have garbled borders. The border consists of some characters with accents and stuff like that in the high ASCII range and they run into the window in places and run off and outside the window in other places. In other words, the terminal windows I see upon bootup look distorted but during the install they weren't distorted like this. Why would they be distorted?

During the install I encountered errors that some packages were not installed or were installed with errors or something like that. Then it ran apt for me in a terminal window. Not knowing what to do I just quit it and it finished the installation. Do I need to run something to get a generic video driver for X Server installed? Thanks for your help!

EDIT: I found a post regarding the XServer not found thing and they said to type "sudo dpkg-reconfigure xserver-xorg." I tried that and got the message:

Package "xserver-xorg" is not installed and no info is available.

Apparently "dpkg-reconfigure" is supposed to create the /etc/X11/xorg.conf file. I assume that the "xserver-xorg" package is what you need for X and the /etc/X11/xorg.conf file is the configuration file for things related to X? I typed "man dpkg-reconfigure" and it says it doesn't install the package, but will "reconfigure" an already installed package. How do I install xserver-org from the CD and why didn't it install when I installed Ubuntu?

> And in regard to the sound card, I have one as well, and I can attest to the fact that it is difficult to set it up, but at this point there are so many topics and solutions in these forums on how to use your particular soundcard that I don't think there will be much of any problem. It will take some time, thats about it.

One thing I've learned from Debian, or maybe just Linux in general, is that there is nearly always a solution

Thanks. The configuration stuff I'm TOTALLY LOST with but it's good know that someone probably has a solution somewhere.

---

### Post by g7yh7uj8k on 2005-08-06
Xorg -configure 
will generate the /etc/X11/xorg.conf. for you if there is none

---

### Post by blastus on 2005-08-07
[QUOTE=g7yh7uj8k]Xorg -configure 
will generate the /etc/X11/xorg.conf. for you if there is none[/QUOTE]

Tried that, "command not found." Even tried "xorg -configure" Both "which Xorg" and "which xorg" yields nothing.

I think I'm going to reinstall the XP boot loader to the MBR, delete the Ubuntu partition, and then try to install Ubuntu again. I don't mind messing with commands and stuff to get things working but I don't understand why Ubuntu can't load a generic video driver for nVidia GeForce FX5600. I've installed Red Hat 6, Fedora Core 1, and Fedora Core 3 and have had no problems with X Server working from an out-of-the-box installation. All of these loaded generic video drivers for either ATI and nVidia on different computers. 

What really bothers me the most though are these DISTORTED terminal windows. Maybe it's an international character set problem or something but my language was set to U.S. English and everything is North American. Drawing a border on these windows with some characters from a code page (like U.S. ASCII) should be no problem but apparently Ubuntu has BIG PROBLEMS with it. During the installation the terminal windows weren't distorted--it was only after my botched installation was finished and I get these X Server errors and stuff every time I boot up.

---

### Post by blastus on 2005-08-07
Well I restored the XP MBR, deleted the Ubuntu partition in XP, then installed Ubuntu again. I don't believe I did anything differently this time than last and for some reason it seems to work now. What the...the X Server loads and I can hear sound too! Some sounds sound hissy or scratchy but I can work on that later. The modem, however, seems to be detected but doesn't want to activate properly (modem port or whatever can't be autodetected.) But I can work on that later. At least I can use a GUI now. :razz:

I don't know why NOTHING worked the first time I installed Ubuntu. :roll: I don't know if it has anything to do with my monitor because on certain resolutions and stuff the picture becomes unstable...like during the second phase of the install with all the scrolling text. Also earlier today I downloaded a newer (and finally Windows certified) driver for my nVidia GeForce FX5600 on XP but I don't know if that has anything to do with it affecting Linux. I know they are different OSs and installed on different partitions but maybe the new Windows driver does with some cryptic or nobody-knows-anything-about setting on the graphics card I don't know. Or maybe it was just a botched install but why why why I'll never know. All this stuff drives me crazy though. ](*,) 

I guess I need to download an nVidia driver or something. I also need to be able to change the gamma settings because I have an old CRT monitor but I think that would only be accessible through a driver (like it is on XP.) I have a FAT32 partition on my second hard drive that I can share data between XP and Linux with. I successfully edited the /etc/fstab and added a mount entry for it there and it works. Now that I actually have X Server working and can read/write data on my FAT32 partition, I want to try to get my Lucent WinModem working IF that is possible. 

I guess I'll have to figure out how to setup a "repository" or something that apt can use on my FAT32 partition and download everything using XP. I have no clue how to use apt or synaptic and especially like this with NO Internet access.

I'm glad I tried to install Ubuntu again from scratch because I was going to totally give up on this distribution. My first opinion of the GNOME interface in Ubuntu is that it is more organized and less cluttered than in Fedora Core.

---

