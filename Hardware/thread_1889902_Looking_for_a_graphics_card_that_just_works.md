---
title: "Looking for a graphics card that just works"
date: 2011-12-02
forum: Hardware
---

### Post by darkmaster_101 on 2011-12-02
I'm not sure if this is the right section, if not please tell me how to move it to the correct one.

The graphics card I was using (Asus 8400GS 512MB) has died on me, the place where I got it from can't fix it or get a replacement, so I am getting a refund.

I have up to £50 to spend on a low end graphics card.

I had so many problems setting up the last one (mostly sound and resolution) that I want a card that is easy to set up and does't have any odd issues.

The main use will be for my server/media server/home theatre pc so it needs to be able to watch HD video, at a resolution of no less than  1366 * 768 (for some reason my TV likes this resolution)

All videos will be viewed from XBMC with both picture and audio via the HDMI port

I am currently running Ubuntu Server 10.04 LTS but I can change if newer versions have better support, however it will be a server, so I don't want to move to a full desktop version if I can avoid it.

Hardware wise, is nothing fancy or powerful as it's primarily a home server for me to play about with, but since it is holding all my media, I figured I may as well use it to play it as well.

Intel Pentium Dual Core E6600 (3.06GHz)
ASUS Motherboard (might have to be replaced)
2GB of RAM
2*2TB HDDS

Does anyone have any suggestions of card they are using or have used without issues and minimum setup?

Also I know my hardware setup is probably not ideal for what I'm doing, so if you have any suggestions I'll more than happily take them on-board, but for now I'm mostly interested in getting a video card that fits my needs.

---

### Post by d3anevan on 2011-12-02
hello guys...

nice meeting you guys!

:popcorn:[web developer new york](http://www.dzineit.net)

---

### Post by AlbertP on 2011-12-02
A graphics card that "just works" does not exist. Both nVidia and ATI/AMD require you to install a driver. Intel does not have discrete graphics cards.
However, installing a driver shouldn't be very difficult on Ubuntu.

nVidia often has issues with HDMI audio, and to get resolution working right you need the horrible NVidia X Server Settings program. Perhaps you use the Monitors program instead? That program indeed does not remember the resolution after a reboot, when you use nVidia's official driver.

With ATI/AMD the normal Displays / Monitors program works fine to set the resolution, and Catalyst Control Center can do it as well. HDMI audio also seems to work fine on Radeon HD cards. Many computer shops sell cheap Radeon 5450's.

nVidia's counterpart to this card is GeForce 210. But I'd stay away from nVidia as you didn't manage to get the right resolution with their driver.

---

### Post by gradinaruvasile on 2011-12-02
With proprietary drivers it is recommended to use the proprietary drivers gui to set up stuff.
With Nvidia you have to use their GUI (nvidia-settings) and if you want to remember the settings, launch the utility with sudo , set the display settings and click "Save to X configuration file". This worked for me every time on any computer.

I would say a nvidia gf 210 is enough for what you need.
Or its AMD counterparts - here i would advise the 5/6 series cards because those seem to work really well (also the latest 11.11 AMD Catalyst driver is recommended, it has some stability and compatibility fixes).
To avoid tearing, the catalyst control center has an option - tear free desktop - that applies to video playback too.

HW acceleration wise Nvidias VDPAU is far better than AMD's current Linux UVD2/3 implementation via vaapi though.
But with that CPU of yours even software decoding is ok for 1080p so its a non-issue unless you really dont want to use much CPU (in case of Nvidias VDPAU the CPU usage is as low as 5-10% as opposed to AMD+UVD2/3+libva's 30-40%).
Anyways dont forget to install the vdpau driver (nvidia) or the xvba driver (AMD).
Dont know about HDMI, didndt have the chance to test it on any card, but i heard that there are issues with it on Nvidia at least (especially sound?).

---

### Post by darkmaster_101 on 2011-12-02
Thanks for the response guys, just to clear a few things up

1) I did get the resolution working and sticking after reboot and audio over HDMI, however I do remember having problems with it, and I'd like to avoid that again if possible.

2) I know I'm going to have to install drivers, when I said "Just works" (perhaps that was poor choice of words by me) what I meant was, easy to set up and I'm not going to have to spend hours on the internet googling various problems that I have (such as sound, resolution, tearing etc. )

3) As for the hardware/software decoding, I don't have to much of a problem using software to decode, if I'm watching a video it's probably not doing much else, but if the hardware can do it, then I may as well let it.

As for what card to get, looks like it will probably be a nvidia 210-240, I googled "nvidia gf 210 ubuntu hdmi no audio" and the first thing that came up was the XBMC wiki explaining how to get audio over HDMI for these cards, which at least confirms to me they work with XBMC and my previous card was nvida, which did work after some tweaking rather than going in blind with an ati card.

If anyone has any experience with these cards on Ubuntu good or bad it would be nice to hear about it, otherwise I think I'm done.

Thanks for your help :)

---

### Post by kurt18947 on 2011-12-02
If the card that died was working as you wished, would it be simple to replace it with another 8400GS from a different manufacturer?  I don't know how much difference there would be between different brands using the 8400GS chip set.

---

### Post by darkmaster_101 on 2011-12-02
> **kurt18947 said:**
> If the card that died was working as you wished, would it be simple to replace it with another 8400GS from a different manufacturer?  I don't know how much difference there would be between different brands using the 8400GS chip set.

This is definitely an option, I don't imagine there would be much of a difference if they use the same driver, and it should stop me having to do much (any?) configuration.

I think I assumed that if they ran out of the card I had, they had run out of all versions, but a quick check on the site shows this isn't the case.

---

### Post by wolfen69 on 2011-12-02
> **AlbertP said:**
> resolution working right you need the horrible NVidia X Server Settings program. Perhaps you use the Monitors program instead? That program indeed does not remember the resolution after a reboot, when you use nVidia's official driver.


You need to run it as root and save it to X, that's why it didn't "remember" the resolution. The Nvidia Settings app works just fine, and I've used it for years with no issues.

Personally, I use the nvidia GT430 which is a fairly powerful card that is pretty cheap.

---

### Post by gordintoronto on 2011-12-02
Most of your difficulties are due to using 10.04 Server. Desktop Ubuntu uses a little bit more RAM, but you have lots. And it uses a tiny bit more CPU, but that's not an issue with your system.

If you're running a high-volume web site, Server is just the thing. Otherwise, you're just wasting a lot of time running man this and man that.

I have had no difficulty with my Nvidia 9400GT, which Nvidia has replaced with the very similar GT 210. I fool around with a new version or distro at least once a month.

---

