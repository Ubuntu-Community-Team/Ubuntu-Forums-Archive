---
title: "HOWTO install the best drivers for Wacom Intuos4 Tablet?"
date: 2011-10-04
forum: Hardware
---

### Post by Conzeit on 2011-10-04
Hey all! I'm pretty new in Linux, even though I've had Linux for a while  I've had a Wacom  tablet (Intuos4 with mouse and ereaserpen) for about a year, I installed drivers for it from synaptic  back in Karmic, but I found they didnt work so I stopped using my tablet.

Now I'm in Natty and I'd like to get my tablet to optimal performance, what is the best series of drivers to install?   I'm not sure which drivers I have, I searched synaptic for wacom and the matches are "xserver-xorg-input-wacom" and Mypaint. Mypaint works fine BTW, but I'd like to have full funcionality for the tablet on any program (GIMP doesnt register pressure, I cant use the buttons on the tablet at all, and the mouse buttons dont work...it'd be nice if I could have the GUI menus to program the buttons like I do in windows...but I dont want to ask for too much :p)  

Thank you in advance for reading my topic =)

---

### Post by Favux on 2011-10-04
Hi Conzeit,

With Natty things should be pretty good.

You can get some benefit from cloning the latest input-wacom and xf86-input-wacom git repositories.  Instructions for doing both are in the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  The input-wacom because now support for the LEDs and OLEDs is in input-wacom's wacom.ko (the Wacom usb kernel driver).  It has been accepted by the 3.2 kernel.  See the OLED thread:  [http://ubuntuforums.org/showthread.php?t=1380744&page=25](http://ubuntuforums.org/showthread.php?t=1380744&page=25)  Work on the xsetwacom part has reached patch [v3] but has not yet been accepted into xf86-input-wacom.

You can pretty much configuring anything on the pad (ExpressKeys) using xsetwacom and a xsetwacom script:  [http://sourceforge.net/apps/mediawiki/linuxwacom  /index.php?title=Tablet_Configuration](http://sourceforge.net/apps/mediawiki/linuxwacom  /index.php?title=Tablet_Configuration)  Most of the stuff you need to know is on the mediawiki's HOW TO page:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO)

Oneiric has GNOME 3.2 which has the first version of the Wacom Tablet control panel applet in System Settings.  It only configures the stylus but there are already more hooks in the gnome-settings-daemon so no reason the capabilities can't be expanded.  However pad may be another kettle of fish.  Current configuration gui's are a bit hit and miss:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=External_applications#Graphical_Configuration_Tools](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=External_applications#Graphical_Configuration_Tools)  There has been so much change in the driver over the past year they've had a hard time keeping up.

---

### Post by Conzeit on 2011-10-05
Alright, Favux thank you so much for the help...I'll follow the threads and figure out how to do what you said...and WHAT exactly it is that you're saying XD...Should I update to a nightly build of Oneric or stay with my Natty ? (if you think I should update to Oneric please tell me how)

Glad to be in this Ubuntu, it does feel like that's what it literally is. =)

---

### Post by Favux on 2011-10-05
I'd update to Oneiric as soon as it is stable.  Not much reason I can see to stay in Natty.

However the Oneiric Beta 2 seems more buggy than the Natty Beta 2 was at the same point.  The usual rule of thumb is to wait a month after the release to get a stable version.  I'm thinking that may be more true for Oneiric than ever.  But I've always considered Natty to be sort of a Beta for Unity and Oneiric seems nicer to me.  And it upgrades your Wacom drivers automatically.

---

### Post by Conzeit on 2011-10-19
Ok favux since you told me that Oneiric would update my wacom drivers I upgraded...I kinda missed the part where I should wait a month XD

I updated to Oneiric and started the process in appendix 2 of the Bamboo HOWTO and I got stuck at this part
```

user@ubuntu:~/Desktop$ cd xf86-input-wacom-0.11.1
user@ubuntu:~/Desktop/xf86-input-wacom-0.11.1$ 
user@ubuntu:~/Desktop/xf86-input-wacom-0.11.1$ cd xf86-input-wacom-0.11.1
bash: cd: xf86-input-wacom-0.11.1: No such file or directory
user@ubuntu:~/Desktop/xf86-input-wacom-0.11.1$ 
```I cant really tell you what went wrong...I'm just following your instructions blindly because I dont know what all of this code I paste means :p

---

### Post by Favux on 2011-10-19
Hi Conzeit,

Not your fault.  Input-wacom hasn't yet been updated to work on the 3.0 kernel.  I don't know if they are planning to do that in fact.  You can work around the lack of support for 3.0 in the make files by doing this in your new input-wacom folder:
```
cd /input-wacom/2.6.36/

make -C /lib/modules/$(uname -r)/build SUBDIRS=$(pwd) modules

sudo cp wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/
```
That will create the wacom.ko you are after and copy it into place.  Work continues on the xsetwacom side of the OLED and I think [v3] of the patch set was submitted.

Unfortunately I was prophetic about Oneiric being buggy.  There's a show stopper bug right now that makes Gimp unusable.  See this Launchpad bug report:  [https://bugs.edge.launchpad.net/ubuntu/+source/gimp/+bug/863154](https://bugs.edge.launchpad.net/ubuntu/+source/gimp/+bug/863154)

---

### Post by Conzeit on 2011-10-19
Alright..I'm starting to feel silly XD  Favux, I tried your instructions but it tells me there's no input-wacom folder

I'm sure there's one somewhere but the only input-wacom folder I can find is "xf86-input-wacom-0.11.1" it doesnt have any /2.6.36/ folder and it's at my desktop. I've tried searching "input-wacom" with the unity Dash, but it's really bad for searching folders.

---

### Post by Favux on 2011-10-19
Hmmm.  It should be on the Desktop because you change directories to it before you clone the repository:
```
cd Desktop

git clone git://linuxwacom.git.sourceforge.net/gitroot/linuxwacom/input-wacom

```
Did you maybe clone into /home/yourusername?  Or did you get an error message when you tried to clone it because you haven't installed ***git-core***?  See part II. a) for that.

---

### Post by Conzeit on 2011-10-19
Ok, since it wasnt working I cloned the wacom-input again and now that's working fine...but now it seems I cant find wacom.ko which is more than a little weird c.c

EDIT: ok, found out about the locate command...now I know it's at

/lib/modules/2.6.38-11-generic/kernel/drivers/hid/hid-wacom.ko
/lib/modules/2.6.38-11-generic/kernel/drivers/input/tablet/wacom.ko
/lib/modules/3.0.0-12-generic/kernel/drivers/hid/hid-wacom.ko
/lib/modules/3.0.0-12-generic/kernel/drivers/input/tablet/wacom.ko

which of those should I copy?...does it matter?...sorry to be thick but I'm very novice at Ubuntu and Linux as well...

---

### Post by Favux on 2011-10-19
If there wasn't any errors when you compiled it should now be in the /input-wacom/2.6.36 folder/directory.

---

### Post by Conzeit on 2011-10-19
it's...not. I only followed the II appendix of the BambooHOWTO thread...should I do one of the steps before that?

What I have at the home/input-wacom/2.6.36 folder is 
Makefile.in
 wacom.h
 wacom_sys.c
 wacom_w8001.c
 wacom_wac.c
wacom_wac.h

and a subfolder

.tmp_versions

---

### Post by Favux on 2011-10-19
Hard to tell what's happening unless you post the output in the terminal so I can see what's happening.

Did you see I added to the instructions in appendix II.  You could check out the link to the post and see if seeing that helps.  Or I also described it on the OLED thread:  [http://ubuntuforums.org/showthread.php?t=1380744&page=25](http://ubuntuforums.org/showthread.php?t=1380744&page=25)

---

### Post by Conzeit on 2011-10-19
I just copy-pasted it manually in GUI and went on with the following steps in II b and everything seemed to go ok, do you think that will do?

---

### Post by Favux on 2011-10-19
It should but the wacom.ko should appear because it should be compiled.

---

### Post by Conzeit on 2011-10-19
Ok.heh...I think I'll leave it as it is since I'm a little confused and tired heh. I'll figure out how to  configure my expresskeys with xsetwacom later XD thanks a looot for all the patience and explanation

---

