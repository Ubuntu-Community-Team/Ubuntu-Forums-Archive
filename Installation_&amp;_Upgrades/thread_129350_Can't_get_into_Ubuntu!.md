---
title: "Can't get into Ubuntu!"
date: 2006-02-13
forum: Installation &amp; Upgrades
---

### Post by bulletbutter on 2006-02-13
System:
AMD Athlon 64 3200+
2.01GHz.    1.25 GB of Ram
MSI Neo4 Plantinum/SLI NVIDIA nForce 4

I downloaded the ubuntu-5.10-install-amd64.iso and burned it to cd.  The install seems to work fine I got no errors during the install.  When I reboot and select to boot into ubuntu, it goes to the loading screen and shortly after freezes on a black screen with a white cursor, which is not blinking.  I get no response from pressing any combination of buttons.  The only time I get a response is when I hold down the power button to my pc for a few seconds.  It proceeds to the login prompt but I am unable to type anything.

---

### Post by calimarno on 2006-02-13
Hi bulletbutter,
Did you try Ctrl+Alt+F1 to switch to a shell? It seems that you have a problem with your graphic card. I think you should try to install the nVidia drivers.

---

### Post by bulletbutter on 2006-02-13
I did some searching and found what I think I needed to do [http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver).  I did the following

```

sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings

When I try to do the next line I get an error

sudo cp /etc/Xll/xorg.conf /etc/Xll/xorg.conf_backup
*error can not stat ' /etc/Xll/xorg.conf: No such file or directory

```
I am lost now.

---

### Post by taurus on 2006-02-13
Of course, you would get an error since there is no such thing as /etc/Xll/xorg.conf!  Your xorg.conf is in /etc/X11, i.e., /etc/X11/xorg.conf...

---

### Post by bulletbutter on 2006-02-13
Thanks, but now I have another problem.  
```

gedit /usr/share/applications/NVIDIA-Settings.desktop

```
Gives me the error:  Gtk - WARNING **: Can not open display

---

### Post by wrtrdood on 2006-02-13
With no X display, you won't be able to use a graphical editor.  Try nano instead.

---

### Post by bulletbutter on 2006-02-13
I have no idea what you mean.  But I went a head and opened up the /usr/share/applications/NVIDIA-Settings.desktop file with nano and made the changes I was told.
```

[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;

```
and I get the same error.

---

### Post by shamrock_uk on 2006-02-13
[QUOTE=bulletbutter]I have no idea what you mean. 
[/QUOTE]

Just FYI:

> With no X display...

X is the name of the graphical interface that runs to give you a windows-like environment. X is not running as you're currently at a command-prompt.

> ...you won't be able to use a graphical editor.

You ran *gedit*, a graphical text editor that is designed to run under X. The error you received was just linux telling you it can't open a graphical display and therefore can't run gedit.

---

### Post by bulletbutter on 2006-02-13
Ok, after doing all that I am still unable to get into gedit....not sure if that should be a concern.  I just want this thing to boot up into Ubuntu!  Been searching quite some time now for possible problems with no success.

I am starting to wonder if I should instead try to download the files from nvidias website instead of using apt-get.

---

### Post by pnmerk on 2006-03-02
i am having the seame problem fresh first time install on an old 566Mhz dell with an Nvidia PCI 128Mb 5200 512MB RAM 80Gb HDD after a full install the system starts to boot the i get a Black screen with a non flashing cursor 
i am entirely new to linux and tired of M$ i dont know the first thing about anything if someone has the patience and the know how to resolve this problem i wuld appreceate your time and effort 

honestly i cat wait to try Ubuntu thanks in advance

---

### Post by pnmerk on 2006-03-02
well i had gone to bed but like a lightning strike the idea of disconnecting the secondary nvidia video card and using the integrated video card prevented me from sleeping and it worked ...wohoo!!!! \\:D/  now how do i install stuff on this gues its time to hit the search button but first some well deserved rest (if the wife lets me back in that is) [-(

---

### Post by Bartender on 2006-03-02
pnmerk -
One of the things that isn't really talked about too much is that a functional, fast internet connection is just about the most important thing to have once you've successfully installed.
If you have that the fun begins.  Look up Synaptic, the program that finds, downloads & *installs* the programs you want to get.  The whole concept takes a little gettin used to.  I still just sit there and watch, grinning like a fool.
If you have a fairly modern, capable computer you can have fun with your desktop, installing gdesklets, themes, etc.  Older PC's will take a noticeable performance hit with too many gdesklets and various eye candy running.  I decided to pull all of them back off the desktop of the PC in sig.
If you want to take care of a whole basket of programs all at once, look up Automatix.  Some will squawk that Automatix broke their machines, and/or that you don't learn anything by letting it do all the work.  It didn't break mine.  It wasn't until after running it that I began to feel maybe I too could have a working Linux machine without having to go back to college for a Linux degree.

---

### Post by manchette on 2006-03-02
i've kinda got the same problem installing x86 Breezy :
i installed ubuntu dual boot with suse and ubuntu will not let me log in at the user connection screen ... no keyboard nor mouse at all.

is this hardware and usb not managed correctly?
or software and X server wrong ?
i checked and have usb legacy enabled in my bios (well this should be ok for it is in Suse )

i ran using root console from suse in my ubuntu partition (/ubuntu) :
```
chroot/ubuntu
dpkg-reconfigure xserver-xorg
```
answered the questions of the x server but i still don't have any keyboard nor mouse available at the log in screen.

shall i then run in root :
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudi nano /etc/X11/xorg.conf 
```

can you help me ?

---

### Post by neocron on 2006-03-02
Well I'm encountering the exact same problem.  I got my Ubuntu discs yesterday and figured I'd try the Live CD first before deciding to bite the bullet.  That didn't work so I figured maybe I'd have better luck if I just bit the bullet and installed (the computer I installed to isn't used much anymore)... only to run into the same problem.  

In both instances, I'd get through the boot process with the Ubuntu logo and the initialization process only to be met with a black screen with a white "_" in the upper left hand corner of the screen that doesn't blink or anything.

I tried CTRL+ALT+F1 to switch to the shell... to no result.  The only thing that worked was holding the power button in... which rebooted my computer.

I'm sure this is a graphics-hardware related problem because if I use GRUB to boot in recovery mood, I'm able to login to the system using the username/password I set during installation and gain access to BASH.

However, from here, I'm clueless as to how to proceed.  I am a total linux noob and don't have the foggiest idea as to how to get this to work.  I've browsed assorted threads on this forum and I'm positive the problem can be solved by modifying the X-Windows configuration file... but how one goes about doing this and what modification(s) need to be made are unknown to me.

My system configuration is as follows:

Intel Celeron 633MHz
256MB RAM
15GB Hard Drive (guided-partitioned as 649MB swap / 14.4GB ext2 during install)
SoundBlaster Live! Sound Card
ATI All-in-Wonder VE PCI Video Card (based on the Radeon 7500 chipset)

I also checked my system BIOS and the video display device is set to PCI (which is what I'm using).  I don't have the option to disable the onboard video.

Any help here would be appreciated.  :)

---

### Post by neocron on 2006-03-02
Ok... here's an update:

I used the following command at the BASH prompt (after logging in):

sudo dpkg-reconfigure xserver-xorg

entered my password (same as the username/password I set during installation) and was taken to the X Windows configuration program.  At this point, it prompted me if I wanted to auto-detect my video card, which I selected Yes.  It automatically detected Intel 810 Graphics Controller (my onboard video chipset).  It also prompted me for the physical BUS location of the card in decimal format.  The instructions said I could use the command "lspci" to determine the physical BUS location of the card, but warned me "lspci" returned the location in hexadecimal values rather than decimal values.

I quickly went through the rest of the configuration program and when I was back at the prompt, I ran "lspci" and came back with the following results (only listing the VGA controller entries btw):

0000:00:01:0 - VGA compatible controller - Intel Corp 82810 CGC

0000:01:0e:0 - VGA compatible controller - ATI Technologies inc Radeon RV200 QW (Radeon 7500)

Now in the X Windows configuration program, it auto-detected the Intel 810 controller to be at 0:1:0 (which is the physical location of the controller in decimal format).  

What is the decimal format for 01:0e:0 (which is the physical location of my ATI video card)?  If I can figure that out, I'm pretty sure that'll solve my problem.

Thanks in advance.

---

### Post by neocron on 2006-03-03
Okey dokey!

Fixed the problem.  :)

Compliments of the Decimal to Hexadecimal Conversion Chart located at:

[http://www.ster-ling.com/ww1/dectohex.htm](http://www.ster-ling.com/ww1/dectohex.htm)

I was able to convert the hexadecimal location of my PCI video card into a decimal value, which is PCI:1:14:0.

I plugged that value into the X-Windows configuration program at the appropriate spot and restarted the computer.  Ubuntu loaded up perfectly.  That said, if your encountering the solid white "_" in the upper hand corner of the screen when u try to get into Ubuntu, follow the following steps:

1.  When GRUB starts, press ESC and select the Recovery Mode option to boot into the shell.
2.  Put in your username and password
3.  At the BASH prompt, enter lspci
4.  Write down the hexadecimal value for the video card you want to use.
5.  Goto [http://www.ster-ling.com/ww1/dectohex.htm](http://www.ster-ling.com/ww1/dectohex.htm) and convert the hexadecimal value into a decimal value
6.  At the BASH prompt, enter sudo dpkg-reconfigure xserver-xorg
7.  When asked to auto-detect your video card, say "NO"
8.  Enter the type of video card you have (example, "ati")
9.  When prompted, enter the decimal value for the location of the video card (example, PCI:1:14:0)
10.  When prompted, enter the amount of memory the video card has.
11.  Follow the rest of the prompts.
12.  When the program saves the configuration and exits, restart your computer.

That should get you into the Ubuntu GUI.  :)

---

### Post by piggysmile on 2006-03-03
Thanks Neocron. My system with an NVIDIA video card is already working but the autodetection worked for me.

---

