---
title: "Laptop Battery - power saving tips."
date: 2007-05-02
forum: Hardware &amp; Laptops
---

### Post by ksudbury on 2007-05-02
My laptop battery is not lasting as long in Ubuntu 7.04 as it did in XP on my laptop. in windows i get about 3 / 4 hours or so in Ubuntu it is stating around 2.5 hours. 

Are they any tips for power saving option in Ubuntu e.g CPU scaling, turning down the screen brightness etc?

Many Thanks

---

### Post by shof2k on 2007-05-03
There is power management from SYSTEM-PREFERENCES-POWER MANANGEMENT

Use can install laptop-mode.  This is something that works in the background to help save power.

If you CPU supports it you can install powernow or cpufreq to control your CPU speed.

---

### Post by jjordan on 2007-05-03
There are many factors that contribute to battery like.  The laptop-mode that shof2k mentioned will help, it makes the HD spin up less often.  The big three power suckers on a laptop are the CPU, the screen especially the backlight and the HD.  

CPU frequency scaling is probably the largest gain, we would need to know your laptop and preferred desktop to make specific recommendations.  Turning down the backlight can also be a big saver, once again, need to know you laptop.  There are some other places to save power such as the sound card, wifi card and other integrated peripherals.

Hardware manufactureres work with Msoft and write their own drivers to make these things work well under Windows.  This is an area where Linux still has room for improvement especially in making it easy to set up.  

As manufacturers recognize a market in the Linux/FOSS community they will help, hopefully by providing information so that better open source drivers can be created.

Send the Manufacturer of your laptop an email asking them to support Linux and open source.  If enough people do that they will respond.

-j

---

### Post by ksudbury on 2007-05-06
Sorry guys, I should o provided more info. 

Its a Samsung X05 / centrino with 1gb of ram, I have actually bought a 4000Mah battery for it to improve battery life. 

I know the back light makes alot of difference however... I can't seem to adjust this in Ubuntu 7.04 before I could use fn and the back light key. However if i do this now it crashes the laptop totally crashes X cant even get to a console only option is a hardware reboot. 

I will try the above modules and try cpu scaling. 

Thanks 
Keith

---

### Post by flixer on 2007-05-06
> **shof2k said:**
> 
If you CPU supports it you can install powernow or cpufreq to control your CPU speed.
Powernowd is installed by default...

---

### Post by ksudbury on 2007-05-06
Yeah, I noticed that when I tried to install it... Just added CPU Scaling gnome applet all seems good on that front! 

I presume that after installing laptop-mode and rebooting that should take effect and save me a bit of power?

Thanks

---

### Post by flixer on 2007-05-06
I don't recommend using laptop-mode, because it wears down the hd. It really doesn't save that much power. It's quite useless imho. The best way to save power is to dim the backlight.

---

### Post by ksudbury on 2007-05-07
It wears the HD out !? I can't seem to dim the back light the software in gnome does not allow it and if i try do to use the fn key and the brightness button on the keyboard it crashed it (Samsung X05) I will have to submit a bug as this used to work with previous Ubuntu versions.

---

### Post by flixer on 2007-05-07
Well that was a bit of an overstatement. My point is, in the long-run(few years) it's not good for your HD. And it only gets you about 9 minutes more.

---

### Post by stealth17 on 2007-06-07
How can I make the backlight autodim after a few minutes? One of my buddies has a MacBookPro lappy and I noticed that when you stop using the mouse for a few minutes the backlight dims down and pretty much shuts off. The whole screen doesn't disappear though, you can still see the stuff on the screen but it not very bright.

Seemed like a good idea to me, especially since it returns to full brightness the instant you touch something, no lag what-so-ever.

Now I understand there is probably limited support for backlight dimming via the OS, but obviously you can control some aspects since you can configure it to shut the monitor off after x time.



And to reply to what flixer said about the hard drive wear, I definitely agree. The reason resides in the fact that when a hard drive is spinning up there is much more wear and tear on the motor compared to being in a steady on state. This is a proven fact and also why there is much debate on the topic even at the desktop end. I typically set the drives to always on or to shut off only when inactive for 2+ hours. I will also say that I have had zero complete hard drive failures when using these settings and I have been building computers for around 10 years now.

---

### Post by klato on 2007-06-07
It does that dimming thing on mine automatically...you might need to be using the appropriate video driver (?)

---

### Post by madmetal on 2007-06-07
since you got an Intel cpu you can download and use powertop
[http://www.linuxpowertop.org/](http://www.linuxpowertop.org/)
(at forthcoming gutsy its at repos ;) )

---

### Post by stealth17 on 2007-06-07
> **klato said:**
> It does that dimming thing on mine automatically...you might need to be using the appropriate video driver (?)

heh could be the problem. I have some ATi card in my lappy and I have been using the default driver that comes on install of Dapper.

I'll have to look into the ATi drivers as I have never installed one yet :p

Thanks

---

### Post by 444 on 2007-06-07
On my laptop the brightness is independent of the video driver.

---

