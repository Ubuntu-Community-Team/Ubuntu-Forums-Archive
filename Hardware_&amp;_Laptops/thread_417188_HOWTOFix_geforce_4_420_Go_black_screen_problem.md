---
title: "HOWTO:Fix geforce 4 420 Go black screen problem"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by hesicong2006 on 2007-04-21
I've been having trouble with my laptop geforce 4 420Go video card on NVIDIA driver. The problem, like most other 420Go users, is the BLANK SCREEN problem.
The problem appear on my BENQ Joybook 3000 is like this: 
After I installed the restricted driver and reboot , it's blank screen when I login but I can hear the sound. I type my user and password, it seems OK and login. But I still get blank screen.
I can get to the terminal when I press CTRL+ALT+F1 and I can switch back again by pressing CTRL+ALT+F7.
I make sure that Xserver and the video driver are both working fine, but video driver may not initialized the LCD display!
So I google again and I found this article: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/96430](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/96430)
This is a bug report about this problem. I read about this L--O--N--G discussion and near the bottom of the article, I see  jdriessen( said on 2007-04-12) told us :
"in response to my previous post
those of you having similar problems if you have a Geforce4 420 Go 32MB.
the 9631 driver is looking for a CRT monitor and not and LCD (those of you having the problem on LCD monitors)
to fix this:
edit your xorg.conf
go to Section "Screen"
below defaultdepth, add: Option "UseDisplayDevice" "UFP-0"
this should fix the blank screen issue on LCD displays."

I tried it ,but it not work!
And again, very lucky, I googled for keyword ""UseDisplayDevice" I found some discussion about it. In a Chinese forum, some one managed to let even Geforce 2 MX to work with beryl!
He said add Option "UseDisplayDevice" "DFP" to xorg.conf and reboot.

I tried it, YEAH! It works! NVIDIA logo appears when I before my login(I set Option "NoLogo" "False"), and compiz in ubuntu 7.04 works very well!!!!

So, if you can hear the login sound, if you use 96.31 driver, if you use ubuntu 7.04

[COLOR="Red"]TRY ADD 
   Option "UseDisplayDevice" "DFP" or
   Option "UseDisplayDevice" "DFP-0"
 to help this NVIDIA Driver find your first LCD display! 
[/COLOR]

---

### Post by Dr_Deadmeat on 2007-04-21
Thank you very much! I owe you one for this fix =)

---

### Post by hesicong2006 on 2007-04-21
Did you try this and your laptop worked?

---

### Post by Dr_Deadmeat on 2007-04-22
Yes, but whenever I reboot my computer my X-server wont start and I get a max resolution wont go higher than 800x600 with 50hz, but I am working on that issue now =P

---

### Post by markthecarp on 2007-04-22
I've been having just terrible luck getting nVidia 9631 and previous versions working with this chipset.

My machine: Toshiba Satellite 1415 S173; nVidia GeForce4 420 Go 16M VRAM. I found _a solution here...
[http://www.nvnews.net/vbulletin/showthread.php?t=84773]("http://www.nvnews.net/vbulletin/showthread.php?t=84773")

I now have 1024x768; glxgears reports 295 fps.

hopefully helpful

-mark
now to some 3d desktop goodness...

---

### Post by Dr_Deadmeat on 2007-04-22
Thank you very much... It now works flawlessy (I think. I havent rebooted my computer yet).
At any rate should this fix be posted on the other threads about resolution troubles and it might help other people too...

Thank you again...

---

### Post by markthecarp on 2007-04-22
I think yes. I've had this laptop for two years; been using Linux since '99; this is the best I've ever been able to get the graphics setup.

Compiz is locking it up but that's another issue.

-mark

---

### Post by marioquark on 2007-04-28
and how about the NOT FOUND nvidia kernel module?
what can i do?

---

### Post by grolschie on 2007-04-28
I have a Toshiba Satellite 2410 with the same issue with my **Geforce4 420 Go**.  After installing Ubuntu Feisty Fawn and installing the Restricted Drivers, I was greeted with a black screen (but could hear the startup sounds, etc).

I then added the following line to the **Device section** of my xorg.conf:
*Option    "UseDisplayDevice"    "DFP"*

However the screen was set to **800x600@50hz** no matter what I did.  The solutions here didn't work for me.  I solved it here:    [_http://forums.computers.toshiba-europe.com/jive3/thread.jspa?threadID=19664_]("http://forums.computers.toshiba-europe.com/jive3/thread.jspa?threadID=19664")

Basically here is what I did:

1). I added the following line to /etc/modprobe.d/options:
    *options nvidia NVreg_SoftEDIDs=0 NVreg_Mobile=1 NVreg_EnableAGPFW=1 NVreg_EnableAGPSBA=1*

2). Downloaded this file to /etc/X11 folder:
    _[http://core.syscall.org/linux/Toshiba_s_1410.bin](http://core.syscall.org/linux/Toshiba_s_1410.bin)_

3). Add the following line to the **Monitor section** of /etc/X11/xorg.conf:
   *Option "CustomEDID" "DFP-0:/usr/lib/Toshiba_s_1410.bin"*

I hope that this helps somebody.

---

### Post by mayamaniac on 2007-04-30
Thank you hesicong2006, I have a Dell Inspiron 8200 with a Geforce 440 64M. I had the black screen problem after installing the nvidia driver with Envy.

I used the  Option "UseDisplayDevice" "DFP-0" line and that works. :)

---

### Post by deroby on 2007-04-30
Woohoo, I too have an Inspiron 8200, and adding the option indeed fixed the 'blank' screen issue !

(I now have another issue, namely that my resolution seems limited to 1400x1050, but I'll look for that in a minute... I'm already exited that it works this far =)

For those that are new to Ubuntu (or unix in general I suspect) too, here's the steps I did to edit the xorg.conf file, took me some trial & error so there might be easier ways to do this (newbie alert =) : 

* Press ctrl-alt-F1 to switch to a 'free' terminal
* log in
* type : "cd /etc/X11" + enter  (always keep in mind : linux is CASE-SENSITIVE !!!)
* type : "emacs xorg.conf"

Now 2 things may happen : 
   + 1. you already have emacs installed, in that case you will enter the editor
   + 2. you don't have the editor installed and a list of packages is presented with an 'apt'-command line on how to get them 
=> in the latter case : simply type the proposed command line with your preferred package (I used e3 because it was the least amount of typing 8) )

once the package is installed, retry "emacs xorg.conf" to see if things worked.

Since this is a system file, we cannot simply make changes to it, but will need to do this as the super user. Hence, we first need to exit emacs again with our current 'lowly' credentials : in my case I used : CTRL-X folllowed by CTRL-C and needed to press N to indicate I did not want to save. (if you didn't make any changes, it probably won't ask for this). 

On with the show : 

* Type : "sudo emacs xorg.conf" + Enter
(as a safety measure you will have to confirm with your password)
=> use the editor to add the lines as proposed above
=> again, press CTRL-X, CTRL-C to close the editor, this time press Y to save the changes.

Next thing : reboot the machine, for this you need to 
* Type : "sudo reboot"
(and again, confirm with your password)

The computer will then reboot and YAY, it works...
Going back to Desktop Effects allows you to do the wobbly thing stuff, neat ! =)

---

### Post by marcelloconti on 2007-05-07
Look this, solution in my case.

[http://www.nvnews.net/vbulletin/showthread.php?t=54638&page=9]("http://www.nvnews.net/vbulletin/showthread.php?t=54638&page=9")

---

### Post by drowner on 2007-05-08
> **hesicong2006 said:**
> I've been having trouble with my laptop geforce 4 420Go video card on NVIDIA driver. The problem, like most other 420Go users, is the BLANK SCREEN problem.
The problem appear on my BENQ Joybook 3000 is like this: 
After I installed the restricted driver and reboot , it's blank screen when I login but I can hear the sound. I type my user and password, it seems OK and login. But I still get blank screen.
I can get to the terminal when I press CTRL+ALT+F1 and I can switch back again by pressing CTRL+ALT+F7.
I make sure that Xserver and the video driver are both working fine, but video driver may not initialized the LCD display!
So I google again and I found this article: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/96430](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/96430)
This is a bug report about this problem. I read about this L--O--N--G discussion and near the bottom of the article, I see  jdriessen( said on 2007-04-12) told us :
"in response to my previous post
those of you having similar problems if you have a Geforce4 420 Go 32MB.
the 9631 driver is looking for a CRT monitor and not and LCD (those of you having the problem on LCD monitors)
to fix this:
edit your xorg.conf
go to Section "Screen"
below defaultdepth, add: Option "UseDisplayDevice" "UFP-0"
this should fix the blank screen issue on LCD displays."

I tried it ,but it not work!
And again, very lucky, I googled for keyword ""UseDisplayDevice" I found some discussion about it. In a Chinese forum, some one managed to let even Geforce 2 MX to work with beryl!
He said add Option "UseDisplayDevice" "DFP" to xorg.conf and reboot.

I tried it, YEAH! It works! NVIDIA logo appears when I before my login(I set Option "NoLogo" "False"), and compiz in ubuntu 7.04 works very well!!!!

So, if you can hear the login sound, if you use 96.31 driver, if you use ubuntu 7.04

[COLOR="Red"]TRY ADD 
   Option "UseDisplayDevice" "DFP" or
   Option "UseDisplayDevice" "DFP-0"
 to help this NVIDIA Driver find your first LCD display! 
[/COLOR]

Thankyou hesicong! This worked PERFECTLY for me

Beginners see my post here: [http://ubuntuforums.org/showthread.php?t=436952](http://ubuntuforums.org/showthread.php?t=436952)
for a REALLY basic guide on  how to do this

---

### Post by jdriessen on 2007-05-09
worked for me!!

is this solution in the wiki??

---

### Post by steevols on 2007-05-10
Thanks very much!

I will point out that if you use a Linux that lets you compile Nvidia drivers from source, the 8774 driver works out of the box.

Thanks again!

---

### Post by Bruegger on 2007-06-04
Hi guys,
any way the 9631 or 9639 drivers can be made to work with geforce2 mx integrated gpu on a feisty fawn??
not having any luck on it so far.
have to use windows to post this.
any help will be really appreciated.

thx.

---

### Post by marioquark on 2007-06-04
yes, 4 me worked:

this is my xorg.conf:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Nov  9 17:55:20 PST 2006

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

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/CID"
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "it"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "Emulate3Buttons" "true"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
    Option         "SHMConfig" "true"
EndSection

Section "Monitor"
    Identifier     "Monitor Generico"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV17 [GeForce4 420 Go]"
    Driver         "nvidia"
    Option  "CustomEDID" "DFP-0:/etc/X11/Toshiba_s_1410.bin"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV17 [GeForce4 420 Go]"
    Monitor        "Monitor Generico"
    DefaultDepth    24
    Option         "UseDisplayDevice" "DFP-0"
    # beryl
    Option          "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       8
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

and this is my /etc/modprobe.d/options

```
# Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2

options nvidia NVreg_SoftEDIDs=0 NVreg_Mobile=1 NVreg_EnableAGPFW=1 NVreg_EnableAGPSBA=1

```

note that you have to download the **DFP-0:/etc/X11/Toshiba_s_1410.bin** file from the nvidia forum.

then use envy (search google!) to install the specified driver
good luck!
quark

---

### Post by ammark on 2007-08-02
> **marioquark said:**
> yes, 4 me worked:
...
note that you have to download the **DFP-0:/etc/X11/Toshiba_s_1410.bin** file from the nvidia forum.

then use envy (search google!) to install the specified driver
good luck!
quark

I've downloaded envy, but where can I get the Toshiba_s_1410.bin file? the link given earlier is dead. Please post a working link here please. Or someone who has it please put it up on megauploads and give the link here please.

Ammar

Toshiba Satellite 2455-S305
Intel P4 2.4GHz
512 MB DDR RAM
32 MB Nvidia Geforce Go 420 graphics controller
on Feisty.

---

### Post by Dr_Deadmeat on 2007-08-04
> **ammark said:**
> I've downloaded envy, but where can I get the Toshiba_s_1410.bin file? the link given earlier is dead. Please post a working link here please. Or someone who has it please put it up on megauploads and give the link here please.

Ammar

Toshiba Satellite 2455-S305
Intel P4 2.4GHz
512 MB DDR RAM
32 MB Nvidia Geforce Go 420 graphics controller
on Feisty.

I have uploaded the file on my personal server. I'll try to have 100% uptime on it, but I am on vacation and a lightning might take it down.
Anyway the link is [http://drdeadmeat.dnsalias.com/ssh/edid.bin](http://drdeadmeat.dnsalias.com/ssh/edid.bin).

Just copy the file to a location of your choice and you make your /etc/X11/xorg.conf have the option marked with bold here. (You might need some of the other options too, this is how my /etc/X11/xorg.conf is like)

```

/etc/X11/xorg.conf:

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA GeForce 4 420go"
    Monitor        "Standard skjerm"
    DefaultDepth   16
#   Option         "ExactModeTimingsDVI"
    Option         "UseEdidDpi" "FALSE"
    Option         "ModeValidation" "NoEdidDFPMaxSizeCheck, NoVesaModes"
    Option         "UseDisplayDevice" "DFP"
    Option         "NoVesaModes" "true"
    Option         "NoLogo" "true"
    **Option         "CustomEDID" "DFP-0:*/etc/X11/*edid.bin"**
#    Option        "AddARGBGLXVisuals" "true"
#    Option        "RenderAccel" "true"
#    Option        "AllowGLXWithComposite" "true"
#    Option        "backingstore" "true"
#    Option        "TripleBuffer" "true"

```
The italic style characters is the path to your edid.bin file. Just change it to your own needs.

I hope this gave you the help you needed, and if you need more help I will try to help you as much as I can :)

---

### Post by tombott on 2007-11-15
Thanks to everybody for all the info on this one.
Has anybody managed to get the desktop effects working?

---

### Post by danlaptic on 2008-07-13
> **grolschie said:**
> I have a Toshiba Satellite 2410 with the same issue with my **Geforce4 420 Go**.  After installing Ubuntu Feisty Fawn and installing the Restricted Drivers, I was greeted with a black screen (but could hear the startup sounds, etc).

I then added the following line to the **Device section** of my xorg.conf:
*Option    "UseDisplayDevice"    "DFP"*

However the screen was set to **800x600@50hz** no matter what I did.  The solutions here didn't work for me.  I solved it here:    [_http://forums.computers.toshiba-europe.com/jive3/thread.jspa?threadID=19664_]("http://forums.computers.toshiba-europe.com/jive3/thread.jspa?threadID=19664")

Basically here is what I did:

1). I added the following line to /etc/modprobe.d/options:
    *options nvidia NVreg_SoftEDIDs=0 NVreg_Mobile=1 NVreg_EnableAGPFW=1 NVreg_EnableAGPSBA=1*

2). Downloaded this file to /etc/X11 folder:
    _[http://core.syscall.org/linux/Toshiba_s_1410.bin](http://core.syscall.org/linux/Toshiba_s_1410.bin)_

3). Add the following line to the **Monitor section** of /etc/X11/xorg.conf:
   *Option "CustomEDID" "DFP-0:/usr/lib/Toshiba_s_1410.bin"*

I hope that this helps somebody.

1.  This link [http://core.syscall.org/linux/Toshiba_s_1410.bin](http://core.syscall.org/linux/Toshiba_s_1410.bin) is dead.  

2.  Another user posted this link to the .bin file [http://drdeadmeat.dnsalias.com/ssh/edid.bin](http://drdeadmeat.dnsalias.com/ssh/edid.bin)  but it seems to be dead too.

3.  I found this link [http://users.zenwalk.org/user-accounts/ursvik/EDID/](http://users.zenwalk.org/user-accounts/ursvik/EDID/)

It seems to be working as of today, 13-July-2008.
 
I hope this helps keep this thread updated.

---

### Post by danlaptic on 2008-07-13
> **grolschie said:**
> I have a Toshiba Satellite 2410 with the same issue with my **Geforce4 420 Go**.  After installing Ubuntu Feisty Fawn and installing the Restricted Drivers, I was greeted with a black screen (but could hear the startup sounds, etc).

I then added the following line to the **Device section** of my xorg.conf:
*Option    "UseDisplayDevice"    "DFP"*

However the screen was set to **800x600@50hz** no matter what I did.  The solutions here didn't work for me.  I solved it here:    [_http://forums.computers.toshiba-europe.com/jive3/thread.jspa?threadID=19664_]("http://forums.computers.toshiba-europe.com/jive3/thread.jspa?threadID=19664")

Basically here is what I did:

1). I added the following line to /etc/modprobe.d/options:
    *options nvidia NVreg_SoftEDIDs=0 NVreg_Mobile=1 NVreg_EnableAGPFW=1 NVreg_EnableAGPSBA=1*

2). Downloaded this file to /etc/X11 folder:
    _[http://core.syscall.org/linux/Toshiba_s_1410.bin](http://core.syscall.org/linux/Toshiba_s_1410.bin)_

3). Add the following line to the **Monitor section** of /etc/X11/xorg.conf:
   *Option "CustomEDID" "DFP-0:/usr/lib/Toshiba_s_1410.bin"*

I hope that this helps somebody.

I just want to warn that for the above mentioned step three says to add the following to xorg.conf

option "CustomEDID" "DFP-0:/usr/lib/Toshiba_s_1410.bin

You should actually have the Toshiba_s_1410.bin file located in usr/lib.

The above directions have the Toshiba_s_1410.bin file downloaded to the /etc/X11 folder so you are going to have to move the file to usr/lib/ for the added option to xorg.conf to work.  

If all goes well it should eliminate the black bar at the right and allow for screen resolution adjustment. 

It worked for my Toshiba Satellite 1415-s173 running Ubuntu 8.04

---

### Post by Dr_Deadmeat on 2008-07-14
> **danlaptic said:**
> 1.  This link [http://core.syscall.org/linux/Toshiba_s_1410.bin](http://core.syscall.org/linux/Toshiba_s_1410.bin) is dead.  

2.  Another user posted this link to the .bin file [http://drdeadmeat.dnsalias.com/ssh/edid.bin](http://drdeadmeat.dnsalias.com/ssh/edid.bin)  but it seems to be dead too.

3.  I found this link [http://users.zenwalk.org/user-accounts/ursvik/EDID/](http://users.zenwalk.org/user-accounts/ursvik/EDID/)

It seems to be working as of today, 13-July-2008.
 
I hope this helps keep this thread updated.


The [http://drdeadmeat.dnsalias.com/ssh/edid.bin](http://drdeadmeat.dnsalias.com/ssh/edid.bin) link is dead because I am on vacation, and the server went down because of a thunder... I expect it to get up in august, but I cannot promise anything...

---

