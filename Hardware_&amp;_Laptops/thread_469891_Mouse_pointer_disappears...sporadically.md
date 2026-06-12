---
title: "Mouse pointer disappears...sporadically"
date: 2007-06-10
forum: Hardware &amp; Laptops
---

### Post by Old *ix Geek on 2007-06-10
(solved it myself)

---

### Post by Old *ix Geek on 2007-06-13
Anyone?

---

### Post by Old *ix Geek on 2007-06-18
bumpety-bumpety-bump!

---

### Post by sadata on 2007-10-26
Old *ix Geek wrote:

> (solved it myself)

Care to share the solution? 

I'm having a similar problem. It seems that the mouse pointer disappears when any display-or-CPU-intensive activity takes place. For instance, it will disappear when a page is loading in Firefox. It will also disappear while waiting for an application to start up. I'm pretty certain that this is not a hardware-related issue because the same thing happens on three entirely different machines that are similarly configured (a Compaq nc6220 laptop, an HP Pavillion 8230ca, and a Dell 2350 desktop).  The only thing in common between these three configurations is Ubuntu 7.10 with Compiz ('normal' enhancement level) with VirtualBox running an XP Pro guest.

Thanks for any help you can provide.

---

### Post by Tokke on 2007-10-26
I'm also interested in a solution for this.  I have the same problem on my HP Pavilion DV5157eu portable.

Thx in advance

---

### Post by kenfeyl on 2007-10-27
Hi guys, I'm having a very similar problem since upgrading to Gutsy yesterday. After going to a locked screen for a while, after restoring the screen sometimes my cursor is gone. It clearly still exists because I can see tooltips as I mouse over various icons, but I can't see the cursor itself. I've tried two things recommended in other threads:

- Putting Option "SHConfig" true in my xorg.conf
- Running update-icon-caches /usr/share/icons

Neither fixed the problem. The only thing that fixes it is a reboot.

I have an AMD64 X2 laptop of the dv6000 model from HP with 2G of RAM. Any ideas on things to try? Thanks,

Ken Feyl

---

### Post by HankB on 2007-10-28
With Dapper, the video screen was totally scrambled coming out of suspend. I could fix it by switching to a text console <ctrl><alt><F1> and then switching back to the X screen <alt><F7>.

Maybe this will provide a work around for you.

-hank

---

### Post by nelcon24 on 2007-11-18
I have figured out a way to predictably make my mouse pointer disappear under ubuntu 7 on my dell latitude.   

Whenever I use the keyboard to change the brightness, By pressing the Fn (function key) and the up or down arrow (brightness up or down). 

This was bugging me for a while and it seemed to happen sporadically at first. But I been using ubuntu the last few days and my mouse pointer has not disappeared unless I change the brightness by using the keyboard.  I have been only using a select group of programs, Firefox, Pigdin, XMMS (with visualizations).  I have visual effects on extra, the highest setting.

It may be that whenever a program, such as a 3d video game, that has brightness settings that alter the current brightness would make the pointer disappear.  I havent had a chance to test that yet.  

I hope this information may be used by some as a sort of workaround as it has for me,  Also I hope maybe this can be used by the community in order to aid in a future patch or fix.

P.S.I searched the internet for at least a week for a fix or workaround, Actually, it was hard to find any info on this bug at all. This thread seems to be the most active, so I registered today for the sole purpose to reply to this thread.  I think it was very surprising to find a thread started by someone like this in the open source community.  Its hard to believe someone interested enough to install an operating system based on the free sharing of information would act this way.  <shrug>

---

### Post by MikeGH on 2007-11-18
Ken Feyl,

I had the exact problem you described.  The following fix worked for me.  In my /etc/X11/xorg.conf file I set HWCursor to "off".  It's a good idea to make a backup copy of your xorg.conf before changing it.  Here is the section I modified:

```
Section "Device"
        Identifier      "nVidia Corporation C51 [GeForce 6150 LE]"
        Driver          "nv"
        BusID           "PCI:0:5:0"
        Option          "backingstore"          "true"
        Option          "HWCursor"              "off"
EndSection

```

(It might not matter, but the left margin indents are actually tabs in the file.  If you use makefiles, then you know why I mention this.)  After that, you can logout and login again.  The pointer should be back.

I found the above fix on the debian forum at:
[http://forums.debian.net/viewtopic.php?t=21201&postdays=0&postorder=asc&start=15](http://forums.debian.net/viewtopic.php?t=21201&postdays=0&postorder=asc&start=15)
under the thread "mouse disappears after logout".  The posting also suggested "CorePointer" "true", but I didn't need that. 

Hope this helps.

-Mike

---

### Post by neoakiraz on 2007-12-04
Anyone still having this problem? This is the only post I found which describes my problem pretty closely...

I'm using Kubuntu Feisty. With Compiz, but this happens both with Compiz on and off. It happens mostly in Firefox. When the PC is just powered up it works fine, but as time passes and mostly when CPU usage becomes higher (multiple tabs in Firefox) the pointer starts sporadically disappearing... it happens only when hovering the Firefox window: when I move the mouse over the desktop the pointer returns and hovering back to Firefox makes it disappear again. (sometimes *maybe* also over other gtk applications, but I'm not sure of this yet).

And sometimes its fixed without rebooting, just as now for example... I've been writing this post (the CPU usage is low again) and the pointer is back steadily over the window.

Any idea? This has been very annoying... Some more info about my setup: using ATI with fglrx driver, but happened also with the open driver. Also I've tried the HWCursor option in xorg.conf with no luck... any other idea?

Thanks!

---

### Post by gerardlouw on 2007-12-16
I have the exact same problem as neoakiraz. Kubuntu Gutsy with Compiz Fusion - in Firefox my mouse cursor disappears when I hover it over certain objects. This happens especially when at least one of my tabs is busy loading. The problum occurs in Opera as well, and very occasionally in Konqueror.

---

### Post by kmfdmk on 2008-01-18
I'm having the exact same issue. This occurs for me when I leave the laptop running overnight or idle for long periods of time. I'm using Ubuntu to recover data from an external hard drive to another good external drive and the copy process is very slow. So I let it run overnight (been going at it for about a week now). When I get up in the morning to continue the process the mouse is gone however keyboard controls still work.

HP DV2000US Laptop
AMD Turion64 1.8Ghz
1GB Ram
120GB HDD
Edimax EW7318USG wifi
Gutsy Gibbon 7.10

---

### Post by kmfdmk on 2008-01-29
*bump* Still having this problm the only thing that fixes it is either completely restarting the computer.  Restarting X (I think that's what it is, it's the Linux CTL+ALT+BKSP) doesn't fix the missing mouse.

---

### Post by neoakiraz on 2008-02-01
I still have the problem... The only thing I haven't tried is reinstalling, But I hate to think that when I reach my actual configuration again the problem will probably come up...

I had an ATI before. Now I changed to a NVIDIA card the problem persists.
Also happens in Opera for me as well.

Did anyone tried reinstalling? Thanks...

---

### Post by tribble222 on 2008-02-14
Have you tried what is described in this post? [http://ubuntuforums.org/showpost.php?p=3664399&postcount=13](http://ubuntuforums.org/showpost.php?p=3664399&postcount=13)

This solved the problem I was having.

---

### Post by neoakiraz on 2008-03-08
For ****'s sake... THANK YOU!

> The problem with animated mouse cursors disappearing (like the loading cursor in Firefox) is described here [beryl-project.org]. Apparently the 'Scale the mouse pointer' and 'Hide original mouse pointer' options of the Enhanced Zoom plugin from Compz Fusion work by changing the size of the cursor to 1x1. After zooming out the static cursors are restored, but the animated are not. This is also why the bug appears so random. It only occurs after the first usage of the zoom function.

The solution is to disable the options mentioned above, and probably use the 'Sync Mouse' option, log out and log back in. The size of the cursor will now always stay the same, but it will also not disappear anymore.

---

### Post by gdonal on 2008-07-03
I had the same problem with the pointer disappearing when adjusting the brightness on a Dell x200 laptop, and this should work for any computers with intel graphics chipsets:

edit /etc/X11/xorg.conf to add:

	Option	"SWCursor"	"true"

in the "Device" section for your video adapter.

---

### Post by mysterious1der on 2008-07-04
gdonal, you are the MAN!  This is the exact fix my Lat X200 needed!

---

