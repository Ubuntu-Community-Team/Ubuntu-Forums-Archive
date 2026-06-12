---
title: "Double monitors problem"
date: 2017-07-25
forum: Hardware
---

### Post by nigro.orlando on 2017-07-25
Hi! 
I have a projector (hdmi through a display port adapter) connected as a second display and it is correctly detected by Ubuntu together with the first monitor (hdmi) by my graphic card.

The monitor is my main display and I use the projector only occasionally. 

I made the displays mirrored and turned the projector off. When I then restarted the computer I couldn't log in because the screen where I type my password was reflected only on the projector and not on the ordinary monitor. I had to turn the projector on in order to see the log on screen.

How do I solve this issue? I tried to make the monitor primary and the projector secondary but I still get the projector as the display where I see the docky and the dash. 

In the display menu of the settings the projector is counted as 1 and the monitor as 2. Could this be the reason? How do I change that?

Edit: Actually this happens always at boot in any case. If I  want to boot into the bios I only see it on the projector. Is only after booting in Ubuntu (or windows) that the displays are actually mirrored.

---

### Post by vocx on 2017-07-25
> **nigro.orlando said:**
> Hi! 
I have a projector (hdmi through a display port adapter) connected as a second display and it is correctly detected by Ubuntu together with the first monitor (hdmi) by my graphic card.

The monitor is my main display and I use the projector only occasionally. 

I made the displays mirrored and turned the projector off. When I then restarted the computer I couldn't log in because the screen where I type my password was reflected only on the projector and not on the ordinary monitor. I had to turn the projector on in order to see the log on screen.

How do I solve this issue? I tried to make the monitor primary and the projector secondary but I still get the projector as the display where I see the docky and the dash. 

In the display menu of the settings the projector is counted as 1 and the monitor as 2. Could this be the reason? How do I change that?
I can't say I know how to solve your problem. My computer does not show numbers 1 or 2, it just says builtin display, and the name of the second monitor. It just works. I am using a laptop, so there's also the key combination «Fn»+«F7» to switch the monitor output. If the screen is not shared correctly with a projector, I hit that combination to switch among the options mirrored, extended, or only one screen on.

My advice for the moment is to boot the computer with the second monitor not plugged in. After the login screen you should plug it back. Also, another suggestion. Do not turn off your computer, just suspend it. In this case, the system may have already detected the screens correctly, and maybe you won't see this issue.

---

### Post by 1clue on 2017-07-25
This sounds weird, but try switching the connectors on your video card. I fought this a couple years ago, and this was the only way I could do it.

I think that the dual-head video cards have a port 1 and port 2, and if something's in port 2 then they automatically assume something's in port 1.

---

### Post by nigro.orlando on 2017-07-26
Thank you for your help. 
@Vocx yes, it works if I unplug the projector, but I would prefer to keep both plugged so that I don't have to crumble under the desk (is a stationary pc) when I want to see a movie :). 

@1clue I did as you suggested and switched the displays. I put the monitor in the display port adapter and the projector's hdmi directly in the GPU.

Now the monitor is 1 and the projector 2 and I see the boot screen on the monitor instead of the projector. It was that simple :) . 
I didn't think about it because I wanted the monitor to go directly in the GPU with the HDMI and the projector to use the display port adapter. I guess it can't be done. Does it matter?

---

### Post by vocx on 2017-07-26
> **nigro.orlando said:**
> Thank you for your help. 
@Vocx yes, it works if I unplug the projector, but I would prefer to keep both plugged so that I don't have to crumble under the desk (is a stationary pc) when I want to see a movie :). 

Of course, I get that!

> 
@1clue I did as you suggested and switched the displays. I put the monitor in the display port adapter and the projector's hdmi directly in the GPU.

Now the monitor is 1 and the projector 2 and I see the boot screen on the monitor instead of the projector. It was that simple :) . 
I didn't think about it because I wanted the monitor to go directly in the GPU with the HDMI and the projector to use the display port adapter. I guess it can't be done. Does it matter?
It does not matter. Are you using a graphics card with two outputs HDMI and DisplayPort, or are you using one graphic card for one output, and the integrated video card of your motherboard for the other output?

The way you say, "connected directly to the GPU" is confusing. If you are using a discrete graphics card, it is using a single GPU. Both the HDMI and DP outputs are connected to the GPU. What I would do is stop using a DP-HDMI adapter, and just use a DP-HDMI cable. There are cables out there with these terminals. Basically, the fewer moving parts (adapters), the better.

---

