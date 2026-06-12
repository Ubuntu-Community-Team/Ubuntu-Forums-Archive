---
title: "Ubuntu Live Cd Help"
date: 2005-10-20
forum: Hardware &amp; Laptops
---

### Post by Kulluminatii on 2005-10-20
I just recieved two cds that I ordered from the ubuntu website. One is a install cd and one is a live cd. I wanted to try out Ubuntu first and tried to install the live cd. Everything was going correct and what looked like the last part of it before the cd ran it showed me an error:

Temporary Fail in Name Resolution

It said if I wanted to continue I clicked yes and then it showed me something like this

Cannot start the X server(graphical interface)

I took out the live cd and tried again, the same thing happened.

This is the first time i'm doing anything with linux so i'm pretty xcited:p And I hope that someone knows of a way to "fix" this.
oh and.....
[FONT="Fixedsys"][/FONT][COLOR="Red"][/COLOR]**HI!!!!!!!!**

---

### Post by PaganHippie on 2005-10-20
The error messages are unrelated.

The 'name resolution' error happened because you're either not connected to a network or Ubuntu doesn't know how to talk nicely with your network interface.  If all you want is to check out Ubuntu Linux from the live CD (which is exactly how I got started), that's perfectly safe to ignore.

The 'Cannot start X' message is a trifle more serious, though hardly fatal.  It means that Ubuntu doesn't recognise either your graphics chip or (more likely) your actual display hardware (I've seen this issue on some laptops).  Are you running on a laptop/notebook computer or a desktop PC?  Do you know, or can you find out, what your graphics hardware is, and what it's capable of?

If worst comes to worst, you can always run in text-only mode.  I rather doubt it will come to that (and there are plenty of folks out there more experienced in Linux & Ubuntu than I -- surely someone will have graphics-mode recommendations for you), but one of the beauties of Linux is the fact that it will work on just about anything.

---

### Post by Kulluminatii on 2005-10-20
[QUOTE=PaganHippie]The error messages are unrelated.

The 'name resolution' error happened because you're either not connected to a network or Ubuntu doesn't know how to talk nicely with your network interface.  If all you want is to check out Ubuntu Linux from the live CD (which is exactly how I got started), that's perfectly safe to ignore.

The 'Cannot start X' message is a trifle more serious, though hardly fatal.  It means that Ubuntu doesn't recognise either your graphics chip or (more likely) your actual display hardware (I've seen this issue on some laptops).  Are you running on a laptop/notebook computer or a desktop PC?  Do you know, or can you find out, what your graphics hardware is, and what it's capable of?

If worst comes to worst, you can always run in text-only mode.  I rather doubt it will come to that (and there are plenty of folks out there more experienced in Linux & Ubuntu than I -- surely someone will have graphics-mode recommendations for you), but one of the beauties of Linux is the fact that it will work on just about anything.[/QUOTE]I am using a desktop pc. The following is all i pretty much know/can find about my pc:

Pentium 3- 500mhZ
256mb
Elsa TNT2 Vanta-display thingy adapter:razz: 

and thats about all i know how to find about my pc, sad aint it?

thank you so much pagan for trying to help me, hopefully this is enough information to help you help me:D . I remember this one way of checking what your pc's specs was but I cant remember. Thanks once again

---

### Post by xmastree on 2005-10-21
[QUOTE=Kulluminatii]Pentium 3- 500mhZ
256mb
Elsa TNT2 Vanta-display thingy adapter[/QUOTE]That ought to be adequate. Is there a Network card in it? As Pagan said, the first error is no big deal. It just means you're not online.

Try it again, and when you 'cannot start X' do you get a command prompt?
Type **startx** then hit return. It probably still won't start but you may be able to see some error messages. If you do, note them and report back. The more information we have, the more chance we can fix it.

Oh, and **welcome aboard!** :)

---

### Post by Kulluminatii on 2005-10-21
I'm glad to be aboard:p 

I'll go do what you just said right now!

---

### Post by Kulluminatii on 2005-10-21
[QUOTE=xmastree]That ought to be adequate. Is there a Network card in it? As Pagan said, the first error is no big deal. It just means you're not online.

Try it again, and when you 'cannot start X' do you get a command prompt?
Type **startx** then hit return. It probably still won't start but you may be able to see some error messages. If you do, note them and report back. The more information we have, the more chance we can fix it.

Oh, and **welcome aboard!** :)[/QUOTE]
Yeah I get a command prompt before the cannot start x error. I tried it again and wrote down what looked important, here it is.

After the command prompt it took me to that Cannot start x server error, this is the everything that error said:
'I cannot start the X server. IT is likely that it is not set up corectly. Would you like to view the x server output to diagnose the problem?'

I clicked yes and this is what it showed(most of it that is):
X Windows System Version 6.8.2
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System Linux 2.6.10 i686[ELF]

after i clicked ok it showed me this.

'Would you like to view the detailed X Server output as well?'

what it showed me is the same that I typed above.

after i clicked ok once more it showed me this.

'I will disable this X server for now. Restart GDM when it is configured correctly'

After i clicked ok it took me to the command prompt where I typed startx like you said and yes it did show me more errors.

Hope this helps you guys determine the problem.

---

### Post by xmastree on 2005-10-21
[QUOTE=Kulluminatii]'I will disable this X server for now. Restart GDM when it is configured correctly'[/quote]Try this:
**dpkg -reconfigure xserver-xorg**

> I typed startx like you said and yes it did show me more errors.Those errors would be useful to know. Like 'no screens found' or something?

---

### Post by PaganHippie on 2005-10-21
Indeed, those error messages are diagnostic -- that is, they tell you a lot of information about what went wrong, & give hints about what to do to fix the problems, or at least where to look for a solution.

Please be as exact and detailed as you can when reporting error messages.

There will now be a brief intermission....
[My pet peeve as an IT help-desk person goes something like this:

  Me:  "Hello, thank you for calling {mudflap enterprises}.  How can I help you today?"
  Customer:  "My {thingamabob} is broken.  Fix it."
{pause as I bang my head against the nearest immovable object}
Me:  "Well, did you get any error messages?  What exactly happened when you tried to use {thingamabob}?"
Customer:  "Oh, I got some message, but I (deleted/don't remember) what it said."
{additional intermission as I tie a hangman's knot in the nearest handy rope and sling the slack over the nearest horizontal surface likely to hold my weight.}
]
... you get the idea.

Anyone who has *ever* worked in IT tech support, tell me you haven't been in this scenario!  I dare you!  ;)

Ah, but I digress....

Seriously, don't be afraid of being too verbose.  In computing, _***there's no such thing as too much information***_.  Tell *everything* that happened when you tried to start Xwindows.   Everything.  We won't bite.  Honest.  I promise.  :)

---

### Post by Kulluminatii on 2005-10-21
[QUOTE=PaganHippie]Indeed, those error messages are diagnostic -- that is, they tell you a lot of information about what went wrong, & give hints about what to do to fix the problems, or at least where to look for a solution.

Please be as exact and detailed as you can when reporting error messages.

There will now be a brief intermission....
[My pet peeve as an IT help-desk person goes something like this:

  Me:  "Hello, thank you for calling {mudflap enterprises}.  How can I help you today?"
  Customer:  "My {thingamabob} is broken.  Fix it."
{pause as I bang my head against the nearest immovable object}
Me:  "Well, did you get any error messages?  What exactly happened when you tried to use {thingamabob}?"
Customer:  "Oh, I got some message, but I (deleted/don't remember) what it said."
{additional intermission as I tie a hangman's knot in the nearest handy rope and sling the slack over the nearest horizontal surface likely to hold my weight.}
]
... you get the idea.

Anyone who has *ever* worked in IT tech support, tell me you haven't been in this scenario!  I dare you!  ;)

Ah, but I digress....

Seriously, don't be afraid of being too verbose.  In computing, _***there's no such thing as too much information***_.  Tell *everything* that happened when you tried to start Xwindows.   Everything.  We won't bite.  Honest.  I promise.  :)[/QUOTE]
:p , k i will do it again and remember to write down what errors showed up.

---

### Post by Kulluminatii on 2005-10-21
I tried startx again and this is what I got(for the most part):

Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o": No Symbols found



Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o": No Symbols found


Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o": No Symbols found 
(EE) No devices detected.

A couple lines after that I got this:

Fatal server error:
no screens found

A couple lines more down I got this:

X10:   Fatal IO error 104 (Connection reset by peer) on X server ":O.O"
         after 0 requests (0 known processed) with 0 events remaining.

Some of the 0 and O's mightve been mixed up but I know I got most of it down right. Hopefully this is enough...but then again....hope dont help much;)

---

### Post by Kulluminatii on 2005-10-21
Oh and I almost forgot to mention that after I did that I typed 
'dpkg-reconfigure xserver-xorg' in the command prompt and it said that it must be run as root.

---

### Post by Kulluminatii on 2005-10-21
Oh and I dont think i mentioned that this is the older 5.04 Hoary Hedgehog version i'm trying to use, not the breezy badger 5.10 one.

---

### Post by Ken-san on 2005-10-21
[QUOTE=Kulluminatii]Oh and I almost forgot to mention that after I did that I typed 
'dpkg-reconfigure xserver-xorg' in the command prompt and it said that it must be run as root.[/QUOTE]Quick mention: To run something as root, type "sudo" (without the quotes) before it; in your case, it would be like this:
sudo dpkg-reconfigure xserver-xorg
Hope it helps.

---

### Post by Kulluminatii on 2005-10-21
[QUOTE=Ken-san]Quick mention: To run something as root, type "sudo" (without the quotes) before it; in your case, it would be like this:
sudo dpkg-reconfigure xserver-xorg
Hope it helps.[/QUOTE]
Yes it does help a lot, thanks for telling me that:D

---

### Post by Kulluminatii on 2005-10-21
I guess the people before who have been responding havent logged on as of yet, anyone else know of anything?

---

### Post by MakubeX on 2005-10-22
If it's okay to ask in this Ubuntu Live CD help Thread, what is the default sudo/root/superuser password when the LiveCD is running? I was trying to set my resolv.conf file and I had not found it, thus I'm considering making a resolv.conf file but I don't know the password for the superuser privilege.

TIA!

---

### Post by Kulluminatii on 2005-10-22
I tried 'sudo dpkg-reconfigure xserver-xorg' and I think this is the only way to make the live cd work, it asked me loads of configuring questions which most of i didnt understand, i'm going to try it again and write down as much information as possible.

I got the stuff that sounded most important down, this is extremely long, so sometimes I might stop halfway if I need to go do something.

after I typed 'sudo dpkg-reconfigure xserver-xorg' this is what appeared:

                                             _Configuring XServer-xorg_

   Accept this option if you would like to attempt to autodetect the recommended x server and driver module for your video card. If autodetection fails, you will be asked to specify the desired x server and/or driver module. If autodetection succeeds, further debconf questions about your video hardware will be pre-answered.

   If you would rather select the x server and driver module yourself, decline this option. You will not be asked to select the x server if their is only one available.

Attempt to autodetect the video hardware? <Yes> <No>

after I chose yes this is what came up

   For the X Window System graphical user interface to operate correctly, it is necessary to select a video card driver for the X server.
Drivers are typically named for the video card or chipset manufacturer, or for a specific model or family of chipsets.
   Select the desired x server driver:
apm, ark, ati, chips, cirrus, cirrus_alpine, cirrus_laguna, cryix, fbdev, glide, glint, i128, i740, imstt, mga, neomagic, newport, nsc, nv, rendition, riva128, s3, s3virage, savage, siliconmotion, sis, tdfx, tga, trident, tseng, vesa, vga, via, vmware.

I chose vga because I heard that word alot, but I was unsure. After that this is what popped up.

   The X Server configuration file associates your video card with a name that you may provide. This is usually the vendor or brandname followed by the model name. Enter an identifire for your video card.
   VIA Technologies, Inc. VT8605 [ProSavage PM133]______________
                      <OK>
I didnt know what the hell that meant so I just left what it gave already and clicked ok. This is what was next.

   Users of PowerPC machines, and users of any computer with multiple video devices, should specify the BusID of the video card in an accepted bus specific format. 
   Example: ISA: 1, PCI: 0: 16: 0, SBUS:/iommu00,10000000/sbus00,10001000/SUNW,tcx02,80000
   For users of multi-head setups, this option will configure only one of the heads. Further configuration will have to be done manually in the x server configuration file, /etc/X11/XF86Config-4.
   Users of SGI Indigo2 XL machines, or machines with other buses not yet fully supported, should specify simply "1" here. (Not guranteed to work.)
   You may wish to use the "lspci" command to determine the bus location of your PCI or AGP videocard. Keep in mind that lspci reports the bus, device, and funtion numbers in hexadecimal, not decimal.
   Users of machines other than PowerPcs or SGI Indigo2 XLS with only 1 video car should leave this entry blank. <OK>

After I clicked ok this popped up, and on the line I put "1".

   Please enter the video card's bus identifier.
PCI: 1:0:0____________________________
                             <OK>

I added the "1" on the line and clicked ok.

   Typically, the amount of dedicated memory your video car has is autodetected by the X server, but some integrated video chips (such as the Intel i810) have little or no video memory of their own and instead borrow main system memory for their needs.
   It is perfectly acceptable to leave this paremter blank; only if your video car lacks RAM, or if the X server has trouble autodetecting the amount, is it necessary to specify the amount of video RAM
   Enter the amount of memory(in kB) to be used by your video card.
_____________
<OK>

I didnt put anything and clicked to continue.

   Rather than communicating directly with the video hardware, the X server maybe be configured to perform some operations, such as video mode switching, via the kernel's framebuffer driver.
   Use kernel framebuffer device interface?
<YES>   <NO>

I chose yes and this popped up.

   For the X server to handle your keyboard correctly, a keyboard layout must be entered. Avaiable layouts depend on which XKB rule set and keyboard model were previously  selected.
   Advanced users(not me!) can use any layout supported by the selected XKB rule set. If the xlibs package has been unpakced, see the /etc/X11/xkb/rules/ directory for available rule sets and the /etc/X11/xkb/symbols directory for available layouts.
   Users of U.S. English keyboads should enter "us." Users of keyboards localized for otehr countries should generally enter their ISO 31666 country code.
________
<OK>

I typed in us on the line above and clicked ok.

   For the X Server to handle your keyboard correctly, an XKB rule set must be chosen. Users of most keyboards should enter "xorg". Users of Sun Type 4 and Type S keyboards, however, should enter "sun".
   Advanced users can use any definde XKB rule set. If the xlibs package has been unpacked, see the /etc/X11/xkb/rules directory for avaiable rule sets.
   If you don't know what rule set to use, enter "xorg".
   Please select the XKB rule set to use.
   ____________
        <OK>

I typed in "xorg" and clicked ok. In the following I didnt write some parts that I found not necessary, like the part where it tells me what a mac keyboard is or stuff like that. So if it dont make too much sense, lemme kno.

   Users of U.S. English keyboards should generally enter "pc104".

I entered pc104 in and clicked ok.

   For the X server to handle your keyboard as you desire, a keyboard variant may be entered. Available varaints depend on which XKB rule set, model, and layout were previously selected.
   Many keyboard layouts support an option to treat "dead" keys such as non-spacing accent marks and diaereses as normal spacing keys, and if this is the preferred behavior, enter "nodeadkeys"
   Users of U.S. English keyboards should generally leave this entry blank. 
   Please select your keyboard varaint. 
__________________
      <OK>

I left this area empty because I am a user of U.S. keyboards, I skipped a few parts with some useless info and then I came to this.

   If you have a mouse attached to the computer, an attempt to detect it can be made, it may help to move the mouse while detection is attempted (also, the gpm program should not be running).
   If you accept and it fails, you will be asked this questoin again. You may attempt multiple times. If autodetection suceeds, further debconf questions about your mouse will be preanswered.
   Attempt moust autodetection? 
     <YES>      <NO>

I chose YES. Then it showed me this.

  Please choose your mouse part.
/dev/psaux,/dev/ttyS0,/dev/ttyS1,/dev/ttyS2,/dev/ttyS3/,/dev/input/mice,/dev/atibm,/dev/sunmouse,/dev/gpmdata.

I chose /dev/input/mice but did not know what I was doing. Then this popped up.

   Select the X.Org server modules that should be loaded by default.
GLcore, bitmap, ddc, dri, extmod, freetype, glx, int10, record, type1, v4L, vbe.

I chose GLcore, but also didnt kno what I was doing. This was the last part of it and after I hit enter it doesnt do nothing except show me the command prompt on the lower half of the screen.

---

### Post by Kulluminatii on 2005-10-23
I know that was alot, but you guys did tell me to write down as much info as possible:D .

I also had some questions and comments about what happened.

Questions-

How do I find out what my videocard is(model, brand, everything)?

What is xlibs?

How do I see the etc/X11 directories?

What is the configuration file?
Where is it?

Also I went to my cousins house and the live cd worked on his pc. It was a HP computer, pentium III, and he installed Windows XP on it(orginally was '98 i think). Too bad I couldn't stay for long and try out Ubuntu on his pc. His pc is also a year or two older than mine.

I have Windows '98 running on my pc and have tons of viruses/adaware/spyware on it. Could this change/affect the graphical interface? I thought that so I got rid of the adaware and spyware and the viruses I have quarantined. Hopefully this is enough information;)

---

### Post by Kulluminatii on 2005-10-24
By the way, how do I find out how many bits my pc monitor is. THe options are 1, 4, 8, 16, and 24 I think, and I generally pick 24. That is the last phase of reconfiguring xserver and after that the top screen shows that I picked 24 and on the bottom part is the command prompt, and then the pc just waits. I THINK that I have to type something after I did all that in the command prompt to make the live cd run, am I correct? If i am what is it?!??!?!?	](*,)

---

### Post by xmastree on 2005-10-24
Still trying? You certainly have patience!
[QUOTE=Kulluminatii]By the way, how do I find out how many bits my pc monitor is. [/quote]It's not the monitor, it's the video card. Depending on the amount of vram, higher bit depth may limit the resolution. 24 bit ought to be ok.

> I THINK that I have to type something after I did all that in the command prompt```
startx
```Is the command you're looking for. (If you've used Windows 3.x and DOS, think of it as typing **win** at the DOS command prompt)

---

### Post by Kulluminatii on 2005-10-24
[QUOTE=xmastree]Still trying? You certainly have patience!
It's not the monitor, it's the video card. Depending on the amount of vram, higher bit depth may limit the resolution. 24 bit ought to be ok.

```
startx
```Is the command you're looking for. (If you've used Windows 3.x and DOS, think of it as typing **win** at the DOS command prompt)[/QUOTE]
Thanks for the compliment(i think....) and the tips:p  Is it just 'startx' or do you type 'sudo-startx-' or something like that?

---

### Post by Kulluminatii on 2005-10-24
I should never get my hopes up[-o<.....because they always come crashing down:-({|=..well when it comes to this that is.

I typed in startx after I tried to configure everything to work and I got the same error I got last time I typed it in.

Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o": No Symbols found



Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o": No Symbols found


Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o": No Symbols found
(EE) No devices detected.

A couple lines after that I got this:

Fatal server error:
no screens found

A couple lines more down I got this:

X10: Fatal IO error 104 (Connection reset by peer) on X server ":O.O"
after 0 requests (0 known processed) with 0 events remaining.

Even though I might have some patcience....i'm reaching a breaking point.

---

### Post by xmastree on 2005-10-24
[QUOTE=Kulluminatii]Fatal server error:
no screens found[/QUOTE]Something is wrong with your x server config file. That's the one made when you do the xorg config thing.

I would take a look at your /etc/X11/xorg.conf file... But you only have a console so you're gonna have to use a console based editor. Not fun for a newbie...

Have a look at this (my xorg.conf):
```
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
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

[COLOR="DarkOrchid"]Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NoLogo"
EndSection
[/COLOR]
[COLOR="DarkSlateBlue"]Section "Monitor"
	Identifier	"NEC CI CT700"
	Option		"DPMS"
EndSection
[/COLOR]
[COLOR="SeaGreen"]Section "Screen"
	Identifier	"Default Screen"[/COLOR]
[COLOR="DarkOrchid"]	Device		"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"[/COLOR]
[COLOR="DarkSlateBlue"]	Monitor		"NEC CI CT700"[/COLOR][COLOR="SeaGreen"]
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection[/color]

[COLOR="Red"]Section "ServerLayout"
	Identifier	"Default Layout"
**[COLOR="SeaGreen"]	Screen		"Default Screen"[/COLOR]**
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection
[/COLOR]
Section "DRI"
	Mode	0666
EndSection

```
See the bit at the end, in red? That's where it gets the info for the window system to start up. Looking back through the file you should see the bits it's referring to. **screen** in green refers to the section just above, also in green. **Monitor** in blue refers to the section above, also in blue.
Basically, everything it looks for at the end ought to be previously defined. Something, somwhere in yours isn't matching up. It can't find the screen.
Mine's looking for a section with identifier "**default screen**". Likewise, that 'default screen' section is looking for sections **device** and **monitor**. If I were to alter something in there, like renaming the monitor from 'NEC CI CT700' to simply NEC then I would expect the same error you get.

If you're still here after reading that, you're going to be ok... It's rather confusing. Next thing is how to look at yours...
I would use **vi** but others have suggested **nano** is better for new users, so I'll recommend that instead.
**sudo nano /etc/X11/xorg.conf**
to open the file for editing. Try to look near the end, for the sections I mentioned. There will be a lot of commented out stuff there (lines starting with #) ignore that, delete them even, they make the file rather large and daunting. Everything referred to in the 'Server layout' should be present above it somewhere, and everything in the 'Screen' likewise. Try changing your video driver to **vga**. That's the line in mine that looks like: [COLOR="DarkOrchid"]Driver		"nvidia"[/COLOR] But make sure the identifier line above it matches the one in the 2Screen" section further down.

Good luck...


BTW, Congrats on getting the violin smiley to work, I've never managed to use that one. :???:

---

### Post by Kulluminatii on 2005-10-25
Thank you soooooooo....oooooo....ooooooo...ooooooo much xmastree:p 
Oh and I can help you with the violin thing, copy and paste my friend;)

---

### Post by MistaED on 2005-10-25
It looks like GLcore is playing up. I'd guess a quick fix for this could be what xmastree said and edit /etc/X11/xorg.conf

So Kulluminatii, try this exactly:

sudo vi /etc/X11/xorg.conf

The config will display like xmastree showed.

Go down until you get to Section "Module"

Find GLcore, and hit the insert key.

Type # in front of it to comment it out like so:

#GLcore

Once that's done, hit escape, then :w [enter], :q [enter]

Then run startx (without sudo)

Cross fingers! :)

Alternatively, where it specifies the Driver like xmastree said (under Section "Device") try each of the following for Driver:

"nv" "vesa" "vga"

nv is the open source nvidia driver which should work with your TNT/TNT2 video, if not, try vesa which should be considered a "bog standard" driver which should work on any PC's/x86 machines. If not, try "vga"

If you take the plunge and remove win98 for Ubuntu, you can use the good official "nvidia" driver with a simple apt-get download, and this will cure this problem and give you 3D acceleration. But that's another day :)

Good Luck

Edit: Ah, I see you got it to work. Nevermind :)

---

### Post by Kulluminatii on 2005-10-25
[QUOTE=MistaED]It looks like GLcore is playing up. I'd guess a quick fix for this could be what xmastree said and edit /etc/X11/xorg.conf

So Kulluminatii, try this exactly:

sudo vi /etc/X11/xorg.conf

The config will display like xmastree showed.

Go down until you get to Section "Module"

Find GLcore, and hit the insert key.

Type # in front of it to comment it out like so:

#GLcore

Once that's done, hit escape, then :w [enter], :q [enter]

Then run startx (without sudo)

Cross fingers! :)

Alternatively, where it specifies the Driver like xmastree said (under Section "Device") try each of the following for Driver:

"nv" "vesa" "vga"

nv is the open source nvidia driver which should work with your TNT/TNT2 video, if not, try vesa which should be considered a "bog standard" driver which should work on any PC's/x86 machines. If not, try "vga"

If you take the plunge and remove win98 for Ubuntu, you can use the good official "nvidia" driver with a simple apt-get download, and this will cure this problem and give you 3D acceleration. But that's another day :)

Good Luck

Edit: Ah, I see you got it to work. Nevermind :)[/QUOTE]
Nope, havent event started doing anything yet:D Probably will tomorrow when I have more time. Thanks for showing me this way also, Ill try to write down what xm told me to write down and then do what you told me just now. Thanks a lot guys, hopefully I can finally demo this dam thing8-[

---

### Post by xmastree on 2005-10-25
[QUOTE=Kulluminatii]Probably will tomorrow when I have more time.[/QUOTE]Just make sure you have plenty of coffee...

MistaED may have hit the nail on the head when he suggested commenting out GLCore. I'd do that first, if it's in there.

Wether you use **vi** or **nano** is up to you...

Of course, if you're running from the live CD, anything you do will evaporate when you reboot. If it's as simple as comenting out GLcore then that's not a big deal, just means you have to go through that ritual every time.

Once you decide to install it properly though, any changes will stick. Much better.


Something really weird occurred to me after I had written all that stuff about xorg.conf... It's like a recipe.

Consider a pizza. :) 

At the end of the recipe is an instruction to spread the sauce on the base, then put on the toppings. Base? sauce? toppings? What are those?
Look further up the file and you'll see a breakdown of the sauce (tomatoes etc...) base (dough...) toppings (sliced mushrooms, pepperoni etc...).
Read it in the right order and it all makes sense. Anything referred to at the end should already have been prepared.

Your computer is saying "Hey, I don't have any pepperonI!" :-({|=

---

### Post by Kulluminatii on 2005-10-25
Wow...that was deep and very well said:---)

---

### Post by Kulluminatii on 2005-10-25
I tried to do what MistaED said about GLcore and I didnt find that  under "Module" I looked over what xmastree had and he didnt have GLcore on his Section "Module" either. Whats up with that:confused:

---

### Post by xmastree on 2005-10-25
[QUOTE=Kulluminatii]I tried to do what MistaED said about GLcore and I didnt find that  under "Module"[/QUOTE]Well, if GLcore isn't there, don't comment it. :razz: 

Take a look at the last section, then make sure that whatever it refers to earlier is in place (make sure you have the pepperoni...).

What is it trying to use for the video driver? [COLOR="DarkOrchid"]the purple section in my example.[/COLOR] Try changing that like to nv, vesa or vga as MistaED suggested. remember to keep the **identifier** the same as the one referred to in the **Screen** section, or it won't find it.

---

### Post by Kulluminatii on 2005-10-25
k thanks:D

---

### Post by xmastree on 2005-10-25
If and when you do eventually get a desktop displayed, don't forget to invite me to the celebration party.
 \\:D/ \\:D/ \\:D/ \\:D/
I'll bet I could hear the W00Ts of delight from here...

I **really** hope you get it working, after all this.

---

### Post by Kulluminatii on 2005-10-25
[QUOTE=xmastree]If and when you do eventually get a desktop displayed, don't forget to invite me to the celebration party.
 \\:D/ \\:D/ \\:D/ \\:D/
I'll bet I could hear the W00Ts of delight from here...

I **really** hope you get it working, after all this.[/QUOTE]
Dont worry I wont forget, You helped me through all this, it will eventually work with all this stuff i'm learning from you and the other people. Now for the celebration party, what should be in the goody bags?#-o. If I could I would order some "entertainment"=P~

---

### Post by Kulluminatii on 2005-10-26
Omg...................................................................................................................................................................................................
[SIZE="7"]
ITWORKED!!!!!!!!!!!!!!!!!!!!!!!WOOOOOOOOOOOOOOOOOOHOOOOOOOOOOOOO!!!!!![/SIZE]
And its all thanks to you guys:p Now its time to celebrate
\\:D/\\:D/\\:D/\\:D/\\:D/\\:D/\\:D/

---

### Post by xmastree on 2005-10-26
Excellent! 
\\:D/ 
What did you eventually do to fix it?

---

### Post by Kulluminatii on 2005-10-26
changed the drivers name to "nv":D. Now i'm trying to figure out how to go on the internet..the games are pretty fun on it:p . Its awesome!, as soon as I get hang of how to work linux/ubuntu i'm going to install badger on this pc.

---

### Post by Kulluminatii on 2005-10-27
Been trying to configure the internet for a while on the live cd..dont know why its not working:-k. I tried to configure it through 'sudo pppconfig' from the terminal on the live cd and after i thought i configured it I saw no signs of it having effect on the live cd. I tried to set it from the live cd and when I activate it it still doesnt work. Hmm.........:???:

---

### Post by xmastree on 2005-10-27
Can't help here, having never used dial up with ubuntu.

I'd suggest you start a new thread about it.

---

### Post by Kulluminatii on 2005-10-27
Ok, thanks for all your help

---

### Post by wieck on 2006-04-25
[QUOTE=Kulluminatii]Ok, thanks for all your help[/QUOTE]

Hello everyone, i have read more or less what has been written here abt the live cd and i didn't understand a single thing, I'm sorry, I'm new in this, so I'll just say my problen, if anyone can help I'll be so grateful. 
I have the live cd and when I try to run it, I can't see anything. I know the thing is working because I can see until the LODING screen shows the bar complete, and I can hear the music that tells me the session is started but at that moment the screen goes black and i cant see anything, it says out of range. ive tried changing the resolution of the screen but it still doesn't work. 
Can you please give me an answer? But please in English I am not a computer expert... :confused: :confused: :mrgreen:

---

### Post by xmastree on 2006-04-26
Wow, I remember this one... Out of range, that sounds like it's trying to run your monitor at too high a resolution. you say you tried changing it? what did you do to change it?

One easy way is Ctrl-Alt-Plus or minus (on the right side, numerical keypad)

Waht's your hardware? Video card, monitor size.

---

### Post by pumpkinman on 2008-01-01
i also have just recieved the ubuntu cd ..ive tried to install t on different lap tops ..nothng appears..but it appears in {MY Computer} i wanted to try the live cd portion of it but theres so amny files in MY COMPUTER  i dont know what to do thanks steve

tring to nstall on laptop dell xps m140 2002 editon

---

### Post by xmastree on 2008-01-02
To try the live CD, put it in the CD drive and boot from it. It matters not what's already on the hard disk.
When you say you tried to install, and it appears in 'My Documents', what do you mean? To install it, you need a blank space on the disk. blank as in unpartitioned, not just free space.

---

