---
title: "HowTo: Getting you stylus to work on a Serial Tablet (Laptop/Tablet combo)"
date: 2007-10-25
forum: Hardware &amp; Laptops
---

### Post by malfist on 2007-10-25
How to configure a wacom stylus for serial tablets:

Determining if you have a serial tablet:
```

dmesg |grep ttyS

```
That should return something, specifically like irq = 4 or irq = 5. That means this how to is for you.
example:
```

[	012.891641] 00:02: TtyS0 at I/O 0x6a8 (irq = 4) is a 16550A

```

If you do not have a serial tablet use this [http://linuxwacom.sourceforge.net/index.php/howto/main](http://linuxwacom.sourceforge.net/index.php/howto/main) this is also for you if this tutorial does not work for you.

Downloading and installing what you need:
	install the package wacom-tools
```
sudo aptitude install wacom-tools
```
	the download the latest package from [http://linuxwacom.sourceforge.net/index.php/dl](http://linuxwacom.sourceforge.net/index.php/dl)
	Unpack the package, you will only need one file from it, ./prebuilt/32 (or 64 if you are 64 bit)/wacom_drv.so

Replacing driver
	locate where ubuntu placed the default wacom_drv.so it is usually stored here: /usr/lib/xorg/modules/input/wacom_drv.so
	back that file up and replace it with the one from the package you downloaded.
	```

sudo cp /usr/lib/xorg/modules/input/wacom_drv.so /usr/lib/xorg/modules/input/wacom_drv.so.backup
sudo cp ./prebuilt/32/wacom_drv.so /usr/lib/xorg/modules/input/wacom_drv.so
	
```

Editing xorg.conf
	first backup xorg.conf, then open it up for editing:
	```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backupPrewacom
sudo gedit /etc/X11/xorg.cong
	
```
	Remove entire sections that the device (or driver) is listed as wacom, stylus and eraser.
	replace it with this:
	```

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
#  Option        "Device"        "/dev/input/event0"   # USB ONLY
  Option        "Type"          "stylus"
#  Option        "USB"           "on"                  # USB ONLY
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
#  Option        "Device"        "/dev/input/event0"   # USB ONLY
  Option        "Type"          "eraser"
#  Option        "USB"           "on"                  # USB ONLY
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
#  Option        "Device"        "/dev/input/event0"   # USB ONLY
  Option        "Type"          "cursor"
#  Option        "USB"           "on"                  # USB ONLY
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection
```

	Now at the bottom of the xorg.conf there should be a Section 'ServerLayout' add these lines:
		*Side note: Sometimes (especially 7.10 and maybe 7.04) these lines will already be there and only thing you will have to do is uncomment them.*
```

        InputDevice    "stylus"    "SendCoreEvents"
        InputDevice    "eraser"    "SendCoreEvents"
        InputDevice    "cursor"    "SendCoreEvents"    # For non-LCD tablets only

```
	Now, save and exit gedit.

Restarting X
	Now you should restart the X (or graphical) server. You can do this by pressing Ctrl+Alt+Backspace. Your screen will go black for a moment, then with any luck you will be presented with a login screen. If not, get to a command line and type this:
	```

sudo cp /etc/X11/xorg.conf.backupPrewacom /etc/X11/xorg.conf
	
```
	Then attempt to redo the step, editing xorg.conf. If it still fails go to the webpage and try to find out what you are doing wrong, you may not have a serial tablet.

	Now, with any luck you will have a working stylus. Drag it along the screen watch the cursor follow it. Fun isn't it? Try a right click. It doesn't work does it?

Configuring the all glorious right click
	If your stylus has a button for right click, read this and fix it. Otherwise, this isn't for you.
	Run this command:
	```

xidump stylus
	
```
	Play with your stylus, find which button is representing the right click, usually it is Button2 (should say 2-UP or 2-DOWN when you press it and click).
	Now replace the button that yours is with the button in this following code:
	```

xsetwacom set stylus Button2 "button 3"
	
```
	Now test it out, it should work!
	Enjoy your right click.
Configuring Screen Rotating
	To rotate the screen you need to run the command
	```

xrandr -o {0,1,2,3}
	
```
	0 is default position, 3 is usually the tablet position.
	Now, rotate the screen, play with your pen. It doesn't line up like it should does it?
	Rotate the screen back to 0.
	
Scripts for rotation:
	Open up gedit and type this in:
	```

xrandr -o 3
xsetWacom set stylus Rotate CW
	
```
	Now, save that as toTablet.sh and run this command where you saved it:
	```

sudo chmod +x ./toTablet.sh
	
```
	Now make a new file in gedit and type this in:
	```

xrandr -o 0
xsetWacom set stylus Rotate NONE
	
```
	Save this one as toLaptop.sh and run this command where you saved it:
	```

sudo chmod +x ./toLaptop.sh
	
```

	toTablet.sh will rotate the screen and the co-ord plane for the stylus and toLaptop.sh will revert it back to normal.

Making it stick:
	To make it stick make a new file in gedit and type this:
	```

xsetwacom set stylus Button2 "button 3"
	
```
	Save this file as tabletInit.sh and run:
	```

sudo chmod +x ./tabletInit.sh
	
```
	Add this file to System > Preferences > Sessions to have it ran on startup. There is a better way to do this, but I do not know it. Sorry.

Now your stylus should be fully configured, please enjoy it.

Improvements are welcome before posting this on the wiki.

---

### Post by High Camp on 2007-10-25
Wow, Malfist, best tut. ever.

Very easy to follow and worked like a charm. I just did a clean install of Gutsy and had forgotten the steps I took to make the stylus work. After reading it I remembered that all I had to do was uncomment the "ServerLayout" section and that got the stylus working. Not only did I learn a lot about Linux but I now have the right click working as well.

Thanks so much for taking the time to do that,

---

### Post by suchawato on 2007-10-25
at the step where I enter [COLOR="Red"]sudo cp ./prebuilt/32/wacom_drv.so /usr/lib/xorg/modules/input/wacom_drv.so[/COLOR] it gives me an error message saying:
[COLOR="#ff0000"]cp: cannot stat `./prebuilt/32/wacom_drv.so': No such file or directory
stu@stu-desktop:~$ cp?
bash: cp?: command not found[/COLOR]
I discontiued the process until I get this cleared up

---

### Post by High Camp on 2007-10-25
Hi Suchawato

You've got two different syntax errors here.

First: The original poster put ./prebuilt/32/wacom_drv.so because he doesn't know were the file is stored on your computer he just knows that it is going to be in these folders because these are the ones in the .tar. You have to replace the "." with the rest of the path, which is something like /tmp/linuxwacom-0.7.8-3... I.E. Figure out the full path from root to the new downloaded wacom_drv.so file and put that in and you should be fine.

Second: For whatever reason cp? was entered into the terminal and then enter was hit creating the second error "bash: cp?: command not found", which basically is the terminal saying "what?" or "pardon me? or "I don't get it" (you get the idea).

That was probably a bit over kill on the explanation since you probably just wanted an answer not an explanation. Hopefully you can get what you need from my lunatic ramblings.

---

### Post by malfist on 2007-10-25
> **suchawato said:**
> 
[COLOR="#ff0000"]cp: cannot stat `./prebuilt/32/wacom_drv.so': No such file or directory[/COLOR]

You need to naviagate to the root directory of where you unziped the file you downloaded from wacom tools webpage. Although, I'm not 100% this step is necessary but it doesn't hurt.

Tested on Gusty for Gateway C-140x.
I had spent about a week making it work and then I got on IRC to ask a question and someone asked how to get the stylus working and I worked him through it and decided to make a tut, because obviously it's needed. The one on the website is way too long and confusing.

---

### Post by malfist on 2007-10-25
> **High Camp said:**
> Wow, Malfist, best tut. ever.

Very easy to follow and worked like a charm. I just did a clean install of Gutsy and had forgotten the steps I took to make the stylus work. After reading it I remembered that all I had to do was uncomment the "ServerLayout" section and that got the stylus working. Not only did I learn a lot about Linux but I now have the right click working as well.

Thanks so much for taking the time to do that,

Thank you, this is my first howto :P

---

### Post by suchawato on 2007-10-27
> **High Camp said:**
> Second: For whatever reason cp? was entered into the terminal and then enter was hit creating the second error "bash: cp?: command not found", which basically is the terminal saying "what?" or "pardon me? or "I don't get it" (you get the idea).
So, should I just leave this line out?

---

### Post by suchawato on 2007-10-27
Thanks for the help guys, and to MAlfist for the OP.

---

### Post by malfist on 2007-10-28
Did it work?

---

### Post by suchawato on 2007-10-29
No.:) LOL.

---

### Post by suchawato on 2007-10-29
I have an old Art II 12x12.
It was one of the earlier ones and one of the nicest ones when it came out.
it has a bunch of programable tool buttons at the top if that helps.
On the back it says Digitizer II and the model number is:UD-1212-R.

---

### Post by malfist on 2007-10-29
Did you copy the driver like you was supposed to?

---

### Post by suchawato on 2007-10-29
the /32/wacom_drv.so or whatever it was, yes, as far as I know, it's in the right directory.
I put it in ```
/usr/lib/xorg/modules/input/wacom_drv.so
```
I'll post a copy of my xorg.conf.

---

### Post by High Camp on 2007-11-03
Just to let everyone know. My hibernate button actually works and after my tablet comes out of hibernation the rotation doesn't work. The cursor rotates fine but the screen does not. You'll know real quick if this happens to you because your cursor will not match up with your stylus. No idea what's doing it, why, or how to fix it but I can live with it. The fix I use is press ctrl+alt+backspace to restart the xserver and the you'll be fine.

Hope that helps,

---

### Post by suchawato on 2007-11-04
Ok,  here is my xorg.conf

```
# xorg.conf (xorg X Window System server configuration file)
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

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
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
#  Option        "Device"        "/dev/input/event0"   # USB ONLY
  Option        "Type"          "stylus"
#  Option        "USB"           "on"                  # USB ONLY
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
#  Option        "Device"        "/dev/input/event0"   # USB ONLY
  Option        "Type"          "eraser"
#  Option        "USB"           "on"                  # USB ONLY
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
#  Option        "Device"        "/dev/input/event0"   # USB ONLY
  Option        "Type"          "cursor"
#  Option        "USB"           "on"                  # USB ONLY
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Silicon Integrated Systems [SiS] 630/730 PCI/AGP VGA Display Adapter"
	Driver		"sis"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Gateway EV91"
	Option		"DPMS"
	HorizSync	30-95
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Silicon Integrated Systems [SiS] 630/730 PCI/AGP VGA Display Adapter"
	Monitor		"Gateway EV91"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x450" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

   InputDevice    "stylus"    "SendCoreEvents"
        InputDevice    "eraser"    "SendCoreEvents"
        InputDevice    "cursor"    "SendCoreEvents"    # For non-LCD tablets only
EndSection
```

---

### Post by High Camp on 2007-11-04
What do you get when you put enter the following code in the terminal:
```
xrandr -o 1
```

Post the output of that and we can go from there.

---

### Post by suchawato on 2007-11-05
> **High Camp said:**
> What do you get when you put enter the following code in the terminal:
```
xrandr -o 1
```

Post the output of that and we can go from there.
It gives me a clean prompt.
```
stu@stu-desktop:~$ xrandr -o 1
stu@stu-desktop:~$ 
```

---

### Post by malfist on 2007-11-05
what is the result of 
```
dmesg | grep ttyS
```

---

### Post by suchawato on 2007-11-05
```
stu@stu-desktop:~$ dmesg | grep ttyS
[   18.722125] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   18.725813] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
stu@stu-desktop:~$ 
```

---

### Post by malfist on 2007-11-05
That's odd, you have two reports for a device at ttyS0, both on irq 4. Not exactly sure what that means. I'll look into it, but I don't have any advice at the moment.

---

### Post by High Camp on 2007-11-05
That is odd. Since you're not getting any errors when you attempt to rotate it makes me think that the rotation is working ok but it's being sent to the wrong device possibly.

I'm busy right now but I'll also look into it and see what I can find.

---

### Post by High Camp on 2007-11-07
AAAARRRRGGG

I've learned a valuable lesson in the last 24 hours. If you're going to mess with your system it's worth having two OS's on the computer. One to mess with and one for everyday use. I ended up completely reinstalling the kernel. Fortunately I have my Home folder on a different partition so it saved most of my settings but it didn't save the changes I made to get screen rotation working.

Anyway, to the point. Has anyone seen this error:
```
simon@simon:~$ xrandr -o 1
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  158 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12
simon@simon:~$
``` 
I know I've gotten it before and when I got this working last time I did something to fix it, I just can't remember what I did or were I found the solution.

Thanks,

EDIT: I forgot to add this:
> Option "RandRRotation" "On"
to the screens section of the xorg.conf file.

Malfist: It might be worth editing the original post to have people check that it's there.

Suchwato: I suspect this is your problem too. You xorg.conf should look like this:
> Section "Screen"
	Identifier	"Default Screen"
	Device		"Silicon Integrated Systems [SiS] 630/730 PCI/AGP VGA Display Adapter"
	Monitor		"Gateway EV91"
	Option 		"RandRRotation" "On"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x450" "720x400" "640x480"
	EndSubSection
EndSection
Note the RandR

Hope that helps,

---

### Post by Revfisk on 2007-11-09
Dunno if anyone's around on this one, but I've installed the wacom-tools and that's as far as I got.  I cna't find the path in the tmp files, or anywhere else.  I still don't really know what "root" means, so maybe that's my problem.

Any help?

---

### Post by suchawato on 2007-11-09
Well I can't answer your more advanced question,
But Root, I can.
In Linux when you log in, you are typically using your username.
This account, your settings, your desktop, and everything specific to you are stored in a separate folder than all of the rest of your system files. 
This is done for security, so that if you were to screw up your home folder, the system would still run.
To install most applications, and to make system-wide changes and especially to make changes regarding stuff like the wacom tablets, or how your mouse works or monitor is detected, etc. you need to either log in directly (from the log in screen) as "root", or more usually, temporarily log in using a sort of gateway into root.
This usually takes the form of say:
```
sudo *your command here*
```
where "sudo" means Super User Do.
This is a way to quickly run and install root level-access programs and changes, without actually logging out and logging back in as a different(root) user.
If you wanted to navigate your file system graphically (with windows), you would type ```
 gksudo nautilus
```(gksudo is usually the best way to launch a graphic program as super-user)  or ```
  sudo nautilus
``` (which will also usually work but can lead to some problems with some graphical apps other than nautilus).
Does this answer your question?

---

### Post by Revfisk on 2007-11-09
Well...it sounds like I need to get to my root tmp files, where the download happened, in order to find the driver so I can begin step 1 of the whole process.  But I'm not sure how to do that.  You're explanation of root helps though.  Jargon is important!

I have an X41 tablet, which I never used as a tablet because windows absolute CRAWLED on it.  I'm rediscovering this wonderful laptop through Ubuntu, but I'd really like to use the tablet feature for the graphic arts I do.  So this is a huge milestone issue.

Basically, at the beginning of this thread, someone talked about finding the "." in the root in order to direct the path for the replacement driver.  This is the key issue.  

In my /tmp folder I have folders:

evenvince
gconfid
keyring
orbit
ssh-adur
tracker
virtual

I can't find any wacom_drv.so in any of them.

Anyone?

Thanks:confused:

---

### Post by Revfisk on 2007-11-09
Anyone?

---

### Post by High Camp on 2007-11-10
Howdy

Alright, first to answer your questions.

There are two types of root that people refer to in here. First, there is the root file system or "/". This is the base file system and is sort of equivalent to My computer in M$. To see your root file system type this in the Terminal:
```
nautilus /
Edit: I notice you're on Xubuntu so type thunar /
```
The other root is the root user. This is like the administrator in M$. You have to be the root to install programs or do anything that could potentially damage your system. To do this type this in the terminal:
```
sudo -s
```
After entering your password you'll now see that your terminal says "root@..."

Now, the root we're talking about in this post is the root file system. If you get to the root file system you can probably find a folder called "tmp" and that is generally were Firefox downloads internet files unless you specifiy otherwise. It sounds like you already found that folder and the file you were looking for wasn't there. This is because, unlike Internet Explorer, Firefox cleans up after itself. Rather than go through the long process of explaining how to change were Firefox downloads files I will just give you a command that should download the .tat.gz to your home folder. 

First, something I have learned the hard way is that you should read all the instructions in a post before doing anything.

Type the following command into the terminal (or copy and past). Just remember not to do it as root user because it will probably be saved somewhere other than your home folder:
```
wget http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.7.8-3.tar.bz2
```

Hopefully that worked and you now have a new file in your home director called linuxwacom-0.7.8-3.tar.bz2. 

Now you just need to copy the driver you just downloaded to the correct directory, which involved uncompressing the .tar and then moving the file. I'll let you give that a try and then I'm guessing you'll have to post here again to get it working.

I hope that helps and remember to just post on here if you need any help, the last thing we want you to do is go back to the Dark Side...Luke.

P.S. When using the Terminal don't be scared of all the text output it gives you. That's just the OS actually telling you what it's doing were as M$ just does it and tells you it worked or didn't.
[B]
P.S. #2: For anyone reading this post in the future, this downloads the current latest version of the Linux Wacom Tools, which may not be the correct version forever. It is your responsibility (not mine) to ensure you're downloading the right thing.[/B]

---

### Post by High Camp on 2007-11-10
OK, I'm sitting at work and procrastinating about actually doing anything today (my boss would be so proud) so I will write this before you ask for it (no offense intended but I'm guessing you will still have a hard time moving the new driver into the right place).

Remember, as I said in the last post, read all directions first.

1. Open your home folder.
2. Right click on linuxwacom-0.7.8-3.tar.bz2 and select "Extract Here"
3. Now there should be a folder there called linuxwacom-0.7.8-3
4. Rename that folder to just linuxwacom (I always do this because I'm too lazy to type all the version numbers)
Here comes the hard part:
5. Copy the new driver to the right location by typing this in your Terminal:
```
sudo cp /usr/lib/xorg/modules/input/wacom_drv.so /usr/lib/xorg/modules/input/wacom_drv.so.backup
sudo cp linuxwacom/prebuilt/32/wacom_drv.so /usr/lib/xorg/modules/input/wacom_drv.so
```
Let's break down what exactly you're doing here:
sudo - we know that one, it means super user do.
cp - copy {file to be copied} {new file name and location}
The first line backs up the current driver. The second line copies the new driver into the location of the old one.

Now go back to the first post and find those lines and continue with the tutorial from there.

---

### Post by Revfisk on 2007-11-10
Thanks.  I'll give all that a try and set you know how it went.:)

---

### Post by BarakNaveh on 2007-11-10
unfortunately, the right-click trick doesn't work well. after trying the:
 ```

xsetwacom set stylus Button2 "button 3"

```

i was initially glowing to see the right click working, but then i realized that normal clicks ("left clicks") are also mapped to be right clicks. that's of course a bit too much of right-clicks. any way to get them to co-exist? 

ideas? 

thanks,
barak

---

### Post by BarakNaveh on 2007-11-10
ok, found it -- pretty much a "duh" solution:

```

xsetwacom set stylus Button2 "button 3"
xsetwacom set stylus Button1 "button 1"

```

the first line fixes button3, but ruins button1. the second line restore button1. weird, but it works... :)

---

### Post by vmsda on 2007-11-12
Thank you for this how-to; worked for me in an IBM X41Tablet I am trying to customize for a daughter of mine, using Ubuntu 7.10. The stylus is not very stable at all times; could this be due to the fact that the driver does not yet support the Gutsy kernel version?

ALSO: this machine has a "rotate" button which is not working at present; could anybody point me to some source of enlightenment regarding this problem? Thanks in advance.

---

### Post by Revfisk on 2007-11-14
It works!!!!!   Thanks so much for your help!  HUGE!:guitar:

---

### Post by malfist on 2007-11-14
For those having problems with the buttons, check what
```
xidump stylus
``` says and use the correct parameters when using xsetwacom.

For the quesiton about the root directory, I believe I was refering to the root of where you extracted the file. Example, if you unzipped it to ~/installation/extractedHere/ then the root folder would have been ~/installation/extractedHere/packageName/

---

### Post by DrNick664 on 2007-11-23
I just want to say thanks because I spent so much time trying to figure this out on my own...without success and this really helped me.
Also however you have a slight mistypesudo gedit /etc/X11/xorg.cong I believe it should say sudo gedit /etc/X11/xorg.conf and When you talk about the server layout it would be easier if you said to just delete the three #.
 If I'm wrong just ignore me... I don't really know what I'm talking about. But Thanks a lot this really helped.

---

### Post by malfist on 2007-11-23
It seems the default from a fresh install has those three lines commented out but if you update or are running an older version or have deleted them, or one of the many reasons you might not have them is why I left it in. I'll clarify.

---

### Post by sangamc on 2008-01-20
my fujitsu 4020 has a group of buttons just below the screen that can be used to rotate the display and the stylus config when i used to have windows. does anyone know how i cna configure these in ubuntu. id like to map the xrandr command to these buttons

---

### Post by malfist on 2008-01-22
```
xidump stylus
```

That should show which buttons are which. Set the xsetwacom accordingly.

What you want to do is bring your pen to the screen and click normally, that is button 1.
Then right click, that is your other button.

---

### Post by vpik01 on 2008-02-19
**malfist** - thanks for the great guide!  I'm very new to linux and am feeling the thrill of victory after finally getting something working - the wacom stylus, with right click!

---

### Post by Atomjack Magazine on 2008-02-20
Hey, guys, just a word about my experience in installing and getting this stuff to work.

First, xrandr didn't seem to do anything (it had no error messages, tho), until I did I restarted my X server (logout).  Then it rotated properly.

Also, in the scripts you wrote to automatically set the rotation and the cursor, i had to add the line:

xsetwacom set cursor rotate cw

to the toTablet.sh

and xsetwacom set cursor rotate NONE

to the toLaptop.sh

to get the cursor to match up with my pen.  It was all crazy otherwise.

Those are the only two problems I had though.  I want to thank you for writing a great, easy to understand HOWTO.  Good job.

---

### Post by malfist on 2008-02-21
Those scripts are dependant upon several factors, the ones I posted worked for mine and I assumed it would work for all.

---

### Post by bwisdom on 2008-03-02
Im having a problem and its not really concerning the tutorial. I've followed a different tutorial and everything works except screen rotation. When I type in:
sudo randr -o 3; I get:
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  159 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12

Its the same error for any option of the -o type. I have inserted the Option "RandRRotation" "On" bit and still no dice. I saw somewhere else that you needed to add Option "Rotate" "CCW" to manually rotate counter-clock wise (It could be changed to CW if you wanted clock wise) but to no avail. Ive even done both commands by themselves with no good stuff.

EDIT: I just tried this tutorial and I got the same results.

Hopefully someone here will know how to help!
Thanks,
bwisdom

---

### Post by malfist on 2008-03-02
Do you have a graphics driver that will run randr correctly? I've heard reports that VESA doesn't but I'm running VESA and I don't have that issue. Can you get the version number for randr? Perhaps you could look at randr's man page and play around with the options and see what happens.

---

### Post by gorcq on 2008-03-10
[FONT="Times New Roman"]I'm getting the same problem as bwisdom. Did anybody find a solution? I'm using the trident driver, but I really don't know how to find out if that works with randr.[/FONT]

---

### Post by malfist on 2008-03-12
You can add the Rotate option to the Xorg.conf but in my experence it never helped. What does randr say when you try to rotate, and what does it do?

---

### Post by gorcq on 2008-03-13
It doesn't do anything, except display this error:
```

gorcq@Otter:~$ sudo xrandr -o 3
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  155 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12

```
It does this for any number greater than 0.

And, on an only partially related topic, my stylus stopped working. I set it up according to the guide above, and though it worked yesterday and I haven't changed any of the pertinent settings, it stopped working.

---

### Post by malfist on 2008-03-13
did you set the script to run on start up? What happens if you use the non-integer parameters for randr?

---

### Post by gorcq on 2008-03-14
I set the script that enables the right-click button to run on startup, but I can;t tell if that's working now because the stylus stopped moving. I'm guessing not. I didn't set the xrandr script to run anytime, because it doesn't work.

Using non-integer numbers just gets me the list of available xrandr commands:
```

[gorcq@Otter ~]$ xrandr -o 0.164
usage: xrandr [options]
  where options are:
  -display <display> or -d <display>
  -help
  -o <normal,inverted,left,right,0,1,2,3>
            or --orientation <normal,inverted,left,right,0,1,2,3>
  -q        or --query
  -s <size>/<width>x<height> or --size <size>/<width>x<height>
  -r <rate> or --rate <rate>
  -v        or --version
  -x        (reflect in x)
  -y        (reflect in y)
  --screen <screen>
  --verbose
  --dryrun
  --prop or --properties
  --fb <width>x<height>
  --fbmm <width>x<height>
  --dpi <dpi>/<output>
  --output <output>
        --auto
        --mode <mode>
        --pos <x>x<y>
        --rate <rate> or --refresh <rate>
        --reflect normal, x, y, xy
        --rotate normal, inverted, left, right
        --left-of <output>
        --right-of <output>
        --above <output>
        --below <output>
        --same-as <output>
        --set <property> <value>
        --off
        --crtc <crtc>
  --newmode <name> <clock MHz>
                     <hdisp> <hsync-start> <hsync-end> <htotal>
                     <vdisp> <vsync-start> <vsync-end> <vtotal>
                     [+HSync] [-HSync] [+VSync] [-VSync]
  --rmmode <name>
  --addmode <output> <name>
  --delmode <output> <name>
```

---

### Post by malfist on 2008-03-14
I meant the strings, sorry. Like CW or left.

Here's something that might help you:
[http://lists.freedesktop.org/archives/xorg/2005-October/010510.html](http://lists.freedesktop.org/archives/xorg/2005-October/010510.html)

---

### Post by gorcq on 2008-03-14
[font=serif]Oh. No, that gives me the same error message I posted originally. No difference.

Interesting side note: shouldn't xidump -l and xsetpointer -l give basically the same output?[/font]
```
gorcq@Otter:~$ sudo xsetpointer -l
0: "Synaptics Touchpad" [XExtensionDevice]
4: "Configured Mouse"   [XPointer]
5: "Generic Keyboard"   [XKeyboard]
3: "stylus"     [XExtensionDevice]
2: "cursor"     [XExtensionDevice]
1: "eraser"     [XExtensionDevice]
gorcq@Otter:~$ sudo xidump -l
Synaptics Touchpad             extension
Configured Mouse               disabled
Generic Keyboard               keyboard
```

---

### Post by gorcq on 2008-03-15
[FONT="Times New Roman"]And on closer inspection, it appears that my stylus does work properly when I first boot up, but putting the machine into hibernation somehow turns the stylus off. I haven't yet found a way to get it back other than restarting the computer.[/FONT]

---

### Post by malfist on 2008-03-17
hibernation is finicky, I don't use it.

---

### Post by gideon793 on 2008-04-13
i just got my stylus to work... thanks

---

### Post by cbaze on 2008-05-07
Please help.  I am using a 2710p and still cannot get this to work.

chris@chris-laptop:~$ dmesg |grep ttyS
[   13.104926] 00:02: ttyS0 at I/O 0x200 (irq = 6) is a 16550A


# xorg.conf (xorg X Window System server configuration file)
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

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
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by malfist on 2008-05-09
Can you tell me what it is doing? Other than it doesn't work?

---

### Post by aaronwh98 on 2008-05-09
BTW - I have a X61T.  I was having trouble getting the eraser to register as the middle mouse button.  It would activate the cursor but was acting just like the stylus.  For some reason the line 
```
Option  "Button3" "2"
```
wouldn't work.  I got it to work by changing it to:
```
Option  "Button1" "2"
```
and moving the entire eraser section to before the stylus and cursor sections.  Gotta love simple trial and error. :)

---

### Post by cbaze on 2008-05-10
> **malfist said:**
> Can you tell me what it is doing? Other than it doesn't work?

It's doing nothing.  Completely unresponsive to stylus.  Do you know of anything else I can check?  FYI I have 64 bit Ubuntu.

Thanks

---

### Post by cbaze on 2008-05-10
Tablet worked fine when I was running windows, so I know the hardware is not at fault.

---

### Post by malfist on 2008-05-11
Try this and tell me what you see.
```

xidump stylus

```

---

### Post by cbaze on 2008-05-11
chris@chris-laptop:~$ xidump stylus
Unable to find input device 'stylus'

---

### Post by cbaze on 2008-05-13
hmmm can't find stylus, that can't be good

I replaced the driver... what else am I missing?

---

### Post by malfist on 2008-05-14
if xidump can't find your stylus it's because you didn't put it in your Xorg.conf, or you don't have it in the correct spot or do not have a serial tablet.

edit: It looks good, what does
```

xidump -l

```
Tell you?

---

### Post by cbaze on 2008-05-15
chris@chris-laptop:~$ xidump -l
Configured Mouse               disabled
Generic Keyboard               keyboard

forgot to mention that I have a MoGo bluetooth mouse... perhaps that could be interfering with something?

---

### Post by malfist on 2008-05-16
According to that, there is not stylus. There should be three other devices there, being the ones that are in your Xorg.conf

Can you repost your /etc/X11/xorg.conf? Try to put it in [html]```
 
```[/html] tags, it makes it more readable.

---

### Post by cbaze on 2008-05-17
```
# xorg.conf (xorg X Window System server configuration file)
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

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
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection
```

---

### Post by malfist on 2008-05-17
Have you restarted your X server (I.E restarted the computer)? Are the drivers in the correct place?

---

### Post by linuxnube on 2008-07-08
Hi, 

I've read though this whole thread and tried the exact procdure outlined here on a fresh install of Hardy on a new Fujitsu T2010U several times but no joy. There is simply no response to the stylus.

```
dmesg |grep ttyS
```
outputs
```
[   21.610114] 00:05: ttyS0 at I/O 0x220 (irq = 4) is a 16550A
```

My xorg.conf file is
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
#  Option        "Device"        "/dev/input/event0"   # USB ONLY
  Option        "Type"          "stylus"
#  Option        "USB"           "on"                  # USB ONLY
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
#  Option        "Device"        "/dev/input/event0"   # USB ONLY
  Option        "Type"          "eraser"
#  Option        "USB"           "on"                  # USB ONLY
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
#  Option        "Device"        "/dev/input/event0"   # USB ONLY
  Option        "Type"          "cursor"
#  Option        "USB"           "on"                  # USB ONLY
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
	InputDevice    "stylus"    "SendCoreEvents"
        InputDevice    "eraser"    "SendCoreEvents"
        InputDevice    "cursor"    "SendCoreEvents"    # For non-LCD tablets only
EndSection
```

I noted that the tutorial mentioned removing sections form xorg.conf listed as wacom, stylus and eraser but there weren't any in there in the first place. 

Also 
```
xidump -l
```
gives
```
Virtual core keyboard          keyboard
Virtual core pointer           disabled
Generic Keyboard               unknown
Configured Mouse               unknown

```

If that helps.

I had previously tried an approach mentioned [here]("http://www.digriz.org.uk/debian-fujitsu-t2010") but abandoned those changes as they didn't seem to do anything either...

I've been at this for days now but being a total rookie at this I am about to give up on Ubuntu, so if anyone can suggest something that might help I'd be eternally grateful.

---

### Post by High Camp on 2008-07-08
Unfortunately I can offer no help here. If you've tried other options I would try a completely clean install of Ubuntu to be safe if thats an option. What I do is have my /home folder on a separate partition from the rest of the OS so I can literally install as many times as I want and most of my setting remain unchanged.

On a side note. I did a clean install of 8.04 (because I don't believe in the upgrade process). Before doing the install I backed up my xorg.conf file. I was able to install the wacom-tools, drop in the backed up file and everything works perfectly so that means 8.04 didn't change the xorg.conf file too much.

Hope that helps someone.

---

