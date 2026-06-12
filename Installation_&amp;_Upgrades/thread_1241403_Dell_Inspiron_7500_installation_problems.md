---
title: "Dell Inspiron 7500 installation problems"
date: 2009-08-15
forum: Installation &amp; Upgrades
---

### Post by edyb on 2009-08-15
I just received Ubuntu 9.04 desktop edition. Trying to install to my Dell Inspiron 7500 and getting errors. udev-d problems with modprobe message of some kind... related to PCI and some other hardware. Could you please help? Anyone? Looking forward to installing... I've waited anxiously for the CD in the mail and now disappointed that I can't get it to work!

---

### Post by overdrank on 2009-08-15
Hi and welcome, just a thought, how much memory is installed in the system.

---

### Post by edyb on 2009-08-16
Hi overdrank,

I was thinking about the same thing.... You are right... it has only 128 MB. I have now decided to download Ubuntu 6.06 Alternate Installation CD because it says I can run it on lower end systems. Also, somebody said it works well recognizing Wireless card out of the box easily. Here are my specs and my main goal. Please let me know what I need to do.

MY SPECS:

System is Dell Inspiron 7500 Pentium III 651Mhz 128MB RAM and 11GB hard drive and DVD/CD drive. I am currently using it to post this message. I have WinXP SP2 running on it, with Mozilla Firefox 3.0.11 and Microsoft Office XP installed. I use a Dynex Wireless Card in my PCMCIA slot. It connects to my wireless router using the latest security protocol WPA2-Personal with a Pre-Shared Key (PSK). I also have DVD X Player 3.0.

My GOAL:

The computer will be in the kitchen, plugged in mostly because it's heavy and battery is toast.... For my wife to be able to surf the net and watch a DVD with the kids. That's basically it. 

I can do that now with WinXP, but I thought I'd give Ubuntu a shot because I want to minimize the risk for viruses and trojans getting in. The system is too slow and sluggish when I run an anti-virus program on top (like AVGFree and Avast). I figure by running Ubuntu it will be less prone. Is this true?


Any help would be appreciated in helping me accomplish this with Ubuntu. Thank you.
Sincerely,
Edy

---

### Post by raymondh on 2009-08-16
Still with the Ubuntu flavor, I recently installed and tested crunchbang (after being disappointed with Xubuntu) on a P3, 500Mhz dell inspiron. Initially at 128 RAM and recently bumped to 512Mb.  At 128, it ran well enough for minimal needs (browsing, email).  At 512, I can multi-task better.

Just a .02-cent observation :)

---

### Post by edyb on 2009-08-17
Hi Raymond,

Thanks for the suggestion. I downloaded Crunchbang 9.04.01 and burned the ISO to a CD. When I boot and go to install, it also is hanging. Usually stops and I see 2 lights... the Caps lock and Scroll lock (or Numlock) lights blinking. I have no idea what is locking it up. 

I booted again, but now noticing a bootmenu letting me load either Windows or Ubuntu (whether the CD is in or not). Therefore it must have done something. However, even then when I select Ubuntu and choose Verbose mode for install, still ends up giving me problems. 

I tried booting with vesa VGA drivers and noacpi to be safe, and it is giving me these codes:

udevd-event[2540]: 'path_id /devices/platform/i8042/serio1/input/input6mouse1' abnormal exit

udevd-event[2106]: '/sbin/modprobe -b pci:v0000125Dd00001978sv00001028sd00000009Ebc04sc01i00' abnormal exit

Segmentation fault


I will try and see if I can get it to load from Windows somehow instead of booting it directly. Maybe the CD has something like the Ubuntu 9.04 CD which lets you set it up also from Windows.

Sincerely,
Edy

---

### Post by edyb on 2009-08-17
Update on my status....
 
I never got Crunchbang liveCD to work. However, I did get ubuntu 6.06 alternative CD to install (Dapper Drake?). Went through text mode for whole install, and now boots up to an OEM user with Gnome window manager.
 
I have a few problems though....
 
MOUSE
 
I want to disable the synaptics touchpad tapping, as I prefer to use the buttons to click. The tap is so sensitive that as I slide over things they get clicked. I read a few posts but my mouse shows up installed in xorg.conf as a generic mouse. There is no "Synaptics Touchpad" reference there. Also, the mouse setting panel in Gnome doesn't let me disable tapping. 
 
OEM
 
I am stuck in oem user mode. It said something during install about it being a temporary user, and after doing some config changes I can use sudo oem-config-prepare to eliminate it once I've added users. I'm not sure when and how to proceed.
 
GNOME
 
Finally, following your CrunchBang suggestion, if you think Openbox runs better than Gnome, is there any way to install Openbox instead of Gnome at this stage?
 
Thanks for your help.
 
Sincerely,
Edy

---

### Post by SpikeBoycom on 2009-08-17
Hi. I'm also having trouble installing Ubuntu 9.04 on a Dell Inspiron 7500. My system's specs are slightly different though. I've got a PII 400Mhz. It's an old clunker, but I want to use it as a backup PC. Anyway, at this point I've already installed Ubuntu, but it won't boot. It freezes if I use the regular GRUB startup option, so I use the recovery option and it gives me various error messages. The latest ones appear to be about the sound device. Did you run into similar problems? And if so, how did you fix it?

Thanks,
-Jon

---

### Post by raymondh on 2009-08-17
Edy,

Sorry to hear about the segmentation fault.  As you know by now, it's your computers' way of telling you "I can't go on ... I'm stopping" :).  I reckon it's got to do with compatibility.

What other options are offerred in the install (aside from noapic, etc).

EDIT : I see you've installed D. Drake.  For openbox (as opposed to gnome/metacity) ... see here:

[https://help.ubuntu.com/community/Openbox](https://help.ubuntu.com/community/Openbox)

Good luck.  Have fun.

---

### Post by raymondh on 2009-08-17
> **SpikeBoycom said:**
> Hi. I'm also having trouble installing Ubuntu 9.04 on a Dell Inspiron 7500. My system's specs are slightly different though. I've got a PII 400Mhz. It's an old clunker, but I want to use it as a backup PC. Anyway, at this point I've already installed Ubuntu, but it won't boot. It freezes if I use the regular GRUB startup option, so I use the recovery option and it gives me various error messages. The latest ones appear to be about the sound device. Did you run into similar problems? And if so, how did you fix it?

Thanks,
-Jon

Jon,

How does Jaunty [system requirements]("http://www.ubuntu.com/getubuntu/releasenotes/904") compare with your system specs?

What are the error messages?

As for sound, have you checked the [sound guide]("http://ubuntuforums.org/showthread.php?t=205449") sticky?

---

### Post by edyb on 2009-08-17
Hi SpikeBoyCom,
 
I also had problems until I downloaded the Ubuntu 6.06 Alternative CD iso and booted that. Forget about 9.04 if you don't have enough RAM. I only have 128mb of RAM so I went for 6.06 and it installed fine. My hard drive is 12 GB so I partitioned the primary /root as 10GB and secondary logical partition as /swap. Otherwise I followed all the on-screen instructions and kept the defaults. I also followed the suggestion for some Dell Laptops when it came to the PCMCIA cards to "exclude 0x88-0x8ff" or something like that (whatever they suggested). Not sure if it made a difference.
 
 During setup it asked me to setup password for root account, and also a new account username/password combo. But now I login using my username but password "oem", and I have problems adding new users (won't give me access rights). Also my touchpad is annoyingly sensitive clicking on things which I do not want to start. Now I'm trying to figure out how to get out of this OEM mode and get access rights back!
 
Sincerely,
Edy

---

### Post by edyb on 2009-08-18
Updates...

I managed to fix the Ubuntu OEM stuck-in-that-mode problem where I couldn't do anything due to lack of admin rights. When Ubuntu boots, instead of logging in through the graphical interface using username: "oem" and password (whatever I set up during Alternate CD install).... I switch to a text terminal directly using Ctrl-Alt-F1 and then login as "root". Once in "root" I am able to run "oem-config-prepare" which properly did what it had to do. THen I typed "reboot" at the shell prompt and it rebooted and went through asking me some questions on time zone and to set up a new account that has admin rights.

Now I can get into Synaptic Package Manager and properly do what I need to do.

Now on to the next task....

1. Still trying to fix touchpad sensitivity or turn off tapping
2. Getting Dynex Wireless PCMCIA card configured

-Edy

---

### Post by edyb on 2009-08-18
Success!!!!

I am using my Ubuntu 6.06 installation on my laptop to write this post through a wireless connection! First here are all the dead ends.... 1. I tried the native network configuration under System > Admin > Networking... hoping that the B43 kernel driver would work. I am using a Broadcom 4318 so it theoretically should have. My eth1 card was detected properly (PCMCIA Dynex wireless card). However, there was no WPA2 support. So then I disabled that, and instead installed network-manager Gnome.That seemed to make more progress but the "connection strength" bars were always at 0%. However, it looked as if it was trying to connect. 

Finally, I gave up and went the ndiswrapper way.... Made sure it was installed from the Ubuntu CD (using Synaptic Package Installer). Then I followed word for word the advice on the website [help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper"). First I blacklisted the B43 stuff as it says on that page. Then I took my Dynex Windows setup CD-ROM that came with the Wifi Card and copied over the 2 files to the computer... bcmwl5.inf and bcmwl5.sys. These are the Windows XP or 2000 drivers that Windows uses. Then I ran all the command-line commands in a terminal that it says to do on that page. 

Finally, I loaded up nm-applet again and this time it detected my network, and all of my neighbouring networks as well. Remember I have my wireless card disabled in the System>Admin>Networking area. 

Now I wonder if it will remember all this next time I boot up... or do I have to retype all these commands? The page above says if using nm-applet to configure then I should just edit the /etc/modules file and add the line with the word "ndiswrapper" to the end of it.

Will report back on progres... Lastly I need to fix this infernal touchpad sensitivity issue....

-Edy

---

### Post by edyb on 2009-08-19
UPDATED! Synaptics touch-click disabled! Also DVD/CD problems FIXED! Here's HOW:

FIRST: Wanted to disable touchpad tapping click (too sensitive). 
SECOND: Get CD/DVD to work properly

Followed the instructions here to get Synaptics entered into xorg.conf file:

[https://help.ubuntu.com/community/SynapticsTouchpad/Hardy](https://help.ubuntu.com/community/SynapticsTouchpad/Hardy)

Then I installed a few things, but not sure which of them worked... somehow it managed to do it. With my internet on, I typed the following at a command prompt:

sudo apt-get install xfree86-drivers-synaptics

A good discussion is found here:

[http://www.debuntu.org/2006/06/18/67-how-to-setting-up-touchpad-on-a-laptop-a-complete-guide/](http://www.debuntu.org/2006/06/18/67-how-to-setting-up-touchpad-on-a-laptop-a-complete-guide/)

Finally to get rid of the click I added to my xorg.conf file the lines:

Option "MaxTapTime"  "0"

(this is the section on InputDevice)

Basically, if you Google the above line it will show you some pages that display all the options you can put directly into xorg.conf. Like this:

Section "InputDevice"
   Identifier "Synaptics Touchpad"
        Driver "synaptics"
        Option "SendCoreEvents" "true"
 Option "Device" "/dev/psaux"
 Option "Protocol" "auto-dev"
   Option	"LeftEdge"      "1700"
 Option	"RightEdge"     "5300"
    Option	"TopEdge"       "1700"
 Option	"BottomEdge"    "4200"
 Option	"FingerLow"	"25"
 Option	"FingerHigh"	"30"
 Option	"MaxTapTime"	"180"
 Option	"MaxTapMove"	"220"
 Option	"VertScrollDelta" "100"
 Option	"MinSpeed"	"0.09"
 Option	"MaxSpeed"	"0.18"
 Option	"AccelFactor"	"0.0015"
 Option	"SHMConfig"	"on"
 Option	"HorizScrollDelta"	"0"
  EndSection
 

 Finally, I think this solved the issue....
 

 ln -sf /usr/X11R6/lib/modules/input/synaptics_drv.o  /usr/lib/xorg/modules/input/synaptics_drv.o
 

 That puts a symbolic link of the driver file into the proper directory. Then typing "synclient -l" works. Finally rebooting or restarting Gnome worked. I jumped to another term and logged in, restarted gnome completely by doing "/etc/init.d/gdm restart".
 

 WOOO HOOOO!!!!! No more annoying tapping-clicks and inadvertantly doing stuff I didn't want! Yay!

 

 

Then you don't need to load any gsynaptics package (which I had a difficult time with) and also the newer version.

In my quest to figure this out, came across some other nice pages:

[http://www.pcurtis.com/ubuntu.htm](http://www.pcurtis.com/ubuntu.htm)

With respect to getting the CD/DVD working, I was getting crashes with the default Movie Player TOTEM. It just would crash when inserting a DVD, or have errors. I finally managed to figure out that DMA was set to OFF on my drive. So I turned it on using the hdparm command, and then adding that line to the config file so it would always do it by default on reboot. Good page to start is:

[https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)

My settings are:

sudo hdparm -d 1 /dev/cdrom
sudo hdparm -d 1 /dev/dvd

I added this to my hdparm.conf file:

/dev/cdrom {
dma = on
}
/dev/dvd {
dma = on
}That seemed to help. I also managed to install VLC player to see if that would work better, which it did (once DMA was on). Also one post suggested gxine was better, so I installed that and it seems to be fine for viewing DVD's. 

So I successfully resolved the following problems over the last few days, by ripping my hair out and essentially Googling and reading up on various forums and pages on what other people ran into and how they seemed to resolve the problem:

1. First, trying to figure out how to even install Ubuntu... 9.04 didn't work (low mem), Crunchbang didn't work, Ubuntu 6.06 LiveCD didn't work... finally Alternate CD worked.
2. Then I had issues with oem account... couldn't get out of it, and limited rights. Finally resolved that by successfully launching oem-config-prepare command somehow.
3. Then issues with Wireless... got that to work using ndiswrapper and the CD that came with my Dynex wifi card for the drivers.
4. Then CD/DVD issues - needed to install other software and turn on DMA
5. Finally figured out the Touchpad. 

Why do we torture ourselves with this when I had WinXP SP2 running fine on the machine and did everything I needed above and more? We must all be masochistic...

-Edy

---

### Post by raymondh on 2009-08-19
> **edyb said:**
> 

Why do we torture ourselves with this when I had WinXP SP2 running fine on the machine and did everything I needed above and more? We must all be masochistic...

-Edy

:) Great learnings, I figure.

Congratulations Edy.  Happy Ubuntu-ing.

---

