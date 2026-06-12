---
title: "OQO Model 02 installation issues"
date: 2011-09-10
forum: Hardware
---

### Post by cjcardinal on 2011-09-10
I recently acquired an OQO Model 02 off of eBay and absolutely love it.  I do not love that I can not manage to install a distro other than the following 8.10 installer that another OQO user put together a few years back

([http://www.oqotalk.com/index.php?topic=3287.0](http://www.oqotalk.com/index.php?topic=3287.0))

I have tried various things that I have found here via the search, as well as the very dated help on the oqotalk forums.  That Intrepid install works very well, but i do not like the fact that I am forced to use the "old release" repos.  The setup that i last had that worked was the above stated 8.10 install, with the xubuntu desktop package.  Everything on the OQO Model 02 worked out of the box to include WIFI, Sound (with minor tweaking) and even the wacom screen.

I have tried the alternate installer for 9.04, 10.04, and 11.04 to no avail.  I am met with the same issues that many other OQO owners are met with and that is the screen resolution issues that stop the install in it's tracks.

the following xorg.conf was posted years ago on the oqotalk forums which seems to be incorporated into the 8.10 install that i listed above:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"

	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"

	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"

EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/ttyS1"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"	

EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/ttyS1"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"	

EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/ttyS1"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"	

EndSection

Section "Device"
	Identifier	"openchrome"
  Driver	 "openchrome"
  Option	 "VBEModes" "true"
  BusID		 "PCI:1:0:0"
  Option   "ForcePanel"

Option   "SWCursor" "true"
EndSection

Section "Device"
	Identifier	"vesa"
  Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"

	Identifier	"panel"
	Option		"DPMS"
  HorizSync    30-92
  VertRefresh  50-85
  Modeline     "800x480" 40 800 864 928 1088 480 481 484 509 +Hsync
EndSection

Section "Screen"

	Identifier	"vesascreen"
  Device		"vesa"
	Monitor		"panel"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"800x480" "640x480"

	EndSubSection
EndSection

Section "Screen"
	Identifier	"openchromescreen"
  Device		"openchrome"
	Monitor		"panel"
	DefaultDepth	24
	SubSection "Display"

		Depth		24
		Modes		"800x480" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  Screen		"openchromescreen"

#Screen		"vesascreen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
        InputDevice     "stylus"	"SendCoreEvents"
        InputDevice     "cursor"	"SendCoreEvents"

        InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

In short, aside from the "friendly" installer that i linked in the beginning of the post, I am unable to get anything else installed, even with the alternate installer.  Any help or guidance would be greatly appreciated.

The specs of the device can be found on the wiki page [http://en.wikipedia.org/wiki/OQO](http://en.wikipedia.org/wiki/OQO)

---

### Post by Favux on 2011-09-10
Hi cjcardinal,

I gather that the video chipset uses the openchrome driver.  I just checked and it's in my Maverick (10.10) install by default.  Since it appears it can also use the VESA driver why can't you use that during the install and then switch over?  The "forensics" (i.e. my guess) of the xorg.conf indicates that's what was done originally.

However I do notice there doesn't appear to have been any release of the openchrome driver since Oct. 2009 (just prior to the Jaunty release):  [http://www.openchrome.org/](http://www.openchrome.org/)  So Lucid(10.04) is probably a better release to try.  Plus it's LTS.  Although I haven't checked if xserver-xorg-video-openchrome is in Lucid since it is in Maverick I would think it is.

That xorg.conf is a bit messy and could use some tidying up.

---

### Post by cjcardinal on 2011-09-10
> **Favux said:**
> Hi cjcardinal,

I gather that the video chipset uses the openchrome driver.  I just checked and it's in my Maverick (10.10) install by default.  Since it appears it can also use the VESA driver why can't you use that during the install and then switch over?  The "forensics" (i.e. my guess) of the xorg.conf indicates that's what was done originally.

However I do notice there doesn't appear to have been any release of the openchrome driver since Oct. 2009 (just prior to the Jaunty release):  [http://www.openchrome.org/](http://www.openchrome.org/)  So Lucid(10.04) is probably a better release to try.  Plus it's LTS.  Although I haven't checked if xserver-xorg-video-openchrome is in Lucid since it is in Maverick I would think it is.

That xorg.conf is a bit messy and could use some tidying up.

yeah i noticed that about the xorg.conf as well, but it seems that is what the user packaged along with that OQO Friendly Intrepid install.  I am not so savvy with that sort of thing so i wouldn't know where to begin.  I have seen the option of doing a xforcevesa CLI which allegedly addresses the graphics issues during install, but i have to say im not sure how to do that.  I have always used UNetbootin for my live disks on the linux, and windows side of the house, and sometimes the liveusb creator within Ubuntu as well.  I know that I can "tab" out of the install menu on the loader that unetbootin uses, but as far as the xforcevesa command, I dont know what to do.  I haven't tackled a CLI before, I have always used the live environment, or directly from unetbootin

---

### Post by Favux on 2011-09-10
Well we can always play with it later.

Anyway I don't think you have to drop to the CLI.  I believe I recall an option to use the "safe drivers" with the alternate(?) install (Lucid) CD.  Safe drivers would be a code phrase for the VESA drivers.  Or am I thinking of Gparted?

I'm assuming when you and the rest are saying the install doesn't complete you are saying X doesn't start?  And that's where it is blowing up?

---

### Post by cjcardinal on 2011-09-10
actually on a normal i386 desktop iso turned into a live disk...you cant get past selecting "install" or "try ubuntu" and im not so keen on the alternate installer, and due to the lack of a CD drive, the disk needs to be modified prior to boot to move past the CD drive detection.  I'll dig some of the links up and post the info and see if anyone has any suggestions

---

### Post by cjcardinal on 2011-09-10
[this]("http://billigites.blogspot.com/2007/08/ubuntu-linux-on-oqo-o2.html") includes some info on using the alternate cd method

[this]("http://billigites.blogspot.com/2007/08/two-weeks-with-ubuntufied-oqo-o2.html") is more info from the same user a couple of weeks after that particular install, mind you, it is from 2007

and this is generally the same result as I get from all installs (taken from the oqoasis forums)

> But I did a quick check trying to start the live systems 9.04 and 9.10(beta): both don't work :-(

Short results:
 ubuntu 9.04 (desktop i386): 
gets the kernel (2.6.28-11) loaded, but that's almost everything. 
Drops to the command line. Even the simplest things don't work (e.g. "more"), so I'm not able to dig the logs... 
Found that Via C7 not listed on the kernel supported CPU's (?)
 ubuntu 9.10 beta (desktop i386): 
drops to busybox, not finding initframfs

[This]("http://www.kiskeyix.org/articles/549") is fromma user that seems to have been successful with Natty:

> I used the grub2 on a USB stick method because it's just way easier to put ISOs on USB drives than to burn a CD or setup tftp+pxe boot for the OQO. In addition, this allows me to have 6 or more OSes on a USB stick plus a copy of SpinRite.iso!

The only thing to remember is when you choose Install Ubuntu Only (32 bit), you will need to update your CLI arguments for the kernel with:

... xforcevesa --
Which will cause the X server to run with VESA drivers instead of the SGI driver which chooses a weird resolution with the wrong refresh rate.

[This]("http://www.kiskeyix.org/wiki/os%3Aubuntu") is a blog from a user that includes some interesting information, a lot of which I am not so savvy on, so i'm wondering if even though it discusses an EOL release, if anything from this can be applied to a later release?
> Hardware Specific

oqotalk.com

OQO 02

 - install Ubuntu Hard 8.04 from alternate CD or using PXE boot ([[os:ubuntu#preseed|preseed]])
 - go to **Recovery Mode** and drop to a root shell
   - edit /etc/X11/xorg.conf ([[[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/222873|Bug](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/222873|Bug) #222873]]) 
   Section "Device"
       Identifier "Configured Video Device"
       Driver "openchrome"
       Option "VBEModes" "true"
       BusID "PCI:1:0:0"
   EndSection
   - create file /etc/modprobe.d/blacklist-oqo 
   blacklist via_agp
   blacklist agpgart
 - (optional) apt-get install ubuntu-mid
 - copy [http://www.oqo.com/unsupported/linux/wwan](http://www.oqo.com/unsupported/linux/wwan) to **/etc/ppp/peers** (make sure you change **sprint-connect** to **wwan-connect**)
 - copy [http://www.oqo.com/unsupported/linux/wwan-connect](http://www.oqo.com/unsupported/linux/wwan-connect) and [http://www.oqo.com/unsupported/linux/wwan-disconnect](http://www.oqo.com/unsupported/linux/wwan-disconnect) to **/etc/chatscripts**
 - edit /etc/rc.local and add a line **/usr/bin/pon wwan** so it starts your network at boot time
 - reboot
Configuration
Turn off graphic acceleration on netbook-launcher

 $> gconftool-2 --set /apps/netbook-launcher/force_low_graphics --type bool true
 $> gconftool-2 --recursive-list /apps/netbook-launcher
 force_low_graphics = true
 disable_single_instance = false
 monitor = 0
 volume_exclude_list = []
 $> killall netbook-launcher
 $> netbook-launcher &
 $> get fences failed: -1
 ** (netbook-launcher:13113): DEBUG: CONFIG: Forcing low graphics mode from GConf

---

### Post by Favux on 2011-09-10
Well if you want to edit the xorg.conf for a different release just comment (#) out the openchrome entry in "ServerLayout" and remove the # from the VESA line.

But anyway I think you can, or used to be able to, force VESA with the kernel boot option switch *xforcevesa*.  That's probably what you want.

---

### Post by cjcardinal on 2011-09-10
would you be able to explain to me how to do that in a little more detail?  I'm still cracking the surface of CL and things of the sort, so it would be greatly appreciated if you could start me off at the unetbootin options screen of the live disk, or ubuntu's live disk menu hahaha

---

### Post by Favux on 2011-09-10
Sorry, don't want to mislead you.  I'm no install guru so I can't give you step by step.  And I've never used unetbootin.  But from:  [http://sourceforge.net/apps/trac/unetbootin/wiki/commands](http://sourceforge.net/apps/trac/unetbootin/wiki/commands)  it appears it is possible:
> kernelopts

Specifies parameters to be passed to the kernel. Should be used with "method=custom", "kernelfile", and "initrdfile".

Examples:
unetbootin method=custom kernelfile="/home/geza/vmlinuz" kernelfile="/home/geza/initrd.img" kernelopts="ro splash quiet noapic"
Where you would use *xforcevesa* instead of e.g. *noapic*.  And for the CD version:  [https://help.ubuntu.com/community/LiveCDBootOptions#Common_Kernel_Options](https://help.ubuntu.com/community/LiveCDBootOptions#Common_Kernel_Options)

I tend look around until I find an option or something that works.  I've always found the Ubuntu installers pretty friendly.

A possibly useful link (but not for your current install question):  [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)  At least it mentions Lucid (10.04).  So someone got Lucid to install on this video chipset.

---

### Post by cjcardinal on 2011-09-10
> **Favux said:**
> Sorry, don't want to mislead you.  I'm no install guru so I can't give you step by step.  And I've never used unetbootin.  But from:  [http://sourceforge.net/apps/trac/unetbootin/wiki/commands](http://sourceforge.net/apps/trac/unetbootin/wiki/commands)  it appears it is possible:

Where you would use *xforcevesa* instead of e.g. *noapic*.  And for the CD version:  [https://help.ubuntu.com/community/LiveCDBootOptions#Common_Kernel_Options](https://help.ubuntu.com/community/LiveCDBootOptions#Common_Kernel_Options)

I tend look around until I find an option or something that works.  I've always found the Ubuntu installers pretty friendly.

A possibly useful link (but not for your current install question):  [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)  At least it mentions Lucid (10.04).  So someone got Lucid to install on this video chipset.

ok i will definitely need to look into this further tomorrow as it is 0215 in afghanistan, but i certainly appreciate all the help Favux!

---

### Post by cjcardinal on 2011-09-10
ah it seems that after the custom install, these options need to be made permenant per [this little how-to]("http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/")

I think im getting somewhere!

> Booting from CD

This section outlines how to workaround the video issue while booting from the CD. Your mileage may vary, depending on your video card, but hopefully this steers you in the right direction:

At the install screen press ‘F6‘ and insert one of the options below, depending on your hardware.
On first boot after install, press e to edit the GRUB menu.
Using the arrow keys to navigate, delete quiet and splash and again insert one of the options below.
Press Ctrl and X to boot.
The suggested options that I have found are hardware specific. Here is a list:

Older Intel video card: i915.modeset=1 or i915.modeset=0
nVidia: nomodeset
Generic: xforcevesa
Hopefully one of these options will get you up and running. Keep reading now to make these changes persistent!

GRUB

You’ll want to change these settings in GRUB so they’ll automatically be applied on each reboot. To do so, follow the steps below:

Edit the /etc/default/grub file. You will need Admin privileges to do so (sudo)
Find this line: GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash”
Replace with: GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash <option>”
For example, if I had an older Intel model, my GRUB configuration would read:

GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash i915.modeset=1&#8243;

Save your changes and you should get proper graphics on each reboot.

UPDATE: Based on a lot of user feedback I am reminded that you need to run ‘update-grub’ after you make changes.

obviously my main option being the xforcevesa, atleast to get booted up and address the resolution and xorg.conf issues i am assuming

---

### Post by cjcardinal on 2011-09-11
I am currently grabbing a fresh copy of xubuntu 10.04...Afghan internet is not exactly the best so it may be a while before i report back with the results of the CLI.  my post previous to this made a few things a little easier to understand so hopefully i can find some success


EDIT:  Scratch that-i realized i had a 3 day old ISO of Peppermint Two in my downloads so I am testing all of this out pending the creation of the Live USB.  Will be back with my results

Again, thanks for all the help

---

### Post by cjcardinal on 2011-09-11
ok i tried two different ways:

the first being deleting "quiet splash" and replacing it with "nomodeset" and this allowed me to load all the way to the install screens, but had a screwed up splash.  I went through the install, partitioned my 128gb Runcore SSD with my /, swap, and /home partitions, but after creating my user, time zone, etc, it started the formatting and i got an "installer crash" error.

the second attempt i did the same thing, except i used xforcevesa in the spot of the nomodeset.  same issue.

while this is further than I have been able to get thus far, obviously i need to keep digging.  I am currently throwing out the idea of Peppermint Two and creating a Lucid live disk and giving it another go

---

### Post by cjcardinal on 2011-09-11
Ok i have successfully installed Peppermint Two on the OQO Model 02 and am currently working on WIFI and sound.  when I get those two handled, i will mark this as solved and put up a how-two on the OP because i have spent the last month on this thing!

Thanks to those who assisted in pointing me in the proper direction!

---

### Post by Favux on 2011-09-11
Nice work!  :D

Put the HOW TO in a new thread as the first post.  That way it won't be buried and you can add the appropriate tags.  Then link to it from this thread.

---

### Post by cjcardinal on 2011-09-11
> **Favux said:**
> Nice work!  :D

Put the HOW TO in a new thread as the first post.  That way it won't be buried and you can add the appropriate tags.  Then link to it from this thread.

I shall

Im currently working on the wifi issue via another thread and once i hash that out, i will definitely do so

thanks Favux

---

### Post by cjcardinal on 2011-09-20
I have completed a how-to for my successful 10.04 installation.  thanks for all the help everyone

---

### Post by cjcardinal on 2011-09-23
Ok... as far as my "how-to" is concerned, I currently have 10.04 LTS installed, and running decently.  I converted over to Lubuntu and am running an almost pure LXDE...but I am not happy.  I mentioned the Intrepid install that a user put together, and while I was bored, I popped in the thumbdrive that is currently setup with that ISO.  I located a file called text.cfg and this is the contents:

```
default live
label live
  menu label ^Try Ubuntu without any change to your computer
  kernel /casper/vmlinuz
  append file=/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz via_agp.blacklist=yes xforcevesa=xforcevesa --
label live-install
  menu label ^Install Ubuntu
  kernel /casper/vmlinuz
  append  file=/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.gz via_agp.blacklist=yes  xforcevesa=xforcevesa --
label check
  menu label ^Check CD for defects
  kernel /casper/vmlinuz
  append  boot=casper integrity-check initrd=/casper/initrd.gz quiet splash --
label memtest
  menu label Test ^memory
  kernel /install/mt86plus
label hd
  menu label ^Boot from first hard disk
  localboot 0x80
```

I figured that since the option of
```
via_agp.blacklist=yes xforcevesa=xforcevesa --
```
seems to be the key in this instance, I would try to install Peppermint Two this way (I have not tried a fresh 10.04 LTS using these options).  There was no success.  I am going to assume that things are a little different with peppermint even though it is loosely based off of Ubuntu, but in the same token, it SHOULD work, right?  Forcing Vesa is the key graphics wise and blacklisting via_agp as well because I remember seeing that in the blacklist file when i was running that 8.10 install.  I will report with my success, or lack there of, after trying a fresh 10.04 install, but other than that I am really lost.  Why does that 8.10 install work with those options, but nothing later?

This is really becoming frustrating!

My reason for continuing all of this is that I really want to run ext4, and not ext3.  (I am stuck with ext3 due to the upgrade from 8.10 EOL all the way to 10.04)

I'll download a fresh 10.04 tonight and give it another go tomorrow.

---

### Post by Favux on 2011-09-23
Good luck!

Say did you try it with just the *xforcevesa=xforcevesa* i.e. without the *via_agp.blacklist=yes*?

You can go from ext3 to ext4 on an intact install.  I did that when I upgraded from Karmic to Lucid on my tablet PC. Couldn't see the point of Lucid with ext3.  I could maybe find my notes on that.  But as I recall it is not for the faint of heart.  I seem to remember running into problems that took a lot of tedious hand correcting with fschk.  "Yes I really want to do that" pressing OK and so on for a long time.  But I managed to recover it and succeed.

---

### Post by cjcardinal on 2011-09-24
> **Favux said:**
> Good luck!

Say did you try it with just the *xforcevesa=xforcevesa* i.e. without the *via_agp.blacklist=yes*?

You can go from ext3 to ext4 on an intact install.  I did that when I upgraded from Karmic to Lucid on my tablet PC. Couldn't see the point of Lucid with ext3.  I could maybe find my notes on that.  But as I recall it is not for the faint of heart.  I seem to remember running into problems that took a lot of tedious hand correcting with fschk.  "Yes I really want to do that" pressing OK and so on for a long time.  But I managed to recover it and succeed.

I will try momentarily... the fresh 10.04 is being made into a USB.  I will try xforcevesa=xforcevesa as well as the one above.  I WILL figure this out hahaha

---

### Post by stevencook17 on 2012-10-28
I just purchased an OQO Model 02 off of eBay and I am very interested in seeing if anyone made any progress on this issue or if this is a dead forum?

---

### Post by overdrank on 2012-10-28
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

