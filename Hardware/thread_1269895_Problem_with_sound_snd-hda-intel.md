---
title: "Problem with sound snd-hda-intel"
date: 2009-09-18
forum: Hardware
---

### Post by bogamol on 2009-09-18
I am using an HP Touchsmart tx2z dual boot 9.04 Ubuntu with Vista. I have been working on this problem for several months. I did the comprehensive sound thread without success. I finally gave up and reinstalled 9.04.

When the system starts, the speaker emits white noise, but I can mute it with the mute shortcut key and turn it back on. As soon as I try to run another sound, for example the test sounds in preferences>sound, it stops making the white noise sound until I run shutdown where it makes the sound until the Ubuntu logo with the status bar is halfway through.

Since I reinstalled 9.04, I don't have Wired internet access so I can't get you the results of aplay or anything right now. The touch screen won't work either, though it did automatically when I installed it the first time.

I will probably have time on a wireless internet connection tomorrow, so I'll try to post whatever output you need for diagnostic, but if anyone has seen this bug before and knows what to do about it with as little rigmarole as possible, that would be appreciated.

I'm so frustrated by this that I am actually thankful that the computer came with Vista; I wouldn't have bought Vista on my own, so I'd be working without options right now...studying with a pen and a pad of paper. :-({|=

---

### Post by mikewhatever on 2009-09-18
I've looked up the model and watched a video review here [http://www.youtube.com/watch?v=AtT3kCoVJqM](http://www.youtube.com/watch?v=AtT3kCoVJqM). Don't know anything about touch screens, but it looked ... odd. That aside, let's try and deal with the sound. I suspect that what emits the noise is the internal speaker. Try running **lsmod | grep pcspkr** command to see if the module is present. If it is, blacklist it by adding **blacklist pcspkr** to the end of /etc/modprobe.d/blacklist.conf. Then reboot to check.

---

### Post by Favux on 2009-09-18
Hi bogamol,

It looks like mikewhatever has a good thought.

I can't tell from your post if you've added the options line to alsa-base.conf described in "7) Sound" here:  [http://ubuntuforums.org/showthread.php?p=7863677#post7863677](http://ubuntuforums.org/showthread.php?p=7863677#post7863677)

Hope this is helpful.

---

### Post by bogamol on 2009-09-19
So I blacklisted the pcspeaker but it's still making the noise. I'm pretty sure that the problem is the speakers mounted underneath the screen.

I should also say that, while I'd like to correct the weird white noise issue, I should point out, since I don't think I did already, that the main problem is that all sounds except the startup and shutdown static won't play. (Everything is unmuted, I checked)

> **Favux said:**
> Hi bogamol,

It looks like mikewhatever has a good thought.

I can't tell from your post if you've added the options line to alsa-base.conf described in "7) Sound" here:  [http://ubuntuforums.org/showthread.php?p=7863677#post7863677](http://ubuntuforums.org/showthread.php?p=7863677#post7863677)

Hope this is helpful.

When I did this, I found that my computer does not have /etc/modprobe.d/alsa-base.conf so I just left it as is. I guess this might be the issue then, right?

Anyway, thank you guys for your quick response on this. The last thing I want is to be stuck using Vista for everything. (I really only like it for Onenote...)

---

### Post by bogamol on 2009-09-19
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) <===This is what I was calling the Comprehensive Sound Problems Guide. Since I found that I did not have the conf files necessary, I reasoned that they weren't installed right and decided to reinstall them so I followed the commands:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

Which worked, 

sudo apt-get install linux-sound-base alsa-base alsa-utils

Which did not work and said that they were outdated. So, now I don't have those packages.

---

### Post by Favux on 2009-09-19
Hi bogamol,

Just to check, you are on Jaunty (9.04), correct?  I ask because your info. under your forum name says Hardy (8.04).  So actually you don't have sound at all, other than some "white" noise?

They renamed alsa-base to alsa-base.conf going from Intrepid to Jaunty.  So it was called alsa-base with Intrepid and earlier.  I know the options line also works with Intrepid (and maybe Hardy?).

Jaunty is 9.04 = released April 2009 and Hardy is 8.04 = released April 2008.

I noticed the sound guide you were following says at the bottom of the post "Last edited by LordRaiden; November 12th, 2006".  So maybe that's part of the problem?

---

### Post by bogamol on 2009-09-19
> **Favux said:**
> Hi bogamol,

Just to check, you are on Jaunty (9.04), correct?  I ask because your info. under your forum name says Hardy (8.04).  So actually you don't have sound at all, other than some "white" noise?

Correct on all counts. I'll update that on my Profile. I am on 9.04, and likely to go to 9.1 when it comes out...(I like to stay on the cutting edge. ;) )

> They renamed alsa-base to alsa-base.conf going from Intrepid to Jaunty.  So it was called alsa-base with Intrepid and earlier.  I know the options line also works with Intrepid (and maybe Hardy?).

Jaunty is 9.04 = released April 2009 and Hardy is 8.04 = released April 2008.

Just to confirm I checked in About Ubuntu. I have 9.04 Jaunty Jackalope. (I think the reason I can't catch it is because it is silent and stealthy, not necessarily fast. :D )

> I noticed the sound guide you were following says at the bottom of the post "Last edited by LordRaiden; November 12th, 2006".  So maybe that's part of the problem?

I noticed that also, but not after I followed in a way that may or may not have been destructive to this exercise... I posted the code I followed that I thought might be detrimental, just in case I deleted something I wasn't supposed to.

---

### Post by bogamol on 2009-09-20
I don't know what the heck I did, but I have sound now.

---

### Post by HammoD on 2009-10-03
[FONT=Arial][SIZE=2]Guys, thank you so much for all the valuable information... Now I have different issue. Sound does not come out of laptop speakers but does with headphones:confused:

i have tried Alsamixer from Konsole to unmute all the channels but didn't work either! Any suggestions

I am using Ubuntu 9.04 - the Jaunty Jackalope on "LG S1 Pro Express Dual" laptop

BTW, now I can see one of the jacks on the right side of the laptop is reflecting a red light!!! I think it is digital output because it has a sign of an arrow like zig zag style.
                
[/SIZE][/FONT]Any Suggestion

---

