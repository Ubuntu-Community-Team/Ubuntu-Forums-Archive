---
title: "Keyboard volume control stopped working and other problems"
date: 2019-02-27
forum: Hardware
---

### Post by jians5 on 2019-02-27
I'm novice but not green with Linux. I'm trying to move away from Windows somewhat permanently and I think I'm mostly having a hard time understanding how drivers function in Linux. I've managed to successfully install Ubuntu on my i7 4770k z87 machine and my Baytrail Windows tablet. By successful, I mean I can boot to the GUI. We can ignore the tablet for now but I'll surely be posting about it later. I'm also running an Unraid server on another Xeon machine which is... irrelevant. 


The tablet's problem is simple - its headphone detection is backwards. When headphones are unplugged, the internal speaker is muted and sound is being routed to the 3.5mm jack. When headphones are plugged in, sound only comes from the internal speaker. I posted here about it and was instructed to use pavucontrol (which was not installed by default). In pavucontrol I'm able to set it up such that sound will go where I want it to, but if anything about that configuration changes - if I unplug the headphones - if I restart the machine, etc - I have to go back in and manually tell it to send audio to the headphones, which say (unplugged) in pavucontrol. This is the point at which I expect most reading to realize that I fundamentally do not understand how drivers work in Linux and should be educated on that, perhaps rudely. Onward - we can ignore the tablet for now, I'm sufficiently satisfied leaving it on and plugged in all the time - for now. 

On the z87 - I've installed KDE, proprietary Nvidia drivers for a  RTX2080, and some software. Sound was immediately an issue on both this  machine and the tablet. Linux seems to use the headphone detection in a  strange way. The tablet's backwards, and this machine has 2 line-out jacks - a dedicated L/R line-out, and a dedicated headphone line-out (as well as centre/sub and rear channel outputs I'm not using). When I plugged the headphones in to the headphone port I was able to configure pavucontrol such that I got sound out of them! Horay! Except now the volume control on my keyboard doesn't do anything. Well OK - I guess the driver doesn't let you control volume to that port - ok well my (wireless) headphones have their own volume control I'll use that it's fine. Well, it's the next day now and the sun's still up, I don't need the headphones. So I went back to pavucontrol and switch to my other Line-Out aaaand no audio. Ok - pull my PC out of my desk again, unplug the headphones from the back of it, and now I have sound coming out of my speakers, but only up to about 200hz in frequency. So I open alsamixer, mute everything, unmute everything, and now I have sound except still, no volume control from my keyboard. Restart the PC, same issue - also now the widget for the weather on my panel is blank and all the other system icons that were there like, volume, are gone apart from the clock and Show Desktop.

Imagine my frustration.

I've thought briefly about building my own hardware solution for switching audio, and even went out and purchased a bluetooth device to simplify the audio on the tablet - but I've decided that purchasing stuff to make a free OS work is stupid. So, can anyone tell me what it is that I'm not grasping here because this is probably the 4th or 5th time in my life I've attempted to use Linux and I've never been able to use it for more than a week because of issues like this. Is there, like, a guide to making sound work on things that actually works? Because the multitude that I've found haven't helped. My Unraid server by contrast is rock solid, but that's because it just sits there serving files and doesn't have to actually do anything.

---

### Post by coffeecat on 2019-02-28
Duplicate. Closed.

---

