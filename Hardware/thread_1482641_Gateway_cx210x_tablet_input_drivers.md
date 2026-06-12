---
title: "Gateway cx210x tablet input drivers"
date: 2010-05-13
forum: Hardware
---

### Post by fasteddi on 2010-05-13
Hey all....

I am new here and would like to start out by saying I should have gotten into Linux a long time ago!!!!! This stuff is great!!!! 

With that said..... I have searched long and hard for the answer something like  four hours today and sometime last week. I am a total, complete, greener than green noob when it comes to coding and linux. I took a class in C++ but only stayed in for a week or two but, I am good with computers and can figure things out on the most part but now I am completely baffled and looking for help. 

I need an installation guide or a configure guide (step by step) to get my tablet pen and screen to function under Ubuntu 10.04. I have (think I have) installed the latest fpit drivers or code.....not really sure how to tell. Also, some of the threads said to edit xorg.conf...... I don't have it.....I followed instructions on how to create it but i get a system error. I can however open it in gedit but it is a blank screen with nothing on it. Haven't tried to input anything in and I don't mind trying stuff out but i don't feel that I am going in the right direction.... I'm sorry for beating this horse somemore but I really need help to get my tablet back. I love ubuntu so far but would love it even more if I had my tablet working. How do you get it to work. I am not afraid if I have good instructions but the ones Ive seen said edit xorg.conf with such and such.....and add this to setserial...... don't forget to add tablet input to server xorg part.....ect.....   I am just confused and beginning to think that my computer is too old or not able to use ubuntu. 

I'm just tired of searching and running into the same brick wall......Could someone please help.

Thanks everyone:confused:

---

### Post by Favux on 2010-05-13
Hi fasteddi,

Welcome to Ubuntu forums!

> I have (think I have) installed the latest fpit drivers or code.....not really sure how to tell.
Could you describe what you did to install the fpit driver in more detail.  Like where you got it from, etc.

Let's see if you have an xorg.conf.  Check in the directory /etc/X11/ for it using Places/Nautilus.

If it is there then post it's contents by using:
```
gksudo gedit /etc/X11/xorg.conf
```
Be sure not to change anything.

Hope this helps.

---

### Post by fasteddi on 2010-05-13
I downloaded it from x update (x ubuntu) site after reading about it in a thread....cant remember which one...there has been soooooooo many. I followed the instructions and downloaded the files and it installed itself...it did say that the files that i had were older than the one that I was trying to install but it also said that the newer files may not be completely supported...... i installed anyways and like the other person in the thread it didnt work. 

when I look for xorg.conf it is not there either by searching for it or going into the directory manually. When I put in that code

gksudo gedit /ect/x11/xorg.conf it opens up xorg.conf with nothing in it.

---

### Post by Favux on 2010-05-13
Hi fasteddi,

OK, hopefully all you need are the configurations files and the new fpit driver works in Lucid.  This is a slightly modified old xorg.conf.  Some of the lines may not be needed anymore.  Use the command that got the blank file and add the entire contents of this into it.:
```
Section "InputDevice"
	Identifier "Tablet"
	Driver "fpit"
	Option "Device" "/dev/ttyS0"
	Option "AlwaysCore" "on"
	Option "InvertY"
	Option "MaximumXPosition" "12550"
	Option "MaximumYPosition" "7650"
	Option "MinimumXPosition" "400"
	Option "MinimumYPosition" "400"
	Option "Passive" "false"
	Option "SendCoreEvents"
EndSection

Section "ServerLayout"
	Identifier  "X.org Configured"
	InputDevice "Tablet"
EndSection
```
Save, Close, and reboot.

If this breaks X, ie the gui won't start try:
```
sudo nano /etc/X11/xorg.conf
```
and remove the contents from the file.

---

### Post by fasteddi on 2010-05-13
Ok... I opened it by using the command and went to save it but it said that it couldnt find the file /ect/x11/xorg.conf check location and try again.

Do I have to install or let ubuntu create the file first?.... I have read in many threads that xorg gets updated quite frequently and I have even been to the xorg site but donno how to install it.

---

### Post by Favux on 2010-05-13
You should have created the file xorg.conf the first time you used the command, which is why I asked you not to unless you found it there with Nautilus.  No harm done.  It's 'etc' not ' ect'.  Copy and paste the command into the terminal rather than type it.  And by the way it is a capital X in X11.

---

### Post by fasteddi on 2010-05-13
Ok... you said it should have created the file when I typed the command.... but it didn't. I went in there and checked the folder and nothing is there. sorry about my type errors...so when you say copy the text in the terminal.......how do I do that, do I type in the command for the xorg.conf file and then type in what you want me to copy and paste before I hit enter? but from what I understand from what you are saying... i need the file first before I can edit it or add to it. BTW..... a big THANK YOU for helping me....and putting up with my noobness/confusion. :)

---

### Post by fasteddi on 2010-05-13
[QUOTE=Favux;9296004
```
sudo nano /etc/X11/xorg.conf
```and remove the contents from the file.[/QUOTE]

I used this to access xorg.conf right now and I am able to input that code but it asks where to save it?

---

### Post by fasteddi on 2010-05-13
So I found and have been studying this thread

[http://ubuntuforums.org/showthread.php?t=1365055](http://ubuntuforums.org/showthread.php?t=1365055)

But I am stuck at when you ask the user to input the first line of code to get the file to preserve? when I input that code I get nothing back.
But I checked in Synaptic Package Manager and I have the latest fpit files

---

### Post by fasteddi on 2010-05-13
Ok...so now I have an xorg.conf file inside X11 using this guide [http://ubuntulinux.co.in/blog/ubuntu/ubuntu-9-10/xorg-conf-file-create-on-ubuntu-9-10/](http://ubuntulinux.co.in/blog/ubuntu/ubuntu-9-10/xorg-conf-file-create-on-ubuntu-9-10/)...... and it only took me a few hours to figure it out and a lot of searching the internet. I had to do it twice to get it to move the file over but it worked the second time. now I am going to try to input the command for the tablet stuff....wish me luck.

---

### Post by Favux on 2010-05-13
Hi fasteddi,

You have completely lost me.  I'm asking you to use gedit, a graphical editor, rather than the command line editor nano because it is easier to use.  When you enter (copy and paste) in a terminal:
```
gksudo gedit /etc/X11/xorg.conf
```
doesn't it first ask you to enter your password and then an empty file appears in the text editor?  Then just go to the post with the xorg.conf in it and copy and paste it into the empty file.  Save (which will create the xorg.conf file), Close, reboot.

Are you saying your Lucid doesn't have gedit (gnome editor) installed?

---

### Post by fasteddi on 2010-05-13
ok so i created an xorg file using a post that I found.....and am now ready to input the text for the tablet commands in it but does it matter where I put it?

---

### Post by Favux on 2010-05-13
**[SIZE="4"]Stop!!![/SIZE]**

If you generated an xorg.conf I need to see what's in it before you do anything else!!!

---

### Post by fasteddi on 2010-05-13
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "dri2"
    Load  "glx"
    Load  "dbe"
    Load  "extmod"
    Load  "record"
    Load  "dri"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    #DisplaySize      300   180    # mm
    Identifier   "Monitor0"
    VendorName   "SEC"
    ModelName    "3257"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "Dac8Bit"                # [<bool>]
        #Option     "BusType"                # [<str>]
        #Option     "CPPIOMode"              # [<bool>]
        #Option     "CPusecTimeout"          # <i>
        #Option     "AGPMode"                # <i>
        #Option     "AGPFastWrite"           # [<bool>]
        #Option     "AGPSize"                # <i>
        #Option     "GARTSize"               # <i>
        #Option     "RingSize"               # <i>
        #Option     "BufferSize"             # <i>
        #Option     "EnableDepthMoves"       # [<bool>]
        #Option     "EnablePageFlip"         # [<bool>]
        #Option     "NoBackBuffer"           # [<bool>]
        #Option     "DMAForXv"               # [<bool>]
        #Option     "FBTexPercent"           # <i>
        #Option     "DepthBits"              # <i>
        #Option     "PCIAPERSize"            # <i>
        #Option     "AccelDFS"               # [<bool>]
        #Option     "IgnoreEDID"             # [<bool>]
        #Option     "CustomEDID"             # [<str>]
        #Option     "DisplayPriority"        # [<str>]
        #Option     "PanelSize"              # [<str>]
        #Option     "ForceMinDotClock"       # <freq>
        #Option     "ColorTiling"            # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "RageTheatreCrystal"     # <i>
        #Option     "RageTheatreTunerPort"     # <i>
        #Option     "RageTheatreCompositePort"     # <i>
        #Option     "RageTheatreSVideoPort"     # <i>
        #Option     "TunerType"              # <i>
        #Option     "RageTheatreMicrocPath"     # <str>
        #Option     "RageTheatreMicrocType"     # <str>
        #Option     "ScalerWidth"            # <i>
        #Option     "RenderAccel"            # [<bool>]
        #Option     "SubPixelOrder"          # [<str>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "ClockGating"            # [<bool>]
        #Option     "VGAAccess"              # [<bool>]
        #Option     "ReverseDDC"             # [<bool>]
        #Option     "LVDSProbePLL"           # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "DRI"                    # [<bool>]
        #Option     "ConnectorTable"         # <str>
        #Option     "DefaultConnectorTable"     # [<bool>]
        #Option     "DefaultTMDSPLL"         # [<bool>]
        #Option     "TVDACLoadDetect"        # [<bool>]
        #Option     "ForceTVOut"             # [<bool>]
        #Option     "TVStandard"             # <str>
        #Option     "IgnoreLidStatus"        # [<bool>]
        #Option     "DefaultTVDACAdj"        # [<bool>]
        #Option     "Int10"                  # [<bool>]
        #Option     "EXAVSync"               # [<bool>]
        #Option     "ATOMTVOut"              # [<bool>]
        #Option     "R4xxATOM"               # [<bool>]
        #Option     "ForceLowPowerMode"      # [<bool>]
        #Option     "DynamicPM"              # [<bool>]
        #Option     "NewPLL"                 # [<bool>]
        #Option     "ZaphodHeads"            # <str>
    Identifier  "Card0"
    Driver      "radeon"
    VendorName  "ATI Technologies Inc"
    BoardName   "Radeon Mobility X1400"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection


This is what is in the file..... I read the read-out and it used the files from my computer to create this file.

---

### Post by Favux on 2010-05-14
OK, the question is does your tablet boot with that in place?

All you need in the xorg.conf is what I posted.  All the rest of that is handled automatically by udev rules and the .conf files in /usr/lib/X11/xorg.conf.d/.  We didn't try a .conf file like 90-fpit.conf because the xorg.conf should be easier!  :)

---

### Post by fasteddi on 2010-05-14
GREAT.... I an checking now to see if my computer will boot with the file in place.... and if so I will add your text to the file...... hopefully that will do it like you said.

---

### Post by fasteddi on 2010-05-14
not only does my computer boot with this file but works much better than without it.........trying the code now.

---

### Post by Favux on 2010-05-14
But first back up your new generated xorg.conf, ie place it in another file.  You can just use the regular text editor, Applications > Accesories > Text Editor or gedit or whatever it's called.  For that you do not have to root/super user ie sudo or gksudo.  Then delete everything and just add what I posted.

---

### Post by fasteddi on 2010-05-14
Ok so I backed up the original to my desktop as xorg.conf.bak and erased all the code inside the file and replaced it with yours, restarted and nothing.....

---

### Post by Favux on 2010-05-14
Good work!

This is disappointing.  At least X starts.  So what is going on?  The fpit driver isn't working?  Or does the Gateway cx210x need the serial lines added, along with setserial, because the udev rules upstream of xorg.conf don't set it up to work correctly.

Did we check in /usr/lib/X11/xorg.conf.d/ to see if there was a 90-fpit.conf or similar?  Also check in /etc/X11/xorg.conf.d/.

---

### Post by fasteddi on 2010-05-14
check with gksudo gedit..... how to check.....

---

### Post by Favux on 2010-05-14
First just navigate there with Places/Nautilus and see if it's there.  Then you can right click on it and tell it to open in text editor.  You won't be able to edit it but you can look at the contents and copy and paste it to your post.

---

### Post by fasteddi on 2010-05-14
nevermind....momentarly forgot how to check..........noob.....what can you do with them?......hehehe

anyways... i checked and there is no file in usr/lib/X11/xorg.conf.d that is or like 90-fpit.conf

it has four files they are

05-evdev.conf, 10-synaptics.conf, 10-vmmouse.conf, and 10-wacom.conf

and I dont even have a xorg.conf.d file in etc/X11

BTW setserial is installed on my computer...... I did it before chatting with you from reading another post.

---

### Post by Favux on 2010-05-14
> BTW setserial is installed on my computer
Ahh.  I don't know if it will interfere or not.   But let's check.  Go to Synaptic Package Manager and search setserial.  Then right click on it and tell it to uninstall it and reboot.

---

### Post by fasteddi on 2010-05-14
Sorry but that doesnt work either.....

---

### Post by Favux on 2010-05-14
OK, check in /usr/lib/xorg/modules/input/ if fpit_drv.so (the fpit X driver) is present.

Otherwise we'll have to try the manual route with setserial and adding the serial line to setserial.conf.

---

### Post by fasteddi on 2010-05-14
yes it is in there

---

### Post by Favux on 2010-05-14
Alright.  OK, one last try before going to manual configuration.  See what happens if you change the xorg.conf to:
```
Section "InputDevice"
	Identifier "Tablet"
	Driver "fpit"
	Option "Device" "/dev/ttyS0"
	Option "SendCoreEvents" "true"
	Option "Passive" "false"
	Option "InvertY"
	Option "TrackRandR" "on"
	Option "MaximumXPosition" "12550"
	Option "MaximumYPosition" "7650"
	Option "MinimumXPosition" "400"
	Option "MinimumYPosition" "400"
EndSection

Section "ServerLayout"
	Identifier  "X.org Configured"
	InputDevice "Tablet"
EndSection
```

---

### Post by fasteddi on 2010-05-16
Favux

Sorry I havent been on the forums in a while....life catches up with you sometimes......

I havent used the pen input in a while so I decided to reinstall vista to see if the pen input was working....no point in asking for your help if the pen input was not working to begin with. So I did a clean install of 10.04 and now I cannot get fpit to install. It wants to remove a bunch of xorg files and when I say "mark" in synaptic it tries to install then it says cannot install xserver-xorg.......   and aborts the installation with no files installed. I am trying to remember the site that I used to install the package that I installed before but I cannot find it anywhere. Maybe you know or know how to get it to install properly...... Im gonna try the older latest version of fpit an maybe that will work. I shouldnt have did this and left things alone.

---

### Post by Favux on 2010-05-16
Hi fasteddi,

Sorry to hear that.  But you didn't say whether the stylus works under Vista.  So I assume it does?

I think you got fpit from here:  [https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=lucid](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=lucid)

---

### Post by fasteddi on 2010-05-17
Favux

Yes that is where I got it from....funny I have been googling for it for some time and it never came up... anyways...yes the pen works under Vista and no the pen still does not work even with the new xorg configuration that you recently posted........looks like manual installation? I sure hope we can get this to work, when I loaded Vista...I instantly missed Ubuntu..and I have only been playing with it for a few days....is that weird?

---

### Post by Favux on 2010-05-17
Hey fasteddi,

> I instantly missed Ubuntu..and I have only been playing with it for a few days....is that weird?
I don't thinks so, the linux concept is so cool.

Alright reinstall setserial.  Then add the following line to /etc/serial.conf:
> /dev/ttyS0 port 0x06A8 uart 16954 irq 4 baud_base 38400
You can use:
```
gksudo gedit /etc/serial.conf
```
then do:
```
sudo /etc/init.d/setserial reload
```
You still probably have to reboot.

---

### Post by fasteddi on 2010-05-17
Favux

That worked but the cursor is off, its to the far right  side and it clicks randomly so when I tested it out I got a million new  folders on my desktop and then shortly after x crashed as I was replying  to this thread. I guess I could play around with the x values in the  xorg file. my screen resolution is 1024x786....dont know if that  matters.

---

### Post by Favux on 2010-05-17
Hi fasteddi,

Great it's working!  Or at least we have a response from the digitizer.

Right, may need to fine tune coordinates or xorg.conf options. And actually some of that may be bugs in the driver that have been there a while.

Here's an old read me:  [http://www.xfree86.org/current/fpit.4.html](http://www.xfree86.org/current/fpit.4.html)  Digitizer resolution should be a separate matter from screen resolution.

---

### Post by fasteddi on 2010-05-18
Thanks Favux
I read that article and if i understand that correctly the x and y determine screen size? and if I increase or lower then the pointer will only go to those values? And so the random clicking is meer bugs in the fpit drivers, I hope there's gonna be a fix for it or Ill have to see if someone has already found a remedy to the problem by searching. 

Thanks for all your help......... it is MUCH appreciated.

---

### Post by fasteddi on 2010-05-18
I am not sure if Im doing this correctly or not....... but here is an interesting observation....when I move the pen to the right side of the screen the cursor gets further and further away from the actual pen but when I move the pen to the left side the cursor gets closer and closer until they are almost in sync at the edge of the screen...... how do I adjust that and is there a way to restart the gnome desktop so I can test the settings without having to reboot the whole computer?   

I guess I need further explanation of what max x and max y and min x and min y stand for.

---

### Post by Favux on 2010-05-18
> I need further explanation of what max x and max y and min x and min y stand for. 
Min x & y are the upper left corner when in landscape.  So they should be around 0 & 0.  Max. x is the horizontal "distance" from the left to right edge of the screen.  It's not in pixels, it's determined by the resolution of the digitizer.  And max y is the vertical equivalent.  From top to bottom of screen/digitizer.

The last few posts on this bug report are reporting the same problems:  [https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-input-fpit/+bug/565540](https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-input-fpit/+bug/565540)  You probably want to monitor this.  It could be a problem with the fpit driver, or maybe with Xinput, or possibly your video chipset/drivers.

---

### Post by Geeses on 2011-08-11
fasteddi,

I was wondering if you had resolved this issue (Digitizer versus screen resolution; e.g. your stylus is now calibrated)?  I got tired of using the trackpad on my CX210X to highlight and annotate PDFs in Xournal (0.4.5), and I stumbled on this thread.  

Favux,

I followed your instructions on creating the xorg.conf file (pgs.1-2 of thread), and I got a little lost after you started talking about 90somethings.  I did look in the locations that you specified, and the only xorg.conf file I could find was the one that you had instructions on creating.  Obviously, the only content this file had was what you had defined (and I copied and pasted into the file).  What do I do now, and what info do you need?

Thank you ahead of time for any help!

---

### Post by Favux on 2011-08-12
Hi Geeses,

Welcome to Ubuntu forums!

What release of Ubuntu are you using?  Which version of fpit?

Can you post your current working xorg.conf?

Now days we should probably use a fpit.conf file in xorg.conf.d instead of a xorg.conf.  It should probably look something like this:
```

Section "InputClass"
        Identifier "fpit class"
        MatchProduct "FUJ02B2|FUJ02B3|FUJ02B4|FUJ02B6|FUJ02B7|FUJ02B8|FUJ02B9|FUJ02BC|FPI2002|FPI2004"
        Driver "fpit"
        Option "TrackRandR" "on"
EndSection

Section "InputClass" 
        Identifier "fpit FPI2004 default configuration" 
        MatchProduct "FPI2004"
        Option "BaudRate" "38400"
	Option "MaximumXPosition" "12550"
	Option "MaximumYPosition" "7650"
	Option "MinimumXPosition" "400"
	Option "MinimumYPosition" "400"
        Option "InvertY" "on"
EndSection
```
Let's check on the keyword for MatchProduct by doing a little attributes walk.  You are probably on ttyS0.  Let's check that first.  Post the output of:
```
sudo dmesg | grep ttyS
```
in a terminal.  If so then post the output of:
```
udevadm info -a -p $(udevadm info -q path -n /dev/ttyS0)
```

---

### Post by Geeses on 2011-08-12
Favux,

Okay.  Using Natty (11.04 [latest update]).  fpit is "Free Point Indicator"?  What does this do (obviously a driver, but for what exactly?), and where can I find it?  I typed in "find fpit.conf" into Terminal, but nothing could be found.  What is the file pathway?  I also ran a search in Nautilus and got two files: mcfpit.h (2 copies).  These are locked (does that mean they are only root accessible?).

The only xorg.conf file I have is what I copied out of one of your previous posts.

Code:

Section "InputDevice"
    Identifier "Tablet"
    Driver "fpit"
    Option "Device" "/dev/ttyS0"
    Option "AlwaysCore" "on"
    Option "InvertY"
    Option "MaximumXPosition" "12550"
    Option "MaximumYPosition" "7650"
    Option "MinimumXPosition" "400"
    Option "MinimumYPosition" "400"
    Option "Passive" "false"
    Option "SendCoreEvents"
EndSection

Section "ServerLayout"
    Identifier  "X.org Configured"
    InputDevice "Tablet"
EndSection



This didn't result in an output.

sudo dmesg | grep ttyS

Okay, the second command gave me something.


Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/platform/serial8250/tty/ttyS0':
    KERNEL=="ttyS0"
    SUBSYSTEM=="tty"
    DRIVER==""

  looking at parent device '/devices/platform/serial8250':
    KERNELS=="serial8250"
    SUBSYSTEMS=="platform"
    DRIVERS=="serial8250"

  looking at parent device '/devices/platform':
    KERNELS=="platform"
    SUBSYSTEMS==""
    DRIVERS==""


So, I am on ttyS0.  What exactly am I looking at, and why is there only one driver between the three entries?

What now?  Also, how do I get the codes in indented blocks like yours?


**Thank you for replying so quickly, and I apologize beforehand if I fail to process anything.  I'm working on some term papers, and my brain is feeling like an egg on a sidewalk in 120 degree weather.  >.<

---

### Post by Favux on 2011-08-12
Actually fpit is an abbreviation of Finepoint, so it is the Finepoint driver.  They were a digitizer maker who went out of business, I think.

Search in Synaptic Package Manager for fpit.  If it isn't installed go ahead and install it and reboot.  Let me know if the stylus starts working.

You get the stuff indented by inserting it between the code blocks and you get those by clicking on the # on the top right.

Alright so there was no xorg.conf until you added one.  Since you can still boot into your Desktop we can assume you're good.  :)

Don't worry about the fpit.conf yet.  Let's first get it working with the xorg.conf and then we can try to switch.

I'm not convinced that we know which ttyS you are on althoug it should be ttyS0.  Because there should be a device ID called FPI2004, I'm pretty sure.  They go from 0 to 3.  If fpit wasn't installed see what udevadm on ttyS0 shows now.

Try running this command:
```
setserial -g /dev/ttyS*
```
and post the output.  But although useful I don't think that output shows the which ttyS is active.  We may have to give xxd or evtest a go.


If we have to we can do some other stuff to check such as substituting the next number sequentially in the udevadm command.

Concentrate on the term papers for sure and don't worry about me.  I remember that overloaded feeling well.

---

### Post by Geeses on 2011-08-12
Wow.  I just finished laughing at myself.  Okay, so I've been looking over this thread:     It explains a lot.  I downloaded the fpit (apparently a driver for Fujitsu tablets [and compatible with CX210X]).  

This is the version Software Center gave me: 

1:1.3.99+git20101206.020c04e2-0ubuntu1 (xserver-xorg-input-fpit)

Now I have to go think for a few more minutes; I'm this will all make more sense to me in a minute.

---

### Post by Geeses on 2011-08-12
Okay.  Restarted, but the stylus isn't working.

I ran the command and got this:

```


The program 'setserial' is currently not installed.  You can install it by typing:
sudo apt-get install setserial


```

I did what it said and got this:

```


Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.38-8 esound-common libesd0 linux-headers-2.6.38-8-generic
  libaudiofile0
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  setserial
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 39.0 kB of archives.
After this operation, 180 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ natty/main setserial i386 2.17-45.3ubuntu1 [39.0 kB]
Fetched 39.0 kB in 4s (8,573 B/s)    
Preconfiguring packages ...
Selecting previously deselected package setserial.
(Reading database ... 182297 files and directories currently installed.)
Unpacking setserial (from .../setserial_2.17-45.3ubuntu1_i386.deb) ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db ...
Setting up setserial (2.17-45.3ubuntu1) ...
removing the old setserial entry in the rcn.d directories
Update complete.
Saving state of known serial devices... backing up /var/lib/setserial/autoserial.conf done.



```

So I'm running setserial 2.17-45.3ubuntu1 now?  (What is the setserial?)

Hold on.  I just ran:

```


setserial -g /dev/ttyS*

```

and I got:

```


/dev/ttyS0, UART: unknown, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: unknown, Port: 0x02f8, IRQ: 3
/dev/ttyS10, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS11, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS12, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS13, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS14, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS15, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS16, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS17, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS18, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS19, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS2, UART: unknown, Port: 0x03e8, IRQ: 4
/dev/ttyS20, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS21, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS22, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS23, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS24, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS25, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS26, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS27, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS28, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS29, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS3, UART: unknown, Port: 0x02e8, IRQ: 3
/dev/ttyS30, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS31, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS4, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS5, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS6, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS7, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS8, UART: unknown, Port: 0x0000, IRQ: 0
/dev/ttyS9, UART: unknown, Port: 0x0000, IRQ: 0



```

Shouldn't it have picked up the setserial I just installed.  I'm confused.

Also, I tried this:
```


sudo dmesg | grep tty0


```

and got this:
```


[    0.000000] console [tty0] enabled


```

---

### Post by Favux on 2011-08-12
Alright.  Let's see if doing dmesg from a console without X makes any difference.

So do ctrl+alt+F2 to get into the console (the tty0 from your last dmesg).  You use ctrl+alt+F7 to get back to X.  When in the console run:
```
sudo dmesg | grep ttyS
```
again.  If it works I'm reasonably sure what you should see is something close to:
```
[    1.189964] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
```
Given you got:
```
/dev/ttyS0, UART: unknown, Port: 0x03f8, IRQ: 4

```
from *setserial -g /dev/ttyS**.  By the way I've never seen an output like that from it.  The output I would have expected to see is:
```
/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4
```
along with a line from S1, S2, and S3.  So weird.

Setserial configures serial ports.

1:1.3.99+git20101206.020c04e2-0ubuntu1 (xserver-xorg-input-fpit) means you have version 1.3.99 of the fpit driver.  Version 1.3 was released a couple of years ago and then they switched to git.  That's what the +git is saying.  The driver is actually from around 12/11 I think with a fair number of commits (changes to the code) added since 1.3 came out).  I think they tagged it with the label 1.3.99 around December.  Anyway version 1.4 got released a few weeks ago and it has even more commits/changes including a 50-fpit.conf for xorg.conf.d.  But it only includes the Fujitsu tablet PCs and I'd like to submit patches to be committed to add the other fpit tablet PCs.  That includes not just Fujitsu, but the Gateway ones and Compaq models.  Apparently using the Finepoint digitizer was a fad a few years back.  If we can get it working.  That way it should work out of the box and we can avoid this set up fun in the future.

---

### Post by Geeses on 2011-08-12
Yes, having the Tablet functionality out of the box would be great, but then I wouldn't get to have all of this fun.  :P

Okay.  I'm still not getting anything from:
```

sudo dmesg | grep ttyS
```It's acting as if I just hit enter without anything in the code line.

I also tried *setserial -g /dev/ttyS* *again and got the same output.  With the same values in S0, S1, S2, and S3.

Remember, this is a Gateway, so it's redundant to say that ANYTHING about it is weird.  

Is there another path we can take trying to find ttyS*?  I'm not understanding why *setserial -g /dev/ttyS* *results in output and *sudo dmesg | grep ttyS* doesn't.

---

### Post by Favux on 2011-08-12
That's one of the joys of setting up serial tablets.  For reasons I don't understand the dmesg command doesn't work for some folks while for others it works fine.  Heck some don't even have to use sudo.  I haven't been able to figure out what's going on.

The reason we want the output is we want to actually use the information from your system and not another one as they might be different.  For example I have one CX210x where it is:
```
[    1.189964] 00:06: ttyS0 at I/O 0x6A8 (irq = 4) is a 16550A
```
but given your setserial said Port: 0x03f8 let's go with the output, if it would produce it, is:
```
[    1.189964] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
```

Now you have:
1) Installed fpit
2) Set up a xorg.conf - and it appears correct
3) Installed setserial - needed in newer releases?  I think it is suppose to be auto-installed when Ubuntu installation detects a serial port now days but I'm not sure.

So the stylus should be working, but yours isn't.  Or at least it does work  with some.  You used to have to put a line in /etc/serial.conf but I don't think you are suppose to have to do that anymore.  I think setserial is suppose to auto-configure the port now, which may be part of the reason there isn't a dmesg output.  And then with some the stylus would start working after a reboot.  But for others it wouldn't.  Again I don't know why.

The magical incantation that finally got it working for those unfortunates was found here:  [https://help.ubuntu.com/community/FujitsuStylus](https://help.ubuntu.com/community/FujitsuStylus)  But what is the magical command/entry?  No one investigated to find out as far as I know.  Are they all needed?  Based on a fpit README I found somewhere I'm guessing it is adding the line in rc.local.  It said something about udev not handling fpit serial configuration correctly.  So let's try that.

Use this to edit rc.local:
```
gksudo gedit /etc/rc.local
```
In it you'll see:
```
# By default this script does nothing.

exit 0
```
Add the line:
```
setserial /dev/ttyS0 port 0x03f8 uart 16954 irq 4 baud_base 38400
```
so it looks like:
```
# By default this script does nothing.

setserial /dev/ttyS0 port 0x03f8 uart 16954 irq 4 baud_base 38400

exit 0
```
And reboot.

My fingers are crossed.

---

### Post by Geeses on 2011-08-12
Still nothing.  After reboot I checked the rc.lcoal file to make sure that it was saved correctly, and it still looks like this:
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

setserial /dev/ttyS0 port 0x03f8 uart 16954 irq 4 baud_base 38400

exit 0

```

I may as well be using a #2 pencil, though.  The stylus didn't get any response.

Question: Is the autoconfig command needed?  E.g.
```

setserial /dev/ttyS0 autoconfig

```

This line is present in the (rather old) tutorial before the setserial descriptor.

---

### Post by Favux on 2011-08-12
I have no idea.  It looks like the two lines are doing the same thing.  Why repeat them?  But go ahead and try.  If that doesn't work we can try adding the full descriptive line to serial.conf next.

---

### Post by Geeses on 2011-08-12
Yeah, it didn't do anything.  How do we go about  adding the full descriptive line to serial.conf?

---

### Post by Favux on 2011-08-12
```
gksudo gedit /etc/serial.conf
```
I forgot what it looks like (you can post the contents if any) but you just place the line at the end I think.

---

### Post by Geeses on 2011-08-12
This file came up, but nothing was in it.  I put the line in, saved, and rebooted.  

The stylus still isn't responding.  It was still responding the last time I tested it with Windows XP Tablet Ed. (several months ago).  This leads me to believe that the battery is still okay.  

However, even *if* the battery gave up the ghost, that in no way explains the strange outputs (and lack of outputs) to the setserial prompts.


I am perplexed and slightly frustrated by my sudo-Tablet.

---

### Post by Favux on 2011-08-12
It could be the battery I suppose, but probably not if it was working a few months ago.  I'd feel better if you could dual boot into Windows and prove it still works.
> However, even if the battery gave up the ghost, that in no way explains the strange outputs (and lack of outputs) to the setserial prompts.

I agree.

The xorg.conf looks good.  Well lets check for what ttyS it is on.  We could use xxd or evtest.  First run *ls /dev/ttyS**.  As I mentioned there should only be four ports or so.  But you seem to have more.  I'm interested if whether the output is the same as before.  Then:
```
xxd /dev/ttyS0
```
xxd (hidrawX hexdump) will exit for devices not listed, otherwise CTRL and C to quit.  Run through each device listed by "ls /dev/ttyS*" eg. ttyS0, ttyS1, etc.  Bring the pen to the screen and move it around.  You know you have the right ttyS* when you see a reaction with an output of characters.  That's the ttyS* you want to use in xorg.conf.

---

### Post by trungvkvk on 2011-08-13
can I  join the topic?.
 I am a newbie so do not know what is involved to learn.
 thanks

---

### Post by Favux on 2011-08-13
Hi trungvkvk,

Sure, you can join the thread!  The more perspectives the better.  You might want to skim through the thread if you haven't already.  Do you have a Gateway cx210x tablet also?

---

### Post by Geeses on 2011-08-13
trungvkvk,

Hello!  If you  have a CX210X, then we can compare results.  It may help in narrowing down how to get the stylus working with your/mine.  


Favux,

Yesterday I checked every one of the 32 (!???!) ttyS.  The stylus didn't respond to a single one of them.  At this point I began to wonder in earnest if the stylus is working at all.  I'm wondering if it will work in VirtualBox?  I began trying to load XP Tablet to test it, but then that began giving me problems.  I was wanting to try this as an alternative to loading Windows to dual boot right now, because I didn't feel good about trying to load it while I'm finishing out the Summer term.  Wouldn't Windows XP try to overwrite Ubuntu?  I know that loading Ubuntu *after* loading Windows will give me a good dual boot, but will loading Windows after Ubuntu do the same?


Right now, I'm thinking that the stylus needs to be ruled out as a complicating factor, but there are other factors (e.g. deadlines looming for papers) that are affecting my willingness to be juggling OS's at the moment.

---

### Post by Favux on 2011-08-13
Sure I understand.  Priorities.

What happens is Windows overwrites the MBR and you lose Grub and can't boot into linux.  All you need to do is install Grub2 with a live CD and you'll get your Natty partition back:  [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)  also see:  [http://ubuntuforums.org/showthread.php?p=10871917#post10871917](http://ubuntuforums.org/showthread.php?p=10871917#post10871917)

That's assuming you have created a separate partition for Windows with Gparted or whatever.  Remember Windows wants to be in the first partition.

> Yesterday I checked every one of the 32 (!???!) ttyS. The stylus didn't respond to a single one of them.
Something ain't right.  For one thing there shouldn't be 32 ttyS's.  You have to add a kernel boot line switch to add another ttyS, say ttyS4!


Edit:  Oops!  **I am clearly wrong!**  I just checked and sure enough in Natty with Unity there are 32 ttyS's.  ttyS0 to ttyS31  I checked Lucid and Maverick and they just have the usual four ttyS0 to ttyS3.  So clearly some change to handling serial ports has been made to Natty.  I have no idea what that means to us.  And I checked Ubuntu Classic and it has the same thing.  Now I'm wondering if this might be why we couldn't set up a Compaq TC1000 (also uses fpit) the other day in Natty.  He changed to Lucid and it worked there.

---

### Post by Geeses on 2011-08-13
Okay, let me see if I understand.  Installing Windows removes Grub (the bootloader) _only_.  Provided that Windows and Ubuntu have their own partitions, reinstalling Grub2 will allow _existing_ Ubuntu files to boot (without having to reinstall Ubuntu and applications).  Or is my understanding of what Grub is and how it functions completely off?


With Alpha 3 out is there any chance that Canonical would incorporate appropriate drivers for stylus functionality out of the box?  Perhaps they could be persuaded to release a Tablet version (compatible with active input digitizers)?

Also, do you think that running XP Tablet in VB has any merit (provided I can get it to work)?

---

### Post by Favux on 2011-08-15
> Okay, let me see if I understand. Installing Windows removes Grub (the bootloader) only. Provided that Windows and Ubuntu have their own partitions, reinstalling Grub2 will allow existing Ubuntu files to boot (without having to reinstall Ubuntu and applications). Or is my understanding of what Grub is and how it functions completely off?

That's my understanding.  I've always already had Windows installed and made a partition for Linux and installed Ubuntu or whatever into it.
> With Alpha 3 out is there any chance that Canonical would incorporate appropriate drivers for stylus functionality out of the box?
My guess is they'll have version 1.4 of the fpit driver.  But we could install version 1.4 now if we wanted to, it's not hard.

I don't think that's our problem.  We've gotten Wacom serial tablets running off of ttyS0 in Natty.  Admittedly they're using inputattach to feed the raw data from ttyS0 through to kernel serio module/drivers rather than a X driver.  But still that indicates the serial stuff including ttyS0 works.  Plus Wacom ISDV4 serial tablets (tablet PCs) work in Natty and they all use ttyS0.  Sure with the Fujitsu tablet PCs restarting X may be necessary to initialize the digitizer, but that's another issue.

We seem to be having some other problem, I just don't know what.  Maybe the system doesn't set the line discipline correctly, even with setserial?  But the fpit driver site seems to imply that the Fujitsu tablet PCs that use fpit work fine in recent kernels, like Natty's.  So what's different with the Compaq and Gateway tablet PCs?
> Also, do you think that running XP Tablet in VB has any merit (provided I can get it to work)? 
That's what some folks advocate now days.  They don't see the point of partitions and dual boot installs when you can use VBox.  To me that's just another level of complexity, which will invariably make figuring things out tougher.  Of course I don't know much about virtual machines because I don't use them.

---

