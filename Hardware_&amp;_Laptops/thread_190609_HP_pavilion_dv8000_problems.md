---
title: "HP pavilion dv8000 problems"
date: 2006-06-06
forum: Hardware &amp; Laptops
---

### Post by mochaspro on 2006-06-06
**_About 3D acceleration:_**

- I tried to install the fglrx drivers in the repositories
- I tried to install the ATI driver from the page (the 34.6 MB file) and i did it in 2 ways... creating the deb files and then installing them with dpkg and just running it and installing.
- I tried to download a file i saw somewhere (a rpm) fglrx_6_8.... and i used alien and then tried to install the .deb 

With all of that I modify the xorg.conf with a lots of things, adding some Options in the Device Section like:

- Option "VideoOverlay" "on"
- Option "OpenGLOverlay" "off"
- Option "UseInternalAGPGART" "no"

i added this modules too:

- modprobe agpgart
- modprobe -r fglrx 

and if you are thinking this: yes, i installed headers and restricted modules for my kernel

so as you can notice i'll be doing a lot of things without success... 

Sometimes i got this error too: when the X (gdm) is starting i can see the desktop BEFORE i can log in, then the login screen appears, after that i can see everything real slowly and if i write fglrxinfo i see like all it's good, nothing about mesa, but a few minutes after my computer freeze... if this is not happening i see the MESA stuff with fglrxinfo....

And yes, i changed the UMA thing in the bios, i have 256 ram in video, 128 by the card and 128 by the ram...

**_About the Wireless:_**

I tried 3 things:

- Using different kinds of win drivers with ndiswrapper: the winXP 64 bits, the WinXP 32 bits
- Using the bcm43xx-fwcutter
- Using a script that comes in the repositories (it download, extract and install a driver) but no success.

Now the led in the computer turns on and off if i do sudo ifconfig eth1 up/down and SOMETIMES i can sudo iwlist eth1 scan and see available ESSIDS, but never ever i can get an IP with dhclient or whatever :S

I hope you can help me with this guys because i love linux and i dont want to use Windows or that in my machine :)

Thank you

---

### Post by Dromio on 2006-06-08
I'm having the same two problems with mine as well.  

I *think* I've got the wireless working by grabbing my driver from the windows partition and using fwcutter.  But I'm at work right now, I'll have to try it when I get back home.

I can't get fglrx to work no matter what -- it hard locks the system.  If you get it working, I really want to know how.

---

### Post by rjstevens3 on 2006-06-08
I read elsewhere that you have to enter the bios and change the video card settings to use some of the shared memory. My hp dv8000 default setting was to just use the 128mb of video ram.

---

### Post by Dromio on 2006-06-09
[quote=rjstevens3]I read elsewhere that you have to enter the bios and change the video card settings to use some of the shared memory. My hp dv8000 default setting was to just use the 128mb of video ram.[/quote]

Yes, I read that as well.  Unfortunately, it doesn't seem to solve the issue for me.

---

### Post by hedge on 2006-06-23
Regarding the wifi issue I have a HP ZD 7168cl with the same wifi card. Previously in Breezy I had to use the ndiswrapper, and the only one that worked was the Win2K driver using the bcmwl5.inf. Don't try the bcmwl5a.inf cause it won't work. In Dapper however it was detected and set up correctly from the get go. But was not named wlan0 but eth1. So, I just activated it in the networking admin added ssid and key and it connected..:) How cool is that!

Sorry but can't help with the video nvidia here on this laptop...

l8r

hedge

---

### Post by kcallis on 2006-06-25
[QUOTE=hedge]Regarding the wifi issue I have a HP ZD 7168cl with the same wifi card. Previously in Breezy I had to use the ndiswrapper, and the only one that worked was the Win2K driver using the bcmwl5.inf. Don't try the bcmwl5a.inf cause it won't work. In Dapper however it was detected and set up correctly from the get go. But was not named wlan0 but eth1. So, I just activated it in the networking admin added ssid and key and it connected..:) How cool is that!

Sorry but can't help with the video nvidia here on this laptop...

l8r

hedge[/QUOTE]
I just pulled down the latest version of Ubuntu 6.06 and athough iwconfig can see the interface, if I try to do a ifconfig eth1 up, I get no response from the interface... So what did you do to get it immediately going that I missed...

---

### Post by Rob_H on 2006-10-27
I thought I'd revive this thread now that Edgy is out.

I gave up on the integrated Broadcom wifi adapter long ago. Could never get it to work right, so I bought an Atheros-based PC Card and it works perfectly. I wish I could just as easily replace the Radeon Xpress 200M video adapter. The only way I could get it to work with 3D acceleration in Dapper was to enable UMA in the BIOS and use version 8.24.8 of the proprietary ATI driver. No newer version would work including the latest one (8.29.something).

Well, I just upgraded to Edgy and the trusty 8.24.8 driver took a nose-dive. Compiling the kernel mod failed, and based on forum postings, I don't think it supports the new X11 either. I've tried both the "ati" driver and the "fglrx" drivers bundled with Edgy, but 3D acceleration won't work under either one. (If I use the "fglrx" driver, X won't even start unless I set the "NoDRI" option. Nothing but a black screen.)

So has anyone gotten 3D acceleration to work on a Pavilion dv8000 with Edgy? If so, how'd you do it? Thanks!

---

### Post by bryhawks on 2006-10-30
As far as the Video goes the 8.24 one seems to be the last one to work, it's a bummer really because the machine is so nice and the driver sucks! For the wireless NIC I uesd the package bcm4318.networkmanager.tar.gz and my wireless works flawlessly... here is a link that you can scroll down and grab it from [http://www.ubuntuforums.org/showthread.php?t=197102&highlight=broadcom](http://www.ubuntuforums.org/showthread.php?t=197102&highlight=broadcom) 

If anyone has had any luck with the new ati drivers please post and let us know!

---

### Post by Rob_H on 2006-10-31
My only suggestion at this point is to make some noise at ATI. Report it as a regression bug through their support channel. I've already done this and was dismissed with: "We don't provide support for the Linux driver." But if more people complain, maybe someone there will pay attention.

---

### Post by quiquoqua on 2006-12-04
i'm getting stuck too with ati x200m... and i'm still trying to work it out
i have a dv8000 (p/n: et001ea#abz) (bought in Italy)
but maybe i resolved the wireless issue
this is what i did:
(i resolved without ndiswrapper - this means i didn't install it and used the  bcm43xx service that edgy has included as default)
(IMPORTANT: i'm just a newbie in linux, so i can't give you more precise instructions, but the basic is that you follow the bcm43xx method and obtain the firmware from the ndiswrapper site)

1) install ubuntu edgy eft amd64
2) download bcm43xx-fwcutter (you can easily find it in synaptic package manager)
3) found a compatible firmware for my card (maybe is the same as yours - lspci shows it as a Dell 1470 Dual-Band wireless cards, but i downloaded a driver from the ndiswrapper list site that refers to "Laptop:a DV8050  [HP] Pavilion 8050AE" -REMEMBER: I DIDN'T INSTALL ndiswrapper, just surfed their site!)
3.1) so.. look at your lspci and look in ndiswrapper site for a compatible driver, download all the drivers you want and try to bcm43xx-fwcutter them
4)test the work: reboot (or rmmod and then modprobe) and open terminal, then issue: dmesg | grep bcm43xx - and look for errors! no errors? well, try to issue iwconfig and see if your card is working!

5) more... to make it swift: removed the default network manager, and installed wifi-radar. i don't care for eth0, 'cause the kernel identifies and make it works ok.

6) sorry for the way i share my experience, i know that many users will tell "hmmm, i can give a try, but what does this means? and that?" but you can reply with more questions and i'll try to give my best. good luck

---

### Post by Rob_H on 2006-12-04
I vaguely recall that I had gotten it working with fwcutter, but speed was limited to 11 Mbps. Is that your experience?

---

### Post by quiquoqua on 2006-12-10
> **Rob_H said:**
> I vaguely recall that I had gotten it working with fwcutter, but speed was limited to 11 Mbps. Is that your experience?

yes, exactly! and moreover, in my case i have to boot with the options "noapic, nolapic"
and blacklist ipv6 in /etc/modprobe.d/blacklist

ave you got any clue on making beryl work with this pc? fglrx is installed ok 8.28.8, but when gdm (or the Xserver?) starts my system hangs and i don't know how to track the fault. 
specifically-- atix200m sucks, but i guess that maybe is a video card firmware related problem... do you know of any firmware version that makes it work?

---

### Post by Rob_H on 2006-12-10
> **quiquoqua said:**
> ave you got any clue on making beryl work with this pc? fglrx is installed ok 8.28.8, but when gdm (or the Xserver?) starts my system hangs and i don't know how to track the fault. 
specifically-- atix200m sucks, but i guess that maybe is a video card firmware related problem... do you know of any firmware version that makes it work?

Sorry, I can't even get DRI working with the ATI Xpress 200M, much less Beryl. The 200M is just horrible, and based on what I've read in various forums, it seems to be particularly touchy in HP/Compaq notebooks. I, for one, won't buy an HP again.

---

### Post by Rob_H on 2006-12-19
Hey, good news! It seems the latest ATI driver (8.32.5) fixes the 3D acceleration/DRI problems with the Xpress 200M! Here's what I did:

(1) Followed the Edgy Method 2 instructions [here]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide").
(2) Ran **aticonfig --initial --force**. For some reason, direct rendering still didn't work with my existing xorg.conf, even after upgrading the driver.
(3) Enabled Sideport RAM only in the BIOS. I used to have to set this to UMA+Sideport.

---

### Post by d-E-a-D on 2006-12-19
Just follow this: [http://ubuntuforums.org/showthread.php?t=321766&highlight=200m](http://ubuntuforums.org/showthread.php?t=321766&highlight=200m)

And you can get Ati, xgl, beryl and your Broadcom card working with no problem!

Cumps

---

### Post by Rob_H on 2007-01-06
So now that ATI drivers finally work, has anyone figured out how to easily switch between the internal and external displays using Fn+F4 or something similar? Right now, I have to maintain two separate "xorg.conf" files and manually switch between them if I want to use the internal LCD or the external monitor port exclusively.

---

