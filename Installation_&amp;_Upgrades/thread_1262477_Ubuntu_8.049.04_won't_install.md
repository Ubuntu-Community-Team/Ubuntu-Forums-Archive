---
title: "Ubuntu 8.04/9.04 won't install"
date: 2009-09-09
forum: Installation &amp; Upgrades
---

### Post by CyborMonkeez on 2009-09-09
For starters I'm a Linux noob.
When I boot from CD I get the initial install GUI screen.  At first I selected the standard install method.  Then many others, even changing settings.  Amidst the installer loading everything to start installation, I get a CMD style screen (just black w/ text) the stops at a command prompt giving me no errors:
> ubuntu@ubuntu:~$ _I searched "install how to's" to find nothing about getting a cmd prompt and I get the same result from doing a LiveCD and Boot From First Hard Disk installs.  Tried the install with both 8.04 and 9.04 versions. MDK5 and Ubuntu check says my iso and disk are fine. Thought it might be my laptop [Sager NP9262 (Clevo D901C based)] but I did a search to find many other people have the same rig running Ubuntu 9.04 or Linux Mint 7.  Even one triple booting Vista, OS X 10.5, Ubuntu 9.04.  Also posted those sites hoping for an answer to this dilemma.

---

### Post by earthpigg on 2009-09-10
can you give us more detail, please?

exactly which install methods did you try, what options did you choose, etc?

and, just for fun, you could try this at the command prompt:

> sudo apt-get install ubuntu-desktop

---

### Post by CyborMonkeez on 2009-09-10
Tried running the command> ubuntu@ubuntu:~$ sudo apt-get install ubuntu-desktop the result is > Reading Package list... Done
Building dependency tree
Reading state information... Done
ubuntu-desktop is already the newest version.
0 upgrade, 0 newly installed, 0 to remove and 0 upgraded
ubuntu@ubuntu:~$ And it goes right back to the prompt.
What I've tried is installing from CD, running it through LiveCD, and installing from Hard Drive option, changing the F4 Options (Normal, Safe Graphical Mode), and F6 Options turning on/off ACPI, APIC, LAPIC, EED.  What really stumps me is I can't boot into Ubuntu even from LiveCD but I can run it in VirtualBox on WinXP on the same laptop it wont install to.

---

### Post by earthpigg on 2009-09-10
what happens if you type either of these two commands?

> startx

> xinit

---

### Post by CyborMonkeez on 2009-09-10
Both "startx" and "xinit" give the same feedback.
> (==) Log file: "/var/log/xorg.0.log
(==) Using config file: "/etc/x11/xorg.conf"
Primary device is not PCI
(EE) No devices detected
Fatal server error:
no screens found

Please consult the X.Org Foundation support at [http://wiki.x.org](http://wiki.x.org) for help
Please also check log file at "/var/log/Xorg.0.log" for additional information

ddxSigGiveUp: Closing log
giving up.
xinit: No such file or directory (errno 2): unable to connect to X server
xinit: No such process (errno 3): Server errorI searched through x.org troubleshooting database to find that my video chipset (nVidia m9800 GTX) isn't support without propriatary drivers, but can be bipassed with VESA or VGA settings in xserver.  I'm not finding anything about unsupported PCI-E bus that my video cards are on.  Which is the reason I'm guessing for the > Primary device is not PCI
(EE) No devices detected Maybe it's not recognizing the mainboard chipset (Intel P965g)

Thanks for the advice so far, its helped to get further info on the problem and closer to resolving it.

---

### Post by CyborMonkeez on 2009-09-10
Still not finding any known problems through Ubuntu forums, x.org's forums or anywhere else.  According to the Linux Hardware Database, Xserver should do an auto install of my gfx cards on the core installation without implementing x11.  That being said I did "alternate installation CD" the text based install went seemlessly, until it finished and restarted.  Upon logging into Ubuntu I get a command line login only, no GUI.  Maybe now that Ubuntu is installed onto the drive it will be easier to troubleshoot and fix.

---

### Post by earthpigg on 2009-09-10
i just woke up.

it seems you are online too -- im gonna keep this tab open and come back to it in a few minutes :D

---

### Post by earthpigg on 2009-09-10
> I searched through x.org troubleshooting database to find that my video chipset (nVidia m9800 GTX) isn't support without propriatary drivers,

did it tell you ***which*** proprietary drivers you needed?

well, lets go ahead and install nvidia-common.

verify your internet is working:
> ping -c 3 google.com
install:
> sudo apt-get install nvidia-common

> nvidia-common - This package will find obsolete NVIDIA drivers in use, detect the hardware, and recommend the most appropriate driver.

this will also include a bunch of these packages:

> nvidia-173-modaliases - The modaliases provide a list of pci id's which makes it possible to detect the model of the graphics card

where 173 may be 180, 71, 96, etc.



i have never configured a graphics card from the command line in Ubuntu. i suppose, after nvidia-common is installed, go ahead and restart and then try startx and xinit...

---

### Post by CyborMonkeez on 2009-09-10
> nvidia-common is already the newest version
Even funnier is lspci command lists all my pci devices installed, including
> 01:00.0 PCI bridge: nVidia Corporation Device 01b3 (rev a3)
02:00.0 PCI bridge: nVidia Corporation Device 01b3 (rev a3)
02:01.0 PCI bridge: nVidia Corporation Device 01b3 (rev a3)
03:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GTX (rev a2)
04:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GTX (rev a2)
along with every other pci device in the system...

---

### Post by CyborMonkeez on 2009-09-10
is there a command to check for installed video drivers, since Ubuntu obviously does recognize the gfx cards?  But it all doesnt make sense that the given error is > Primary device is not PCI
(EE) No devices detected when trying startx/xinit.  Seems like it's not connecting to Xserver at all, xinit gives "server error" and "unable to connect to Xserver"

---

### Post by earthpigg on 2009-09-10
see if this helps you out any:

[http://ubuntuforums.org/showthread.php?t=606905](http://ubuntuforums.org/showthread.php?t=606905)

---

### Post by earthpigg on 2009-09-10
also:

> sudo dpkg-reconfigure xserver-xorg


[http://ubuntuguide.org/wiki/Ubuntu:Jaunty#Reconfigure_xserver-xorg](http://ubuntuguide.org/wiki/Ubuntu:Jaunty#Reconfigure_xserver-xorg)

---

### Post by earthpigg on 2009-09-10
and yeah, i can imagine your frustration that your first experience with Ubuntu is having to deal with this because your hardware is not supported...

for me? if it aint listed as completely supported[here]("https://wiki.ubuntu.com/HardwareSupport"), i do not purchase it.

my video card, for example, is listed as: "_***3D***_ requires nvidia-glx, see BinaryDriverHowto."... which means i have 2d oob, which was enough for me to boot into a GUI and install the proprietary drivers by pointing-and-clicking.

...which is the same for most ubuntu users, i think.

...which also means its a bit harder for us 'veterans' to help you out. since we know we are going to be using Ubuntu and thus plan our purchases ahead of time, we often have to think back to the *very first time* we installed ubuntu and try to remember what we did and how and why.

for example, i have not personally dealt with hardware not supported out-of-the-box since 7.10, about 2 years ago. since then, if it aint supported OOB i simply do not purchase it and take my business elsewhere.

---

### Post by CyborMonkeez on 2009-09-10
I'm completely lost as to what the problem is anymore.  Going through all these troubleshooting tutorials I have figured out thats its not the gfx cards.  Nvidia-settings are fine, Ubuntu recognizes the cards... But Xserver just isnt loading. Think this is going to take alot of reading and learning to figure out whats wrong, and finding another Sager NP9262 laptop user running Ubuntu couldnt help either.

May have just solved the problem... I'm hoping
> 
If you have a problem where after installation and reboot you end up at a console prompt, it is possible that you have multiple display cards and X is not able to pick the primary card. /var/log/Xorg.0.log contains entries like the following:    (EE) No devices detected.The following command provides information on hardware installed on your system: 
[LIST]
[*]    sudo lshw -businfo | grep -i display
[/LIST]
If you see multiple display cards listed, you need to explicitly add the PCI bus ID to your /etc/X11/xorg.conf file: 

[LIST]
[*]Use your text editor to open /etc/X11/xorg.conf. (try sudo vi /etc/X11/xorg.conf)
[*]Find the line that says Section "Device"
[*]Insert a new line that says BusID    "PCIx.x.x", where x.x.x is the PCI address displayed by lshw command.
[*]Save the file. If you had to restart into recovery mode, type reboot, otherwise restart your display using sudo /etc/init.d/gdm restart.
[/LIST]


---

