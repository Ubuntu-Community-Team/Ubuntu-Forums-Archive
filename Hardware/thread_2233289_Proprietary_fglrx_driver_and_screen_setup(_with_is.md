---
title: "Proprietary fglrx driver and screen setup( with issues)"
date: 2014-07-07
forum: Hardware
---

### Post by Gfurst on 2014-07-07
Hello fellow nerds
I've recently( like last week) built a new desktop PC, with worthy AMD hardware.
I'm using the ATI R7 260X, the system is actually Debian testing( Jessie).
I've used the [smxi scripts]("http://smxi.org/") to install the recent liquorix kernel and proprietary ATI driver, this was actually my first time using it and sort to try it out.
```
guiu@guiu-desktop:~$ uname -r
3.15-3.dmz.1-liquorix-amd64
```

With the smxi script I had the option to choose between the actual latest driver from AMD or the one in the debian repo. I chose the AMD one, which is slightly different, more recent and no man pages.
So, what are the issues I'm having?

I'm using a AOC 23' monitor through the HDMI port, with the open-source drive, it actually worked pretty good, full screen resolution, native composite hardware acceleration.
After the fglrx install, the screen is scaled down and slightly blurred, switching settings in the Catalyst config doesn't affect anything.
Researching this I've found some pretty similar issues, some option about underscan, [here]("http://www.linuxquestions.org/questions/linux-newbie-8/fglrx-display-is-offset-and-obscured-by-black-border-4175438797/") and [here]("http://ubuntuforums.org/showthread.php?t=960904&page=2").
This setting didn't seem to affect me, either way the file in question seems to be updated as [this user]("http://askubuntu.com/questions/219044/ati-proprietary-driver-over-underscan-setting-ignored-after-reboot") found out.
Searching for a more stable and safe answer I started looking at the aticonfig app, which has a great number of available settings. I don't have a man page on this, since it was installed from AMD directly.
Found this setting  which has sort of fixed it, but not in a permanent way yet:
```
guiu@guiu-desktop:~$ aticonfig --query-dispattrib=dfp5
Query monitors dfp5 ,Cap:0x1ff
Supported adjustment type for dfp5 : brightness, contrast, saturation, hue, positionX, positionY, sizeX, sizeY, overscan 

 brightness attribute information of monitor dfp5 :
 default:0, value:0, min:-100, max:100, step:1

 contrast attribute information of monitor dfp5 :
 default:100, value:100, min:0, max:200, step:1

 saturation attribute information of monitor dfp5 :
 default:100, value:100, min:0, max:200, step:1

 hue attribute information of monitor dfp5 :
 default:0, value:0, min:-30, max:30, step:1

 positionX attribute information of monitor dfp5 :
 default:76, value:0, min:0, max:1920, step:1

 positionY attribute information of monitor dfp5 :
 default:43, value:0, min:0, max:1080, step:1

 sizeX attribute information of monitor dfp5 :
 default:1767, value:1920, min:960, max:1920, step:1

 sizeY attribute information of monitor dfp5 :
 default:994, value:1080, min:540, max:1080, step:1
```
note that --query-dispattrib (query display attributes), has a corresponding --set-dispattrib, which then I was able to set correct position and size.
Note the default values, position slightly offset and size slightly smaller. So I figured out the source of the issue, but still haven't figured out how to make this permanent. 
Right now I have no time to dig in more into the aticonfig setting but I'd suspect I can make that permanent by writing it to a xorg.file
Still anyone with experience on this is welcome.


Besides this I would like to know if anyone had any luck trying to get backlight brightness control through software on the AMD driver, Nvidia had a xorg option that could work( used it on a iMac).
This AOC 23' modern monitor, apparently has this capability, reported DDC2B/CI capable. There even is a bundled software to control the screen on Windows®.
Besides that, I'm just hoping the driver has good efficiency controlling the ATI card, allowing for awesome games. :) (though I am worried wtih steam, since it required the i386 respective drivers, this may conflict)

Thanks folks, I know its a lot of stuff, but any help on setting up configuration for this driver is very welcome.

Additional reference for safe keeping:
[http://man.cx/aticonfig%281%29](http://man.cx/aticonfig%281%29)
[http://www.blackmoreops.com/2013/10/12/helpful-aticonfig-fglrx-commands/](http://www.blackmoreops.com/2013/10/12/helpful-aticonfig-fglrx-commands/)

---

