---
title: "Gateway MT6919 -- Intel GM965"
date: 2008-04-26
forum: Hardware
---

### Post by paultopia on 2008-04-26
Hi everyone, 

It's been about a decade since I used any *nix flavor -- frustration with Vista finally drove me back, so please be gentle.  :-)  

Sooo... I'm having display problems.  I installed 8.04 on my Gateway MT6919 laptop, and the display is very blurry (particularly with text), plus part of the window manager is oddly cut off.  The latter problem has been reported before with this device here --  [http://ubuntuforums.org/showthread.php?t=712303](http://ubuntuforums.org/showthread.php?t=712303) -- but the poster tells me that there's been no resolution.

What I've tried: 
- Looking on the "laptop testing team" page for info -- no dice.
- Switching to xubuntu -- no difference.  
- looking for drivers for the video.  According to Gateway, the video runs on an Intel GM 965 chipset.  According to this thread -- [http://ubuntuforums.org/showthread.php?t=731476](http://ubuntuforums.org/showthread.php?t=731476) -- that chipset has posed problems, but it turns out to work fine on 8.04 with the xserver-xorg-video-intel driver.  

Sooo... I went looking for that driver.  Lo and behold, Synaptic tells me I already have it.  But my display doesn't work right anyway...

Any other bright ideas?

Bearing in mind that while I've used *nix before (years ago), I'm totally new to linux system *administration*, so I don't really know how to install drivers -- it might be that I have the driver noted, but it isn't activated... I'm not sure how to tell, or how to activate it if that's the case.  (Nothing shows up in system --> administration --> hardware drivers, if that matters.)   

Sorry for the newbie question... and thanks.

---

### Post by rdlmitedu on 2008-04-26
I fixed the problem for this user in person, but am posting so if anyone else finds this bug in a search he will know how to fix it himself.

The Intel G965 driver ("intel") has a TVOutput issue -- it appears gnome and/or xorg get confused on autodetection, and gnome uses the TV resolution while x11 uses the correct resolution.

The fix is to add the following to /etc/X11/Xorg.conf and restart X:

Section "Monitor"
    Identifier "TVOutput"
    Option "Disable" "true"
EndSection

and in the "Device" section add the line:
    Option "monitor-TV" "TVOutput"

I confirmed that this is still a problem with 2.2.99 xserver-xorg-video-intel from Debian experimental, too.

I am not sure how this could be fixed at installation time, but I think it should be, as it's a pretty obscure and annoying bug, and this is a common graphics chipset.  I think the number of users who will want to use TVOutput by default is very low, so possibly the Intel driver should default to disabling TVOutput explicitly in xorg.conf.

---

