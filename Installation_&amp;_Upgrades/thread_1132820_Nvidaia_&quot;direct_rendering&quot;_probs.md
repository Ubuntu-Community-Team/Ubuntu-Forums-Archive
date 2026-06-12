---
title: "Nvidaia &quot;direct rendering&quot; probs"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by BobJ on 2009-04-22
I'm running 8.04 on a AMD 64 dual core. I have XP up on a dual boot the graphics are fine in windows. When I try too install Cedega or try to run a pgm under wine I get "no direct rendering" messages and it fails. I have installed the media packages and the nvidia drivers. No error messages on either. It's almost as though Ubuntu can't detect my 6800 Nvidia card.

Has anyone seen this before? Any suggestions?

Thanks for your time and consideration

BobJ

---

### Post by WatchingThePain on 2009-04-22
Hi,
There is a way to edit the file /etc/X11/xorg.conf and enable direct rendering if that might help.

---

### Post by BobJ on 2009-04-23
> **WatchingThePain said:**
> Hi,
There is a way to edit the file /etc/X11/xorg.conf and enable direct rendering if that might help.

I don't mean to sound ungrateful, but if there's a way, how about shareing it? I don't happen to know any ways to fix this, that's why I posted.

Thanks for your time and consideration
BobJ

---

### Post by BobJ on 2009-04-23
It's fixed :\.

Seems that the developers in their infinite wisdom decided that when we do all the gyrations necessary to obtain and install a non-free driver are just diong it for the fun of it. So the driver, once installed gets set to "disabled".

I don't want to know why this decision was made or who made it. I would like to pass this personal opinion along to the grief^H^H^H^H^H developers.

When a person spends the time and effort to go thru a more-than-necessarily-difficult process they probably want to use the result. Setting the result of these labors to disabled (and not telling the person that you have done so) is seriously retarded. (unless you are the sort who pulls wing off flies for entertainment)

Note: Drivers are NOT disk filler. they are meant to be used.

BobJ

---

### Post by javyn999 on 2009-04-23
I haven't upgraded to Jaunty yet, but I'm having all sorts of horrible Nvidia driver issues with Intrepid.  I just wanted to reply and say this isn't the fault of anyone involved with Ubuntu.  Nvidia's drivers are proprietary, so the blame goes to them.  Granted, I can't really expect a company at this point to just open up their proprietary code, but they can at least work a bit harder on Linux drivers that are less buggy.  Save your anger for Nvidia who only cares about its Windows customers.

---

### Post by cornflake000 on 2009-04-23
I've been working with jaunty since alpha 3.  There are big changes in jaunty that make it state of the art.  The developers have been working their a**es off compiling new open source drivers to make up for the lackadaisical behavior or even apathy of the proprietary hardware manufacturers.  That includes intel, ATI and nVidia.  

I have not had my video acceleration running for a while but so what.  Linux is the future of computing and is now so far ahead of the rest it's hard to believe the hardware companies aren't keeping up the pace.  

These issues will be taken care of, no doubt.  But it's still an uphill struggle against microsoft and their monopoly on the industry.

My hat is off and flying high for the developers, bug busters and public support people for pushing that proverbial envelope that is dragging us out of the quagmire of the past.

Here here!

---

### Post by javyn999 on 2009-04-23
My biggest problem with Nvidia and Ubuntu is the fact that on many applications, the file menu text is invisible.  Say you click on File, then go to click on Open to open a doc....well once you click on 'File', all the options under that are invisible.  You can still click on the Save or Open button or any option, if you know what it is, but if you don't, you are SOL because it's invisible.

This happened on Wine, OpenOffice, Scribe, and PDF Edit.  If I disable Compiz and go to low quality visual settings, the menus reappear, but what's the fun in using the Cube if you can't even run your apps properly?  

I managed to go into OpenOffice's settings, and disable font antialiasing and it fixed it for that suite, but still a no-go on Wine, Scribe, and PDF Edit.  Disabling font antialiasing did nothing for those apps the option was even available for.

I'm open to any ideas!

---

### Post by javyn999 on 2009-04-23
Cornflake, I've been aware of Linux for years of course, but haven't tried it since the 90s when I attempted a Red Hat install and failed miserably.

What exactly has changed that will make Linux the future of computing?  I know it is a superior OS to Windows, but I'm sure Linux has been superior for a long time.  Is there something going on right now specifically that is waking people up in general to Linux? 

Honestly, I've been happy with Windows XP for a long time, but REFUSE to upgrade to Vista or Win7.  So it's either MacOS or Ubuntu for me, and I chose Ubuntu to not have to spend thousands on upgrading hardware.

---

### Post by cornflake000 on 2009-04-23
For most saving money is the first thing that comes to mind; certainly it was for me.  But I think there is an underlying philosophy that makes a whole lot more sense to me.  Let's say a guy want's to build a house.  He has a hammer but then sees he needs a screw driver as well.  He starts to use the screw driver but before he uses it he sees that it's a standard instead of a philips, so he buys another screwdriver.  Then he sees the builder next door has a nicer color one, so he gets the nicer color...  blah... blah. The house never gets built because he is always worried about the tools.  In open source the idea is to focus on the inovation of real stuff... not spend all your time and money on the tools.

Now for the short of it.... no virus software, no expence, 10 times as many productivity programs, the best art programs... uses less space, considerably faster, uses almost any hardware... Manufacturers are just now beginning to see that microsoft is not their only boss.  

Gosh, the list can go on and on and this probably isn't the forum for this.  You can find many and better posts on the subject than I can possibly dish out.  Here's my 2 cents anyway.

---

### Post by javyn999 on 2009-04-23
Unfortunately, I think productivity is lacking in Linux, at least for the average business user.  I plan on formatting this weekend and going back to a dual boot system with XP because many of the apps I need for work just aren't even being thought about for Linux yet, like a full fledged PDF Editor.  I'm sure PDF Edit for Linux is great if I can ever get it working properly, but I doubt it has the full set of features I need that only Acrobat or Nitro can provide (like Bates stamping for instance).

Also, since I work at a law firm, we do 90% of our word processing in WordPerfect just like most other firms out there.  No Linux alternative there either.

I guess my problems are just poetic justice, with me working in intellectual property law and trying to go open source!

---

### Post by WatchingThePain on 2009-04-23
Hi ,
Sorry m8 I was not being rude, my kid was running riot.
Of course I would share if you needed extra help.


You might want to back up your xorg.conf file in case this doesn't work. To backup, open the console and and type:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

If you have a nVidia card installed, add " Option "RenderAccel" "True" " to the "Device" section of your xorg.conf file in the directory /etc/X11 :

Section "Device"
Identifier "nVidia Corporation NV43 [GeForce 6600]"
Driver "nvidia"
Option "RenderAccel" "True"
EndSection

It should say nvidia not nv.

Then Ctrl-Alt-Backspace to restart xserver.

If the X server does not start, hit Ctrl-Alt-F1, log in and type
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
And then reboot.

---

### Post by BobJ on 2009-04-23
> **WatchingThePain said:**
> Hi ,
Sorry m8 I was not being rude, my kid was running riot.
Of course I would share if you needed extra help.


You might want to back up your xorg.conf file in case this doesn't work. To backup, open the console and and type:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

If you have a nVidia card installed, add " Option "RenderAccel" "True" " to the "Device" section of your xorg.conf file in the directory /etc/X11 :

Section "Device"
Identifier "nVidia Corporation NV43 [GeForce 6600]"
Driver "nvidia"
Option "RenderAccel" "True"
EndSection

It should say nvidia not nv.

Then Ctrl-Alt-Backspace to restart xserver.

If the X server does not start, hit Ctrl-Alt-F1, log in and type
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
And then reboot.

Thank you :) this is exactly what a noob like myself needs. 
BobJ

---

