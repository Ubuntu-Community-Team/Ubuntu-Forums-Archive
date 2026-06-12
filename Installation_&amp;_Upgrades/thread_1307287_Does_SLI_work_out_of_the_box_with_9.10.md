---
title: "Does SLI work out of the box with 9.10?"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by SirWeazel on 2009-10-31
Hello, i was wondering if sli will work with ubuntu 9.10 easily on a fresh install. I have 2 geforce 7950GT cards, but after some fooling around i could never figure it out on Ubuntu 9.04 so my simple fix was to take one out.  So I've been using 9.04 since it came out and have loved it except for my second card sitting on the shelf.  Before i do a clean install of 9.10 i am wondering if i should attempt to put the second card back in my box.  Anyone have any experience/tips for sli in ubuntu 9.10.  

Thanks in advance for any help.

---

### Post by TutonicMonkey on 2009-10-31
I worked for me with 185 restricted drivers..."out of the box" 
(ubuntu 9.10 x64) With 2 - eVGA 8800 gt SSC @ 1920x1200 @ 60 HZ 

I am Happy now GO UBUNTU!! :KS:p

My Specs:

MSI 750I MB
Q6600
4gb 1066 ram
2 - eVGA 8800 gt SSC
150gb 10K hdd
Creative Xf-I
Ubuntu 9.10 x64

[IMG]http://img.photobucket.com/albums/v734/tutonicmonkey/Screenshot-2.png[/IMG]

---

### Post by SirWeazel on 2009-11-01
Tutonic,
Cool thanks, i'll be putting my other one back in before i install.  But one other question.  How do u know they are working together in SLI configuration vs just two video cards installed and working seperate of eachother.  Is there an option somewhere? When i was trying to get it to work before i read you had to edit a config file somewhere otherwise they weren't working "together". Thank you for help.

On another note, (which i'll probably start another thread), but i noticed in your specs you have the x-fi card.  Do you have the "breakout box" with inputs and remote control and if you do, is it fully working. (I also have this sitting on a shelf in my closet. I couldn't get the breakaway box to work so i just put it on the shelf till the future.)  Thanks again.

---

### Post by autocrosser on 2009-11-01
I write a custom xorg.conf to setup SLI----PM me & I'll send the info to you--you will need to edit the section to match your hardware...

TutonicMonkey--check to make sure that you are SLI--there is a checkbox in the nVidia settingspanel to "enable heads-up display" If that is not there, you are just running 2 separate cards--not SLI. Take a look at the screenshots to verify....

---

### Post by TutonicMonkey on 2009-11-01
> **autocrosser said:**
> I write a custom xorg.conf to setup SLI----PM me & I'll send the info to you--you will need to edit the section to match your hardware...

TutonicMonkey--check to make sure that you are SLI--there is a checkbox in the nVidia settingspanel to "enable heads-up display" If that is not there, you are just running 2 separate cards--not SLI. Take a look at the screenshots to verify....


Ahh I think you are correct...  I do not have this option in Miscellaneous.

As for the X-FI - It was recognised during the initial install and I can see and select it in sound prefs "hardware" and "Output" but I hear no sound.  My USB headset and internal sound work fine.  Only noise I hear from the X-fi is during the Ubuntu loading window ... sort of a clicking noise. "breakout box" I asume you mean the front panel thing - I never used it so im not sure. I have this sound card..[http://support.creative.com/Products/ProductDetails.aspx?catID=1&CatName=Sound+Blaster&subCatID=208&subCatName=X-Fi&prodID=14065&prodName=X-Fi+Platinum&bTopTwenty=1&VARSET=prodfaq:PRODFAQ_14065,VARSET=CategoryID:1](http://support.creative.com/Products/ProductDetails.aspx?catID=1&CatName=Sound+Blaster&subCatID=208&subCatName=X-Fi&prodID=14065&prodName=X-Fi+Platinum&bTopTwenty=1&VARSET=prodfaq:PRODFAQ_14065,VARSET=CategoryID:1)

[IMG]http://img.photobucket.com/albums/v734/tutonicmonkey/Screenshot-1-1.png[/IMG]

---

### Post by autocrosser on 2009-11-01
OK--the other place you look at is the other screenshot I posted--note that it will say X Screens:  Screen0(SLI) if you are "really" SLI---If not, post back & I'll set both of you up with the custom xorg.conf I use....

You will need to define the card slot you are using as your "main" card for SLI to work properly.....For that I will need to see your Xorg.0.log---located in /var/log--just copy the log to your desktop & right-click on it--then "compress" it as a .tar file. You can PM me if I don't get back here right away......

---

### Post by SirWeazel on 2009-11-02
Cool, thank you. I'll probably PM you in a couple days when i go to install. Was going to do it tonight, but i ran out of time.  But let me ask this.  With Ubuntu 9.04 (currently running), when i had both cards in the computer and i enabled the Nvidia drivers, when it tried to reboot all i got was a terminal screen and  i was stuck... So when i go to install 9.10 should i do my clean install with both cards in the computer and then do u think i'll still be able to boot after i enable of drivers... or should i edit the xorg.conf file before i enable the drivers... or can i enable the drivers and if it doesn't work use the boot cd to edit xorg.conf file/email it to you?

Sorry if this long rambling question doesn't make any sense.  I'm just trying to prevent problems from occuring. It's difficult to look up solutions when your comptuer is down.

Thank you both for your help.

---

### Post by autocrosser on 2009-11-02
It's OK--Short answer--Install with one card in--get the nVidia driver installed, make your edits to xorg.conf, shut down & install the other card & bridge--then reboot. You "might" be able to install with the second card & bridge in your unit (I guess that TutonicMonkey was able to), but I don't bet on it......

As for the Xorg.0.log--you can send it any time you want--you just need to have it available just before you are ready to reboot & install the second card--I only need the slot address for your "main" card & card type you are using to set up a conf for you....It takes 10 minutes or so to mod the file to your specs.....

Any other questions--just ask--Remember: there are no stupid questions--just answers..:D

---

### Post by Metal_Reign on 2009-11-06
I can't really comment about the out of the box part since i switched to 9.10 during beta and had to do a bit of configuration to get my 2 9600gt's to work, but once i got them going i could not be more pleased with the ease of use and stability 9.10 has provided on this my first standalone Ubuntu box. :grin: (edit. i did indeed have to install one card solo to begin with FYI, but i can't say if this is really necessary now since as i mentioned i did this all during beta)

---

### Post by sum1nil on 2009-11-07
Hi! Love Ubuntu. 
How do I get rid of the SLI Hud (now that I know I am running in SLi)? 
It seems to be hanging/displaying in there although I unchecked the box. 

Thanks.

---

### Post by autocrosser on 2009-11-07
Have you logout/in again? The HUD will persist with your current session.


> **sum1nil said:**
> Hi! Love Ubuntu. 
How do I get rid of the SLI Hud (now that I know I am running in SLi)? 
It seems to be hanging/displaying in there although I unchecked the box. 

Thanks.

---

### Post by SirWeazel on 2009-11-08
autocrosser, i did a fresh install of ubuntu 9.10 with both cards installed with the bridge.  After everthing was installed and updated, i enabled the video drivers and rebooted.  Then i ran "sudo nvidia-xconfig --sli=Auto" this command edited my xorg.conf file. I crossed my fingers and rebooted. With my surprise, (i thought i would have to edit busid's or something) everthing loaded correctly and i now have the option in my nvidia x server settings to enable sli. I have it enabled and as far as i can tell it is working. Next to xscreens it says (sli).  My other concern is i am running identical cards, but when looking at the performance levels (in xserver settings) that show clock speeds, one card reads slower clock speeds then the other. Is this normal, and do you think it is working correctly.

I would love to post pics to show, how did you capture your screen shots?  

Thanks for the help.

---

### Post by autocrosser on 2009-11-09
Use Accesories>Take Screenshot & "Grab current Window"--set the delay for whatever works for you--I set it for 5 sec & don't show cursor....

Glad Xorg config'd it ok for you--you might look at nVidia site for the current settings--could increase your performance--Also--I manually install a small app called NVdock(google-search it)--puts the nVidia settings in the Notification panel--also--you'll find NVclock in Synaptic to clock your cards....

Normally if you are running "Identical" cards with different BIOS setting you will see different clock speeds--That's normal & the driver will default to the lower speed of the two so the slower card is not overworked....

Good site for the Linux driver status:  [http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by SirWeazel on 2009-11-09
I appreciate all the input. I'm trying to understand everything, so i know why something is setup up the way it is.  Now that i have sli enabled.  I've got just couple other questions.  Right now in my config file i have sli set to auto (which means the driver auto selects the rendering mode).  But do you think this is the best/optimal setting?  Or should i have it set to to AFR or SFR? I'm running a dell 32" monitor at 2560x1600.  Ex: when i am watching a youtube/megavideo or other type video online.  When i run it at full screen there are obvious slow downs when rendering the video.  If i run at a smaller resolution i don't have this issue, but when it is full screen i do.  This is making me think that something is not working correctly. I would think it would be smooth with both cards running. Here's a couple questions:

1. What do you think optimal settings should be? (auto/afr/sfr/aa)
2. Does heads up display have to be checked in order for sli to be working? Is this what is causing the words "SLI" and some lines to appear on my screen from time to time?

Thanks for the help, i'm trying to understand and comprehend so i "know" what i'm doing and not just blindly changing settings.  Once i think i have something figured out i read something somewhere which adds a twist to the mix.  Basically i have this once upon a time expensive hardware and i'm just wanting it used to its potential.

Specs by the way for any customizatin you think i should do: (asus a8n32sli-deluxe, 64FX proc, 2 Geforce 7950GT cards, Dell 32" LCD (forget wich model).

---

### Post by ed-koala on 2009-11-09
I'm quite interested in hearing the answers to your questions myself.  I wonder just what effect checking the sli hud box has on performance.

Also, as a duel video card system, I've YET to be able to upgrade a version without having to manually configure video settings just to be able to boot up to a GUI.  This is a really glaring problem that I expected to be fixed some time ago, yet still exists in 9.10 with nvidia restricted drivers and duel video.

That brings up a question ... if I upgrade to 9.10 (and I've tried once already and couldn't get video, again) ... what exactly should I edit before rebooting so my GUI/video will boot up?  Xorg.conf has always needed editing, is it possible to edit that before rebooting so it'll stick?

Thanks for the posts/answers, this thread helped me figure out my SLI that I've had questions about, and I'm almost ready to try an upgrade, if I could be sure it'll work without having to navigate the command prompt and hope I'm getting things right.

---

### Post by FOBioPatel on 2009-11-15
> **SirWeazel said:**
> autocrosser, i did a fresh install of ubuntu 9.10 with both cards installed with the bridge.  After everthing was installed and updated, i enabled the video drivers and rebooted.  Then i ran "sudo nvidia-xconfig --sli=Auto" this command edited my xorg.conf file. I crossed my fingers and rebooted. With my surprise, (i thought i would have to edit busid's or something) everthing loaded correctly and i now have the option in my nvidia x server settings to enable sli. I have it enabled and as far as i can tell it is working. Next to xscreens it says (sli).  My other concern is i am running identical cards, but when looking at the performance levels (in xserver settings) that show clock speeds, one card reads slower clock speeds then the other. Is this normal, and do you think it is working correctly.

I would love to post pics to show, how did you capture your screen shots?  

Thanks for the help.


I had Windows 7 RC installed; but only because Ubuntu 8.xx didn't let me use my dual nVidia 9800 GX2 cards in SLI mode (or at least in a way easy for me to figure out).

I took the dive into Ubuntu 9.10 and was rewarded with SLI. I followed the above steps with one exception.

1.) Installed Ubuntu.
2.) As soon as Ubuntu booted up I installed all the updates.
3.) Opened restricted drivers and the nVidia (185) [recommended] driver was Activated.
4.) Rebooted.
5.) Opened Terminal and typed:
> sudo nvidia-xconfig
sudo nvidia-xconfig --sli=Auto
6.) Rebooted.

Now I'm doing some additional twiddling; but I see "SLI" next to "X Screens" in the GPU 0, GPU 1, GPU 2, and GPU 3 in my Nvidia X Server Settings page.

"Enable SLI Heads Up Display" was not visible as an option to me before I did step 5, now it was there but not checked off. I am checking it off now; and about to reboot to see if that makes a difference.

Compiz was enabled; and for the first time I saw it say "Ubuntu" and then fade out when the desktop first loads up. Before I enabled the SLI Heads Up Display I experienced the "Screen Tearing" effect (wikipedia if confused), but it wasn't a showstopper. Just a weird thing to see, and it went away quickly. After logging out and logging back in everything was fluid.

Debating if I should enable "sync to vblank" or not... If I plan on installing Windows games like Warcraft 3 and Counter Strike Source will this improve or hinder my experience?

---

### Post by SirWeazel on 2009-11-15
FOBio, You have worded the steps nicely. I've been meaning to write it step by step (numbered) the way you did. That's basically the steps i took to get mine working. This is much simpler compared to previous versions (at least with a clean install).  I think people who upgrade are having to configure more than these steps. I wish i knew more, to help with other problems.  But there is so much info out there for older versions and info that contradicts itself that it gets confusing. I hope this thread helps people out for this release (9.10). I think Ubuntu is on its way making multiple video cards work with less setup (command line editing).

I'm interested in hearing answers to your questions.  I don't think you have to have "enable SLI Heads Up Display" checked to be using SLI. I think that function just draws SLI info/stats on the display. It didn't work very well for me, except when i was playing "Nexuiz" it showed SLI info/chart on the screen. Wasn't sure what it even meant so i unchecked the box.

Keep us posted, i'm interested to hear what you find out. I havn't tried playing any PC games yet, if i do i'll post what i expierence also.

---

### Post by TutonicMonkey on 2009-11-19
/var/log/Xorg.0.log
--------------------------------------------------------------------------

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server x86_64 Ubuntu
Current Operating System: Linux ubuntu 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=55dd31ea-75dc-424e-b478-dd99b029403a ro quiet splash
Build Date: 26 October 2009  05:19:56PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Nov 19 08:42:05 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No device specified for screen "Default Screen".
	Using the first device section listed.
(**) |   |-->Device "Default Device"
(==) No monitor specified for screen "Default Screen".
	Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0xb40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(!!) More than one possible primary device found.  Using first one seen.
(--) PCI:*(0:3:0:0) 10de:0611:3842:c806 nVidia Corporation G92 [GeForce 8800 GT] rev 162, Mem @ 0xf3000000/16777216, 0xb0000000/268435456, 0xf0000000/33554432, I/O @ 0x0000bc00/128, BIOS @ 0x????????/131072
(--) PCI: (0:4:0:0) 10de:0611:3842:c806 nVidia Corporation G92 [GeForce 8800 GT] rev 162, Mem @ 0xf6000000/16777216, 0xc0000000/268435456, 0xf4000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  185.18.36  Fri Aug 14 18:27:24 PDT 2009
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  185.18.36  Fri Aug 14 17:51:02 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 03@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 8800 GT (G92) at PCI:3:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 62.92.24.00.06
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 8800 GT at PCI:3:0:0:
(--) NVIDIA(0):     MTK Microtek 815C (CRT-1)
(--) NVIDIA(0): MTK Microtek 815C (CRT-1): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-1
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (90, 92); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(GPU-1): NVIDIA GPU GeForce 8800 GT (G92) at PCI:4:0:0 (GPU-1)
(--) NVIDIA(GPU-1): Memory: 524288 kBytes
(--) NVIDIA(GPU-1): VideoBIOS: 62.92.24.00.06
(II) NVIDIA(GPU-1): Detected PCI Express Link width: 8X
(--) NVIDIA(GPU-1): Interlaced video modes are supported on this GPU
(--) NVIDIA(GPU-1): Connected display device(s) on GeForce 8800 GT at PCI:4:0:0:
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(EE) config/hal: couldn't initialise context: unknown error (null)
(II) config/hal: Adding input device Power Button
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/hal: Adding input device Ideazon Zboard Gaming Keyboard
(**) Ideazon Zboard Gaming Keyboard: always reports core events
(**) Ideazon Zboard Gaming Keyboard: Device: "/dev/input/event4"
(II) Ideazon Zboard Gaming Keyboard: Found keys
(II) Ideazon Zboard Gaming Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Ideazon Zboard Gaming Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/hal: Adding input device Logitech Logitech USB Headset
(**) Logitech Logitech USB Headset: always reports core events
(**) Logitech Logitech USB Headset: Device: "/dev/input/event6"
(II) Logitech Logitech USB Headset: Found keys
(II) Logitech Logitech USB Headset: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech Logitech USB Headset" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/hal: Adding input device Ideazon Zboard Gaming Keyboard
(**) Ideazon Zboard Gaming Keyboard: always reports core events
(**) Ideazon Zboard Gaming Keyboard: Device: "/dev/input/event5"
(II) Ideazon Zboard Gaming Keyboard: Found keys
(II) Ideazon Zboard Gaming Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Ideazon Zboard Gaming Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/hal: Adding input device Logitech USB-PS/2 Optical Mouse
(**) Logitech USB-PS/2 Optical Mouse: always reports core events
(**) Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event3"
(II) Logitech USB-PS/2 Optical Mouse: Found 12 mouse buttons
(II) Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
(II) Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
(II) Logitech USB-PS/2 Optical Mouse: Configuring as mouse
(**) Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE)
(**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
(**) Logitech USB-PS/2 Optical Mouse: (accel) filter chain progression: 2.00
(**) Logitech USB-PS/2 Optical Mouse: (accel) filter stage 0: 20.00 ms
(**) Logitech USB-PS/2 Optical Mouse: (accel) set acceleration profile 0
(II) Logitech USB-PS/2 Optical Mouse: initialized for relative axes.

---

