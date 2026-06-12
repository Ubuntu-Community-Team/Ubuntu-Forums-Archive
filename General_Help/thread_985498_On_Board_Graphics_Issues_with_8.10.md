---
title: "On Board Graphics Issues with 8.10"
date: 2008-11-17
forum: General Help
---

### Post by blueflyt on 2008-11-17
1.  I'm still a total novice with regards to Linux/Ubuntu so please consider me a total idiot.  

2.  I have for the most part converted my shop to Ubuntu 8.04.  However, we decided to upgrade to 8.10 because of the reverse compatibility of Evolution with Google Calendar, which is a very important feature for us.

3.  I upgraded one of our PCs to 8.10 and everything works fine, except for the graphics.  

4.  The PC that I've upgraded has lost it's graphics features in 8.10 and now only runs in Simple Mode.  

5.  I've spent the last 48 hours perusing these forums and the Net via Google for some work-arounds.  All I can seem to find is a TON of information about nVidia graphics driver issues (which tells me to NEVER use an nVidia product with Linux/Ubuntu).  I also found a TON of information on this Compiz application.  In any event, I'm kind of at a loss to understand why I've lost my graphics functionality with the upgrade to 8.10.  

6.  My on board graphics is an Intel 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device

7.  I ran the compiz-check when I first installed/upgraded 8.10 and it gave me an error message about running a vesa driver but no other hints or suggestions on how to trouble-shoot.  In the process of tinkering around, I found on another site a suggestion to run the following:  mkdir -p ~/.config/compiz; echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager  .  Now when I run compiz-check, I get an "OK" across all evaluations.  But now when I try to run the Visual Effects in "Normal" or "Extra" mode, my screen suddenly displays only the desktop background without any taskbars or icons and nothing works so I have to do a cold-boot with the reset switch.  Once I log back in everything is back to normal, but my graphics is once again running in Simple mode.  

8.  Can anyone give me a clue (remember: I'm a total idiot) as to what is going on or what I can do to get my graphics functionality back that I had in 8.04?  

(As an aside, this is not a good development as it appears that Ubuntu has taken a step backwards.  I thought upgrades are supposed to improve on prior successes.  But I'll leave that for another discussion thread.)  

Any help is appreciated.

---

### Post by Marcus Derekus on 2008-11-17
reboot. when prompted to press esc press it. (qiuck you only have about three seconds).

NOw in recovery mode choose the option that says somthing like **Fix xserver**

Then reboot normally

post any problems (like if im not being clear... or really anything) 

Please post results

---

### Post by blueflyt on 2008-11-17
> **Marcus Derekus said:**
> reboot. when prompted to press esc press it. (qiuck you only have about three seconds).

NOw in recovery mode choose the option that says somthing like **Fix xserver**

Then reboot normally

post any problems (like if im not being clear... or really anything) 

Please post results

I appreciate the reply!  

Okay, I was able to hit <esc>  and get into recovery mode and then run the Fix XServer option.  However, I'm not sure what that accomplished, if anything.  When it finished running and rebooted, my system came up normally.  Perhaps my original post was not clear, but the problem I'm having is that my desktop doesn't operate the way it used to in 8.04.  Since upgrading to 8.10, it runs in simple mode, which is to say if I go to the Visual Effects option for configuring my desktop, the option that says "None" is selected.  In 8.04 I could run my desktop in Normal or Extra mode.  After installing 8.10 if I clicked on the Normal or Extra options I would get a message that said something to the affect of "Drivers not available" or "Can't run in this mode" or something of that nature.  After I tweaked the system (8.10), when I click on Normal or Extra options my desktop loses all icons and taskbars.  After running the Fix XServer option that you kindly suggested, the same problem still happens when I click on Normal or Extra options - my desktop loses all icons and taskbars and I have to do a cold reboot by hitting the reset button.  

All I want to be able to do is to run my desktop in either Normal or Extra mode under Visual Effects.  

Thanks!

---

### Post by Marcus Derekus on 2008-11-17
It sound like your graphics drviers aren't installed.

try going to System>Administration>Hardware Drivers and enable your graohics card

Let it download any required packages

if that doesn't work (e.g. you Hardware drivers doesn't diplay your graphics card as an option)

Then in terminal run:

```
sudo apt-get install xserver-xorg-video-i810
```

you must reboot after install

also, **after** installation of drivers using either of the above methods, 
if neither fixes the issue then

open /etc/X11/xorg.conf copy contents and post it.

---

### Post by blueflyt on 2008-11-18
> **Marcus Derekus said:**
> It sound like your graphics drviers aren't installed.

try going to System>Administration>Hardware Drivers and enable your graohics card

Let it download any required packages

if that doesn't work (e.g. you Hardware drivers doesn't diplay your graphics card as an option)

Then in terminal run:

```
sudo apt-get install xserver-xorg-video-i810
```

you must reboot after install

also, **after** installation of drivers using either of the above methods, 
if neither fixes the issue then

open /etc/X11/xorg.conf copy contents and post it.

Okay, I followed your instructions and after running the script the system said the i810 driver was already installed.  So, below is the information listed in my xorg.conf file:  

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
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

------

By the way, I did run System>Administration>Hardware Drivers.  The only drivers my system found were for the sound card.

---

### Post by Marcus Derekus on 2008-11-18
Ok, when i misunderstood earlier and made you run xfix, that regonfigured your xserver.

we will change your xorg.conf to be configured to your drivers, open terminal and type:

```
sudo /etc/X11/xorg.conf
```

Edit your file so it matches the one below.
we will only b changing the code in red.

```


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
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
        Identifier "Configured Video Device"[COLOR="red"]  
        Driver     "i810"
        BusId      "PCI:01:05:0[/COLOR]
EndSection

Section "Monitor"
        Identifier "Configured Monitor"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Monitor "Configured Monitor"
        Device "Configured Video Device"
EndSection


```


Notice that where it says **Driver "i810"** yours says "Configured Video Device" change so it exactly matches above.

Now on the **BusID "PCI:01:05:0"**(yes,  add it), yours needs to be a little different. 

To find out your BusID open terminal and type:

```
lspci | grep VGA
```

You will get an output kinda like

```
[COLOR="red"]01:05.0[/COLOR] VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
```

Type your version of the number in red in the **BusId** SubSection

but a little changed so that if you got the number:

**01:05.0**

it would look like

**"PCI:01:05:0"**(and of course the quotes)


note the adding of **PCI:** and that the **.** after 05 is replaced with **:**


now try enabling visual effects. If this doesn't help. please post

---

### Post by blueflyt on 2008-11-18
Still a no-go.  I followed your post and after reconfiguring the xorg.conf file I rebooted.  On reboot, I got a dialogue box that said something to the effect of Ubuntu has to run in low-graphics mode because the driver could not be found.  I was given multiple options to either reload the original default xorg.conf file or try to trouble-shoot the problem.  I went through multiple times and couldn't get the system to come up, so I finally told it to load the default xorg.conf file.  

I was able to get the system to give me an error log as well as show me where in the xorg.conf file the problem was.  For some reason, it doesn't like the BusId line.  

Anyway, here is the output of my PCI card:  

[COLOR="Red"]00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)[/COLOR]

And here is the revised xorg.conf file that I created:  

[COLOR="Red"]# xorg.conf (X.Org X Window System server configuration file)
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
	Identifier	"Configured Video Device"
	Driver		"i810"
	BusId		"PCI:00:02:0"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection[/COLOR]

Also, here is the contents of the error log I was able to create during one of the troubleshooting screens on boot-up: 

[COLOR="Red"]5621 5434
xinit /etc/gdm/failsafeXinit /etc/X11/xorg.conf.failsafe with-gdm -- /usr/bin/X :0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7 -br -once -config /etc/X11/xorg.conf.failsafe -logfile /var/log/Xorg.failsafe.log

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux S2 2.6.27-8-generic #1 SMP Thu Nov 6 17:33:54 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/var/log/Xorg.failsafe.log", Time: Tue Nov 18 09:33:37 2008
(++) Using config file: "/etc/X11/xorg.conf.failsafe"

error setting MTRR (base = 0xe0000000, size = 0x007d0000, type = 1) Invalid argument (22)
5621 5434[/COLOR]

I think we're getting close to resolving this turkey.  I learned long ago in business that when you get close to the source of a problem, that is when you hear the most squawking. And this thing sure is starting to squawk! ;)

---

### Post by Marcus Derekus on 2008-11-18
Ont the line that says **BusI[color="red"]d[/color]** the "D" needs to be capitalized like this **BusI[color="red"]D[/color]** 

My bad, i showed you wrong. Do everything else like i instructed you before. 


And add the stuff in red (yes replace section "screen")

in the Modes SubSection (in blue)
add any resolution you think you'll need

btw search through and make sure you dont have any sections with the same name, if you do remove the old ones.

(basically you xorg.conf file should look pretty much just like this)

```

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "i810"
        BusID           "PCI:00:02:0"
EndSection

[COLOR="Red"]Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
               [COLOR="Blue"] Modes           "1024x768" "800x600" "640x480"[/COLOR]
        EndSubSection    
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection [/COLOR]
```

---

### Post by blueflyt on 2008-11-18
Still negative function.  Here's the error dialogue box that appears immediately after the Ubuntu splash screen comes up during the boot process: 

[COLOR="Red"]**Ubuntu is running in low-graphics mode**

The following error was encountered.  You may need to update your configuration to solve this.  

(EE) No devices detected.  

<OK>[/COLOR]

Below is my xorg.conf file that I created after your last post (it's since been reverted to the system default one):

[COLOR="Red"]Section "Device"
        Identifier      "Configured Video Device"
        Driver          "i810"
        BusID           "PCI:00:02:0"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection    
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection [/COLOR]

I tried different variations of the above, such as deleting out some of the extra sections you had me put in, all to no avail.  

Are you ready to give up yet?  I'll bet you didn't think it would take this long to troubleshoot a seemingly minor issue.  :|

---

### Post by Marcus Derekus on 2008-11-18
ok, not ready to give up if your not. you should have a file that is in the same direcory as xorg.conf named **xorg.conf.xxxxxxxxx** (where xxxxxxx is is the date the file was created)or maybe more than one. I want you to open the one thats name is the date and time I had you run **Fix Xserver** from recovery.

Replace xorg.conf with it and show me all of the contents of this file.

It will probably already be configured for your hardware (i shoould have remebered this) but maybe not set to all of the correct options.

don't change it just show it to me. so ill know if it's correct

if this doesn't work i still have a few other ideas up my sleeve

---

### Post by blueflyt on 2008-11-18
> **Marcus Derekus said:**
> ok, not ready to give up if your not. you should have a file that is in the same direcory as xorg.conf named **xorg.conf.xxxxxxxxx** (where xxxxxxx is is the date the file was created)or maybe more than one. I want you to open the one thats name is the date and time I had you run **Fix Xserver** from recovery.

Replace xorg.conf with it and show me all of the contents of this file.

It will probably already be configured for your hardware (i shoould have remebered this) but maybe not set to all of the correct options.

don't change it just show it to me. so ill know if it's correct

if this doesn't work i still have a few other ideas up my sleeve

Not giving up...I'm not a quitter (yet).  

With regards to the xorg.conf.xxxxxxxxx file, there are several in there and with the exception of one, they are all dated yesterday (my system date/time is accurate).  There is one that's dated today, and I did run the Fix XServer option once today when I was sitting around trying to tinker with this thing on my own.  I'm not sure if it's going to give you any useful information, but here it is:  

[COLOR="Blue"]# xorg.conf (X.Org X Window System server configuration file)
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
        Identifier      "Configured Video Device"
        Driver          "i810"
        BusID           "PCI:00:02:0"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1600x1024" "1024x768" "800x600" "640x480"
        EndSubSection    
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection [/COLOR]

If this is not what you're looking for, I can provide the contents of the other files.  I suppose I could attach them if you need me to in lieu of posting the contents on here.  Just let me know either way.

---

### Post by Marius Derekus on 2008-11-18
Wait, try this! Before you  do anything else, try reinstalling your graphics drivers (the ones you used before you updated your kernel). When you updated your system you updated your kernel (of course). On certain graphics drivers, you have to reinstall them everytime you update kernel. This may work.

BTW. if this works, do not thank me, thank Marcus Derekus (i am Marius Derekus, his twin bro) He did not have acces to the internet, so he told me to tell you this.

---

### Post by blueflyt on 2008-11-18
> **Marius Derekus said:**
> Wait, try this! Before you  do anything else, try reinstalling your graphics drivers (the ones you used before you updated your kernel). When you updated your system you updated your kernel (of course). On certain graphics drivers, you have to reinstall them everytime you update kernel. This may work.

BTW. if this works, do not thank me, thank Marcus Derekus (i am Marius Derekus, his twin bro) He did not have acces to the internet, so he told me to tell you this.

Ok, bear with me...I'm a total Noob at this stuff.  How do I install/reinstall my original graphics drivers?  When I installed 8.04 the graphics worked fine, so I'm assuming that Ubuntu used a generic driver or fetched on its own a driver on line.  Where do I look for the original driver?

---

### Post by Marius Derekus on 2008-11-18
Oh, i tought you had manually installed the drivers. Try this, open synaptic package manager and type down intel chipset. If you can, try and give me a screenshot of the results.

---

### Post by blueflyt on 2008-11-19
> **Marius Derekus said:**
> Oh, i tought you had manually installed the drivers. Try this, open synaptic package manager and type down intel chipset. If you can, try and give me a screenshot of the results.

I'm assuming when you say "type down" you mean do a search.  If so, here's the screen shot of the search results in Synaptic:

---

### Post by Marcus Derekus on 2008-11-19
reinstall all that were marked green (click on each green box and mark for reinstallation)

after marking each one click the apply button

---

### Post by blueflyt on 2008-11-19
> **Marcus Derekus said:**
> reinstall all that were marked green (click on each green box and mark for reinstallation)

after marking each one click the apply button

Still negative function.  

Is this issue in any way related to Compiz?  When I upgraded and encountered this problem originally, and spent some time perusing these forums as well as others, there seemed to be a lot of talk around Compiz.  I seem to recall reading that Compiz incorporated some graphics features that were stand-alones in previous versions of Ubuntu.  Anyway, I appreciate you guys spending so much time and effort on this endeavor...and I look forward to the next suggestion you have.  ;)

---

### Post by Marcus Derekus on 2008-11-19
Compiz is an app that allows extra desktop effects such as 3d. But I believe you would need the correct graphics drivers to run it...which according to your system you don't.

Were the desktop effects working before you updated your system. If not it IS a possibility that your graphics card can't support extra effects.

WARNING be prepared MORE xorg.conf stuff. LOL!

Try adding all of these sections to xorg.conf.

iF YOU HAVE ANY SECTIONS WITH THE SAME NAME AS ONE OF THE SECTIONS, BELOW REPLACE THEM WITH THE ONES LISTED BELOW.

ALSO, EVERYWHERE YOUR **xorg.conf** FILE SAYS **"Configured Video Device"** REPLACE WITH **"Intel 845"** (CAPS AND ALL)

No need to change BusID as i have it set to yours.

```



Section "Device"
Identifier "Intel 845"
Driver "i810"
BusID "PCI:0:2:0"
VideoRam 64000
        Option "UseFBDev" "false"
        Option "RenderAccel" "true"
        Option "AddARGBGLXVisuals" "true"
        Option "XAANoOffscreenPixmaps" "true"
EndSection

Section "Module"
        Load "i2c"
        Load "bitmap"
        Load "dbe"
        Load "dri"
        Load "ddc"
        Load "extmod"
        Load "freetype"
        Load "glx"
        Load "int10"
        Load "record"
        Load "type1"
        Load "vbe"
EndSection


Section "DRI"
        Mode 0666
EndSection

Section "Extensions"
        Option "Composite" "true"
EndSection

```

---

### Post by blueflyt on 2008-11-20
Okay, sports fans, still not happening.  

I copied and pasted your code into my xorg.conf file, deleting what was already there (below all the lines beginning with '#').  When I rebooted, I got the same dialogue box after the Ubuntu splash screen; however, this time the error message said, [COLOR="Blue"]Failed to load module "Type1" (Module does not exist, 0)[/COLOR]

I went back and deleted the "Load "Type1"" in the Section "Module" and rebooted, but this time I got the usual dialogue box that said "No devices detected".  

Next, please.  :)

---

### Post by Marcus Derekus on 2008-11-20
To answer your question above about compiz. It is the program that gives you extra graphics. Without it your computer will only run in simple mode.

But It is installed by default so i dont think this is your problem.

(Besides if the problem was compiz not being installed it wouldn't give you a driver error. It would give you an error about not finding the "compiz" directory or somthing)

I have done some research and it seems Intrepid is causing a lot of graphics issues with intel cards (especially when it comes to 3d and compiz)

It is possible that it has somthing to do with the new graphics drivers or somthing (I don't think it is your card because Compiz was running fine on 8.04)

Maybe downgrading the drivers would work.(We'll try that later if needed right now i'd wait on downgrading.) Or perhaps Compiz is blacklisting your graphics card or something.

Could you attach a copy **/usr/bin/compiz** so i can look at it.

Also attach a copy of **/etc/modprobe.d/blacklist**. (Even though I don't think it is the problem i'd like to see it just in case.)

Also try these two commands in terminal seperatly and tell me the reults.

**glxgears** and **glxinfo | grep direct**

OK!

---

### Post by blueflyt on 2008-11-20
Good Morning!  

Attached are a copy of each of the files you requested.  

The output of **glxgears** resulted in a graphic with turning gears being displayed.  I finally killed it after a while as I assumed you wanted to just see the latency of the numbers.  Here is that output with the error appearing after I killed it.  If there was more information that was supposed to be displayed then let me know and I'll re-run it.  

[COLOR="Blue"]1714 frames in 5.0 seconds = 342.693 FPS
1633 frames in 5.0 seconds = 326.568 FPS
1728 frames in 5.0 seconds = 345.577 FPS
1728 frames in 5.0 seconds = 345.525 FPS
1725 frames in 5.0 seconds = 344.942 FPS
1727 frames in 5.0 seconds = 345.268 FPS
1729 frames in 5.0 seconds = 345.662 FPS
1725 frames in 5.0 seconds = 344.899 FPS
1729 frames in 5.0 seconds = 345.761 FPS
1728 frames in 5.0 seconds = 345.523 FPS
1627 frames in 5.0 seconds = 325.340 FPS
1566 frames in 5.0 seconds = 313.183 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 63688 requests (7614 known processed) with 0 events remaining.
[/COLOR]

The output of **glxinfo | grep direct** is:  

[COLOR="Blue"]direct rendering: Yes[/COLOR]

Hope this helps.  And if I haven't said it yet, I really appreciate all the time you're putting forth on this endeavor.  It's amazing what you are putting up with!

---

### Post by Marcus Derekus on 2008-11-20
Good! The result to the commands i gave you are the ones i wanted.

I had you run them to see if your direct rendering was running. Which  it is.

the fatal error was just saying that the program was closed.
 
Now i forgot to tell you that you will have to add .txt  extension to the copies in order to attach them. (The files didn't attach. My bad for not telling you.)

And thanks. I enjoy helping out.

---

### Post by Marius Derekus on 2008-11-20
I've been doing a lot of research on this also and (as Marcus Derekus has earlier stated) it is a known bug. According to all the "solutions" i've read so far, compiz does not work with the intel 845 chipset on ubuntu 8.10. 


Try unistalling compiz by doing the following in termial
```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
```

Then reinstall compiz and see if it works.
I think you would reinstall it by typing the following in terminal
```
sudo apt-get install compiz-core
sudo apt-get install compiz
```

Btw, I think this bug is called BUG #259385. But i don't know this for sure

---

### Post by Marius Derekus on 2008-11-20
Something else you might try doing is this (first backup your xorg.conf file). Edit the xorg.conf file the way Marcus Derekus  told you to earlier, only this time try replacing the line that say Driver "i810" edit it to say Driver "vesa".  See the following text.
[COLOR="Red"]
Section "Device"
Identifier "Configured Video Device"
[Color="blue"]Driver "vesa"[/color]
BusID "PCI:00:02:0"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1600x1024" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "true"
EndSection [/COLOR]

---

### Post by blueflyt on 2008-11-20
**Marius:**  We seem to be making some progress here...

I removed and re-installed Compiz per your instructions and then I modified my xorg.conf file so that it now looks like this: 

[COLOR="Blue"]Section "Device"
Identifier "Intel 845"
Driver "vesa"
BusID "PCI:00:02:0"
VideoRam 64000
        Option "UseFBDev" "false"
        Option "RenderAccel" "true"
        Option "AddARGBGLXVisuals" "true"
        Option "XAANoOffscreenPixmaps" "true"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection    
EndSection

Section "Module"
        Load "i2c"
        Load "bitmap"
        Load "dbe"
        Load "dri"
        Load "ddc"
        Load "extmod"
        Load "freetype"
        Load "glx"
        Load "int10"
        Load "record"
        Load "type1"
        Load "vbe"
EndSection

Section "DRI"
        Mode 0666
EndSection

Section "Extensions"
        Option "Composite" "true"
EndSection[/COLOR]

When I reboot now, I don't get any error messages and my system comes up normally with the expected resolution (1280x1024).  And when I go to the Visual Effects option under Appearance Preferences and click on "Normal", my PC no longer freezes up; instead, the dialogue box appears that says it's searching for drivers; the screen goes white for about 30 seconds; and then it reappears in the usual "None", or simple, mode.  

So, the good news is, everything is working normally without any hiccups.  The bad news is that I still can't access "Normal" or "Extra" mode under the visual preferences, which I was able to do in previous versions.  

I think changing the xorg.conf file to "vesa" under the driver section fixed one part of the problem.  Although, I am noticing that my monitor seems to be moving more slowly now, so that when I scroll the movement is very choppy whereas before it seemed a little more smoother.  Alas, I'm happy to have gotten this far.  

**Markus:** I'm attaching the two files with the .txt extensions added.  Let me know if you find anything.  

Thanks!

---

### Post by Marius Derekus on 2008-11-20
Sounds great! Now, just in case do the commands that Marcus had you do on post #20, that way we know if you still have direct rendering. (I'm hoping that you will still have direct rendering through the vesa driver.)

Also, Marcus is going to send you a message in a minute. (I think those files you attached really helped.)

I smell progress!

---

### Post by Marcus Derekus on 2008-11-20
Ok, here is compiz-check. You can save this any where you want to.

remove the ".xcf" extension on the file once downloaded.

To run this script type in terminal:

```
bash /PATH/TO/**compiz-check**
```

---

### Post by yogo on 2008-11-20
@blueflyt

This has been a very interesting thread for me to read through.  I too have the same graphics []("http://ubuntuforums.org/member.php?u=355885")00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE C

Having started several threads myself, I have given up on finding an answer but would like to hope that there is one.

I do not believe that this onboard graphics require a driver because when I check my restricted drivers, it says that none are required for my system. Also mine worked in 8.04, Gutsy and Feisty, only in 8.10 do I now have the problem.

I have done the compiz check and my system passes. 

Anyways this is not to hijack your thread, it seems like the problem is known but there are not any answers  yet. 

I hope you folks can figure this out as there are several people with this problem.

---

### Post by Marius Derekus on 2008-11-20
> **yogo said:**
> @blueflyt

This has been a very interesting thread for me to read through.  I too have the same graphics []("http://ubuntuforums.org/member.php?u=355885")00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE C

Having started several threads myself, I have given up on finding an answer but would like to hope that there is one.

I do not believe that this onboard graphics require a driver because when I check my restricted drivers, it says that none are required for my system. Also mine worked in 8.04, Gutsy and Feisty, only in 8.10 do I now have the problem.

I have done the compiz check and my system passes. 

**Anyways this is not to hijack your thread, it seems like the problem is known but there are not any answers  yet. **

I hope you folks can figure this out as there are several people with this problem.

Quite the contrary, any input is accepted and encouraged. Anything that can bring us closer to the solution of this problem.

---

### Post by Marius Derekus on 2008-11-20
Forgive me for this waste of a post, it was a copy of the one above (post #29)

---

### Post by yogo on 2008-11-20
Thanks Marius,

Here are a couple of threads I started  on this very same problem. They may help in seeing the steps I already took.

[http://ubuntuforums.org/showthread.php?t=983345](http://ubuntuforums.org/showthread.php?t=983345)  and   [http://ubuntuforums.org/showthread.php?t=973187](http://ubuntuforums.org/showthread.php?t=973187)

---

### Post by Marius Derekus on 2008-11-20
> **yogo said:**
> Thanks Marius,

Here are a couple of threads I started  on this very same problem. They may help in seeing the steps I already took.

[http://ubuntuforums.org/showthread.php?t=983345](http://ubuntuforums.org/showthread.php?t=983345)  and   [http://ubuntuforums.org/showthread.php?t=973187](http://ubuntuforums.org/showthread.php?t=973187)

Thank you very much for these threads. They are quite useful. (I saw that a few attempts that caused your desktop to go black. At least we know what to avoid.)

---

### Post by Marcus Derekus on 2008-11-20
Well I looked at your **"compiz"** that you uploaded and it looks like your graphics card is blacklisted. 

Here is the BLACKLIST section of your compiz (look at the line in red and blue).

```

]# blacklist based on the pci ids 
# See http://wiki.compiz-fusion.org/Hardware/Blacklist for details
#T="   1002:5954 1002:5854 1002:5955" # ati rs480
#T="$T 1002:4153" # ATI Rv350
#T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700
T="8086:1132"   # intel i815 (LP: #221920)
T="$T 8086:2e02 " # Intel Eaglelake
[COLOR="Red"]T="$T 8086:3577 8086:2562" # Intel 830MG, [COLOR="Blue"]845G[/COLOR] (LP: #259385)[/COLOR]
BLACKLIST_PCIIDS="$T"
unset T
```

Compiz is blacklisting (in blue) your card.

Now here is the BLACKLIST section on my /usr/bin/compiz file

I use **Ubuntu 8.04**

```

# blacklist based on the pci ids 
# See http://wiki.compiz-fusion.org/Hardware/Blacklist for details
#T="   1002:5954 1002:5854 1002:5955" # ati rs480
#T="$T 1002:4153" # ATI Rv350
#T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700
T="8086:1132"   # intel i815 (LP: #221920)
BLACKLIST_PCIIDS="$T"
```

It appears here that your card is not blacklisted in **8.04**, only **8.10**.
And that is probably why it doesn't work.

But why would compiz developers blacklist your card in **Intrepid** if it worked fine in **Hardy**?

---

### Post by yogo on 2008-11-20
> **Marcus Derekus said:**
> Well I looked at your **"compiz"** that you uploaded and it looks like your graphics card is blacklisted. 

Here is the BLACKLIST section of your compiz (look at the line in red and blue).

```

]# blacklist based on the pci ids 
# See http://wiki.compiz-fusion.org/Hardware/Blacklist for details
#T="   1002:5954 1002:5854 1002:5955" # ati rs480
#T="$T 1002:4153" # ATI Rv350
#T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700
T="8086:1132"   # intel i815 (LP: #221920)
T="$T 8086:2e02 " # Intel Eaglelake
[COLOR=Red]T="$T 8086:3577 8086:2562" # Intel 830MG, [COLOR=Blue]845G[/COLOR] (LP: #259385)[/COLOR]
BLACKLIST_PCIIDS="$T"
unset T
```Compiz is blacklisting (in blue) your card.

Now here is the BLACKLIST section on my /usr/bin/compiz file

I use**Ubuntu 8.04**

```

# blacklist based on the pci ids 
# See http://wiki.compiz-fusion.org/Hardware/Blacklist for details
#T="   1002:5954 1002:5854 1002:5955" # ati rs480
#T="$T 1002:4153" # ATI Rv350
#T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700
T="8086:1132"   # intel i815 (LP: #221920)
BLACKLIST_PCIIDS="$T"
```It appears here that your card is not blacklisted in **8.04**, only **8.10**.

I wonder why.


Is there anything I can do?, I did try running something I found about blacklisted cards but that did not work unless I did not do it right.

This is suppose to help if your card is blacklisted 
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

Found in this sticky [http://ubuntuforums.org/showthread.php?t=765875](http://ubuntuforums.org/showthread.php?t=765875)


Could I just delete the part that lists my card? 845G

TIA

---

### Post by Marius Derekus on 2008-11-20
Unless you have downgraded back to 8.04, perhaps you (yogo) could try what bluflyt has done on post #23 and #25, and give us the results.

(If you do not wish to do so, it is completely understandable.)

---

### Post by Marcus Derekus on 2008-11-20
I got a similar command from [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist)

here is the command:```
SKIP_CHECKS=yes compiz
```
]
It's pretty much the same command that you (yogo) posted but it would't hurt to try it.

both of you guys should try it (bluflyt and yogo)

just cuz it dosn't work on one don't mean it won't work on the other

I wish i could test it myself as well but i have a different card

[COLOR="red"]TO bluflyt: This was added as an edit. I forgot that you already tried this (long thread, but my bad).[/COLOR]

---

### Post by yogo on 2008-11-20
> **Marcus Derekus said:**
> I got a similar command from [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist)

here is the command:```
SKIP_CHECKS=yes compiz
```]



I gave it a try, it did not work for me. My desktop was gone and then I tried  in low graphics mode.  I booted into recovery mode, in the past I have always used console to remove compiz and compiz-core to get my desktop back, this time I chose to let it reconfigure X and that worked as well to get my desktop back.

Thanks Marcus, I appreciate your dedication in trying to resolve this.

---

### Post by Marcus Derekus on 2008-11-20
Has anybody tried using the "intel" driver instead of "i810"

---

### Post by Marcus Derekus on 2008-11-20
Perhaps you could open "/usr/bin/compiz" as root and comment out the line blacklisting your card.

like so:

```

sudo gedit /usr/bin/compiz

```

Then comment out (put # in front of) the line in red. (I added # in blue)

```

]# blacklist based on the pci ids 
# See http://wiki.compiz-fusion.org/Hardware/Blacklist for details
#T="   1002:5954 1002:5854 1002:5955" # ati rs480
#T="$T 1002:4153" # ATI Rv350
#T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700
T="8086:1132"   # intel i815 (LP: #221920)
T="$T 8086:2e02 " # Intel Eaglelake
[COLOR="Blue"]#[/COLOR][COLOR="Red"]T="$T 8086:3577 8086:2562" # Intel 830MG, 845G (LP: #259385)[/COLOR]
BLACKLIST_PCIIDS="$T"
unset T
```

Try, but i the screen will probably go black.

(I now think the card was blacklisted because of this problem (bug #259385) if you look at the red line above so the issue probably comes from another source)

BUT WE WILL NOT GIVE UP FRIENDS!!:lolflag:

---

### Post by yogo on 2008-11-20
> **Marius Derekus said:**
> Unless you have downgraded back to 8.04, perhaps you (yogo) could try what bluflyt has done on post #23 and #25, and give us the results.

(If you do not wish to do so, it is completely understandable.)


I did both of these and I am still on 8.10.  #25 ended up putting me in low graphics mode so I ended having to boot into recovery mode and allow it to reconfigure X.

I have not tried to use Intel driver per your last post.

Thanks

---

### Post by Marcus Derekus on 2008-11-20
Then maybe running the driver might work (although I don't think so).

BTW my previous post has been edited.

---

### Post by Marius Derekus on 2008-11-20
Just as a reminder, let us not give up. Though he still doesn't have visual affects, bluflyt's computer doesn't go black or freeze up any more when he tries to enable them. This is something i havn't seen on any other post about this topic. (Once again, thank you yogo for the tests and research you have performed. As mentioned before, any idea or thought is accepted and encouraged.)

---

### Post by yogo on 2008-11-20
> **Marcus Derekus said:**
> Ignore my previous thread

Perhaps you could open "/usr/bin/compiz" as root and comment out the line blacklisting your card.

like so:

```

sudo gedit /usr/bin/compiz
[code]

Then comment out (put # in front of) the line in red. (I added # in blue)

[code]
]# blacklist based on the pci ids 
# See http://wiki.compiz-fusion.org/Hardware/Blacklist for details
#T="   1002:5954 1002:5854 1002:5955" # ati rs480
#T="$T 1002:4153" # ATI Rv350
#T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700
T="8086:1132"   # intel i815 (LP: #221920)
T="$T 8086:2e02 " # Intel Eaglelake
[COLOR=Blue]#[/COLOR][COLOR=Red]T="$T 8086:3577 8086:2562" # Intel 830MG, 845G (LP: #259385)[/COLOR]
BLACKLIST_PCIIDS="$T"
unset T
```Try, but i the screen will probably go black.

(I now think the card was blacklisted because of this problem (bug #259385 if you look at the red line above so the issue probably comes from another source)

BUT WE WILL NOT GIVE UP FRIENDS!!:lolflag:

Now this I really had high hopes for and thought it would work......it did not. Seems like they know why they blacklisted this card and are not offering any fixes.

Thanks again, I do have a new desktop on it's way next week so this will not be a problem for me, BUT it does bug the heck out of me as to why it does not work in 8.10.

For the record when I try to enable them, 9 out of 10 times I am left with my wallpaper, no panels or desktop items, occasionally I have had a black screen.

---

### Post by Marius Derekus on 2008-11-20
Thanks for trying it anyways, thats the only way we can find out if something works or not. That stupid bug...

---

### Post by Marius Derekus on 2008-11-20
Just so we can compare, could you show us your xorg.conf as well. That may help us narrow something down.

---

### Post by Marcus Derekus on 2008-11-20
Yeah man thanks ALOT. And thank you SO MUCH bluflyt for letting me help you so long without successful fixation of the problem.

I'm still not giving up yet.

---

### Post by yogo on 2008-11-20
> **Marius Derekus said:**
> Just so we can compare, could you show us your xorg.conf as well. That may help us narrow something down.


Here is mine before and now after trying what was in post #25

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
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

---

### Post by Marius Derekus on 2008-11-20
Thank you very much for this. As i thought i looks like bluflyt's used to before he did what was in post #25. Did you try enabling desktop effects after making the changes shown on post #25.

---

### Post by Marius Derekus on 2008-11-20
Gotta get some sleep now, hopefully (and most likely, we'll talk to you guys tommorow)
If there are any updates you have, feel free to post them anyways.

---

### Post by Tom.Servo on 2008-11-20
Please forgive me if this has already been mentioned, but I am having trouble viewing all 5 pages of this post. Has anyone tried to force compiz,etc too ignore the blacklist via: 

[I][B]mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
[/B][/I]

It seems to me this command is what allowed me the extra detail on my old lappy with a 945. However there were some minor glitches, which are what probably led them to blacklist it in the first place. 

Again, I may be way off base here and/or may be repeating something already mentioned, but I'm just trying to offer a possible resolution and help out. :)

---

### Post by Marcus Derekus on 2008-11-21
Thanks. Tom.servo. We had just tried that and it didn't work (for yogo, it may work for blueflyt). 

But we greatly appreciate the input and any other possible solutions are incouraged. It is always nice to have extra help. 

So if think you might have a solution or have helpful links or something pop'em in.
[COLOR="Red"]
ONCE AGAIN MY BAD, blueflyt HAD ALREADY TRIED THIS AND IT FAILED. I SHOULD HAVE REMEBERED[/COLOR].

---

### Post by Marcus Derekus on 2008-11-21
To bluflyt. Just in case. You were offline when pages 4 and 5 were written.

Yogo (who has the same problem)tested these propositions and they failed.

But the results may be different for you, so you may want to test some of those.

---

### Post by duanedesign on 2008-11-21
They tried this around - pg 4 post 34 to be exact. 

Interesting post, A round of thanks foe all you guys.

This is what makes the Ubuntu community so strong.

Update: Marcus must of replied while I was typing sorry for the reiteration.

---

### Post by yogo on 2008-11-21
I am out for the night but will check back tomorrow, thanks to all involved.

---

### Post by heiowge on 2008-11-21
Hi guys.  Since "upgrading" to intrepid I have had no end of trouble.  First my panel kept disappearing, next my fast user switching applet vanished and the option to re-add it went too.

Now I've realised my graphics have done the same as the others on this thread.

Every time I try to switch to extra visual effects, I get booted straight back to none.

I have started several threads in various forums (this one included), but no luck so far.

A lot of what is mentioned here is well over my head, so would appreciate any help that I can get.

---

### Post by heiowge on 2008-11-21
Weirdest thing.  I managed to get the compiz manager working, and when I hit reload window manager, all my effects came back on!:confused::confused:

---

### Post by Marius Derekus on 2008-11-21
Do you have the same kind of graphics card? If not, tell us what kind you do have. And if you can, please show us your xorg.conf file by entering the following into terminal:

```
sudo gedit /etc/X11/xorg.conf
```
Then press ctrl+a (this will highlight all the text in xorg.conf), right-click the highlighted text, select copy, then make a new reply, right-click on that reply and select paste.

Could you please tell us how you reloaded the manger to get them working?

Thank you very much for this post.

---

### Post by blueflyt on 2008-11-21
> **Tom.Servo said:**
> Please forgive me if this has already been mentioned, but I am having trouble viewing all 5 pages of this post. Has anyone tried to force compiz,etc too ignore the blacklist via: 

[I][B]mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
[/B][/I]

It seems to me this command is what allowed me the extra detail on my old lappy with a 945. However there were some minor glitches, which are what probably led them to blacklist it in the first place. 

Again, I may be way off base here and/or may be repeating something already mentioned, but I'm just trying to offer a possible resolution and help out. :)

Tom, I tried that before I started this thread.  It didn't fix my graphics, but what it did do was make my system lock up when I would try to select one of the higher levels of graphics functionality in the Visual Effects module.  One of the Derekus boys (sorry, can't remember if it was Marcus or Marius) managed to fix this problem by having me uninstall and then reinstall Compiz.  

> **Marcus Derekus said:**
> To bluflyt. Just in case. You were offline when pages 4 and 5 were written.

Yogo (who has the same problem)tested these propositions and they failed.

But the results may be different for you, so you may want to test some of those.

Marcus, my sincere apologies, but I've been off-line for the past 24 hours working against an RFP deadline.  My mind is a little mushy at the moment.  Let me go back and read through the posts of the past 24 hours and get back to you on this.  Thanks!

---

### Post by blueflyt on 2008-11-21
> **Marcus Derekus said:**
> I got a similar command from [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist)

here is the command:```
SKIP_CHECKS=yes compiz
```
]
It's pretty much the same command that you (yogo) posted but it would't hurt to try it.

both of you guys should try it (bluflyt and yogo)

just cuz it dosn't work on one don't mean it won't work on the other

I wish i could test it myself as well but i have a different card

I just tried it.  Unfortunately, it made my screen go blank (turned it completely white) and after I waited 5 minutes I finally had to give my PC the cold boot via reset switch.  

> **Marcus Derekus said:**
> Ignore my previous thread

Perhaps you could open "/usr/bin/compiz" as root and comment out the line blacklisting your card.

like so:

```

sudo gedit /usr/bin/compiz

```

Then comment out (put # in front of) the line in red. (I added # in blue)

```

]# blacklist based on the pci ids 
# See http://wiki.compiz-fusion.org/Hardware/Blacklist for details
#T="   1002:5954 1002:5854 1002:5955" # ati rs480
#T="$T 1002:4153" # ATI Rv350
#T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700
T="8086:1132"   # intel i815 (LP: #221920)
T="$T 8086:2e02 " # Intel Eaglelake
[COLOR="Blue"]#[/COLOR][COLOR="Red"]T="$T 8086:3577 8086:2562" # Intel 830MG, 845G (LP: #259385)[/COLOR]
BLACKLIST_PCIIDS="$T"
unset T
```

Try, but i the screen will probably go black.

If I comment out that line and my screen goes blank, how will I be able to reload the backup copy of that file if I can't view anything.  I'm assuming I'd have to reload it via the command line prompt, but would you be able to walk me through on how to do that?

---

### Post by Marcus Derekus on 2008-11-21
Perfectly Ok, blueflyt. We've all still got our external (non computer) lives.

BTW: I edited my original post saying that I forgot that you already did that (disabling compiz blacklist). 

But i guess i was to late

---

### Post by Marcus Derekus on 2008-11-21
If your screen goes black (when you boot) just uninstall then reinstall compiz (through terminal). 

To get to root terminal on ubuntu. just boot into recovery mode then choose the **root terminal** option. 

then uninstall compiz

```
sudo apt-get remove compiz
sudo apt-get remove compiz-core

```

type **exit** to exit the root terminal then choose **resume**.

Now your system should boot up.

then reinstall compiz 

```
sudo apt-get install compiz
sudo apt-get install compiz-core

```

NOTE: Installing **compiz** first will probably automatically install **compiz-core**

---

### Post by blueflyt on 2008-11-21
I just commented out that line and then rebooted my system.  Everything came back up normally.  When I tried to switch the Visual Effects to "Normal" mode, it ran its usual exercise of looking for a driver and then my screen went blank for about 2 minutes and then it eventually returned.  But it was back in its simple mode without the graphics effects I've been trying to implement.  

So, apparently, commenting out that line had no affect whatsoever.  At least the good news is that it didn't produce any bad side affects either.  

Should I go ahead and remove the '#' from that line or leave everything as-is?  I don't want to create any bad side affects in the event I update the system and it ends up interfering with something else.

---

### Post by Tom.Servo on 2008-11-21
Ok. I figured someone had tried it, but since I was having trouble viewing anything but the last page, I figured I'd offer the suggestion. Good luck with a fix. :)

---

### Post by Marius Derekus on 2008-11-21
> **Tom.Servo said:**
> Ok. I figured someone had tried it, but since I was having trouble viewing anything but the last page, I figured I'd offer the suggestion. Good luck with a fix. :)

That is just fine, if you think someone has said before, post it anyways. It is better safe then sorry.

If you have any other advise, feel free to post it.

---

### Post by Marcus Derekus on 2008-11-21
TO blueflyt. I would first change your driver from "vesa" to "i810" in xorg.conf.

If that doesn't work. Un-comment the blacklist line in compiz and then set your driver back to "vesa" in xorg.conf.

Cheers!

---

### Post by yogo on 2008-11-21
So where are we at today?

I am not on my Dell desktop that I have all the problems with, a neighbor brought over a mess of a pc, I have never seen anything so wiped out. I had fixed a pc she sold to the neighbor so she brought this one over it is much worse.

Not a bad pc but it is full of viruses, you can not even do ctrl/alt/delete, only thing you  can do is a power shutdown. Anyways, I booted into a Kbuntu 8.10 usb and am running that on it deciding if I want to get it or not.

I think I will check to see what the onboard graphics is and if it can run compiz in 8.10.

---

### Post by Marcus Derekus on 2008-11-21
Yeah bud, Just wipe the drive and slap on linux. Hope the graphics card works.

Good luck.

well be back in a few hours but don't let that stop any of you from posting.

---

### Post by blueflyt on 2008-11-21
> **Marcus Derekus said:**
> TO blueflyt. I would first change your driver from "vesa" to "i810" in xorg.conf.

If that doesn't work. Un-comment the blacklist line in compiz and then set your driver back to "vesa" in xorg.conf.

Cheers!

Well, that didn't go over too well.  I changed the driver to i810 and then rebooted.  I got an error dialogue box during the boot up process that said the system couldn't load "Type1" (it's the same error I got several page-posts back). I tried to uninstall and then reinstall compiz from the text screen, but still kept getting the same error message.  I finally went into the recover mode and ran Fix XServer.  That seemed to do the trick.  (And in the process I realized how much more comfortable I've become working with this thing since you guys have been teaching me so much!)  

Anyway, I think I'm back to Square One with this.  Everything is working fine on this box with the exception of the beefed-up graphics capabilities.  For this box, I'm going to leave everything as-is until someone comes up with a fix.  The system works and I can get it to do what I want, so I'll just let the sleeping dogs lie for now.  This weekend I'm going to configure one of our last two remaining Vista boxes for dual-boot capability with Ubuntu 8.10.  That machine is very robust and I'm hoping I don't have any major issues with it.  

You guys have all been exceptional and without compare.  This entire experience has convinced me more than ever that Ubuntu/Linux is the way to go.  You are the best "customer service" I've ever encountered in my entire professional experience.  If any of you are ever in the Phoenix metro area then let me know.  The first few rounds of drinks will all be on me.  \\:D/

---

### Post by yogo on 2008-11-21
> **blueflyt said:**
>   This weekend I'm going to configure one of our last two remaining Vista boxes for dual-boot capability with Ubuntu 8.10.  That machine is very robust and I'm hoping I don't have any major issues with it.  




Not reccommended by me, just install 8.04 on the other boxes, there is nothing special about Ibex, Hardy is still  does have long term support. Who knows some Jackal will be coming out soon.

---

### Post by blueflyt on 2008-11-21
> **yogo said:**
> Not recommended by me, just install 8.04 on the other boxes, there is nothing special about Ibex, Hardy is still  does have long term support. Who knows some Jackal will be coming out soon.

I can't run my people on 8.04 because Evolution mail in 8.04 can't reverse sync with Google's business app calendar (which is to say if you make an entry in Evolution Calendar it will not appear in Google's calendar).  That was the only reason I decided to upgrade to 8.10 because I read that it can sync calendar entries with Google.  And on this machine that's been the genesis of this long-winded (but very informative) thread, Evolution in 8.10 syncs up beautifully.  In fact, other than the graphics issue, I have not encountered any other problems.  8.04 can only sync FROM Google calendar, not TO Google calendar.  We are heavily dependent on our calendars for scheduling purposes and it's the reason why we left two boxes running Vista - those boxes are used to make sure everyone's calendar is properly sync'd up.

---

### Post by Marcus Derekus on 2008-11-21
Yeah THANKS ALOT blueflyt and yogo. It's been a great experience for me.

Although we haven't found the answer I'm still very glad to help out.

You guys are all great! Awesome! Hope we run into eachother again.

---

### Post by cammin on 2008-11-22
You're supposed to be using the **intel** driver as it replaces the **i810** driver.

Even if you want to use the **i810** driver you shouldn't have both installed at the same time. You'd be better off removing both drivers and re-installing the one you want. Don't forget to change the driver from **i810** to **intel** in **xorg.conf**.

---

### Post by yogo on 2008-11-22
> **blueflyt said:**
> I can't run my people on 8.04 because Evolution mail in 8.04 can't reverse sync with Google's business app calendar (which is to say if you make an entry in Evolution Calendar it will not appear in Google's calendar).  That was the only reason I decided to upgrade to 8.10 because I read that it can sync calendar entries with Google.  And on this machine that's been the genesis of this long-winded (but very informative) thread, Evolution in 8.10 syncs up beautifully.  In fact, other than the graphics issue, I have not encountered any other problems.  8.04 can only sync FROM Google calendar, not TO Google calendar.  We are heavily dependent on our calendars for scheduling purposes and it's the reason why we left two boxes running Vista - those boxes are used to make sure everyone's calendar is properly sync'd up.


I stand corrected!:) Then there is something special about 8.10.

---

### Post by blueflyt on 2008-11-22
> **cammin said:**
> You're supposed to be using the **intel** driver as it replaces the **i810** driver.

Even if you want to use the **i810** driver you shouldn't have both installed at the same time. You'd be better off removing both drivers and re-installing the one you want. Don't forget to change the driver from **i810** to **intel** in **xorg.conf**.

Hi Cammin, are you saying I should try to change the driver in my xorg.conf file from "i810" to "intel"?  In other words, just change it in that file only?  

Thanks.

---

### Post by blueflyt on 2008-11-22
> **yogo said:**
> I stand corrected!:) Then there is something special about 8.10.

Yogo, I just installed 8.10 on one of my Vista boxes (it's now a dual-boot machine).  Runs like a charm!  (So far, anyway.)  Graphics work great.  All I can say at this point is, Thank you Microsoft for developing Vista.  Had it not been for Vista, I would not have put so much effort into finding another alternative.  And I had no idea the alternative I found would be infinitely better than your piece of s*** bloatware.  Goodbye Redmond!

---

### Post by Marcus Derekus on 2008-11-23
Now your talking bluflyt!

Ok, what cammin is saying is to uninstall both the **xserver-xorg-video-i810** driver and **xserver-xorg-video-intel** driver then reinstall the **xserver-xorg-video-intel** driver only then replace "i810" with "intel" in xorg.conf if your machine didn't do it automatically.
(which it is true, you should only have one driver installed for your card)

If though, for some reason the "intel" driver causes problems you can just go back to "i810"

also sorry for vanishing for awile, we've got family visiting.

Also I think this program would allow you to sync google earth to evolution in 8.04 just in case your still thinkig about going back (if your not that's perfectly fine):

[http://gcaldaemon.sourceforge.net/index.html](http://gcaldaemon.sourceforge.net/index.html)

If you do decide to go this route i can teach you how to install it (if you don't already know how) as it requires you to compile the source-code.

Just thought I'd bring it up cuz it may be a way for you to have both compiz and reverse sync capabilities with google calender.(Using 8.04)

---

### Post by Marius Derekus on 2008-11-23
Hey guys sorry we havn't replyed any time soon, we had family over and all...
So, did changing the "i810" line to "intel" work?  If not, and you still want to get this computer working (assuming the desktop affects still aren't working) I'm always here to help.  You say this other computer runs good eh. Than Congrats! 

To yogo: So, what did you do to that old computer your friend gave ya? Just wandering.

---

### Post by heiowge on 2008-11-23
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

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	BusId      "PCI:01:05:0
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

---

### Post by heiowge on 2008-11-23
To get my compiz online, I just fired it up from the applications menu. (I use the compiz Icon that I got from synaptic)  or some reason though it's not persistant.  I have to reload it each time I restart.

---

### Post by gregphil on 2008-11-23
Two comments:

1) Under a different Linux distribution (CentoOS 5.1)  I had the same issue with the onboard i810 video. I finally found a suggestion in some forum to comment out the "legacy" **i810** driver in xorg.conf and replace it with the "new" **intel **driver.  I tried this and it WORKED!  Orginally the i810 driver was choosen and installed by the default from the CentOS CD.  Once I changed it to "intel" the problem was gone.

2) On other machines, and under Ubuntu/Kubuntu the 'upgrade' from 8.04.1 definatelly broke my video.  The machines had been running just fine with all the 'eye candy' under 8.04..1 using a slightly older Nvidia 440 video cards.  Once I updated to the new 8.10 version it claimed there was no available driver and therefore would only run using the brain dead, super slow, GPU video drivers (but at full 1600 x 1200 resolution).  After MUCH effort I concluded it would never work and simply replaced the video cards with new low cost ($50) GeForce 6200 Nvidia video cards.  That solved all the issues, all the 'eye candy' featues can work again.  It appears the 8.10 change to require a different type of video driver has orpaned many slightly older (say 2003 era) Nvidia video cards.  I do not know if this lack of support carries over into other types of video chip sets.

Good Luck.   

BTW, for me the $50 cost of a new video card was well worth avoiding many more hours of frustration and troubleshooting.

---

### Post by heiowge on 2008-11-23
Cheers for that. Thing is, I actually already use the Nvidia 6200.  That's the card I used when I switched to 8.10 and had all the fun with compiz (that still isn't persistant!)

---

### Post by blueflyt on 2008-11-23
> **gregphil said:**
> Two comments:

1) Under a different Linux distribution (CentoOS 5.1)  I had the same issue with the onboard i810 video. I finally found a suggestion in some forum to comment out the "legacy" **i810** driver in xorg.conf and replace it with the "new" **intel **driver.  I tried this and it WORKED!  Orginally the i810 driver was choosen and installed by the default from the CentOS CD.  Once I changed it to "intel" the problem was gone.

2) On other machines, and under Ubuntu/Kubuntu the 'upgrade' from 8.04.1 definatelly broke my video.  The machines had been running just fine with all the 'eye candy' under 8.04..1 using a slightly older Nvidia 440 video cards.  Once I updated to the new 8.10 version it claimed there was no available driver and therefore would only run using the brain dead, super slow, GPU video drivers (but at full 1600 x 1200 resolution).  After MUCH effort I concluded it would never work and simply replaced the video cards with new low cost ($50) GeForce 6200 Nvidia video cards.  That solved all the issues, all the 'eye candy' featues can work again.  It appears the 8.10 change to require a different type of video driver has orpaned many slightly older (say 2003 era) Nvidia video cards.  I do not know if this lack of support carries over into other types of video chip sets.

Good Luck.   

BTW, for me the $50 cost of a new video card was well worth avoiding many more hours of frustration and troubleshooting.

Believe me, I've thought of doing that myself (forking over a few dollars for a graphics card), but it's not an option on this one box that I upgraded to 8.10 (the one that started this thread).  This box is one of those IWill mini-box desktops and it has only one expansion card slot.  That expansion card slot is used for the wireless card as the box is in a corner office that doesn't have access to a network cable.  I was hoping to get some more life out of it, as well as our other desktops which are all older units.  That was the whole reason I decided to try out Ubuntu because continuing to run these boxes on XP was proving expensive and we didn't want to fork over the bucks to upgrade the hardward to Vista.  

Anyway, I'm expecting a slow week this coming week because of the holiday so I'm going to take the Derekus brothers up on their suggestion to go back to 8.04 and configure the work-around to make Evolution mail sync up with Google apps.

---

### Post by blueflyt on 2008-11-23
> **gregphil said:**
> Two comments:

1) Under a different Linux distribution (CentoOS 5.1)  I had the same issue with the onboard i810 video. I finally found a suggestion in some forum to comment out the "legacy" **i810** driver in xorg.conf and replace it with the "new" **intel **driver.  I tried this and it WORKED!  Orginally the i810 driver was choosen and installed by the default from the CentOS CD.  Once I changed it to "intel" the problem was gone.

2) On other machines, and under Ubuntu/Kubuntu the 'upgrade' from 8.04.1 definatelly broke my video.  The machines had been running just fine with all the 'eye candy' under 8.04..1 using a slightly older Nvidia 440 video cards.  Once I updated to the new 8.10 version it claimed there was no available driver and therefore would only run using the brain dead, super slow, GPU video drivers (but at full 1600 x 1200 resolution).  After MUCH effort I concluded it would never work and simply replaced the video cards with new low cost ($50) GeForce 6200 Nvidia video cards.  That solved all the issues, all the 'eye candy' featues can work again.  It appears the 8.10 change to require a different type of video driver has orpaned many slightly older (say 2003 era) Nvidia video cards.  I do not know if this lack of support carries over into other types of video chip sets.

Good Luck.   

BTW, for me the $50 cost of a new video card was well worth avoiding many more hours of frustration and troubleshooting.

Ok, since my last post, I went into the office and saw that we had one other box with the same integrated graphics, an HP Pavilion a405n.  I decided to go out and buy a video card for this particular box and upgrade it to 8.10.  It's an ATI Radeon 9250 (PCI) graphics card.  I went into the BIOS set-up and specified that the primary video is PCI (vs. on board).  Now when I try to run the Ubuntu set-up disk the progress bar sticks at about the 15% completion point.  Then, after about 5 minutes, the screen goes completely blank, and after about another two minutes a text screen appears and renders the following message:  

[COLOR="Blue"]Segmentation fault
/etc/rcS.d/S10udev: 105: readlink: not found
/etc/rcs.d/S10udev: 1: usplash_write: not found
/etc/init.d/rc: 372: sh: not found
/etc/init.d/rc: 372: sh: not found
/etc/init.d/rc: 372: /etc/rcS.d/S13pcmciautils: not found
Segmentation fault
init: rcS main process (3872) killed by SEGV signal
init: Unable to execute "/bin/sh" for rc-default: No such file or directory
init: rc-default main process (5016) terminated with status 255[/COLOR]

Anyone have a clue why this is happening?  I've already specified the "Safe Graphics" mode during the installation process.

---

### Post by Marcus Derekus on 2008-11-24
Marcus again. I had the same (or at least very similar) error when I first tried to insall ubunt on my old desktop (15% stop and all). 

It may be a problem with the disc. perhaps you could try using another installation disc.

Or also try installing a different release.

One of the above were my issue i just can't place in my mind which one it was.  I know one of the above solved it though.

---

### Post by yogo on 2008-11-24
This has been interesting, I have found a few things out. One thing I had no idea why Cairo dock had a black background around the dock. I see it is because on 8.10 you need compiz for transparency. 

Anyways, I was playing around with this desktop that a neighbor dropped off. I bought it for thirty bucks with a monitor. It is an HP Pavillion a600n, kinda old but not bad other than the mobo is maxed out at i gig. I was surprised it has AGP and sata ports. So I slapped 8.04 on it but still no compiz, the onboard graphics is not as well as my Dell, not that it is great. So I am thinking of getting a card if that helps it run Compiz.

I may be living in Windows for a while, I have a new desktop arriving on Wednesday that has 4 gigs of memory and 500 on the HD with Vista 64bit premium. I believe my warranty is 90 days, so I will probably hesitate about adding Ubuntu so not to void the warranty.

Suggestions on an agp card are welcome.

TIA

---

### Post by Marcus Derekus on 2008-11-24
To yogo: Man i wish i could help on card recommendation, but i guess i'm more of a diagnoser then preventer. I really hope that works out though. (Some form of ATI card like a radeon or somthing would be my best guess but im not really sure.)

To blueflyt: Well i'm glad you decide to try out 8.04. I guess you don't need my help though cuz the package comes with installation instructions.

Good luck. Hope it works. And post if you have any problems!

---

### Post by blueflyt on 2008-11-24
> **Marcus Derekus said:**
> Marcus again. I had the same (or at least very similar) error when I first tried to insall ubunt on my old desktop (15% stop and all). 

It may be a problem with the disc. perhaps you could try using another installation disc.

Or also try installing a different release.

One of the above were my issue i just can't place in my mind which one it was.  I know one of the above solved it though.

I already have two disks of 8.10 burned, one at regular speed and one at the slowest (4x).  As far as I can tell, both disks are good as I've used them interchangeably this weekend to upgrade some of our boxes.  I spent several hours working on this particular box.  I'm throwing in the towel...I think the machine itself is just too old.  It could be something related to the BIOS, which I can't update any longer. In the meantime, I've got a nice graphics card that I'll use on another machine.   

As for the original box that was the genesis of this thread, it's perking along just fine without the advanced graphics capabilities.  I'm planning on reinstalling 8.04 on it next weekend and then working on making Evolution Mail compatible with Google calendar apps.  Thanks to all who posted on this thread, in particular the Derekus brothers.  You guys are awesome!

---

### Post by Marcus Derekus on 2008-11-24
Thanks man! It's been great helping out and i have learned so much from it (haven't we all?). 

These are the kind of challenging yet inticing threads that transform one from "novice" to "guru"!

All of you are AWESOME! 

BTW: blueflyt, on your old junkie, perhaps you might try installing 8.04. Just a suggestion.

GO UBUNTU!

(And as blueflyt basically put it:  Thank you microsoft for screwing up so bad that we were forced to find an alternitive to your OS.:lolflag:

---

### Post by yogo on 2008-11-24
Ok I need some help and ideas on this, that old HP Pavillion I bought seems to have more under the hood than I thought.

HP has specifications at max memory 1 gig HOWEVER it is an Asus board and listed at 2 gigs.

[COLOR=Red]Mb manufacturer name: ASUS A7V8X-LA

HP/Compaq name: Kelut-GL6E                                                                                    **CPU**                                          Socket A

AMD Athlon XP

Core frequency up to Athlon XP 3200+                                                                                    **Chipset**                                          VIA KM400A

VIA VT8237                                                                                    **Front Side Bus (FSB)**                                          400 / 333 / 266 MHz                                                                                    **Memory**                                          2 x 184-pin DDR DIMM sockets

Support up to maximum 2 GB memory (PC manufacturer's maximum memory may differ)[/COLOR]     

Now that extra gig may not sound like much BUT I would definitely have more use for it if I can add two gigs of memory than the current 512 that is in it.

Does anyone her know how to unlock a motherboard that only has Ubuntu installed, I am assuming there are some Windows utilities but it does not have Windows on it.

TIA

---

### Post by darkdan on 2008-12-02
Thank you all for this thread!  I finally got the resolution up on my new (to me) Dell Dimension 2350 and HP Pavilion D3857A monitor!

After a lot of playing around with that file, all I had to do was switch "i810" to "intel" and it worked!

And in case anyone in the future wants to see the settings:


Section "Device"
	Identifier	"i810"
	Driver		"intel"
	BusID		"PCI:0:02:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	HorizSync	30-50
	VertRefresh	50-100
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Generic Monitor"
	Device		"i810"
	DefaultDepth	24
	SubSection	"Display"
		Modes	"1024x768" "800x600"
	EndSubSection
EndSection

---

### Post by blueflyt on 2008-12-05
> **darkdan said:**
> Thank you all for this thread!  I finally got the resolution up on my new (to me) Dell Dimension 2350 and HP Pavilion D3857A monitor!

After a lot of playing around with that file, all I had to do was switch "i810" to "intel" and it worked!

And in case anyone in the future wants to see the settings:


Section "Device"
	Identifier	"i810"
	Driver		"intel"
	BusID		"PCI:0:02:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	HorizSync	30-50
	VertRefresh	50-100
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Generic Monitor"
	Device		"i810"
	DefaultDepth	24
	SubSection	"Display"
		Modes	"1024x768" "800x600"
	EndSubSection
EndSection

Were you able to get the advanced graphics to work?  I implemented your changes on my xorg.conf file and mine still comes up in "None" mode (the graphics effect).  Still can't get it to run in "Normal" mode.

---

