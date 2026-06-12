---
title: "Cannot get nVidia driver working after trying the one from nVidia's website"
date: 2007-09-14
forum: Hardware &amp; Laptops
---

### Post by Dr_Snapid on 2007-09-14
HI all,

I managed to kill my nVidia install. As this is my business PC I'd be happy to sling a AUD$50 gift voucher for wherever you like to whoever gets me over the line!  :)

I had Ubuntu 6.10 running sweetly with dual monitors and xgl/compiz. i386, geforce 6200. I was having a problem where I was periodically logged out unexpectedly and then having to reboot. So I decided to bite the bullet and update to 7.04. I used the update manager to do so... my pc crashed right near the end of the update, but then after reboot update manager told me to finish the upgrade and it seemed to do it ok. I had a working 7.04 system although with no desktop effects and my dual monitors were weird - I had my themed gnome panels on my left monitor, and also unthemed ones on my right monitor (another set of menus too, but no theme just the plain grey buttons, looked like maybe the human theme) and for some reason the mouse wouldnt move off the left monitor onto the right one at all - except for just a few pixels (enough to see the pointer on the right screen only just)

So I set about fixing both the poor glx performance and getting the dual monitors working properly again, and I seem to have killed the lot. I have to use the vesa driver at the moment, no dual monitors or glx...

I turned on the restricted driver, OK, but glxgears was terribly slow (looked great for a few seconds then slowed down) and the desktop effects were impossibly slow... it worked beautiful on 6.10 so i know the card can handle it. I unselected the restricted driver and downloaded the driver from nVidia... assuming my card was a geforce 6 series (being a 6200).

From here on I lost X altogether when using nVidia. First it was something about a mismatch between the kernel and the driver. I re-installed the normal one (apt-get install nvidia-glx) and then the problem is "failed to load module glx". I have tried removing, reinstalling etc.

So now I cant get either the normal or downloaded nVidia driver to work. My system is one which cannot boot the liveCD (tries to run my LCD monitors at a range they cant use, even in safe graphics mode) so at the moment i'm stuck with vesa driver. Is there anyone who would know where I should start to get the nvidia driver working again please?


Thanks guys!

---

### Post by Caffeine_Junky on 2007-09-14
hey there...

Have you tried ENVY to install your NVIDIA driver?   

   [[COLOR="Blue"]Envy Homepage Link[/COLOR]]("http://albertomilone.com/nvidia_scripts1.html")

...it is worth a shot, eh :)

goodluck mate

---

### Post by Dr_Snapid on 2007-09-14
No I have not tried envy... might look it up.

Beleive it or not though, i just found the problem. I had to fully remove the nvidia-glx and linux restricted modules

$sudo apt-get remove nvidia-glx linux-restricted-modules

then installed the downloaded driver in expert mode - why this helped, i do not really know, because i accepted the defaults

$./NVIDIA-linux......pkg1.run -n -e

This got the nvidia driver working, and then the usual xorg.conf tricks workd from there to get the dual screen going. I think the issue was that I must have tried installing the nvidia driver the way I am used to (apt-get) before trying the 7.04 restricted drivers method... this must have screwed up something. I had to purge the whole lot from my system... which I had tried, but I then tried using the restricted drivers method again to no avail. So i had to purge, then use the downloaded driver.

Desktop effects are working... now i have to figure out the new interface to get them like i want them though

Typical, you fight with it for hours, the 20 minutes after begging for help, you find the solution. 

Thanks junky, i will look into envy... i dont want to go through this again next time!

---

### Post by Dr_Snapid on 2007-09-14
Doh!

After a reboot - I get the mismatch error again!

---

### Post by nick_h on 2007-09-14
> I had to fully remove the nvidia-glx and linux restricted modules
You can also add "nv" to the disabled modules list in /etc/default/linux-restricted-modules-common

There was also a bug where a file was left in /lib/linux-restricted-modules but I think this was related to the nvidia-glx-new driver.

To debug a mismatch problem check the driver version loaded using:
```
dmesg | grep NV
```
Also check for versions in the /var/log/Xorg.0.log file.

---

### Post by Dr_Snapid on 2007-09-16
I'm lost. After this:

sudo dpkg-reconfigure --xserver-xorg

i get my desktop on one screen. I edit xorg.cont to re-enable twinview by adding the line

Option		"TwinView" "True"

but what i get is the right screen has a second set of panels with no theme. the right screen has its own desktop background (same image as left, but it used to stretch across both)  and i cant move my mouse onto the right screen anyway.

This worked fine before 7.04. I even had it fine yesterday, but today i got a unexplainable hang again and had to restart, and all my nightmares are back... i am so sick of this.

---

### Post by nick_h on 2007-09-17
It might help if you posted your xorg.conf file.

---

### Post by Dr_Snapid on 2007-09-17
Tried Envy. It worked so far as it installed the driver, like it said it would. But still same problem with twinview - cant use right side screen at all. 2 sets of panels, and glxgears is slow.

---

### Post by Dr_Snapid on 2007-09-17
heres a snippet from xorg.conf. This exactly how envy left it except for the renderaccel and twinview options.


Section "Module"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "int10"
    Load           "vbe"
    Load           "glx"
EndSection

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Nvidia Dualhead"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Nvidia Dualhead"
    Monitor        "Generic Monitor"
	Option		"RenderAccel" "True"
	Option		"TwinView" "True"

    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---

### Post by Dr_Snapid on 2007-09-17
Well this is weird....

I ran 
sudo dpkg-reconfigure -phigh xserver-xorg
which reset my xorg.conf to the basics with the second monitor disabled, but i had to add
Load "glx" 
in the modules section and added the twinview option

it was exaclty how i wanted it! i had the bg image spanning both screens, panels only on the left monitor etc. perfect!

then i rebooted to see if it was ok after that, and i am back where i started. bg image is shown on each monitor separately, 2 sets of panels, mouse wont move to right screen.

redo the above procedure and its perfect again... but when i reboot it's wrong again...what gives?

---

### Post by Dr_Snapid on 2007-09-25
More info:

If I stop gdm:
sudo etc/init.d/gdm stop

and start x without gdm running:
startx

everything is hunky dory. If i start gdm though:
sudo etc/init.d/gdm start (or restart)

I get the stuffed up display... plus, now, after my desktop appears, about 3 seconds later the screen just goes white and i cannot use the pc.

For now i have just removed gdm entirely - and i am logging in at the command line, and starting x. This will be sufficient for now, I am getting a new computer soon and will install from scratch.

I still dont have a clue why this has happened.

---

