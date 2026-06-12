---
title: "X server problem"
date: 2005-11-22
forum: General Help
---

### Post by Fittersman on 2005-11-22
I am having so much trouble with installing Ubuntu 5.04. It installs fine but when I'm required to reboot and finish installing it gives me a black screen that is the terminal. The problem is that the screens are found but dont have a usable configuration or something. My video card is a radeon 7500, monitor is an optiquest something, computer is a compaq presario. There could be a problem with my intel(R) 82845G/GL/GE/PE/GV Graphics Controller because on my windows operating system I had to disable it because the cursor when moved to the left side of the screen it disappeared and kept going off the screen and disabling it seemed to fix the problem. 

If you can help me on this problem it would be greatly appreciated seeing as how linux is better than windows.

---

### Post by narcolept on 2005-11-22
can you provide your /etc/X11/xorg.conf from the video card section to the end?  Also, is there a specific error about a certain line?

---

### Post by Fittersman on 2005-11-23
is there any way that i could print it out or something instead of having to write all that out and re-type it? (using the terminal)

---

### Post by Fittersman on 2005-11-23
o ya and talk in real beginner language beccause i know little about the program

---

### Post by Fittersman on 2005-11-23
well i got this thing im not sure if its what you want but it might help.

when its installing and oking everything this fails: temporary failure in name resolution

and this is the warning thing i get after:

I cannot start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?

and when i select yes i get this:

(a bunch of stuff that isnt important)

(==) using config file: /etc/X11/xorg.conf

skipping

/usr/X11R6/Lib/modules/extensions/LibGLcore.aim_debug_clip.0: No symbols found

skipping

/usr/X11R6/lib/modules/extension/libGLcore.aim_debug_norm.0: No symbols found

(EE) I810(0): cannot read V_BIOS 

(EE) I810(0): UBE initialization failed

(EE) Screen(s) found, but none have a usable configuration.

Fatal server error: no screens found


Then you click OK and it goes back to the other menu i gave you at the start
and when you click NO it says "I will disable this X server for now. Restart GDM when it is configured correctly.

After that instead of having the nice login screen and all that stuff all i receive is the terminal on a black screen.

Hopefully that helps you. If you need any other info i will get it to you later because im at school now and not on my computer.

---

### Post by Fittersman on 2005-11-23
ok and i think this is what you actually asked of me. found in etc/X11/xorg.conf or something like that. Hope it helps ya. There is another warning but it is increadably long and Im not about to rewrite it out.

Section "Device"
       Identifier        "Intel corporation 82845G/G[Brookdale-G]/GE Chipset Inset Integrated Graphics Device"
       Driver            "i810"
       BusID            "PCI:0:2:0"
Endsection

Section "Monitor"
       Identifier        "Q71B-8"
       Option           "DPMS"
Endsection

Section "Screen"
       Idenifier         "Default Screen"
       Device           "Intel corporation 82845G/G[Brookdale-G]/GE Chipset Inset Integrated Graphics Device"
       Monitor          "Q71B-8"
       Default Depth  24
       Subsection     "Display"
                 Depth 1
                 Modes "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
       EndSubsection

       Subsection     "Display"
                 Depth 4
                 Modes "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
       EndSubsection

       Subsection     "Display"
                 Depth 8
                 Modes "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
       EndSubsection

       Subsection     "Display"
                 Depth 15
                 Modes "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
       EndSubsection

       Subsection     "Display"
                 Depth 16
                 Modes "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
       EndSubsection

       Subsection     "Display"
                 Depth 24
                 Modes "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
       EndSubsection

Section "Serverlayout"
       Identifier       "Default Layout"
       Screen          "Default Screen"
       InputDevice   "Generic Keyboard"
       InputDevice   "Configured Mouse"

Section "DRI"
      Mode     0666

---

### Post by Carwash on 2005-11-23
Im also having a very similar problem.

> 
Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?


-> Yes

> 
X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174819 [email]root@crested.warthogs.hbd.com[/email])
Release Date: 9 Februaru 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System : Linux 2.6.8.1 x86_64
Current Operating System: Linux shuttlewash 2.6.12-9-amd64-generic #1
Mon Oct 10 13:27:39 BST 2005 x86_64
Build Date: 10 October 2005
Before reporting problems, check [http://wiki.X.org](http://wiki.X.org)
to make sure that you have the latest version.
Module Loader Present
OS Kernel: Linux version 2.6.12-9-amd64-generic (buildd@king) (gcc version 3.4.5 20050809 (prerelease) Unbuntu 3.4.4-6unbuntu8)) #1 Mon Oct 10 13:27:39 BST 2005
Markers: (--) probed, (**) from config file, (==) default setting, (++) from command line, (!!) notice, (II) informational, (WW) warning, (EE) error, (NI) not implemented, (??) unknown.

(==) Log file: "/var/log/Xorg.0.log", Time: Thu Nov 24 00:42:32 2005
(==) Using config file: "/etc/X11/xorg.conf"
Skipping
"/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found

#1

Skipping

"/usr/X11R6/lib/modules/extensions/libGLcore.a:n_debug_norm.o":  No symbols found

Skipping

"/usr/X11R6/lib/modules/extensions/libGLcore.a:n_debug_xform.o":  No symbols found

cc

(EE) No devices detected

Fatal server error:
no screens found

Please consult the The X.Org Foundation support at [http://wiki.X.Org](http://wiki.X.Org) for help.  Please also check the log file at "/var/log/Xorg.0.log" for additional information.


-> ok

> 
Would you like to view the detailed X server output as well?


-> yes

> 
X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174819 [email]root@crested.warthogs.hbd.com[/email])
Release Date: 9 Februaru 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.8.1 x86_64 [ELF]
Current Operating System: Linux shuttlewash 2.6.12-9-amd64-generic #1
Mon Oct 10 13:27:39 BST 2005 x86_64
Build Date: 10 October 2005
Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org) to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-amd64-generic (buildd@king) (gcc version 3.4.5 20050809 (prerelease) (ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:27:39 BST 2005
Markers: (--) probed, (**) from config file, (==) default setting, (++) from command line, (!!) notice, (II) informational, (WW) warning, (EE) error, (NI) not implemented, (??) unknown.

(==) Log file: "/var/log/Xorg.0.log", Time: Thu Nov 24 00:42:32 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |--> Screen "Default Screen" (0)
(**) |     |--> Monitor "Generic Monitor"
(**) |     |-->Device "ATi Technologies, Inc. ATI Default Card"
(**) |--> Input Device "Generic Keyboard"
(**) |--> Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
Entry deleted from font path.
(WW) The directory "/usr/shareX11/fonts/CID" Does not exist.
Entry deleted from font path.
(WW) 'fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
Entry deleted from font path.
(Run 'mkfontdir'2 on "/var/share/X11/fonts/mist, /usr/share/X11/fonts/100dpi/:unscaled, /usr/share/X11/fonts/75dpi/:unscaled, /usr/share/X11/fonts/Type1, /usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi, /usr/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
X.Org ANSI C Emulation 0.2
X.Org Video Driver: 0.7
X.Org XInput driver : 0.4
X.Org Server Extension : 0.2
X.Org Font Renderer : 0.4

(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/moduels/fonts/libbitmap.a
(II) Module bitmap: vender = "X.Org Foundation"
compiled for 6.8.2, module version 1.0.0
Module class : X.Org Font Renderer
ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModuel: "pcidata"
(II) Loading /usr/X11R6/lib/modeuls/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
compiled for 6.8.2, module version = 1.0.0
AVI class: X.Org Video Driver, version 0.7

(++) using VT number 7
.....


Loads more, didnt realize how big the error message was when i started typing it out.  At the bottom i get the "Fatal server error: no screens found" message again.  Click ok

> 
The X server is now disabled. Restart GDM when it is configured correctly.



How do i open Xorg.0.log to read?
It looks like i need a graphics driver?  Where do i get an upto date one and how do i install it? (i have no floppy drive)

My system spec:
Shuttle SN25P (nForce4 Mobo)
AMD Athlon64 San Diego 3700+
ATi Radeon x1800XL (Sapphire)
Geil 1Gb DDR 400 RAM

---

### Post by rjwood on 2005-11-23
Hi Fittersman,
When you set up your xserver did you accept the automatic settings or did you chose your own monitor resolutions?

---

### Post by Fittersman on 2005-11-24
when installing it never asked me for monitor resolution

---

### Post by Fittersman on 2005-11-24
OK i tried updating from hoary to breezy but i still have to same problem

---

### Post by invalid on 2005-11-24
Have you simply tried to reconfigure xserver?
```
sudo dpkg-reconfigure xserver-xorg
```

Cb

---

### Post by Fittersman on 2005-11-24
hey carwash these are some navigator things that will help you out:

ls -> list the things in a directory

cd (new directory) -> changes to the new directory

pico (the name of the thing if it doesnt open with cd) -> lets you read the thing

sudo pico (the name of the thing) -> lets you open it and edit it (you will need a password)

there are others but those are all i can remember right now

---

### Post by Fittersman on 2005-11-24
put that last comment in the wrong place

---

### Post by tseliot on 2005-11-25
Ok, a quick fix:
```
sudo nano /etc/X11/xorg.conf
```

Find the section Device and make sure the word I put in red is &#8220;vesa&#8221;:

```
Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "[COLOR="Red"]vesa[/COLOR]"
BusID "PCI:1:0:0"
```


```
CTRL+O to save (yes, use the same name and overwrite the file)
CTRL+X to exit
```

Then type:
```
sudo startx
```

And the Graphical interface should start.

AFTER you follow this method you might want to use your ATI card. 
Enter your bios and see if you can switch your cards (select your ATI): perhaps you can select between AGP and PCI or stuff like that.

If you manage to do that I'll give you further instructions.

---

### Post by Fittersman on 2005-11-25
dont that make it extreamly slow? cuz im planning on playing games with cedega or wine

---

### Post by tseliot on 2005-11-25
[QUOTE=Fittersman]dont that make it extreamly slow? cuz im planning on playing games with cedega or wine[/QUOTE]

I have told you to set it to "vesa" for now, so as to be able to use the graphical interface. Then you can install ATI's proprietary drivers.

And check your bios, please

---

### Post by Fittersman on 2005-11-25
i got it working now

---

### Post by tseliot on 2005-11-26
You can find the guide to ATI's driver here: [http://doc.gwos.org/index.php/BreezyCust]("http://doc.gwos.org/index.php/BreezyCust")
(Under 3D Cards)

If you want something (terribly) easier, try Easy Ubuntu: [http://ubuntuforums.org/showthread.php?t=64629]("http://ubuntuforums.org/showthread.php?t=64629")
Be patient in this case as it can take a while.

---

### Post by Fittersman on 2005-11-26
does easy ubuntu work for breazy badger also?

---

### Post by tseliot on 2005-11-26
[QUOTE=Fittersman]does easy ubuntu work for breazy badger also?[/QUOTE]
If you read the thread more carefully you will see:
[QUOTE=]Now support Breezy and ATI cards ![/QUOTE]

The answer is yes, it works on Breezy. I tried it some days ago on an old PC with a Radeon 9200 and it went fine.

---

### Post by Fittersman on 2005-11-26
how do i use easy ubuntu (lol) well it brings up a menu and it has a blank part and an add button and cancel so im totally lost. I opened up the readme but it never helped me so if you would help me out with that. all you have to to is start me out once i get goin im good

---

### Post by tseliot on 2005-11-27
[QUOTE=Fittersman]how do i use easy ubuntu (lol) well it brings up a menu and it has a blank part and an add button and cancel so im totally lost. I opened up the readme but it never helped me so if you would help me out with that. all you have to to is start me out once i get goin im good[/QUOTE]

1) Do you use Kubuntu?
2) Read all the instructions in EasyUbuntu's thread
3) Explain me what you did to make easy ubuntu start (step by step) so that I can help you

---

### Post by Fittersman on 2005-11-27
1. I use Ubuntu v5.10
2. already did
3.These are the steps i took:

1 Downloaded easy ubuntu in windows
2 put it on a floppy
3 mounted the floppy
4 opened floppy0 on desktop
5 double clicked on easy ubuntu (the box symbol)
6 double clicked on the easy ubuntu (folder inside the box)
7 double clicked on the easy ubuntu (foot on paper symbol)
8 a window came up with: 
available applications: 
(an empty box underneath) 
Recent applications: 
(an empty box underneath) 
a button "-Remove"
application: (an empty box here to type stuff)
two buttons "cancel" and "open"

9 click on open from previous window (that step ^)
10 get an error that says:
"Failed to run ./eu as user root:
Child terminated with 1 status"

alternate steps from #4 on

5 clicked on extract on the toolbar
6 a window comes up with options of what to extract and stuff, i picked all and clicked on hte extract button
7 an error came up:
"Extraction not performed (in bold)

You do not have the right permissions to extract archives in the folder media/floppy0"


and thats it

---

### Post by tseliot on 2005-11-27
[QUOTE=Fittersman]1. I use Ubuntu v5.10
2. already did
3.These are the steps i took:

1 Downloaded easy ubuntu in windows
2 put it on a floppy
3 mounted the floppy
4 opened floppy0 on desktop
5 double clicked on easy ubuntu (the box symbol)
6 double clicked on the easy ubuntu (folder inside the box)
7 double clicked on the easy ubuntu (foot on paper symbol)
8 a window came up with: 
available applications: 
(an empty box underneath) 
Recent applications: 
(an empty box underneath) 
a button "-Remove"
application: (an empty box here to type stuff)
two buttons "cancel" and "open"

9 click on open from previous window (that step ^)
10 get an error that says:
"Failed to run ./eu as user root:
Child terminated with 1 status"

alternate steps from #4 on

5 clicked on extract on the toolbar
6 a window comes up with options of what to extract and stuff, i picked all and clicked on hte extract button
7 an error came up:
"Extraction not performed (in bold)

You do not have the right permissions to extract archives in the folder media/floppy0"


and thats it[/QUOTE]

Copy the file "EasyUbuntu-2.4beta4.tar.bz2" from your floppy to your harddisk.

Then right click on your file on your harddisk and select Extract here
A "EasyUbuntu" folder will be created
Enter the folder
Double click on the "EasyUbuntu" file
A window will show up and will ask you: 
```
Do you want to run "EasyUbuntu" or display its contents?
```

Select "Run"
And it will ask you the permission to modify your "sources.list"
Press Ok

In the end you will be able to select the 3d drivers

---

### Post by Fittersman on 2005-11-27
it tells me im not qualified enough or something like that

---

### Post by tseliot on 2005-11-28
[QUOTE=Fittersman]it tells me im not qualified enough or something like that[/QUOTE]
I need the entire output because I have no idea of what your problem can be.

---

### Post by Fittersman on 2005-11-30
it worked but at the start it tells me that i have to select the fglrx driver instead of the ati driver but when i have to select a driver it is not on the list, so do i go and change that in the xorg.conf file after?

---

### Post by Fittersman on 2005-11-30
the error i get that is permission denied or something says that it fails to run as user root. When i installed ubuntu i am wondering if i made an error or something because my accoutn is the only one on the computer but it is not permissioned into places.

---

### Post by tseliot on 2005-12-01
[QUOTE=Fittersman]the error i get that is permission denied or something says that it fails to run as user root. When i installed ubuntu i am wondering if i made an error or something because my accoutn is the only one on the computer but it is not permissioned into places.[/QUOTE]
If you want to enable your root account:

sudo passwd root
(and set the root password which you will need later)

Then type:
su
and you will be root in the terminal. (type "exit" to get back to your username)

Try Easyubuntu again after this.
If it doesn't work you can use the other guide I suggested you (the manual way).

---

### Post by Fittersman on 2005-12-04
how do i run easyubuntu from the terminal?

---

### Post by tseliot on 2005-12-08
[QUOTE=Fittersman]how do i run easyubuntu from the terminal?[/QUOTE]
I mean the manual installation of ati drivers. Have a look at this guide [HOW-TO: ATI fglrx driver 8.16.20]("http://ubuntuforums.org/showthread.php?t=75378")

OR (from the Ubuntu starter guide)

[QUOTE=]How do I install the 3D ATI video card driver?

       1.          Install the xorg-driver-fglrx package with Synaptic (See How do I use Synaptic to install packages?)

          Miscellaneous - Graphical (restricted) > xorg-driver-fglrx
       2.echo fglrx | sudo tee -a /etc/modules
sudo depmod -a ; sudo modprobe fglrx
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup 
sudo sed -i -e 's/"ati"/"fglrx"/' /etc/X11/xorg.conf

       3.          If you are using an NForce2-based motherboard you will also need to do the following:

sudo gedit /etc/X11/xorg.conf
			    

          Change &#8220;Section "Device"&#8221; add the following line:

  Option  "UseInternalAGPGART" "no"

       4.          Restart your machine for changes to take effect.[/QUOTE]

---

