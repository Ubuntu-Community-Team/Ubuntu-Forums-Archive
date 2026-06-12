---
title: "Failed to start the X server.. HELP please"
date: 2007-08-06
forum: Hardware &amp; Laptops
---

### Post by fulio on 2007-08-06
ok well i already install ubuntu on my laptop which has a NVIDIA GeForce Go 6150 graphics. ok when i start up the laptop and it starts up ubuntu then it goes to a screen where it says "Failed to start the X server (your graphical interface). It is likely that it is not set up correctyl. Would you like to view the X server output to diagnose the problem?" before this didnt happen it first happen when i was installing berly onto it, and when i had to reboot it this is what happen.. can anyone please help me with this . THANKYOU!:(

---

### Post by nichipet on 2007-08-06
Boot into recovery mode, then try:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by fulio on 2007-08-06
it said xserver.xorg is not installed :(:(

 i went into recoverymode and i typed in wghat you said then it says llike

/usr/sbin/dpkg-reconfigure: xserver.xorg is not installed 
what do i do?

---

### Post by nichipet on 2007-08-06
From the recovery mode, try:

```

sudo apt-get install xserver-xorg xorg
```

If it says they are both installed already, try the above command with remove instead of install, and then do it with install again.

After all of that, try the directions from earlier (dpkg-reconfigure...)

---

### Post by fulio on 2007-08-06
it seems to freeze alot when i run recovery moode

---

### Post by nichipet on 2007-08-06
I understand your frustration. I've been using Linux for years and can't count the number of times I've run into problems like what you're experiencing.

However, adding three new threads asking for help on the same freezing problem, especially when you already have this thread (which contains many more details of what your situation is), is not going to help. It sometimes will cause people to ignore all of the threads and hope someone else can figure it out. Remember, everyone on here does this voluntarily. No one is paid to help troubleshoot. We'll be more than welcome to try and assist you, but I know that in my case, I am at work and am very limited in helping right now. Honestly, when I do this from work, I mostly use Google to find the answers.

As to the problem of freezing, it sounds like a hardware issue. If it is, you may need to replace a piece of hardware. If you have everything backed up, you could try reinstalling Ubuntu and you may find all of the problems are fixed.

---

### Post by fulio on 2007-08-06
how can i reinstall ubuntu? i got daul boots going on. vista & ubuntu. 
i also tryd to reinstall it by stickin the cd i download of the internet the iso. it boots then it just sticks in a black screen and it freezes right there.

---

### Post by Ub1476 on 2007-08-06
Boot into Vista, search for Computer Management, find the disk management (I believe that's what's it called), and then delete the data on were your Ubuntu partition is installed. 

Next, burn a new .iso file on the slowest speed possible (4x for CD) with the best burning program you have available. 

Now just install.

I also recommend the Computer Management app integrated in Vista for future use of partition creating/editing/whatsoever. It's really good:)

---

### Post by javaJake on 2007-08-07
Sorry, I've been watching this thread for a while, but I will jump in now. First his computer is saying that X crashed. X has to be there in order to crash. Then dpkg tells him "xserver.xorg" isn't installed - there is no xserver.xorg package, because it's xserver-xorg with a "-". :)



fulio, boot normally so that X crashes. This will recreate the errors you got and X will save a log in the process. Now reboot your computer into recovery mode so we can grab that log. Once a root terminal appears, write this command in:

```
cp /var/log/Xorg.0.log ~/Xorg.0.log
```

This will copy X's log into your home folder, saving any error messages that were made. This log will be very useful in determining your issue. Now upload that file from your home directory to this forum by attaching it when you make a new reply.

If you do not know how to get the file off of your computer without a graphical display, you will want a USB stick or floppy, or maybe even a Windows computer on a network. Let me know what you have at your disposal, and I'll provide instructions to download the file onto the device you mention.

---

### Post by fulio on 2007-08-09
i did what "Ub1476" said to do, i deleted the partition and restarted so i can install unbuntu agn. But instead it ****** up something on my laptop, i wasnt able to boot vista or ubuntu anymore.. saw i was like wow, so i tryd to install ubuntu instead cuase you know "VISTA sucks" and so it loads and goes through its phrases. and it says starting kernal then goes to a black screen then it freezes right there. any help?


P.s can someone provide me withe the best or  free iso burniing?

---

### Post by merlinus on 2007-08-09
[SIZE=-1][B][http://infrarecorder.sourceforge.net/](http://infrarecorder.sourceforge.net/)

-merlin
[/B][/SIZE]

---

### Post by Elliot.strumlauf on 2007-08-09
I have been having the same problems. I try to install Nvidia for Compizfusion on my NVidia Geforece Go 6150 laptop, and it keeps crashing.....

---

### Post by fulio on 2007-08-10
Doesnt that **** sucks?

---

### Post by iAndrew on 2007-08-10
What do you mean, freeze?

I've had black screens where it just stood there.

It was because my xserver wasn't configured correctly.

Did you try selecting vesa?

---

### Post by Elliot.strumlauf on 2007-08-10
Yeah, I selected VESA. I have to say, if Ubuntu ever wants to compete with the visually stunning Mac OS, it will have to do a WAY better job on NVidia support. This is, quite frankly, pathetic.

---

### Post by Licurgo on 2007-08-10
Hi guys>
I had the same problem but slighthly different. I installed Ubuntu edgy in a USB, it works fine, but this morning suddendly crashes and appears the same message (failed to start the X server) that you have been experiencing.
I use the Ubuntu at home and at work, so there are different machines, but thata was not a  problem before.
At start I selected disc and started as a live CD, then I explored the files and find the /casper-RW/var/log/Xorg.O.log and says:
X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux ubuntu 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Aug 10 10:53:28 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "SyncMaster"
(**) |   |-->Device "S3 Inc. VT8375 [ProSavage8 KM266/KL266]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.5
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(++) using VT number 7

I understands that the monitor and the video card are not the ones that I am using now, but How can I fixit??

---

### Post by javaJake on 2007-08-10
I understand everyone has a similar issue. However, if you do not match the first poster's complaint, please create a new thread, and link to it here if you want. We're concentrating on fulio in this thread only.

Sorry, but otherwise these forums would be an absolute mess.

---

### Post by fulio on 2007-08-10
i think its my laptop, cuase i messed around with the partition, and i think thats where i messed up after i deleted it cuaes i wanted to reinstall it

---

### Post by javaJake on 2007-08-11
> **fulio said:**
> i think its my laptop, cuase i messed around with the partition, and i think thats where i messed up after i deleted it cuaes i wanted to reinstall it

So, freeze-on-boot is the current issue?

Is the CD running while the screen is black? On my machine the splash doesn't show because it doesn't work (everything else does) so you just have to wait for the 15 minutes it takes for the CD to load.

---

### Post by Elliot.strumlauf on 2007-08-12
I bypassed the boot screen error with hitting f6 when the screen first shows up, and adding this to the end of the line that appears after f6 is hit:

linux noapci nolapic=off

I stll need help with NVidia drivers, they keep crashing my Xserver...

---

### Post by fulio on 2007-08-13
> **javaJake said:**
> So, freeze-on-boot is the current issue?

Is the CD running while the screen is black? On my machine the splash doesn't show because it doesn't work (everything else does) so you just have to wait for the 15 minutes it takes for the CD to load.

The ce doesnt spin like the orange light goess out. i waited for 10 mins last time it doesnt work. i thinik it has to do something with the partition.
the reason why i was running dual boots with vista and ubuntu. and i messed around with teh xserver cuase i was trying to install beryl, and i messed up all the way, so i thought if i deleted the partition it would delete the os. so when i booted agn it said something about error on grug or something. i couldnt boot to vista, so i fresh install windows xp and i tryd to load ubuntu its loads then goes to a black screen then it freezes.

---

### Post by Elliot.strumlauf on 2007-08-14
I also tried dual booting with ubuntu and Vista. What happens when you partition and install Ubuntu is that Ubuntu installs itself as the default boot: when you delete the partition, it looks for Ubuntu, can't find it, and gives you the Grub error nonsense. 

The Ubuntu live CD is what you are having problems with. I found out that our laptops do not have the adequate default drivers for Ubuntu's power setting, the apci. If you try launching the LiveCD without latering the commands, your CD stops spinning and nothing happens, you can wait all day and Ubuntu LiveCD will not load. try this:

hit f6 when you see the first Ubuntu screen that gives you a 30 second count down. type in at the end of the line

linux noapci nolapic=off.

---

### Post by fulio on 2007-08-15
--------------------------------------------------------------------------------

Elliot.strumlauf Scratch that TY ALOT IT FINALLY WORKS!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! THANK YOU!!
Would i always have to type that in if i boot up??

P.S can you also help me with the xserver , cuase i was installing beryl thats where i messed up and i dont wanna mess up this time and go through all this agn. it would really mean alot to me thankyou AGAIN!!!! <3<3<3<3<3<3
__________________

---

### Post by fulio on 2007-08-15
Elliot.strumlauf Scratch that TY ALOT IT FINALLY WORKS!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! THANK YOU!!
Would i always have to type that in if i boot up??

P.S can you also help me with the xserver , cuase i was installing beryl thats where i messed up and i dont wanna mess up this time and go through all this agn. it would really mean alot to me thankyou AGAIN!!!! <3<3<3<3<3<3

---

