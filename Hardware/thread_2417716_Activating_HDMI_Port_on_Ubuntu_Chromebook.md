---
title: "Activating HDMI Port on Ubuntu Chromebook"
date: 2019-04-26
forum: Hardware
---

### Post by Ronco Pizatto on 2019-04-26
I activated SeaBios and replaced ChromeOS with Ubuntu 18.04 on my Acer C720-3605. I remapped a few keys and all works great except my HDMI port.

It appears that the port is deactivated and my ChromeOS key to switch to external monitor is now mapped as a regular function key by Ubuntu.

xrandr shows HDMI-1 as disconnected when a computer monitor is plugged in and turned on. I also booted with the external monitor connected and turned on. Same result.

I installed LightDM and switched back and forth from LightDM to GDM3 with no improvement.

Any suggestions on how to remap a key to switch to an external monitor on the HDMI port or any other possible solution?

Acer C720-3605 i3 4Gb 32Gb
Ubuntu 18.04

---

### Post by TheFu on 2019-04-26
I used an Acer C720 for a few years. Don't remember the HDMI port issue at all.  Might want to check pulse-audio and use lxrandr.  The external monitor/TV output should be set to 60Hz and a very, very, standard resolution like 1920x1080 or 1280x720.

There are lots of chromebook webpages about running Ubuntu on the C720. Look for pre-setup keyboard maps.  Most will probably be old - so for 14.04 -- 16.04, since my C720 keyboard died around 2015.

Is it really with an i3?  Mine had a great CPU for the time - Celeron 2850U. 

[http://www.fascinatingcaptain.com/projects/remap-keyboard-keys-for-ubuntu/](http://www.fascinatingcaptain.com/projects/remap-keyboard-keys-for-ubuntu/) is one.
[https://gist.github.com/tdenkinger/98385267783b0c8b0536](https://gist.github.com/tdenkinger/98385267783b0c8b0536)

---

### Post by Ronco Pizatto on 2019-05-01
Thanks to TheFu for a really great link on key mapping.

That helped but I didn't copy the Chromebook keymap table before replacing ChOS with Ubuntu.
I'll need to find the ctl+F4 ChOS key code to switch to an external monitor.

And yes, the C720-3605 does have an i3 CPU. It makes a really great Ubuntu machine.

Thanks for your help.

---

### Post by TheFu on 2019-05-01
I loved my i3-5015u Toshiba chromebook 2015, mostly. It was like an Ultrabook for over 50% less.  But the keyboard on it wore out and having attempted to replace the keyboard on the C720, I'd learned this wasn't a trivial thing. Generally, replacing a chromebook keyboard is $120+.  
About 3 months ago, I got a used Asus laptop, for more than 1/3rd less ($305) than I'd paid for the Toshiba ($430+). The CPU is 4x faster (8th-gen i5), 8G of RAM, and best of all, it has a DELETE key with F11, F12, home/end pgup/dn keys.  I'm seeing over 8 hrs of battery in my normal use. It does weight 3.7 lbs and the Toshiba was less than 3lbs and it has a 15inch screen vs 13inch, but I'm coping. Both were 1080p.  I'd prefer a 13-14inch screen, that is true.

There was a time when converting a chromebook into an Ubuntu laptop was a good choice.  I suppose if you can find a sub-$100 chromebook, it could still make sense, provided you aren't hard on the keyboard .. by ... typing on it.  I don't expect to ever buy a chromebook again.  If I need a chromebook experience, there are chromiumOS based distros available that run on normal hardware and inside virtual machines.

I don't remember anything funky about keyboard mapping on chromebooks. 
Also, I don't remember having any issues with the HDMI output, provided I used a standard resolution and 60Hz.  I'd teach linux on the weekends at a local university and used my 'buntu-running chromebook to drive the projector.

---

### Post by Ronco Pizatto on 2019-05-10
This Ubuntu C720 has quickly become my hardware of choice and probably my favorite of all.

It runs everything great, even my CAD software. I just need to be able to connect to an external computer monitor. I can connect to my TV when I manually switch the TV to the correct HDMI port.

However, none of my computer monitors will connect. Any suggestions? I'm stumped.

---

### Post by Ronco Pizatto on 2019-05-30
The Acer C720-3605 external HDMI port will run my TV but resolution is poor. It will not even recognize my 3 different computer monitors. My guess is a driver quirk.

But I solved my problem by buying a StarTech USB 3.0/DVI External Video Card which is a "black box" unit that plugs into my HDMI port and offers a DVI connection. It also came with a DVI/VGA converter that allows me to go from HDMI to VGA.

I had to download a driver from StarTech. I used the .sh install file and was quickly up and running.

I am obviously limited to USB 3.0 data transfer rate for USB video but I have no video speed problem doing heavy duty CAD work on my external monitor.

Beware. The cheap USB video units are based on different video chips and do not have Linux drivers. Go with StarTech and text chat with them on their web site before you purchase if you need more details.

My problem is solved.

---

