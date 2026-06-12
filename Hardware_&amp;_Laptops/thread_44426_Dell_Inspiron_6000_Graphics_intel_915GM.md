---
title: "Dell Inspiron 6000 Graphics intel 915GM?"
date: 2005-06-26
forum: Hardware &amp; Laptops
---

### Post by hotplainrice on 2005-06-26
I suspect my system is running intel 915GM.
I had to use the vesa driver and someone's xorg.conf to get my system running at max resolution my screen can support (1680x1050). Okay. Problem: Videos are choppy and crappy when played because of this vesa driver. I've seen many posts about i810 driver and didn't really bother to read everything. There's like so many methods to achieve usability. Someone guide me so that I dont waste my time!.

Thanks.

---

### Post by batrachian on 2005-08-02
Actually, I am able to set the resolution to 1280X800 with Vesa. However, the system freeze every 10 minutes. Anybody know how to install integrated video driver for Inspiron 6000?

---

### Post by tflovik on 2005-08-02
I have a Dell Inspiron 6000 with the i915 graphics.
I have tried Ubuntu and now Kubuntu. Both install with 3D configured automatically.
The only thing i can think of that is causing problems for you is the bios version.
I have bios version A05. I tried updating to version A06 and then i got a black screen when the laptop was starting x.
I had to go back to A05 and then everything was ok.
You can download bios version A05 from Dell.
Hope this will help you :)

---

### Post by batrachian on 2005-08-03
The newest version of Bios is A07 and that's what I have for my Insprion 6000.

Does anybody has the video driver successfully installed with bios version A07?

---

### Post by mbmonk on 2005-08-03
[QUOTE=batrachian]The newest version of Bios is A07 and that's what I have for my Insprion 6000.

Does anybody has the video driver successfully installed with bios version A07?[/QUOTE]

I have the A07 bois as well and have to use VESA as well to even get into XWindows.

---

### Post by tflovik on 2005-08-03
I think that you should try the A05 bios.
Maybe the thing they did in A06 is in A07 also.
Just download the file I6000A05.exe from dell.
Boot up in WinXp and double click the file and follow the instructions, it's wery easy to do.

---

### Post by batrachian on 2005-08-04
Yeah, however, it seems A05 is not available from dell website. :mad:

---

### Post by tflovik on 2005-08-04
You'r right they have removed it.
If you post your email address here i can mail it to you.

---

### Post by batrachian on 2005-08-04
I can't appreicate more. Please send it to [email]batrachian@gmail.com[/email].

Thank you so much! :razz:

---

### Post by tflovik on 2005-08-05
I tried sending you a mail, but i got it returned.
Are the mail address correct or the mailserver down?

---

### Post by mbmonk on 2005-08-05
[QUOTE=tflovik]You'r right they have removed it.
If you post your email address here i can mail it to you.[/QUOTE]

Could you send that file my way? :P.

---

### Post by CCH78 on 2005-08-05
I'm having the same issue, I updated to BIOS v. A07 and can not get X to work now. Can someone please send me V A05 (I6000A05.exe)  Thanks in Advance.

---

### Post by batrachian on 2005-08-06
[QUOTE=tflovik]I tried sending you a mail, but i got it returned.
Are the mail address correct or the mailserver down?[/QUOTE]

It is the correct address and I guess it might be too big for the mailbox.

Can you try [email]pin2000_01@yahoo.com[/email] as well?

Thanks a million.

---

### Post by batrachian on 2005-08-06
[QUOTE=tflovik]I tried sending you a mail, but i got it returned.
Are the mail address correct or the mailserver down?[/QUOTE]


Have you ever tried using usendit?  Just go to [www.usendit.net](www.usendit.net) and upload a file then fill in my email address. I should be able to download it from their site.

Thanks again.

---

### Post by tflovik on 2005-08-06
I have uploaded the file to yousendit.
Let me know if you got it.

---

### Post by CCH78 on 2005-08-06
Hey tflovik,

If you could send that to me as well I would appreciate it.

[email]chorrell@hotmail.com[/email]

Thanks in advance.

---

### Post by batrachian on 2005-08-06
[QUOTE=tflovik]I have uploaded the file to yousendit.
Let me know if you got it.[/QUOTE]
Not really. Did you fill in my email address?

Or you can just email me the link you got in your confirmation email.

Thanks.

---

### Post by tflovik on 2005-08-07
I must have done something wrong using Yousendit.
I tried again, and got a confirmation.
Check your yahoo mailaddress.

---

### Post by batrachian on 2005-08-07
File received. Really appreciate it!

---

### Post by holes1to18 on 2005-08-08
Could you please email me the file also?  Thank you.
[email]holes1to18@yahoo.com[/email]

-Jake

---

### Post by robfindlay on 2005-08-09
Can someone send that file my way also? 


[email]rob@robfindlay.org[/email]

or 

[email]slag7900@yahoo.com[/email]


tkns...

---

### Post by CCH78 on 2005-08-09
tflovik,

Thanks for the firmware. Worked like a charm.

---

### Post by batrachian on 2005-08-09
[QUOTE=CCH78]tflovik,

Thanks for the firmware. Worked like a charm.[/QUOTE]

After I updated the bios, where i am going to do then to update the video driver?

Thanks for the input.

---

### Post by tflovik on 2005-08-10
To all of you that have got the A05 bios!
You can try the live cd to check if it works, and then copy the xorg.conf that the live cd produces.
Anyway i'm posting my xorg.conf here(my screen is 1680x1050).

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
 FontPath "unix/:7100"   # local font server
 # if the local font server has problems, we can fall back on these
 FontPath "/usr/lib/X11/fonts/misc"
 FontPath "/usr/lib/X11/fonts/cyrillic"
 FontPath "/usr/lib/X11/fonts/100dpi/:unscaled"
 FontPath "/usr/lib/X11/fonts/75dpi/:unscaled"
 FontPath "/usr/lib/X11/fonts/Type1"
 FontPath "/usr/lib/X11/fonts/CID"
 FontPath "/usr/lib/X11/fonts/100dpi"
 FontPath "/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
 FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
 FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
 Load "bitmap"
 Load "dbe"
 Load "ddc"
 Load "dri"
 Load "extmod"
 Load "freetype"
 Load "glx"
 Load "int10"
 Load "record"
 Load "type1"
 Load "vbe"
EndSection

Section "InputDevice"
 Identifier "Generic Keyboard"
 Driver  "keyboard"
 Option  "CoreKeyboard"
 Option  "XkbRules" "xorg"
 Option  "XkbModel" "pc105"
 Option  "XkbLayout" "no"
EndSection

Section "InputDevice"
 Identifier "Configured Mouse"
 Driver  "mouse"
 Option  "CorePointer"
 Option  "Device"  "/dev/input/mice"
 Option  "Protocol"  "ImPS/2"
 Option  "Emulate3Buttons" "true"
 Option  "ZAxisMapping"  "4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option  "HorizScrollDelta" "0"
EndSection

Section "Device"
 Identifier "Intel Corporation Intel Default Card"
 Driver  "i810"
 BusID  "PCI:0:2:0"
EndSection

Section "Monitor"
 Identifier "Generic Monitor"
 HorizSync 31.5 - 100
 VertRefresh 60
 DisplaySize 320 200
 Option  "DPMS"
EndSection

Section "Screen"
 Identifier "Default Screen"
 Device  "Intel Corporation Intel Default Card"
 Monitor  "Generic Monitor"
 DefaultDepth 24
 SubSection "Display"
  Depth  1
  Modes  "1680x1050"
 EndSubSection
 SubSection "Display"
  Depth  4
  Modes  "1680x1050"
 EndSubSection
 SubSection "Display"
  Depth  8
  Modes  "1680x1050"
 EndSubSection
 SubSection "Display"
  Depth  15
  Modes  "1680x1050"
 EndSubSection
 SubSection "Display"
  Depth  16
  Modes  "1680x1050"
 EndSubSection
 SubSection "Display"
  Depth  24
		Modes		"1680x1050"
	EndSubSection
EndSection

Section "ServerLayout"
 Identifier "Default Layout"
 Screen  "Default Screen"
 InputDevice "Generic Keyboard"
 InputDevice "Configured Mouse"
 InputDevice "Synaptics Touchpad"
EndSection

Section "DRI"
 Mode 0666
EndSection


Hope this will help you.

---

### Post by varunus on 2005-08-10
tflovik,

Maybe you should post this over in Tips and Tricks.  Any inspiron users who find problems could get help easier that way...

If you need a place to host the A05 BIOS on the internet, i have some web space I can loan you if you send the file my way.  agore187 (AT) gmail (DOT) com for me.

---

### Post by joebrandt on 2005-08-15
[QUOTE=tflovik]To all of you that have got the A05 bios!
You can try the live cd to check if it works, and then copy the xorg.conf that the live cd produces.
Anyway i'm posting my xorg.conf here(my screen is 1680x1050).

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
 FontPath "unix/:7100"   # local font server
 # if the local font server has problems, we can fall back on these
 FontPath "/usr/lib/X11/fonts/misc"
 FontPath "/usr/lib/X11/fonts/cyrillic"
 FontPath "/usr/lib/X11/fonts/100dpi/:unscaled"
 FontPath "/usr/lib/X11/fonts/75dpi/:unscaled"
 FontPath "/usr/lib/X11/fonts/Type1"
 FontPath "/usr/lib/X11/fonts/CID"
 FontPath "/usr/lib/X11/fonts/100dpi"
 FontPath "/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
 FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
 FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
 Load "bitmap"
 Load "dbe"
 Load "ddc"
 Load "dri"
 Load "extmod"
 Load "freetype"
 Load "glx"
 Load "int10"
 Load "record"
 Load "type1"
 Load "vbe"
EndSection

Section "InputDevice"
 Identifier "Generic Keyboard"
 Driver  "keyboard"
 Option  "CoreKeyboard"
 Option  "XkbRules" "xorg"
 Option  "XkbModel" "pc105"
 Option  "XkbLayout" "no"
EndSection

Section "InputDevice"
 Identifier "Configured Mouse"
 Driver  "mouse"
 Option  "CorePointer"
 Option  "Device"  "/dev/input/mice"
 Option  "Protocol"  "ImPS/2"
 Option  "Emulate3Buttons" "true"
 Option  "ZAxisMapping"  "4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option  "HorizScrollDelta" "0"
EndSection

Section "Device"
 Identifier "Intel Corporation Intel Default Card"
 Driver  "i810"
 BusID  "PCI:0:2:0"
EndSection

Section "Monitor"
 Identifier "Generic Monitor"
 HorizSync 31.5 - 100
 VertRefresh 60
 DisplaySize 320 200
 Option  "DPMS"
EndSection

Section "Screen"
 Identifier "Default Screen"
 Device  "Intel Corporation Intel Default Card"
 Monitor  "Generic Monitor"
 DefaultDepth 24
 SubSection "Display"
  Depth  1
  Modes  "1680x1050"
 EndSubSection
 SubSection "Display"
  Depth  4
  Modes  "1680x1050"
 EndSubSection
 SubSection "Display"
  Depth  8
  Modes  "1680x1050"
 EndSubSection
 SubSection "Display"
  Depth  15
  Modes  "1680x1050"
 EndSubSection
 SubSection "Display"
  Depth  16
  Modes  "1680x1050"
 EndSubSection
 SubSection "Display"
  Depth  24
		Modes		"1680x1050"
	EndSubSection
EndSection

Section "ServerLayout"
 Identifier "Default Layout"
 Screen  "Default Screen"
 InputDevice "Generic Keyboard"
 InputDevice "Configured Mouse"
 InputDevice "Synaptics Touchpad"
EndSection

Section "DRI"
 Mode 0666
EndSection


Hope this will help you.[/QUOTE]
 How do I determine my bios version?  I have a Dell Inspiron 6000 circa June 05 with Intel  915 chipset driver i810.  3d not working other than that beautimous screen.  Would like 3d so I can play UT2004 and neverwinter nights though.

---

### Post by andrew_CU on 2005-08-16
[QUOTE=tflovik]You'r right they have removed it.
If you post your email address here i can mail it to you.[/QUOTE]


tflovik,

Could you send that  file to me as well, I would appreciate it very much.

[email]andrewcuhk@hotmail.com[/email]

Thanks in advance.

---

### Post by andrew_CU on 2005-08-17
tflovik,

Got it. Thanks a lot!

---

### Post by remy the stampede on 2005-08-22
Would anyone be willing to send the A5 bios to me?  r3my at cox.net.  

Also, I see Dell has the A8 bios posted.  Has anyone tried with that?

---

### Post by drizek on 2005-08-23
[QUOTE=remy the stampede]Would anyone be willing to send the A5 bios to me?  r3my at cox.net.  

Also, I see Dell has the A8 bios posted.  Has anyone tried with that?[/QUOTE]
 just so you guys know, the 3d works great out of the box in breezy with the i810 drivers(using a06 bios, i810 didnt work with hoary).

---

### Post by Iceman_vtf on 2005-08-28
Could someone send it to me too?  (hot_boy [at] skynet [dot] be)

I have tried upgrading the firmware from AO7 to AO8 but it still doesn't work...

I could also host this file for a while (at least until Breezy comes out in its final release). It's a little annoying having to wait for someone's reply when you're installing a machine (especially when it's not yours).  :roll: 

Anyway, thanks in advance.

Iceman

---

### Post by joebrandt on 2005-08-28
A08 is no good either.
May I have A05 also, please.
[email]joe.brandt@gmail.com[/email]

Thanks in advance.
Joe Brandt

ps using Breezy i810 not working

---

### Post by Iceman_vtf on 2005-08-28
oops, no mean to delete

---

### Post by dixonstalbert on 2005-08-29
could someone send me I6000A05 to dixonjnk AT hotmaildotcom

---

### Post by dixonstalbert on 2005-08-29
I was able to track down the Inspiron 6000 BIOS version A05 here:

[http://jackdied.com/static/I6000A05.exe](http://jackdied.com/static/I6000A05.exe)


I have installed it on my inspiron 6000 /Intel 915 and have a display and a mouse!

now to figure out how to get intel wireless wirelessing


thanks jackdied!

---

### Post by snowjunkie on 2005-08-31
I didn't think it was possible to get 1680x1050 on a dell inspiron 6000 LCD anyway?  In xp the highest you can get is 1280x800.  I tried the xorg.conf file that was attached and it didn't work for me... GNOME still only gave me 1280x800 as the highest.

Any ideas?

---

### Post by tflovik on 2005-09-01
When you order an Inspiron 6000 Laptop you specify if you want it delivered with 1280X800, 1680X1050 or 1900X1200 resolution. All this resolutions work in Linux.
Of cource it's a price difference between them.

---

### Post by snowjunkie on 2005-09-01
I upgraded to the A05 bios and now I get some kind of fatal error listed on booting up regarding my wireless card, although wireless still works ok...  It might have been appearing before and I didn't notice it.

---

### Post by ceverett on 2005-09-21
OK, I'vie downloaded this BIOS flash thingie, how do I get it to run without windows on my latptop?????

---

### Post by caporaso on 2005-09-21
[QUOTE=tflovik] 1280X800, 1680X1050 or 1900X1200 resolution. All this resolutions work in Linux.[/QUOTE]


Has anyone got this working at 1920 x 1200 on Linux? I have the appropriate hardware, but see the following related lines in my Xorg.0.log file (grep for lines containing '1920'):

(II) I810(0): Display Info: LFP (local flat panel): attached: TRUE, present: TRUE, size: (1920,1200)
(II) I810(0): Size of device LFP (local flat panel) is 1920 x 1200
(II) I810(0): Lowest common panel size for pipe B is 1920 x 1200
(II) I810(0): PanelID returned panel resolution : 1920x1200
(II) I810(0): Not using mode "1920x1200" (no mode of this name)

I have heard that people have solved this issue, but I am yet to figure it out for myself.

Thanks!
Greg

---

### Post by chocbar31 on 2005-09-22
This may help some:

[http://www.bay-wolf.com/flashbios.htm](http://www.bay-wolf.com/flashbios.htm)

choc

---

### Post by Pumpino on 2005-09-24
The Kubuntu Breezy preview live CD works fine with the A08 bios.  I tested it.

However, I switched back to A05 in the meantime, as I'm running Hoary.

Even with A05, I cannot run live CDs such as Kanotix, MEPIS or SUSE.  I really want to be able to try other distros as live CDs.  Does anyone know what it is about the bios version that is causing problems, and also how to run other live CDs?  Maybe there is a setting in the bios that can be changed, or maybe we all need to email Dell and make them aware of the problem.

---

### Post by suleiman on 2005-10-05
hello all...I am tracing a problem with the video on my Dell D610 Latitute laptop. I also am running the i915gm graphics processor (same as on this machine) the problem is that my bios automatically allocates a base amount of video memory at boot, of only 8 mb ram. I need to change that amount, but the bios locks me out from being able to do so. I was wondering, since many of you were able to boot into ubuntu by downgrading your bioses, if the older versions of your bioses have different video bioses, and either permit changes to the ram size, or allocate a higher amount of ram at boot. Please let me know thanks! 

P.S. If anyone could let me know what the version is of their video bios, that would be rockin.

---

### Post by Pumpino on 2005-10-13
For all those with Dell Inspiron 6000 laptops, the A09 BIOS revision was released a few days ago.  It works fine with Kubuntu 5.10.  Not sure if it works with Hoary.

[http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R109329&SystemID=INS_PNT_6000&os=WW1&osl=en&deviceid=6999&devlib=0&typecnt=1&vercnt=3&formatcnt=1&fileid=142094](http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R109329&SystemID=INS_PNT_6000&os=WW1&osl=en&deviceid=6999&devlib=0&typecnt=1&vercnt=3&formatcnt=1&fileid=142094)

---

### Post by snowjunkie on 2005-10-14
[QUOTE=Pumpino]For all those with Dell Inspiron 6000 laptops, the A09 BIOS revision was released a few days ago.  It works fine with Kubuntu 5.10.  Not sure if it works with Hoary.

[/QUOTE]

Thanks Man, I'll check it out next week.  I'm off on holidays tonight for a week!  Yipee!

---

### Post by MetalMusicAddict on 2005-10-19
[QUOTE=suleiman]hello all...I am tracing a problem with the video on my Dell D610 Latitute laptop. I also am running the i915gm graphics processor (same as on this machine) the problem is that my bios automatically allocates a base amount of video memory at boot, of only 8 mb ram. I need to change that amount, but the bios locks me out from being able to do so. I was wondering, since many of you were able to boot into ubuntu by downgrading your bioses, if the older versions of your bioses have different video bioses, and either permit changes to the ram size, or allocate a higher amount of ram at boot. Please let me know thanks! 

P.S. If anyone could let me know what the version is of their video bios, that would be rockin.[/QUOTE]
I also have this problem but on a Inspiron 2200. It should be 64 megs. Or is that normally handeled by the OS (windows) Grrr...

---

### Post by denvervp on 2005-10-20
[QUOTE=tflovik]I have a Dell Inspiron 6000 with the i915 graphics.
I have tried Ubuntu and now Kubuntu. Both install with 3D configured automatically.
The only thing i can think of that is causing problems for you is the bios version.
I have bios version A05. I tried updating to version A06 and then i got a black screen when the laptop was starting x.
I had to go back to A05 and then everything was ok.
You can download bios version A05 from Dell.
Hope this will help you :)[/QUOTE]

I have A05 version of BIOS. Ubuntu runs great with preloaded drivers for everything. But using the VESA (generic driver) for display, I can not play any kind of videos or DVDs. Anyone know where to download or how to install the correct display driver for Dell Inspiron 6000?
Thanks.

---

