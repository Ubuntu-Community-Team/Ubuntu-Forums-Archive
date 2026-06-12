---
title: "Ubuntu on Toshiba Satellite Pro 6100 / GeForce4 440 Go - HowTo"
date: 2007-10-14
forum: Hardware &amp; Laptops
---

### Post by r3uk on 2007-10-14
I'm relatively new to this Linux lark and it's taken me hours to get my graphics working on my Toshiba Sat Pro 4100 laptop at 1600x1200 resolution - but with persaverance I got there, noted down every step and just to make sure I flattened the laptop twice before reinstalling first Dapper and then Feisty to confirm the info below is correct and works.

My wife is ready to divorce me for spending my weekend on this but I document it here in case I ever need it again (or if someone else finds it useful). I found other people on this forum with similar problems but no specific answers for my case.

I'm going to write this as a bit of an 'idiots guide' because this is an old laptop now and anyone wanting to install Ubuntu on such a machine may just be doing so in order to have a play to find out what this Linux game is all about (as I was).

After a normal Ununtu installation, this laptop will work just fine at 1600x1200 resolution. This is because it will be using the supplied open source 'nv' driver to power the Nvidia hardware. While this is all well and good for 2D operation, you won't get any 3D shenanigans out of the nv module which means your fancy 32MB graphics card with it's whizzo 3D capabilities is reduced to doing what a 2MB card could have done. You'll soon notice the problem - no GL screensavers, no 3D games and even screen updates in programs like OpenOffice can look broken up (try selecting pages of text in the Spreadsheet application and you'll see your screen flicking like a strobe light!)

The solution is to install the proper Nvidia driver. If only it were that simple though. After installing the Nvidia driver you will find one or more of the following problems:

The driver thinks it detects a CRT screen on the VGA port and tries to use that in preference to the laptop screen resulting in the screen being black and appearing to be off;
The driver tries to use the wrong resolution giving 1280x1024 or 1024x768 instead of 1600x1200 which works but doesn't look pretty;
The driver can't detect any valid resolutions and you get a 'trippy' blotchy white and black fading screen;
You get a 'virtual desktop' at the correct resolution, however the physical screen has been limited to a lower resolution resulting in you scrolling around to see the four corners of your desktop.

If set up incorrectly, other problems will be a failure to start the X server altogether resulting in errors such as 'API mismatch'.

The contents of these instructions have been tested in both Dapper (6.06) and Feisty (7.04).

If you've just installed Ubuntu, you'll find some of the repositories are not available for use. You'll need to open them up in order to get access to some of the required packages. Assuming you've logged into Gnome (using the default nv video driver), open Applications / Accessories / Terminal and use the following command to edit your sources list:

sudo nano /etc/apt/sources.list

Remove the hash '#' from the beginning of all the named repositories, for example change:
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu)
to:
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu)

...obviously if you're not in the UK your repositories may be named differently. Press CTRL-O to save changes and CTRL-X to exit from Nano. Now enter the following command to ensure your installation is fully updated:

sudo apt-get update   ... or use System/Administration/Update Manager to check for and apply outstanding updates.

The following packages need to be installed, either through Update Manager or by using sudo apt-get install [packagename]    -You can check to see if any are already installed on your system with the command:   dpkg-query -l | grep [name]

build-essential
linux-restricted-modules-[arcitecture] (686 for Pentium/Celeron machines)
linux-headers-[arcitecture] (686 for Pentium/Celeron machines)
ghex (a Hex editor for Gnome - others are available if you prefer and I've also used khexedit under Gnome which works well).

Before you log out of Gnome, download the Nvidia driver from [www.nvidia.com/object/unix.html](www.nvidia.com/object/unix.html)
You'll have to check which driver is the correct one for your GPU and architecture. In the case of the GeForce4 420 Go on my Toshiba, it is the Legacy IA32 1.0.96xx driver and at the time of writing, version 96.43.01 is the current version. I'm going to download this to my Desktop for the sake of this guide.

Okay, we're ready to install the new driver. We can't install it while the old driver is in use though so click the exit button and log out of Gnome. When back at the login screen, press CTRL-ALT-F1 for a command login. Log in to the command line with your username and password.

Gnome is still running in the background (press CTRL-ALT-F7 if you want to return to the graphical login), but we need to stop it, so from the command line enter sudo /etc/init.d/gdm stop

Now go to where your downloaded driver file lives (the Desktop in my case):
cd /home/[username]/Desktop

Start the installer:
sudo sh NVIDIA-Linux-[version]-pkg1.run

The installer will prompt you for a few things. Answer as below:
Accept the licence agreement;
Say No when prompted to check for a kernel interface to download;
Hit OK when informed the installer will need to compile a new kernel interface;
Allow the installer to run. If it fails, check the correct dependant packages are installed. If not, install them and try again. Use 'nano /var/log/nvidia-installer.log' to check the installation logs for problems.
Assuming all went well, answer Yes to allowing the installer to run nvidia-xconfig. Installation should now be complete.

The installer will have made changes to /etc/X11/xorg.conf. The main change is that the driver will now read 'nvidia' instead of the open source 'nv' driver. You can edit xorg.conf and put the 'nv' driver back into place if you really get stuck with getting the nvidia driver to work. The installer has also backed up the old xorg.conf file and this can be found under /etc/X11 as xorg.conf.backup should it be required.

You can try the new driver by entering sudo /etc/init.d/gdm start however on my machine I just get a horrible black and white blotchy screen. This is what we need to fix before continuing. If your screen is corrupted like mine, use CTRL-ALT-F1 to return to the command line and use sudo /etc/init.d/gdm stop to kill the display mode. Take a look at /var/log/Xorg.0.log to see if you can spot what the problems are. In my case I have the following line of interest:
(II) NVIDIA(0): Assigned Display Device: CRT-0
..indicating a non-existent external monitor is being assigned by default instead of the laptop LCD (which has the designation 'DFP-0')

To correct this, enter sudo nano /etc/X11/xorg.conf and add the following line to the Device section:
Option    "UseDisplayDevice"    "DFP-0"
A similar command (with the same effect) is: 'Option "IgnoreDisplayDevices" "CRT-0"' although the NVIDIA readme recommends using the former. While in xorg.conf, scroll to the Screen section and set the DefaultDepth to 24 if it isn't set already. Save and exit when editing is complete.

So we don't have an API mismatch error when we reboot the laptop, enter the following command:
sudo nano /etc/default/linux-restricted-modules-common
and change the line that reads "DISABLED MODULES="" to read DISABLED MODULES="nv"
Save changes and quit Nano (CTRL-O, CTRL-X).

Now issue a 'sudo reboot' command to restart the computer. If all is well you should get an NVIDIA logo splashscreen and a graphical login prompt. The resolution won't be correct though (1024x768 in my case and not the 1600x1200 I want). If you don't get a graphical login, check the Xorg.0.log to see what reason is given. Different laptops, drivers and chipsets may yield different results. As I'm writing this about my specific laptop I will continue with my observations.

Here's where it gets really interesting. The reason I don't have my 1600x1200 resolution is because of my pesky EDIDs. This stands for Extended Display Identification Data and is a mechanism for a display to provide information to a graphics card on what it's capabilities are (size, refresh rate, etc.) More info on EDIDs can be found on Wikipedia. In my case, the graphics card and the screen aren't on the same wavelength (so to speak) so my GeForce thinks my screen isn't capable of 1600x1200 resolution and refuses to allow it even though that resolution is specified in xorg.conf. There are numerous options to add to Xorg to ignore EDIDs, ignore EDID DPI's, ignore EDID frequencies, ignore EDID modes, set specific modelines - they're all in the Nvidia Readme and none of them worked for me. The only answer I could find was to edit the EDID settings themselves with a hex editor. To do this, log into Gnome. Press Alt-F2 for a Run box and enter nvidia-settings which should launch the Nvidia X Server Settings application.

Click on DFP-0 (or whatever your screen is called) and click the Acquire EDID button. Save your EDID file to your Desktop and call it EDID-current.bin (or something).

Quit Nvidia-settings and open another Run box. Type ghex2 to open your hex editor (if it was ghex you installed earlier). From within the hex editor, open the EDID-current.bin file you saved.

The hex pairs represent various settings to do with the graphics configuration. Contained within is information such as screen size and frequency as well as detail like serial number and manufacturer. Here's an example - bytes 16 and 17 represent week and year of manufacture respectively. Counting along the top line and calling the left most byte 'zero', I can see that byte sixteen is 2D and byte 17 is 0C. These are hex numbers so convert them to decimal and you get 45 and 12. The 45 indicates manufacture in the month of November while the year is represented as 1990 plus 12 - i.e. 2002. I can therefore see that my chipset was manufactured at the end of 2002. Another example are the 20 and 18 hex pairs at bytes 21 and 22. In decimal these convert to 32 and 24 and represent the physical screen size, horizontally and vertically in centimeters. I'm interested in  byte 56 however - The 'Horizontal Active' value (in pixels). Mine is listed as 34 hex which converts to 52 decimal. This value is wrong!

To work out the correct number, take the desired horizontal setting in pixels (1600 in my case) and convert to hex. This gives me the number 640. Take the last two digits (40) and replace the value in byte 56 with these digits.

Use File/Save As to save the modified EDID file. Plonk it somewhere safe where it won't be deleted. I saved mine as edidnew.bin onto the desktop and then placed it in /etc/X11 so it would sit with xorg.conf. You might not have permission to copy the file over from Gnome but from a terminal just issue the command:
sudo cp /home/[username]/Desktop/edidnew.bin /etc/X11/

Now log back out of Gnome and use CTRL-ALT-F1 to get to a command login. Log into the computer and open xorg.conf for editing with sudo nano /etc/X11/xorg.conf

In the Screen section enter the following line (assuming your edited EDID file is in the same path as mine):
Option    "CustomEDID" "DFP-0:/etc/X11/edidnew.bin"

Save your changes and exit Nano.

Restart Gnome with sudo /etc/init.d/gdm restart

Hey presto! 1600x1200 !  Log in and try out some OpenGL screensavers or some 3D gaming!

Useful Commands:
The following commands may come in helpful for faultfinding with a graphics issue - I know I found them helpful while researching the above. You'll need sudo in front of most of them...

dpkg-query -l | grep [name]                        #Check for installation of a named package
dpkg-reconfigure -phigh xserver-xorg        #Creates a new xorg file based on settings you enter
dpkg-reconfigure xserver-xorg                  #As above but with more options available
sh [package] --uninstall                             #If you need to uninstall a driver you previouslly installed
gtf [hresolution] [vresolution] [refresh] -x    #For generating Modelines to set specific monitor modes in xorg

Useful Links:
Nvidia Linux drivers download page
[http://www.nvidia.com/object/unix.html]("http://www.nvidia.com/object/unix.html")
xconfig options page
[http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/README/appendix-b.html]("http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/README/appendix-b.html")
EDID information on Wikipedia
[http://en.wikipedia.org/wiki/EDID](http://en.wikipedia.org/wiki/EDID)
My site with same information plus screenshots
[http://www.r3uk.com/index.php?option=com_content&task=view&id=173&Itemid=64]("http://www.r3uk.com/index.php?option=com_content&task=view&id=173&Itemid=64")

---

### Post by r3uk on 2007-10-20
A slightly different procedure for getting this laptop working in Gutsy, this time using the Nvidia restricted drivers. Full details are available here:

[http://www.r3uk.com/index.php?option=com_content&task=view&id=174&Itemid=64]("http://www.r3uk.com/index.php?option=com_content&task=view&id=174&Itemid=64")

---

### Post by svaens on 2008-05-31
Hi, 

thank you very much for your helpful guide to EDIDs! With your help, i got my laptop working at a reasonable resolution, and I am pretty much happy. 

I was wondering however, if I may ask a question or three. 

**Question 1.**
I wanted to learn more about EDID hacking... well... particularly about the Horizontal and vertical Active bytes. To be honest, I don't understand how they work. That is, you mention in your guide that to get your value (that you replace the incorrect value with) you find the resolution you want in decimal, convert that to hex, and only use the last two digits (as it is only a byte we need). 
> 
To work out the correct number, take the desired horizontal setting in pixels (1600 in my case) and convert to hex. This gives me the number 640. Take the last two digits (40) and replace the value in byte 56 with these digits.

However, that confuses me, because there may be several values that end in the same 2 digits in hex. 
For example, 
1280 = 500
1024 = 400

they both end in the same two digits (00) and therefore... i would have thought we'd have a problem there... as how then can we specify a specific resolution?

I presume I must have misunderstood. 

The WIKI, while a nice summary, doesn't go into detail

> 54&#8211;71: Descriptor Block 1
  54&#8211;55: Pixel Clock (in 10 kHz) or 0
  If Pixel Clock is non null:
    56: Horizontal Active (in pixels)
    57: Horizontal Blanking (in pixels)


and the only other documents i've found are the a pdf... i think the actual specification... and it seems to concur... and says 'lower 8 bits'.. 
but how!!!?
[B]
Question 2:[/B]

My next related question would be to understand this case, 

lets say the original EDID reports 1024x1024   (however you figure)
which is wrong,  
It should be 1280x1024
BUT as I have explained my confusion above, both times the lower 8 bits end in 00 (hex). 

**Question 3**:

I remember with my old CRT, i was able to pretty much specify any stupid resolution I liked. Real Large resolutions even. The monitor might not have liked it, and the font might have been really small, and a little fuzzy..... but it'd do it. That was back when I was using windows on my old celeron 800MHz. 

Now days i've switched to linux, and I have a laptop (toshiba satellite) and ... while at some stage I did have windows on it, i can't remember if i was able to do the same thing... force an unwise resolution on my screen. 

Currently I have what is probably intended on my laptop. That is, 1024x768.
However, I find this a bit... boxed in. I would like more space. Say, a resolution of 1280x1024

Do you know, Can I create a custom edid that reports this resolution, and force this upon my computer? 

Sorry for the long post, 
Kind regards, 

svaens

---

### Post by svaens on 2008-06-01
Actually... not only that... It can't be even the combination of values to distinguish between resolutions... 
for the lower 8bits of ALL of these values end in '00'

1280x1024   (00x00)
1024x768    (00x00)

So.... 
I would say 'it can't possibly work', except that it obviously does (somehow) ...... but how?

---

### Post by svaens on 2008-06-01
ok.. i should read it all.... 
found where the other 4 bits go.. 

So I tried it out. But instead of (what would happen on my crt many years ago) 1280x1024 pixels fitting squishing inside of my screen, 
they didn't appear to fit... and so the bottom and the right side of my desktop are off the screen now... 

Question is, is there any way to scale it? 
Do LCD's have a definite maximum pixels (whereas with CRT's? You can try and squish them in?)
What is this 'Clone Screens' option in the 'Monitor Resolution Settings' and can it help me?

---

