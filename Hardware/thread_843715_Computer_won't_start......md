---
title: "Computer won't start....."
date: 2008-06-28
forum: Hardware
---

### Post by siefer7 on 2008-06-28
Hi,

I installed ubuntu hardy heron about four days ago. Lately my computer would completely freeze and require a hard restart. It would happen if when I let the screensaver come on, then if I let them just power off automatically. Then it would when I would try and stream any video such as youtube. Then when I tried to watch a video, it froze. I restarted. I didnt hear the usual beep like when I restart. Then both my monitors acted as though they went to sleep. Nothing would happen. Just blank screens with the monitor lights blinking. Is it my graphics card? Is this even related to the ubuntu install?

I was going to see if the same thing happened when I was on xp, but that was when things wouldnt respond at all.

My system is custom built. With an EVGA 680i SLI motherboard, EVGA 8800 Ultra, E6850 Core 2 duo, 8 gigs of patriot extreme RAM, Dual samsung 216BW monitors, A 10,000 RPM raptor 150 gig HD for both Operating systems, Windows XP pro 64 and Ubuntu hardy 64 bit. And a 750 Gig....uh, i cant remember the exact model at the moment, I'm pretty sure its western digital. It was my storage drive. I also have an emu 1212m sound card, but I couldnt get the drivers and such to work, so it has just been sitting in there not doing anything, not even installed. Theres also the PSU which is a PC power and cooling Silencer at 750W. Then a DVD/CD burner, and a standard DVD drive.

I have had this set up for just 8 months now. I got just about everything from newegg.com

The motherboards display that looked kind of like a digital clock said A0 on it. Then i restarted again and it just had a double dash - -. 



Sorry for all the info, I just thought id get all I can out since I always see people asking for more specs to get a good idea of things.

I hope this is the right place to post this. I greatly appreciate any help I can get on this. I am pretty worried as school starts in a week. I do a lot of work with 3d in maya, and photoshop....:(

Thanks in advance :)

---

### Post by dinub1 on 2008-06-28
> **siefer7 said:**
> Hi,

*I installed ubuntu hardy heron about four days ago. Lately my computer would completely freeze and require a hard restart. It would happen if when I let the screensaver come on, then if I let them just power off automatically. Then it would when I would try and stream any video such as youtube. Then when I tried to watch a video, it froze. I restarted. I didnt hear the usual beep like when I restart. Then both my monitors acted as though they went to sleep. Nothing would happen. Just blank screens with the monitor lights blinking. Is it my graphics card? Is this even related to the ubuntu install?*

[COLOR="Blue"]It sounds like your video/graphics card does not put any signal out.[/COLOR]

*I was going to see if the same thing happened when I was on xp, but that was when things wouldnt respond at all.*

[COLOR="Blue"]Not good. Do you get any image on your screen while booting? If you do not hear the boot beep OK signal confirmation, perhaps something is wrong with your hardware. But if you get a picture on screen while booting and only when O/S is trying to start, that may be associated with software, driver, etc.[/COLOR]

*My system is custom built. With an EVGA 680i SLI motherboard, EVGA 8800 Ultra, E6850 Core 2 duo, 8 gigs of patriot extreme RAM, Dual samsung 216BW monitors, A 10,000 RPM raptor 150 gig HD for both Operating systems, Windows XP pro 64 and Ubuntu hardy 64 bit. And a 750 Gig....uh, i cant remember the exact model at the moment, I'm pretty sure its western digital. It was my storage drive. I also have an emu 1212m sound card, but I couldnt get the drivers and such to work, so it has just been sitting in there not doing anything, not even installed. Theres also the PSU which is a PC power and cooling Silencer at 750W. Then a DVD/CD burner, and a standard DVD drive.*

[I]I have had this set up for just 8 months now. I got just about everything from newegg.com

The motherboards display that looked kind of like a digital clock said A0 on it. Then i restarted again and it just had a double dash - -. [/I]



[I]Sorry for all the info, I just thought id get all I can out since I always see people asking for more specs to get a good idea of things.

I hope this is the right place to post this. I greatly appreciate any help I can get on this. I am pretty worried as school starts in a week. I do a lot of work with 3d in maya, and photoshop....:([/I]

Thanks in advance :)

[COLOR="Blue"]So apparently system gets locked at boot. That "smells" like a hardware problem. Can be a lots of things and you may need debugging. Did the CPU show any signs of overheating? If you do not hear the boot beep, then that may be an issue. Another issue to check may be faulty power supply. Does your system emit any beeps at boot at all? if it does, you may need to check with mother board manufacturer, what those codes are. If your motherboard is silent and does not boot, well that is not an Ubuntu issue, but hardware.[/COLOR]

---

### Post by Odrodzona-Sarmacja on 2008-06-30
I had problem like that myself. I solved it. You can read more about in:
[http://ubuntuforums.org/showthread.php?t=840686](http://ubuntuforums.org/showthread.php?t=840686)
It is not fault of graphic driver even if it extremely graphic centric problem. These mysterious freezes on latest Ubuntu looks to me more like some DRM (I see DRM as virus) issue.

---

### Post by Odrodzona-Sarmacja on 2008-06-30
To start your Ubuntu you must check following things when booting up with livecd.

"/etc/fstab" for mounting issues (uuid could change! or "sudo blkid" to reference as the device numbering could change too)

"/boot/grub/menu.lst" for booting issues (but you get picture when booting, so I don't think the problem is there)

and also maybe you need to do "sudo chmod 777 <directory>" for privilege issues when having freshly reformated /tmp partition or /home partition.

---

### Post by siefer7 on 2008-07-02
There were no signs of overheating that I know of. I have the big typhoon on my cpu, and arctic silver 5 thermal paste applied. I kept track of the temps, and they never went over 40 degrees. Usually around 32. 

As for the other replies, I can't get past.....anything, nothing happens when I power it on. All the fans spin, but there is not beep. The monitors light instantly starts blinking like when they automatically shut off after not doing anything for a while. I don't even get anything saying there is no signal.

Thanks for all your help.

---

