---
title: "Can't play games on HDTV in Ubuntu Oneiric"
date: 2012-03-09
forum: Hardware
---

### Post by Wheel on 2012-03-09
Hi,

Using desktop pc.  Nvidia GT 530 card.

I Have been enjoying playing Neverputt and SDL-Ball on my VGA connected monitor.
VGA monitor's max resolution is 1600 x 900 which generates an excellent picture even with a VGA connector.

I have recently disconnected the monitor and connected to my HDTV via HDMI.
HDTV's max resolution is 1280 x 768.

Everything else works great, including playing video.

But my games won't launch.  I have them on my Unity launcher and when  clicked to launch them, the icon pulses as they do when a program is  launched, but then nothing else happens.

I've tried launching Neverputt via Terminal.  I get an error:
  "No video mode large enough for 1600 x 900"
Launching SDL-Ball gives the same error and also says: 
  "Segmentation fault".

I don't know what a segmentation fault is, so I don't know how to begin fixing this.

I  tried re-setting the HDTV's resolution to each of the other offered  settings, but since they are all lesser numbers than 1280 x 768, I get  the same error.

I'm thinking that these games somehow configured  themselves during install to work on the 1600 x 900 monitor and so can't  "squeeze" into the lower resolution on the HDTV.
So I tried installing a 3rd, similar game (Neverball) while in HDTV mode.  
Same problem; same terminal error.

I have tried logging in using all available flavors of Gnome, Gnome  Classic, Unity 2d, etc.   I get the same results with each of them.

I have also tried installing the only other offered driver for my Nvidia  card ( I have been using the "recommended" version).  This also changed  nothing.

Will these games play on HD?

Does anyone have an idea what types of settings I should be looking at to fix this?

---

### Post by Jan D on 2012-03-09
Do you use original nVidia drivers? In that case, have you configured your HDTV in the nvida settings panel?

---

### Post by papibe on 2012-03-09
> **Wheel said:**
> I'm thinking that these games somehow configured  themselves during install to work on the 1600 x 900 monitor and so can't  "squeeze" into the lower resolution on the HDTV.
It seems that way. Like they somehow hardcoded the previous resolution on a config file.

Have you tried connecting back your monitor, and try to reduce the resolution of the game there?  That way when you open the game on the HDTV, the game has been set already to play on a lower resolution.

Just some thoughts,
Regards.

---

### Post by Wheel on 2012-03-10
> **Jan D said:**
> Do you use original nVidia drivers? In that case,  have you configured your HDTV in the nvida settings panel?

Thanks for the reply.

I'm using the driver which Ubuntu installed by default:   
Nvidia  Accelerated Graphics Driver (Version current) [Recommended].
In Additional Drivers, only one other was offered, so I gave it a try with no improvement.  
I have switched back to the first one.

I tinkered with some of the settings in the Nvidia Settings Panel, but it seems to be properly configured.

I did not go to Nvidia.com to find a driver (as I did on Windows).  I  figured it was safer to let Ubuntu show me what I could use since this  is my first experience using a proprietary driver on Ubuntu.

Do you think it would be worthwhile to try and install Nvidia's own  driver?  If so, is there anything I need to pay attention to so that it  gets configured properly?

> Have you tried connecting back your monitor, and try to reduce  the  resolution of the game there?  That way when you open the game on  the  HDTV, the game has been set already to play on a lower  resolution.Thanks, Papibe.  
I did have some luck trying this.  I'm halfway fixed.

I dug through all the folders inside my home folder and I found (in  ~/.config) a settings file for SDL-Ball, which I edited to use 1280 X  768 instead of 1600 x 900.

This worked!  The game now plays on either monitor or HDTV.  Very nice!

Unfortunately, I found no such folder or file for Neverputt  (There was  one for Neverball, so I could adjust the resolution on that one the same  way, but I'm not actively playing Neverball.)

Neverputt and Neverball are from the same developer and in the Software  Center I followed a link to that developer's site where I found a forum  for those games.  

I'll go back there and ask the question if I hit a wall here on the  Ubuntu forums (although there doesn't seem to be too much action on  their boards).

...Just before posting this I discovered a settings area inside of SDL-Ball--with the game opened--where it looks like the same resolution changes could be made (I suppose that's what you were actually talking about in your post).

So I'm posting this as is, then powering down, re-connecting the monitor, opening Neverputt and looking for that settings area.

If I have any luck repairing this way, I'll be back in a few minutes to re-post.

---

### Post by Wheel on 2012-03-10
I'm back....

I was able to adjust the resolution settings from inside of Neverputt with the game open on the monitor.

It now plays on either monitor.

Problem solved!  Thanks for your suggestions.


[U]...However, I may have caused a secondary problem.
[/U]

Since I've been tinkering with resolution settings, I'm now seeing an error message on the HDTV (ONLY  seen on the TV, not on the monitor) when I get to my Ubuntu desktop:

"Could not apply the stored configuration for monitors."  
And it shows a long list of all of the available resolutions for my TV, as well as refresh rates.  This window will simply click away (actually, the Escape key removes it from the screen) as this "untitled window" has no window control buttons on it).  Everything appears to run normally in spite of this.

I have no idea what sort of problems this may cause--if it causes any.  I simply don't know.

I'll keep my eye on this, but does anyone know how to avoid having this error display every time I boot?
OR--how to properly repair my settings to prevent this in the first place?

---

### Post by Wheel on 2012-03-11
After some more tinkering with settings, I've managed to get rid of the error message and still have everything working as desired.

Problem solved.

---

