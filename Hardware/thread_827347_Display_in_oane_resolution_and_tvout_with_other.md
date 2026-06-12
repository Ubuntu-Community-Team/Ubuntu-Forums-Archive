---
title: "Display in oane resolution and tvout with other ???"
date: 2008-06-12
forum: Hardware
---

### Post by flamarro on 2008-06-12
Hi, guys,
i'm now with hardy, and everything is working properly, really, my ATI, sound card, compiz, even moblock has a nice gui now, wonderful...
But i think is linux, we always have something that we would like to see working :-) Is there a possibility of having in my monitor a resolution of 1280-1024 and in my tv and at the some time a 800-600, this as clone or big desktop ???
I say this because in windows i used to use a mediacenter ( mediaportal ) and i can have this working, work in my monitor and have someone watching a movie in tv at the some time without the need of changing resolution on monitor. If i manage to do this in ubuntu, i really have so litle things to stay in windows... ok, there's the need to learn about mythtv ( is this the best mediacenter in ubuntu? MCE ? Can i with those have them in tv and keep working on monitor? 
Sorry about my english and the confused questions?

---

### Post by TheSixthPandava on 2008-09-22
This is exactly the same problem I have. I do not want to work in 800x600, and that is the only resolution that my TV recognize. What is left is to change resolution every time I want to watch something on TV [and that is several times a day], and that is very impractical.

Some month or so ago, I installed Ubuntu Linux for the first time and immediately switched fully to it. In the last couple of weeks I got acquainted with Linux and I am really not going back to Windows under no circumstances. I am still very new and still don't know much, but I am trying and will not give up.

So, after much trouble, I managed to install TVOut on my ATI Radeon 9200 [although picture is slightly moved to upper right corner and the application that should solve this problem is not working], but it only works if my Desktop Resolution is 800x600.

I also thought that maybe, just maybe, there is possibility to make TV "read" 800x600 while I use 1280x1024 on my Desktop. It woudl be GREAT. If not, I will be forced to buy new card.

---

### Post by latev on 2008-10-27
ZDRAVO!

Just curious - what version of Ubuntu are you guys using? I'm struggling with pretty much the same issue now here and it looks like you can have several xorg.conf file versions and you may have a bash script to switch them around but the major downside of this approach is that you have to reset the X server each time you decide to turn the TV on and off
Is this what you're using the tvout utility for?

And as far as I can tell so far there's no way to have the TV and the 
monitor operate at different resolutions :(
Let me know if I'm wrong!

---

### Post by TheSixthPandava on 2008-10-29
Zdravo! :)

I hope I will let you know then, but since nobody answered in more than a month, I think that there is no solution to this problem.

I'm on Gutsy 7.10. How can you change xorg.conf that is used? I thought that it is reading only original file, and this could be answer until I buy new card.

---

### Post by latev on 2008-10-29
Zdravo again!

I spent more than a day researching the tvout issue on ATI cards and I made some progress. Nevertheless it's hard to imagine that a big company like AMD (ATI) can come up with such a worthless piece of crap - I'm talking about the ati proprietary drivers and more specifically the interface - amdccccc and aticonfig. The catalyst control center sucked in WinXP too by the way so I quit using it may be about an year ago.
Anyways, here's what I've found so far:
The two utilities you get when you install the ATI driver are
aticonfig - command line tool - lots of bugs, don't trust the messages you get
amdcccle - catalyst control center for Linux - no command line for that, a bit less buggy than aticonfig, but less useful as well. It'll keep telling you that you need to reboot your machine in order for the changes to take effect, however sometimes just an X reset is required, most often changes are applied immediately. 
Another interesting part is the 
/etc/ati/ folder and the amdpcsdb file in particular. Apparently ATI is trying to eliminate the xorg.conf file from their driver configuration however each time you change settings with the aticonfig utility it'll try to modify the corg file as well - so don't run it with admin rights!
amdpcsb file is save to delete I should mention, it'll be recreated automatically

So - after playing around for hours and trying to figure out how to switch between my monitor and tv I was just about to give up, when I found the xrandr utility - that's the key to my script solution for the problem so far. Turns out the stuff provided by ATI is not sufficient to do that job. Not sure about you, but in my case I want to have my monitor running at 1280x1024 resolution and the TV at 1024x768. If I use 
aticonfig --enable-monitor tv
to switch to TV display, changes are applied immediately, however the TV resolution is not set right - and I couldn't figure out how to change it from the command line, using aticonfig. So here are the two scripts that work for me

SWITCH TO MONITOR AT 1280x1024
tl@AMD64:~/scripts$ cat mon 
#!/bin/sh

echo MONITOR|osd_cat --delay=4 --age=0 --lines=1 --pos=middle --align=center --font=-adobe-helvetica-bold-r-normal-*-*-2000-*-*-p-*-*-* --colour=green --shadow=3 &
aticonfig --enable-monitor tmds2i
xrandr -s 1280x1024 -r 75

exit 0

SWITCH TO TV AT 1024x768
l@AMD64:~/scripts$ cat tv
#!/bin/sh
# Switches to TV only - TL Oct 2008
xrandr -s 1024x768
aticonfig --enable-monitor tv
clear
xrandr -s 1024x768
#xrandr -s 1024x768
echo TV|osd_cat --delay=4 --age=0 --lines=1 --pos=middle --align=center --font=-adobe-helvetica-bold-r-normal-*-*-2000-*-*-p-*-*-* --colour=green --shadow=3 &
exit 0

in the above script I had to change the resolution of the monitor prior to switching to TV in order to get the resolution right.

As for your problem of having both the TV and the monitor on at the same time at different resolutions - I managed to do that as well for a while, however in that particular configuration in Linux /may be the fact that I'm running compiz matters too/ I find the driver to be extremely unstable thus unusable - chances are it'll screw up your display, may even lock up your system so you'll have to the a cold reboot.

If you want to play around with it this command will turn both displays on for ya
aticonfig --enable-monitor tv,tmds2i

assuming tmds2i is the right display attached in your case

I'm not sure what you mean about the xorg.conf file, but you can supply a different xorg file to the aticonfig command or you can keep a properly configured version of xorg.conf somewhere in your system and just overwrite the original one whenever you need to revert back to the previous configuration

its location is
/etc/X11/xorg.conf

Let me know if you find a better/easier solution!
Good luck!

---

### Post by flamarro on 2008-10-30
Hi guys,
glad to now that theres someone like me messing around with ATI boards on tv out.....
I'm sorry not to not even say that i'm alive, but so little time and so much things to do that i think one day must have 36 hours at least...
I made one thing that for now ( and maybe not )i am thinking was a mistake, that was upgrading to intrepid too soon, and so, i don't even have ATI drivers installed, because i think current version of xorg and fglrx don't work together.... and now, no tv out..... maybe next week theres that possibility, praying that Alberto Milone envying comes out or something :) ... I'm writing this and maybe theres something new that i dont know about... I cant keep the pace of this forum... :lolflag:
One thing is for sure, we are a lot closer....

---

### Post by latev on 2008-10-30
That's weird - you're saying the 8.1 ubuntu broke your fglrx support, I got an email from a guy that said he fixed the suspend issue on his machine by upgrading to 8.1 ubuntu.... I'm confused
I'm going to upgrade my x86 distro here, just so I know I've given it a try. This inability to suspend/resume properly now is taking the fun out of the game

---

### Post by flamarro on 2008-10-30
hi again,
i have upgraded to intrepid and lost the capability of my ATI ( X1300 ) had to use VESA drivers.
Last week decided to do a clean install and even worst, black screen and a empty xorg.conf.... have to create one from a backup and use VESA again.....
Read today more about this and gone try some more things.... when i manage to have fglrx working, back to here again to see what we can do about tv out....

---

### Post by latev on 2008-10-30
I think I'm going to postpone the upgrade just a little bit, looks like the whole world is trying to upgrade now at the same time and the Ubuntu servers are freaking out

Not sure whether you've read the 8.10 release notes but they mention some issues with the fglrx ati drivers:

[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

   ATI "fglrx" video support

   The ATI video driver in 8.10 drops support for video cards with r300    
   based chips (the Radeon 9500 - X600 Series of cards). If you have such a 
   card, please use "Hardware Drivers" at System/Administration to disable 
   it before the upgrade. Please see bug 284408 for more information 


Since our model - X1300 doesn't fall into that category I'm surprised to hear about your issues. Maybe its something else, unrelated to that
Chances are I think this is going to get fixed soon, just have to wait for awhile

Keep in touch

---

### Post by utkjamie on 2008-11-02
It took me a long time to get my ATI Radeon 9000 RV250 card to do TV-out properly. I eventually wrote a bash script to allow me to switch to and from TV-out status. Here's what I came up with:

```
#!/bin/bash
# Jamie's script for switching to TV-out!!

case $1 in
    on) xrandr --addmode S-video 800x600
        xrandr --output LVDS --mode 800x600 
        xrandr --output S-video --mode 800x600
    amixer sset Headphone 75%
        xvattr -a XV_CRTC -v 1
    dcop kdesktop KScreensaverIface enable false
    ;;
    off) xvattr -a XV_CRTC -v 0
         xrandr --output LVDS --mode 1400x1050
         xrandr --auto
     amixer sset Headphone 20%
     dcop kdesktop KScreensaverIface enable true
    ;;
    *) echo "use: svideo on|off"
    ;;
  esac
```

It'll need to be tweaked to match your resolutions (and the kdesktop reference is obviously for Kubuntu). The amixer commands adjust the volume of the audio jack (higher for tv-out, lower so I don't blow my eardrums out when I need it for headphones).

To use: svideo on|off

Unfortunately, the upgrade to 8.10 broke my tv-out functionality. The xrandr commands now lock up my machine and I have to kill the power to reboot.

---

### Post by mamuwyllie on 2008-11-04
Hi I'm a noob only moved to Ubuntu a couple of weeks ago. I installed Ubuntu 8.04 
AMD64 on my 64 bit machine. Everything installed easily with the wireless, graphics card all working as soon I started the machine. My only problem has been switching between my monitor and my tv. When I ran windows xp I had the same problem and had to enable hotkeys on ATI catalyst control centre to switch between the two. I always had to manually reconfigure my monitor and tv resolution but I got used to it. In switching to Ubuntu and reading your remarks it looks like I will need a bit more time learning about Ubuntu to try what your doing on your machines to fix the problem. 
I am able to switch from the monitor to the tv using 
aticonfig --enable-monitor tv
but the problem is that if I want to switch back to my monitor I have to switch off the PC and then unplug the cord to the TV so that Ubuntu resets to the monitor. Since I'm still a noob is there a way I can simply switch back from my TV to my monitor through the terminal. I have tried everything that I could think of through the amdcccle and using the various commands in aticonfig --help with no luck.

---

### Post by utkjamie on 2008-11-05
It's surprising to me that TV-out/S-video is still not a supported part of Ubuntu. I've been using Ubuntu for nearly 2 years now and this has been one of my most frustrating gripes (though I was pacified when I found a way to make it work via script). Given the increasing popularity of streaming video, Internet television, Miro, and downloadable content, I can't understand why more emphasis hasn't been placed on making this work. I understand there are issues with proprietary drivers, etc. but c'mon. I had this stuff working before the upgrade.

---

### Post by mamuwyllie on 2008-11-05
Found it man is my face red. 
To switch to the tv I used
aticonfig --enable-monitor=tv
To switch back to the monitor I had to go through and use
aticonfig --enable-monitor=STRING
where I substituted STRING for either one of these commands
            none
            crt1
            crt2
            lvds
            tv
            tmds1
            tmds2
            auto   
Until the monitor turned on which it did when I substituted STRING for crt2. I'm a noob so thats okay. Love Ubuntu will never ever go back to xp. I would still very much like to know if I could streamline the process by being able to switch monitors through setting up some hotkeys but this method will suffice for now.

---

### Post by utkjamie on 2008-11-05
Thanks for the info! I wish I would have seen that a couple of hours ago. I was told the proprietary ATI (fglrx) driver would do the trick. Rather than taking a risk in doing it manually, I used EnvyNG to install the driver and keep me from screwing things up. Big, huge mistake. Rebooting caused Ubuntu to start in low graphics mode with something like a "no device" error. Rather than taking me into low graphics, though, it took me into no-graphics console mode. I swapped my xorg.conf file for a backup and rebooted. I was able to get back in but without some of the graphical features of KDE4. I used EnvyNG to remove the driver it installed, mistakenly placing my faith in Envy once again. I assumed it would take me back to my pre-Envy configuration but now booting into Ubuntu takes me to a really screwed up screen -- black in some parts, white in others, with the faint outline of things I can't quite make sense of.

I'm now using Windows XP to try to find instructions to get me back up and running properly. I'll give your suggestions a try when I can.

UPDATE...

The aticonfig commands apparently only work with the fglrx driver. I ended up running dpkg-reconfigure -phigh xserver-xorg, which recreated my xorg.conf file. After a reboot, everything was back to normal. Just to be sure I ran apt-get remove --purge xorg-driver-fglrx but the fglrx driver had already been removed. The new xorg.conf file was a bare-minimum configuration and there were some custom settings in my old one that I wanted. So, I went ahead and replaced the newly created xorg.conf file with the old customized one and rebooted. Everything still works fine. But, strangely enough, s-video is now working for me the same way it did before upgrading to Intrepid. Bizarre solution and I wish I knew exactly what did the trick. Maybe dpkg-reconfigure...?

---

### Post by utkjamie on 2008-11-07
Ignore whatever success I claimed in my last update. It's a crap shoot. Sometimes it works, sometimes it doesn't. When it doesn't work, the computer freezes and I have to kill the power. Earlier I switched into TV-out mode, switched back, and then it froze up when I tried to go back to TV-out mode. Another time it went into TV-out mode but then froze up when I tried to switch out of it. After killing the power and rebooting, it booted into TV-out mode and then froze up.

I don't know what to do. I'm surprised a bug like this slipped through beta testing.

UPDATE: The last lock-up from this bug resulted in me rebooting to a list of "clearing orphaned inode" messages. Apparently there was some data loss and/or corruption resulting from the lock-up. Completely unacceptable bug that should have never made it into 8.10.

---

