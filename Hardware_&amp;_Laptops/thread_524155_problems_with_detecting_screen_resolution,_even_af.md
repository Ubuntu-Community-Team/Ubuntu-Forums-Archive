---
title: "problems with detecting screen resolution, even after the xserver config"
date: 2007-08-12
forum: Hardware &amp; Laptops
---

### Post by scott pruett on 2007-08-12
I have a fresh 7.04 install on an Alienware Sentia m3450, and I can't get its native screen resolution to function. I ran the 'sudo dpkg-reconfigure xserver-org' script, selected the max resolution & everything lower, restarted the xserver, re-logged in, still no dice. I re-ran the reconfigure xserver thing twice more & the resolutions I initially selected were still set in the script w/in the terminal, but the main preferences still only show 1024x768, 800x600, 640x480.

The chipset is a Mobile Intel 945GM Express. Resolution is 1280x768.

Any ideas? I'm a Linux newb... *sigh*

Thanks!

(repost from beginner forum)

---

### Post by moore.bryan on 2007-08-12
*are you sure your screen can handle the higher resolution?  if so, try out the 915resolution package (it's in the repos).  if that doens't work, repost and we'll try to troubleshoot.*

---

### Post by scott pruett on 2007-08-12
> **moore.bryan said:**
> *are you sure your screen can handle the higher resolution?  if so, try out the 915resolution package (it's in the repos).  if that doens't work, repost and we'll try to troubleshoot.*
thanks.  yes, the display is a 14.1" widescreen, thus the somewhat odd resolution.

I removed the i810 driver & rebooted per post #8 in this thread: [http://ubuntuforums.org/showthread.php?t=454328&highlight=Mobile+Intel+945GM](http://ubuntuforums.org/showthread.php?t=454328&highlight=Mobile+Intel+945GM) - unfortunately nothing changed.

---

### Post by moore.bryan on 2007-08-12
[I]okay...
go to [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl]("http://xtiming.sourceforge.net/cgi-bin/xtiming.pl") and put in all your information.  the script will give you a modeline to put into your /etc/X11/xorg.conf file in the "monitor" section.[/I]

---

### Post by scott pruett on 2007-08-12
not to be completely ignorant here, but do you know where I can find these specs?

edit: specifically dot clock frequency, interlace, doublescan

---

### Post by moore.bryan on 2007-08-13
> **scott pruett said:**
> not to be completely ignorant here, but do you know where I can find these specs?
*no worries...*
> edit: specifically dot clock frequency, interlace, doublescan
*i'm not sure about those specific specs, but i'd check around the web for the specs... what's the exact name/make/model of your monitor?*

---

### Post by scott pruett on 2007-08-13
This is on an Alienware Sentia m3450 notebook.  I'm not sure who makes the LCD.  Windows System Info doesn't reveal anything I'm looking for.  Specs are 1280x768 @ 60hz.

Will look elsewhere in a bit.

thanks. :)

---

### Post by moore.bryan on 2007-08-13
[I]okay... unfortunately, there's not a lot of tech information about the display settings for that laptop.  

just to cover our bases, you installed the 915resolution package, right? 

do me a favor and post your xorg.conf file.  first, copy the file to a text doc and then upload into the thread the xorg.conf.txt file (it should be on your desktop):
```
sudo cp /etc/X11/xorg.conf ~/xorg.conf.txt
```[/I]

---

### Post by scott pruett on 2007-08-13
> **moore.bryan said:**
> just to cover our bases, you installed the 915resolution package, right? 
[n00b] i don't know.  i didn't install anything beyond what was on the base system install, that i know of at least.  [/n00b] 

> do me a favor and post your xorg.conf file.  first, copy the file to a text doc and then upload into the thread the xorg.conf.txt file (it should be on your desktop):
done.

thanks!

---

### Post by scott pruett on 2007-08-13
oh, and FWIW, I've been working on this logged in as root.

for some reason when I log in with the primary user, the screen goes white & I can't do anything but move the cursor around.

also, the display wigs out for a second or so right before the login screen.  the loading screen before then hasn't been affected.

I don't know what this is doing...

---

### Post by moore.bryan on 2007-08-13
> **scott pruett said:**
> [n00b] i don't know.  i didn't install anything beyond what was on the base system install, that i know of at least.  [/n00b] 
[i]no problems... since that's the case, we'll start with that.  install the 915resolution package and run it:
```
sudo aptitude install 915resolution && sudo 915resolution -l
```
oh, and [here]("https://help.ubuntu.com/community/FixVideoResolutionHowto")'s a step-by-step which should help...
i've also attached a "fixed" xorg.conf file in case the 915res doesn't work...[/i]

---

### Post by scott pruett on 2007-08-13
thanks for your help... I assume the 915resolution didn't work:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "915resolution"
The following packages have been automatically kept back:
  linux-restricted-modules-common linux-restricted-modules-generic 
The following packages have been kept back:
  app-install-data app-install-data-commercial apport apport-gtk 
  capplets-data dbus dbus-1-utils gnome-app-install gnome-control-center 
  gnome-panel gnome-panel-data hwdb-client-common hwdb-client-gnome 
  iptables language-pack-en language-pack-gnome-en libdbus-1-3 
  libgl1-mesa-dri libgl1-mesa-glx libglu1-mesa libgnome-window-settings1 
  libmetacity0 libpanel-applet2-0 libslab0 linux-generic mesa-utils 
  metacity metacity-common python python-apport python-gdbm 
  python-launchpad-bugs python-minimal python-problem-report python2.5 
  python2.5-minimal rdesktop tzdata unattended-upgrades update-manager 
  update-manager-core 
0 packages upgraded, 0 newly installed, 0 to remove and 43 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
sudo: 915resolution: command not found

trying the new xorg.conf & restarting... back in a few.

---

### Post by moore.bryan on 2007-08-13
[I]holy stuff being held back, batman!
try this ```
sudo aptitude update && sudo aptitude upgrade
``` then try ```
sudo aptitude install 915resolution && sudo 915resolution -l
```[/I]

---

### Post by scott pruett on 2007-08-13
um... okay, problem... lol.  before I do that... I need advice... :D

I created an archive of xorg.conf using the file browser (or whatever ubuntu calls it), copied/pasted your "fixed" version in, restarted, and now the X server isn't starting.

I'm getting a parse error on line 95: "this section must have only one of either identifier or driver" etc etc "Fatal server error: no screens found"

X server disabled... I gotta reconfigure it somehow.

This figures... haha.

(edit: I don't know how to do this, esp. just from a command line.)

---

### Post by moore.bryan on 2007-08-13
[I]sorry... that was my typo... this is has the correct settings.  you can just use the terminal, rename it, and replace the old one...
```
sudo mv xorg.conf.fixed.txt xorg.conf && sudo mv xorg.conf /etc/X11/xorg.conf
```[/I]

---

### Post by scott pruett on 2007-08-13
no problem, and thanks for your help...

However, I don't know how to get your new file onto my system.  I can load Windows, but XP can't see the Linux partition of the drive.  I'm typing this from another computer.

---

### Post by moore.bryan on 2007-08-13
*if you have a flash drive, you could put it on there and copy it over...  or a floppy (old school).*

---

### Post by scott pruett on 2007-08-13
i'll burn it to a cd... dunno the command to pull it off that drive though.  help me out please. :)

---

### Post by moore.bryan on 2007-08-13
[I]when you put the cd in the cdrom drive, type ```
sudo mount -a
``` then ```
sudo mv /media/cdrom/xorg.conf.fixed.txt /etc/X11/xorg.conf
```
that should replace my flubbed one with the good one.[/I]

---

### Post by scott pruett on 2007-08-13
almost there... says no such file or directory.  

could the disc not have mounted?  I named the disc "scottcd" if that matters.

seriously, thanks for your time... much appreciated.

---

### Post by moore.bryan on 2007-08-13
*after you type ```
sudo mount -a
``` type ```
cd /media/cdrom && ls
``` do you see the file?*

---

### Post by scott pruett on 2007-08-13
mounted /dev/cdrom successfully... the file path /media/cdrom/xorg.conf.fixed.txt isn't working..

---

### Post by scott pruett on 2007-08-13
> **moore.bryan said:**
> *after you type ```
sudo mount -a
``` type ```
cd /media/cdrom && ls
``` do you see the file?*

yup, got rid of the dots: xorgconffixed.txt - stay tuned

---

### Post by moore.bryan on 2007-08-13
*if you can see the file when you "cd /media/cdrom" then just ```
sudo mv xorg.conf.fixed.txt /etc/X11/xorg.conf
```*

---

### Post by scott pruett on 2007-08-13
> **scott pruett said:**
> yup, got rid of the dots: xorgconffixed.txt - stay tuned

this is retarded.  "mv: cannot remove..." 

...b/c the cd is read-only.

-------------------------------------

edit, sorry, still in the cdrom dir.

edit2: still not working from root dir..

---

### Post by moore.bryan on 2007-08-13
*that's okay... just replace the "mv" with "cp"...*

---

### Post by scott pruett on 2007-08-13
that's not doing anything... just jumps to a fresh command line.

---

### Post by moore.bryan on 2007-08-13
*if you're saying ```
sudo cp xorg.conf.fixed.txt /etc/X11/xorg.conf
``` brings up a blank prompt, then it copied.  try restarting the computer... (fingers crossed).*

---

### Post by scott pruett on 2007-08-13
> **moore.bryan said:**
> *if you're saying ```
sudo cp xorg.conf.fixed.txt /etc/X11/xorg.conf
``` brings up a blank prompt, then it copied.  try restarting the computer... (fingers crossed).*
having fun yet? :lolflag:

this is what I entered, and nope, it didn't copy...

sudo cp /media/cdrom/xorgconffixed.txt /etc/X11/xorg.conf

(the dots in the filename were removed during the burn, from OSX)

---

### Post by moore.bryan on 2007-08-13
[I]absolutely!  :-)
how do you know it didn't copy?[/I]

---

### Post by scott pruett on 2007-08-13
good question... I don't... but after two attempts/restarts, I still didn't get past the command line.  I'm looking at the xserver error log thingy again; this time it's saying:
> data incomplete in file /etc/x11/xorg.conf

undefined inputdevice "stylus" referenced by serverlayout "defaultlayout"

problem/error parsing the config file

fatal server error: no screens found
okay, so it did something. :)

hey man i gotta get going... will get back to this in the a.m... thanks again for your help.

---

### Post by moore.bryan on 2007-08-13
*gotcha... stepping away and mulling it over is probably the best bet.  i'll take a look at everything and post back in the morn.*

---

### Post by scott pruett on 2007-08-13
sounds good, thanks.

this is a completely fresh install of 7.04 I'm working with... wanted to fix these bugs ([wireless networking has issues too](http://ubuntuforums.org/showthread.php?t=524152)) before doing anything else... I can just do a complete reinstall of the OS if that'd be faster. :D

peace..

---

### Post by ramjet_1953 on 2007-08-14
Check out this link:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

Regards,
Roger 8)

---

### Post by moore.bryan on 2007-08-14
> **ramjet_1953 said:**
> Check out this link:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

Regards,
Roger 8)
[i]were you reading my mind, roger?  ;-)  this was the exact page i was going to suggest.

as per the networking issues, let's get you a working xsession first...[/i]

---

### Post by scott pruett on 2007-08-14
thanks guys! that looks straightforward enough. :)

 i need to be able to get the x server running again though.  any ideas?

---

### Post by moore.bryan on 2007-08-14
*earlier in this thread, you posted your xorg.conf as xorg.conf.txt... just burn that to a cd a copy your original back.  then, try out the 915resolution package as per the howto...*

---

### Post by scott pruett on 2007-08-14
[SIZE="4"][COLOR="Cyan"][COLOR="Lime"]success!!!
[/COLOR][/COLOR][/SIZE]

thanks again for your help!  this happened before the 915resolution install, but I get a weird flicker/ between the startup screen & the login screen, not sure what's up w/ that.  will snap a pic later.

I just gotta deal with the networking issue now, but I'm off to a lunch meeting... back in a few hrs...

---

### Post by moore.bryan on 2007-08-14
*excellent!  make sure to post specific details about the networking issue... i had to fight through one of those to get my thinkpad working...*

---

### Post by scott pruett on 2007-08-14
actually, problem: when I enable desktop effects, the screen goes white & I can't see anything but the cursor.  what's up with that?

will do re: the networking, thanks :)

---

### Post by moore.bryan on 2007-08-14
> **scott pruett said:**
> actually, problem: when I enable desktop effects, the screen goes white & I can't see anything but the cursor.  what's up with that?
*sorry, not a clue on that one... i have a minimal install and don't have any "eye candy" :-)*
> will do re: the networking, thanks :)
*please do... our aim is to get everything working, pratically, how you want/need it...*

---

### Post by mingo on 2007-08-14
Yeah I am having a "white screen" problem too when I try to install the non-legacy nvidia drivers on my laptop.
I post a thread about this minutes ago:
[http://ubuntuforums.org/showthread.php?t=525516](http://ubuntuforums.org/showthread.php?t=525516)

I'm just glad that I am not the only one having this problem.

---

### Post by scott pruett on 2007-08-14
> **moore.bryan said:**
> *sorry, not a clue on that one... i have a minimal install and don't have any "eye candy" :-)*
b-o-r-i-n-g. :biggrin:

> *please do... our aim is to get everything working, pratically, how you want/need it...*
all my info is in the following thread... i think... haha.

[http://ubuntuforums.org/showthread.php?t=524152](http://ubuntuforums.org/showthread.php?t=524152)

---

### Post by scott pruett on 2007-08-14
> **mingo said:**
> Yeah I am having a "white screen" problem too when I try to install the non-legacy nvidia drivers on my laptop.
I post a thread about this minutes ago:
[http://ubuntuforums.org/showthread.php?t=525516](http://ubuntuforums.org/showthread.php?t=525516)

I'm just glad that I am not the only one having this problem.
interesting.  mine goes white AFTER login, and everything goes white w/ no color shifts.  I just have to shut the power off & log in as a user w/o the desktop effects turned on.

(crosspost)

---

