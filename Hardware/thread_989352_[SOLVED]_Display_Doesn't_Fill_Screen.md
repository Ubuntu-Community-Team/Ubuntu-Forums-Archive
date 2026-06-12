---
title: "[SOLVED] Display Doesn't Fill Screen"
date: 2008-11-21
forum: Hardware
---

### Post by rich1939 on 2008-11-21
I was previously running Windows 2000 Pro on my Toshiba Satellite Proo 4600 Laptop and the display always filled the 14" screen. With Ubuntu 8.10, the display seems to believe that the screen size is only 11" and it appears centered on my 14" screen.

I've tried changing resolution, but that doesn't seem to have any effect...except that when I change to a lower resolution, the display shrinks even smaller on my screen.

My previous experience with changing screen resolution is that even though a lower or higher resolution is chosen, the display still fills the entire physical screen.

How do I get Ubuntu 8.10 to fill the entire physical screen. The highest resolution I can choose is 800x600, whereas the standard resolution for my Toshiba laptop is 1024x768.

Thanks in advance for any answers.

Rich1939****

---

### Post by Pantera116 on 2008-11-24
I have just resolved the same problem on a Toshiba Portege 7200
laptop , so hopefully i can help.

I have discovered that 8.10 makes use of Xrandr an extension to X. Now this system in your case has chosen default horizontal and vertical refresh rates that mean you are limited to 800 by 600.

You will need to have a look at Xorg.log in var/log. This log will tell you what the X system has probed, selected default values for and read from the xorg.conf file.

So the way forward is to edit the Xorg .conf to include Horizontal and Vertical refresh rates. These can then be
set at values which will enable the Xrandr configuration routine (on next reboot) to discover higher resolutions.
 
My Portege has a trident graphics card with 4 mb video ram and a
1024 by 768 panel. Original the best resolution was 800 by 600 at 60 Hz(with a black boarder all around). I changed the max horizontal refresh to 90 kHz and the Max vertical refresh to 85Hz. I now get 1024 by 768at 75Hz full screen.

Hope this helps

---

### Post by rich1939 on 2008-11-26
> So the way forward is to edit the Xorg .conf to include Horizontal and Vertical refresh rates. These can then be
set at values which will enable the Xrandr configuration routine (on next reboot) to discover higher resolutions

I should also point out that I'm using Ubuntu 8.10, just in case it wasn't clear.

I looked at my Xorg.conf file and it doesn't have any resolution information or refresh information. It seems only to be a generic file with no specific info at all for my computer.

Just where in the file do I add the refresh info, and how do I state it in the file (i.e., what section, subsection, and in what format)?

My display adapter is a Trident Cyberblade, and although There are downloadable Windows drivers for my Toshiba Sat Pro 4600, I don't know how or whether these could be used to achieve the 1024x768 resolution that the computer is capable of handling.

Thanks again for your response.

---

### Post by Pantera116 on 2008-11-27
The Windows drivers will be of no use to you. All that is going on is in order not to not damage your screen Xrandr has set
itself to standard SVGA settings.

So the Xorg needs modifing. See example of 'monitor' section of a Xorg.conf file

Section "Device"
Identifier "Trident Microsystems Cyber 9525"
Driver "trident"
BusID "PCI:0:4:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
[COLOR="Red"]HorizSync 28-90
VertRefresh 43-85[/COLOR]
EndSection

To your Xorg.conf just ad the 2 lines in red to the monitor section.

If you do check your Xorg.log file as i mentioned before it may well tell you the pixel clock in Mhz. For my Trident cyberblade e4 it was 112mHz so if your figure is the same or higher it will work with the above settings.

Good luck with it.

---

### Post by rich1939 on 2008-11-27
> To your Xorg.conf just ad the 2 lines in red to the monitor section.

Thanks for your response. Interestingly, my /etc/X11/xorg.conf file doesn't contain [COLOR="Red"]ANY[/COLOR] of the settings you listed in your response. It doesn't list Trident at all and it just says the following:

```
Section "Device"
    IDENTIFIER     "Configured Video Device"
EndSection

Section "Monitor"
    IDENTIFIER     "Configured Monitor"
EndSection

Section "Screen"
    IDENTIFIER     "Default Screen"
    Monitor        "Configured Monitor"
    Device         "Configured Video Device"
EndSection
```

That's the complete file (except for the introductory comments). Somehow, when I installed Ubuntu 8.10, it either didn't recognize that the laptop had a Trident Cyberblade display controller. The laptop had a running version of Windows 2000 Pro on it, but I decided to let Ubuntu wipe out the entire (20GB) hard drive and install itself on the entire drive. The best resultion I can get currently is 800x600 and it's an 11" rectangle centered in my 14" screen.

I don't know whether it would help me to just copy the contents of your /etc/X11/xorg.conf file or look for some other answer.

Any suggestions?

[COLOR="Red"]Rich1939[/COLOR]

---

### Post by Pantera116 on 2008-11-28
What i sent before was a sample of a Xorg.conf file.

here is my full xorg.conf 

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Trident Microsystems Cyber 9540 (rev 52)"
	Driver		"trident"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Integtrated LCD"
	HorizSync 28-90
	VertRefresh 43-85
	#Modeline	 "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
	#Option		"PreferredMode" "1024x768_60.00"
EndSection

Section "Monitor"
	Identifier	"VGA-0"	
	Option		"Ignore" "true"
EndSection

Section "Screen"
	Identifier	"Screen 1"
	Monitor		"Integtrated LCD"
	Device		"Trident Microsystems Cyber 9540 (rev 52)"
EndSection

Now what you should check on is your BusID for the graphics card.
As root run lspci in a terminal. You should see on what PCI channel your trident graphics card is. If this differs from my xorg.conf file entry change it.

Another good link for you to look at is 

[http://ubuntuforums.org/showthread.php?t=904690](http://ubuntuforums.org/showthread.php?t=904690)

I should say that i am running Xubuntu 8.10 with lxde as the default desktop, as this is very lightweight, as the portege laptop is 600 mhz P3 and 192mbytes. It now rarely uses the swap
drive which was heavily used with XFCE.

Hope this finally resolves your problem

---

### Post by rich1939 on 2008-11-28
> What i sent before was a sample of a Xorg.conf file.
here is my full xorg.conf 

Thanks very much for your complete reply. I had played around with changes to my xorg.conf file with only minimal success. The /var/Xorg.0.log file showed that although the installer recognized the Trident 9950 LCD monitor that had 1024x768 resolution, it was unable to create an xorg.conf file that contained any reference to that product (as I pointed out in my earlier post).

My changes to my xorg.conf file showed a full size splash screen, but then when the GUI came up it scaled back down to the 800x600 resolution.

After plowing through a bunch of Ubuntu documentation I came across the description of "xrandr --newmode..." and a utility (whose name I now forget) that would propose a Modeline command that could be used. I used it and it gave me a new Modeline that I applied using "xrandr --newmode ..." and, lo and behold, that added a bunch of new entries to the Display Configuration menu, including 1024x768. I tried the new setting and it worked! (I only wish that I could find the reference to the utility that created the Modeline entry for me...but I couldn't find it again for this post.

My only problem then was that the xrandr command was only temporary, so I looked for ways to make it permanent, the simplest of these was to add the "xrandr --newmode..." command to my .profile file. I did that and rebooted. and was successful in getting my preferred resolution when the GUI reappeared.

I know that adding the proper sections to my xorg.conf file would be preferable and maybe in the future I will play around some more with that...but for the time being, I now have a full screen display at 1024x768! :popcorn:

I want you to know that you have helped me so very much to continue to have a positive attitude about solving my problem, and I appreciate your input no end.

My Ubuntu laptop was one that was gathering dust in the closet, so now it's a full-fledged addition to my arsenal. I'm very happy and plan to start doing some development once I reacquaint myself with Linux (I used Unix in the '70's) and the development software and interfaces. If I come up with anything useful, I'll be sure to submit it to the community.

Thanks again and very best wishes to you and yours in this holiday season.

---

### Post by Pantera116 on 2008-11-29
Very pleased to hear you finally sorted it out.

Iam sure i have seen reference to adding modeline to .xprofile file.

Couldnt find mine! 

I get the impression that the introduction of Xrandr has caught a lot of people out.

I think there is a Xrandr manual page. Iam sure it was there that i saw reference to the xorg.log file. It was looking though that which i found most useful. 

I produced a spreadsheet to work out the horizontal refresh rates at different resolutions and vertical refresh rates. This also allowed me to be sure that i would not exceed the pixel clock.

I really wanted to get the screen issue resolved as xubuntu got the zyxel g202 usb wireless dongle to work out the box and drop slickly back to wired lan if disconnected.

The fact that we are now succesfully able to install a linux distro on such ancient laptops and get a full functional stable and user friendly machine is a testament to how far linux has come with its hardware support.

I have seen significant progress in the 2 1/2 to 3 years that i have been using linux.

I currently have the following linux boxes

suse 10.2 - email PC, online ordering, dvd burning
pclos mini me - general surfing, cd ripping and flac encoding
geexbox - flac file dukebox ftp from mini me 
suse10.3 - mythtv combined front and back end with 2x dvb tuners
suse11.0 - mythtv remote front end for viewing in lounge
xubuntu - on laptop 

I use 2 KVM's so i only need 2 screens.

The laptop lets me view photos , do surfing wired or wireless, capture from camcorder,  watch dvd's, play soduku, transfer files to pendrives, listen to music, upload pictures from digital camera, do word processing and spreadsheets. Pretty incredible on 600mhz an 192mb ram.

Remember to keep having fun.

---

### Post by rich1939 on 2008-11-29
> I currently have the following linux boxes

suse 10.2 - email PC, online ordering, dvd burning
pclos mini me - general surfing, cd ripping and flac encoding
geexbox - flac file dukebox ftp from mini me
suse10.3 - mythtv combined front and back end with 2x dvb tuners
suse11.0 - mythtv remote front end for viewing in lounge
xubuntu - on laptop


WOW! I guess you're really into Linux. I installed SuSe 10.2 as a dual boot on a really fast (4GHZ) dual-processor Dell XPS computer a couple of years ago and I was just playing with Linux...and not doing very much with it. I was also backing up my Windows (work computer) using Retrospect, on the same hard drive, so I was getting to the point where I was running out of disk space...so, dummy that I am, I deleted the SuSe partitions without thinking and then nothing would boot!

I was really frantic and tried reinstalling Windows, and finally got it back running, but the computer was now so slow that I'm only using it as the print server for my network. I still have no idea why it's so slow, but I'm resolved to the situation as I have a fairly fast DELL XPS M1710 laptop that I'm now using for my work. I just upgraded the hard drive on the laptop from 100GB to 250GB by cloning the drive.

I've briefly thought about installing Linux on that machine, but my wife (whose important work files are on it) is against the idea...so I resurected the Toshiba Sat Pro 4600 and it's running just fine with Ubuntu.

I haven't really tried to do much with the Toshiba yet...just trying one thing at a time. I'm a writer and programmer, so I'm looking forward to doing some Linux development (and maybe writing another book...about Linux, of course!).

I've used iTunes a lot on my Windows machines, so I'm not sure how to proceed with Ubuntu with respect to music files/DVDs. One thing at a time.

I'm re-learning how to write shell scripts and then plan to get into GTK+ programming. I'm also a very big fan of TeX, so maybe I'll use that as my typography tool. I've downloaded all of the TeX and Metafont utilities...so I'm set up to use those.

My only Unix/Linux editor experience has been with "vi", so I'll either continue to use that or get acquainted with some of the newer GUI-based editors in Ubuntu.

Anyway...a long post and lots of thanks to you for all your help and support.

Best regards,

Rich

---

### Post by Pantera116 on 2008-11-30
Rich
One last thing, I suppose this post should now be flagged as solved.

Regards

Pantera116

---

### Post by rich1939 on 2008-11-30
> One last thing, I suppose this post should now be flagged as solved.


Definitely...but the only way I can think to do so is to put (SOLVED) in the title of my reply!

As a newbie, there's a lot I still need to learn. :)

Rich

---

### Post by Barking Spider on 2009-02-21
This utility did the trick for me:

[displayconfig-gtk]("http://www.phoronix.com/scan.php?page=article&item=814&num=1")

When you set it for 1024x768 at 60Hz and run test it gives an error but if you just hit 'ok' it resets the screen just fine.

Edit: Scratch that, it doesn't save between boots.

---

### Post by withnail420 on 2009-03-10
Hi, I know this hasn't been active for a while, but it was the only thread I could find on this subject.
I have the exact same laptop and problem as the original poster, and am at my wits end to find out how this is fixed.

Seeing this as "solved" when the solution was "I found a program to fix this - can't remember what it is!" was...unhelpful to say the least.
I didn't have this problem in earlier versions of ubuntu so i loaded up the live cd and copied the xorg.conf section about the monitor over...didn't do a damn thing.

hopefully the original poster will see this and come back and help, or anyone reading this might have an idea.
I tried everything already mentioned.

the name of that program would be useful, it must still be there so it's findable.
thanks in advance

---

### Post by withnail420 on 2009-03-11
Found solution on my own, posted in that thread, posting here....

Well, I managed to fix it.

It was nothing to do with KDE settings, as I suspected. I verified this by dropping to login, then killing kdm (the login manager) and starting X.
Still had the same problem.
After copying the monitor, screen, and video device section of xorg.conf from a copy of ubuntu 6.06 (when the screen worked fine) over, and still nothing, I gave up, backed up the old xorg.conf to xorg.conf.old, and just stuck the years old one in there.
And it bloody worked.
Going to post a copy of that config file here and to the old thread that claimed "solved" so that next time someone with this laptop comes across it, they won't have to mess around for three days like me.

Remember, only use this xorg.conf file if you have a Toshiba Satelite Pro 4600. Otherwise god knows what may happen.

-----------------------------------------

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Trident Microsystems CyberBlade/XP"
        Driver          "trident"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Trident Microsystems CyberBlade/XP"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection

        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

---

### Post by rich1939 on 2009-04-17
> **rich1939 said:**
> 
After plowing through a bunch of Ubuntu documentation I came across the description of "xrandr --newmode..." and a utility (whose name I now forget) that would propose a Modeline command that could be used. I used it and it gave me a new Modeline that I applied using "xrandr --newmode ..." and, lo and behold, that added a bunch of new entries to the Display Configuration menu, including 1024x768. I tried the new setting and it worked! (I only wish that I could find the reference to the utility that created the Modeline entry for me...but I couldn't find it again for this post.

My only problem then was that the xrandr command was only temporary, so I looked for ways to make it permanent, the simplest of these was to add the "xrandr --newmode..." command to my .profile file. I did that and rebooted. and was successful in getting my preferred resolution when the GUI reappeared.


Just to finalize this, the "utility" I used to create the "modeline" was **cvt**, which I executed as follows:

```

cvt 1024 768 60
```

which created the appropriate modeline that I appended to the ```
xrandr
``` command that I placed into my .profile file.

I hope this clears up any questions about how I solved my screen resolution problem on my Toshiba 4600 laptop.

---

