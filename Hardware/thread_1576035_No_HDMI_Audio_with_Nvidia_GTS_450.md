---
title: "No HDMI Audio with Nvidia GTS 450"
date: 2010-09-16
forum: Hardware
---

### Post by soft_kitten on 2010-09-16
I have a small issue with my Nvidia GTS 450 using Ubuntu 10.04 x86. When I use the mini-hdmi port in my Nvidia graphics card, the video is clear and good, but I do not get hdmi audio, nor can I find any way to enable hdmi audio in the sound settings. All I see is the motherboard audio line-out, which works fine. I am using proprietary nvidia drivers installed via the Ubuntu hardware manager.

When I used an ati 5770 I could select hdmi audio in the sound settings, but that option is not available now.

I get hdmi audio through the video card when using windows 7 and nvidia drivers. But I use Ubuntu for everything other than games so I would eventually like to solve this problem.

I understand that it I can't expect support for issues with proprietary drivers, especially on a video card that was released to the public monday this week. I suspect that the problem is the newness of the video card, and the linux drivers are not fully fleshed out. All I *[COLOR=black]need[/COLOR]*[COLOR=black] to know is if any other gts 450 users have a similar problem. If they don't have the same problem then I know that there is something wrong with my setup, and not the drivers.[/COLOR]

Thank you for your help. :)

---

### Post by BobVila on 2010-09-16
> **soft_kitten said:**
> I have a small issue with my Nvidia GTS 450 using Ubuntu 10.04 x86. When I use the mini-hdmi port in my Nvidia graphics card, the video is clear and good, but I do not get hdmi audio, nor can I find any way to enable hdmi audio in the sound settings. All I see is the motherboard audio line-out, which works fine. I am using proprietary nvidia drivers installed via the Ubuntu hardware manager.

When I used an ati 5770 I could select hdmi audio in the sound settings, but that option is not available now.

I get hdmi audio through the video card when using windows 7 and nvidia drivers. But I use Ubuntu for everything other than games so I would eventually like to solve this problem.

I understand that it I can't expect support for issues with proprietary drivers, especially on a video card that was released to the public monday this week. I suspect that the problem is the newness of the video card, and the linux drivers are not fully fleshed out. All I *[COLOR=black]need[/COLOR]*[COLOR=black] to know is if any other gts 450 users have a similar problem. If they don't have the same problem then I know that there is something wrong with my setup, and not the drivers.[/COLOR]

Thank you for your help. :)

Shot out of left field here - someone more enlightened will correct me if i'm off base, i'm sure. Have you run the audio cable from the motherboard/sound card into your graphics card? I recently wanted to do hdmi audio and went with a 5770 because it didn't require any such connection, but think I read that the nvidias need a cable from the mobo or sound card to run audio over hdmi.

---

### Post by soft_kitten on 2010-09-16
I never saw an audio line in or spdif anywhere on the video card, and with the same hardware configuration I get hdmi sound in windoze. Looking through the internet, it appears that the gts 450 does not require a spdif or line in cable for audio. But I am currently away from home so I'll take another look at it when I get back.

Yes, the 5770 is quite nice, and I liked it while it worked. but I think I bricked it after installing an aftermarket cooler :oops:

---

### Post by soft_kitten on 2010-09-17
I uninstalled the hardware manager drivers and updated to the latest nvidia drivers 260.19.06, but the problem is still there. The screenshots show no hdmi audo entry, only the motherboard entries.

---

### Post by lidex on 2010-09-17
You'll need alsa v.1.0.23 
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by soft_kitten on 2010-09-18
[http://www.alsa-project.org/db/?f=099c486f436b7959557fc2da0b646c02d095dad6](http://www.alsa-project.org/db/?f=099c486f436b7959557fc2da0b646c02d095dad6)
I was never prompted for any password, just "Automatically upload ALSA information to [www.alsa-project.org?]("http://www.alsa-project.org?") [y/N]"

An update to the situation- I have tried to follow the instructions at [http://www.nvnews.net/vbulletin/showpost.php?p=2312420&postcount=7](http://www.nvnews.net/vbulletin/showpost.php?p=2312420&postcount=7) .

It references [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules) ; I followed its instructions and can now see an nvidia entry in the hardware tab of sound preferences. But I still don't get sound. That is probably because I couldn't follow step c in the nvnews post. Apparently that steps involves git, and I am too much of a newbie to know how to use it. After installing git-core and gitk via Synaptic, I was confused.

---

### Post by lidex on 2010-09-18
[http://ubuntuforums.org/showthread.php?t=1552250](http://ubuntuforums.org/showthread.php?t=1552250)
[http://ubuntuforums.org/showthread.php?t=1542401](http://ubuntuforums.org/showthread.php?t=1542401)

---

### Post by goltoof on 2010-09-29
I got the same card, but I'm not having audio problems, my problem is the card is just flat out not working.  Normally there will at least be a splash screen or boot screen when you start up.  I'm not finding the proper drivers (still using my old card).

Any tips on what drivers you used to get it up and running would be great.

---

### Post by soft_kitten on 2010-10-01
lidex, I was able to find the nvidia card in alsamixer and unmute them, but I still don't get any sound. I'll look through those threads again for anything else I can do.

A razor1394 on the nvnews forums got his sound to work by using the Maverick mainline 2.6.36-rc5 kernel.

Goltoof, I can try to help you and I know of two main ways you can go about this. Have you tried to grab the proprietary Nvidia drivers via System>Administration>Hardware Drivers? You can hobble you way there even if you run ubuntu in low-graphics mode with screwed up colors. If that doesn't work you can try installing the linux drivers in the nvidia site. But I'm having a problem there-I can't find 32bit gts 450 linux drivers-it says there are no drivers available? Phooey. This way is the way I did it and my memory is a little fuzzy. But the thing is you need to have the drivers downloaded first. I downloaded linux drivers for the gts 450 a few days after launch and now they disappeared??

---

### Post by ICANSEEYOU7687 on 2010-10-04
Did you ever solve this?

I am trying to buy a new nvidia card (integrated ati card tears and cant fix it) but I hear a lot of people have trouble getting audio to work through HDMI and my only screen is my 40 inch samsung... (media server)

I was looking at the fermi but I thought u had to use the beta drivers or something.  Im trying to look into cards to get but I just dont know.  I hear a lot of the nvidia cards have problems with audio and HDMI...

while ati has display issues, haha.

thanks!

---

### Post by soft_kitten on 2010-10-11
An update:

Still no joy. 


My current configuration:
x86 Maverick 10.10 with 2.6.35-22-generic kernel

Nvidia Driver Version 260.19.06 (I think this driver version is a beta and for some reason I can't find any driver updates on the nvidia website for gts 450 linux 32 bit)

linux-alsa-driver-modules-2.6.35-22-generic and linux-headers-alsa-driver-2.6.35-22-generic from [https://launchpad.net/~ubuntu-audio-dev/+archive/ppa](https://launchpad.net/~ubuntu-audio-dev/+archive/ppa)
These packages allowed me to see and select the sound output to be Nvidia HDA and unumute the 4 nvidia channels in alsamixer; however, I still get no HDMI audio.

icanseeyou do you get those problems when selecting any visual effect setting besides none? if you choose no visual effects do you still get those? if you only get those problems when enabling any visual effects, you might want to try googling "no backfill". I had to use that when I had an ati 5770. Its like some kind of patch for x? I'm not sure what i'm talking about, but it helped me.

---

### Post by Maletor on 2010-10-12
Try upgrading to 2.6.36 kernel.
Some people on LaunchPad had success with that on rc6. I tried rc7 and had no luck when outputting directly to the TV.

---

