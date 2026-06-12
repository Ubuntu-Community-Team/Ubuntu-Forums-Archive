---
title: "Using Hoary on old hardware?"
date: 2005-05-19
forum: Hardware &amp; Laptops
---

### Post by biodiesel-bri on 2005-05-19
Hi all-

I'm using Hoary on newer machines to great effect but I just installed it on an old AMD K6 366mhz processor with 192mb of RAM and it's just too slow.

I'm looking for ideas on getting it running.  For example, can I easily switch window managers to something like Ice?  Any kernel options I can pass through Grub?

Thanks,

-B
GoBiodiesel Cooperative
[http://www.gobiodiesel.org](http://www.gobiodiesel.org)

---

### Post by garnertr on 2005-05-19
Just a thought, b/c I'm going through something, what is the flavor of the distribution are you attempting to use 686 or 386 distro?

command:  uname -r
2.6.10-5-386

or something like that for some reason the 686 flavor is killing my laptop, but on the 386 flavor, it screams like a bandit... I probably need to do tweaking, but right out of the box... 386... :)

---

### Post by biodiesel-bri on 2005-05-19
I'm using the 386 flavor.  Your machine is screaming and you've got about 366mhz?  I wonder whats wrong with this machine?

---

### Post by metallikop on 2005-05-19
You might want to check out xfce4 as your desktop environment, GNOME is a bit heavy for a machine that dated.  If you're insistent on staying with GNOME try replacing metacity with sawfish, a more lightweight window manager.

---

### Post by biodiesel-bri on 2005-05-20
Thanks, I installed xfce4.  It did speed up the windowing a bit, but the machine is still unusable.  It must have taken 5 minutes to load OOo and once it came up there was a 1-3 second delay between pressing a key and seeing something show up.

I'm not expecting a miracle, but I thought there were some other options that might improve things.  I saw that some people reported 'usable' systems at 400mhz and double the RAM, so I'm wondering if RAM is the big issue.

---

### Post by SickTwist on 2005-05-20
I'd like to share a few tricks that I've learned to make Ubuntu more responsive on old hardware without giving up GNOME.  Some of these are mentioned in the Help guide that is on the System menu (System->Help->Desktop->System Administration Guide->Improving Performance).  One thing to keep in mind is that not all modern Linux desktop software will run smoothly on old hardware so you have to find a balance between how many features you need and how responsive you want to the desktop to feel.

**Desktop Configuration**
Here are some settings that can be configured in GNOME to enhance responsiveness.

[list]
[*]Use one panel with the absolute *minimum* number of applets.  (Right-click on the panel you wish to remove and select "Delete This Panel..."  Right-click on any applets/launchers you wish to remove and select "Remove From Panel".)

[*]Disable desktop wallpaper.  (System->Preferences->Desktop Background and select "No Wallpaper" at the top of the list.)

[*]Disable menu icons.  (System->Preferences->Menus & Toolbars and uncheck "Show icons in menus".)

[*]Change your Window border to something less resource intensive like "Atlanta".  (System->Preferences->Theme->Theme Details->Window Border->Atlanta)

[*]Use only one workspace.  (Applications->System Tools->Configuration Editor->apps->metacity->general.  Double-click on "num_workspaces" and set it to 1.)

[*]Run Metacity in reduced resource mode.  This will make windows appear as a simple wireframe when resizing them.  It will also turn off animations when minimizing windows.  (Applications->System Tools->Configuration Editor->apps->metacity->general.  Double-click on "reduced_resources" and set it to true.)

[*]Disable viewing icons on the Desktop.  (Applications->System Tools->Configuration Editor->apps->nautilus->preferences.  Double-click on show_desktop and set it to false.)
[/list]

**Applications**
Here are some lighter alternatives to those that ship with Ubuntu.  You may need to enable some additional Ubuntu respositories but all are available via apt-get/Synaptic.

[list]
[*]Leafpad - simple text editor (sudo apt-get leafpad)
[*]Abiword - word processor (sudo apt-get abiword-gnome)
[*]Gnumeric - spreadsheet (sudo apt-get gnumeric)
[*]Mozilla Thunderbird - e-mail client (sudo apt-get mozilla-thunderbird)
[*]Beep Media Player - digital audio player (sudo apt-get beep-media-player)
[/list]

Hopefully this will be of some help.  I have a Pentium II 333 MHz with 160 MB of RAM sitting next to me and it runs Ubuntu Hoary pretty well, (despite a problem with the [soundcard](http://www.ubuntuforums.org/showthread.php?t=12525)  ](*,) ).

---

### Post by SickTwist on 2005-05-20
[QUOTE=biodiesel-bri]Thanks, I installed xfce4.  It did speed up the windowing a bit, but the machine is still unusable.  It must have taken 5 minutes to load OOo and once it came up there was a 1-3 second delay between pressing a key and seeing something show up.

I'm not expecting a miracle, but I thought there were some other options that might improve things.  I saw that some people reported 'usable' systems at 400mhz and double the RAM, so I'm wondering if RAM is the big issue.[/QUOTE]

On my Pentium II 333 box running Hoary only 65 MB (of 160 MB total) is being used when I log-in.  If I start up Firefox and go to Slashdot it's still only using about 75 MB.

More RAM is never a bad idea but OpenOffice.org is very resource hungry.  You may want to consider trying another word processor instead.

---

### Post by deception on 2005-05-20
I run Ubuntu on a system almost identical to yours. I did a server install then apt-get install xorg-server and apt-get install x-window-system. Then I apt-get'ed XFCE4 and then machine runs very nicely, I'd use Abiword for word processing if I were you.

---

### Post by biodiesel-bri on 2005-05-21
Thanks, that did the trick!  It's running acceptably well now.

---

### Post by thomask on 2005-05-30
I am in desperate need of help with running Hoary on my old machine. I have an AMD K6-2/333 with an old PC Chips mobo, its a super 7 socket board with both AT and ATX power supply connections... I can get slackware to install, though I have grown to love Hoary (on a newer machine) but when I do the basic desktop install of  Hoary, it runs fine, untill it reboots. It says it has a problem finding hda1 (cant remember verbatim)... and then halts with a kernel panic. It found the drive fine during the install (done it 3 times to a similar result) but I think there is something I am missing. I think there is a command line it should be passed at boot, like pci=noacpi or something. one of the things i did notice was it said failure on initrd... is there something i can tell it so that it will work with my motherboard's ide stuff? I believe it is a VIA chipset...

I am running setup again now, with the expert mode on, I think I can add the command line interface somewhere in here... It just went through the Detect and Mount CD-ROM phase and told me it was unable to load certain modules --> 

ide-mod
ide-probe-mod
ide-detect
ide-floppy

was I supposed to enter a command line before one or all of these modules loads?
if so, any suggestions?

please help !

---

