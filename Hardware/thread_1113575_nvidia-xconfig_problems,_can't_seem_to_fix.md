---
title: "nvidia-xconfig problems, can't seem to fix"
date: 2009-04-01
forum: Hardware
---

### Post by creative blank on 2009-04-01
After countless Google searches, forum browsing, rebooting, and three clean installs in one day (very frustrating, might I add), I have decided to post this problem here.  It should be noted that this is my fourth day ever using Linux, and though I like to think that I'm learning at a fairly quick pace, this is quite an aggravating problem and I can not seem to find a fix for it.

I've read several forum threads, here and elsewhere, which run through the installation of the most recent nVidia drivers (hint:  not default Ubuntu installer), followed the steps precisely, and ran through the nVidia installation with absolutely no error messages.  However, the primary reason why I downloaded them was to enable the SLI capabilities of my system in hopes of better performance (so far, the only games I've run like to crash).  The command I found to be the most useful in getting all of this done:  [PHP]sudo nvidia-xconfig -a[/PHP]
This command also runs through with no errors.  However, once I boot into Ubuntu, I find that the only visible part of my screen is the top-left corner of the screen, with the rest of my monitor being completely blank.  I take advantage of this and run [PHP]sudo nvidia-settings[/PHP] to find that it has two screens enabled and supposedly running.  Clicking anywhere while the desktop appears like this is very touchy, mostly resulting in windows closing for no apparent reason.

I open up a virtual console (surprisingly everything still seems functional), and run [PHP]sudo nano /etc/X11/xorg.conf[/PHP] to see what's going on.  I find that nVidia seems to have properly set everything up, however there is a "screen 0", a "screen 1", a "screen 2", a "monitor 0", a "monitor 1", and a "monitor 2", all of which have different settings.  Surprisingly, however, SLI was shown as being enabled, with both of my GPUs detected (something that has been a problem since day one).

Upon using xfix in recovery console, everything works fine, I'm just without drivers.  When I run nvidia-xconfig without the "-a" suffix (shortcut for "--enable-all-gpus"), I find a much bigger problem on my hands: Ubuntu completely locks up and hangs immediately after the splash screen.  Using "xinit" in the console gives me a "no screen" error that I can't seem to find a fix for, and using reboot in the console leads to an indefinite hang.  I've been working on this on and off for a few hours now, and I'm currently resorting to using out-of-date drivers until I find a solution.

Does anyone have any suggestions?  I will gladly post whatever error logs and text files you wish, but I must remind you that I am a complete newbie when it comes to Linux, and therefore don't know how to do some of these things.  Thank you very much for your time, sorry for typing so damn much...  And hello, I'm new ):P

---

### Post by creative blank on 2009-04-02
...nothing?  Well, one new development has occured on this end:  upon my second reboot after initially installing the drivers, xinit does not start at all.  I get an (errno 111) and (errno 3) message, and x fails to start.  Through Google, I have found many solutions to this problem, but they all seem to involve broken, damaged, or missing files that show up as errors while x starts.  I have inspected Xorg.0.log and can safely say that absolutely no error messages appear until the very end, which simply states "no screens found".

Another solution that seems to be popular is using [PHP]sudo dpkg-reconfigure -phigh xserver-xorg[/PHP] with or without the -phigh.  However, this only asks me a series of questions about my keyboard (I have a keyboard and it's in English, OK?), and nothing else.  The xorg.conf file it generates only tells me that there's some default screen, configured monitor, and video device, however there are no specifics, not even BusIDs.  This is quite frustrating, I'd really like it if someone responds.  If I am not giving enough information, please tell me what you need to know.

---

### Post by norwoods on 2009-04-02
nvidia has an extensive README of each of their drivers that contains troubleshooting and configuration information.  i suggest that you google your driver version and README.

---

