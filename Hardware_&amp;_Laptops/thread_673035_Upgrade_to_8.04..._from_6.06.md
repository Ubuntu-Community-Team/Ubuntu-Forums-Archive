---
title: "Upgrade to 8.04... from 6.06"
date: 2008-01-20
forum: Hardware &amp; Laptops
---

### Post by Papa-san on 2008-01-20
I am a Linux idiot. 

I have been flailing around in Ubuntu since I discovered 5.10 and used it to overwrite windows XP on my old laptop.

My question here is this:
Are any older systems going to be considered in the new LTS release? I am running 6.06. I tried to upgrade to the newer ones, but my wireless and video couldn't be made to work right by me or the dozens of others who helped me with trying. There was a kernal release for 6.06 a week ago that fried my wireless, so I am running the old one. 

My box is an old veteran. (Dell Latitude C610) Worked OK with win XP, but doesn't meet specs for Vista. (As if I'd be fool enough to buy into their 'lease' in the first place... Yeah, I won't ever go back) I know for myself, I don't have the money to purchase a newer system. I also know that this is the case for millions of others. 

Are the drivers going to be included in the next release, or should i put them on a disc for installation into ndiswrapper? (bcm38xx) I know that someone tried for the edgy release, but it didn't work. I haven't had the courage to try since then. I know 6.06 works with the tweaking I know how to do. (After I figured out how to blacklist the included ones. lol)

I'm just curious, as I know many wonderful people are working on this, and would like to know what I can expect.

Thanks!

---

### Post by Yellow Pasque on 2008-01-20
What drivers are you referring to? Please run the following to give us an idea of what hardware you have:
```
sudo update-pciids
sudo lspci
```

---

### Post by Papa-san on 2008-01-20
The drivers are bcmwl5.inf and bcmwl5.sys
The hardware is :```
john@john-laptop:~$ sudo lspci
0000:00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
0000:00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 04)
0000:00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
0000:00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
0000:00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
0000:02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
0000:02:01.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
0000:02:01.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
0000:02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
john@john-laptop:~$
```
I just know that this generation of Dells has been a source of many threads in regards to wireless issues and hard lock-ups from video driver and setting issues. I still don't have my video working right in 3D, but it doesn't lock the system anymore. If I can get back to this, at least, I'll upgrade when the time is right.

---

### Post by Sef on 2008-01-20
> Upgrade to 8.04... from 6.06

It's been rumored that you will be able to upgrade straight from 6.06 to 8.04.   I have not seen anything to support or deny this yet.

---

### Post by Papa-san on 2008-01-20
Yes, that's what I heard that got me wondering. I just know that there were some insurmountable (for me) issues in the intermediate releases. I can't even tell you how nice it would be to have it be a seamless transition!

---

### Post by AndyC_772 on 2008-01-20
I have very similar hardware in my Inspiron 8200, and given the trouble I know some people have had getting Ubuntu to work on their systems, I think I've got off lightly!

I use ndiswrapper to run the bcmwl5 drivers and - though I've no doubt it's tempting fate to say so - it's been reliable. With an earlier Ubuntu release (I forget which one) I had to compile ndiswrapper from source to get the latest version, and thereafter my wireless connection broke every time there was a kernel update. But I'm running Gutsy now with the ndiswrapper version that's in the repositories and haven't had any problems. (That said, I'm not entirely sure whether there's been a kernel update since I installed Gutsy either!).

I keep a known working copy of bcmwl5.inf and bcmwl5.sys safe on my network fileserver, ready for when I do have to set up wireless again. Of course, it helps if you have a wired connection and/or another PC available!.

Also note: Some versions of bcmwl5 offer better performance than others, and I found that updating the firmware in my WAP helped a lot in that respect too. I've also managed to confuse my WAP sometimes during wireless setup, with the result that nothing connects properly. A reboot fixes that, but it can be very frustrating to find you have a configuration which should be working but which stubbornly refuses to connect. Another PC helps here too.

I tend to listen to music, streamed from the fileserver over the wireless LAN to my Squeezebox while setting up a wireless PC - then if the music stops I know it's time for a reboot :)

---

