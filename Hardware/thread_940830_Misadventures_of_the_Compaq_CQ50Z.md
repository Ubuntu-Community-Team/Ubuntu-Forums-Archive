---
title: "Misadventures of the Compaq CQ50Z"
date: 2008-10-07
forum: Hardware
---

### Post by issact on 2008-10-07
So far this has been a wild ride.  Hours so far of searching various forums, scavenging google, and reinstalling a few times have brought me here.  I still have a ways to go, too, but at least I've made a little progress.

My two main concerns for right now are as follows:
Atheros AR5009 wlan NIC
nVidia GeForce 8200m 

To begin with, I installed the AMD64 version.  Installed and booted fine, but wlan would not work at all.  The physical wireless button up top was stuck on orange and would not budge to blue.  Also, the disabled nvidia device driver, when enabled, fails to download.  I did a little research and gave up early because I know 64bit still sucks.

So I reverted back to x86.  Wlan still was a lost cause on install, but the nvidia restricted driver actually downloaded and installed.  Rebooted the computer aaaaand black screen.  Seems the driver didn't take.  I'm still pretty new to linux and haven't used it for a few years, so my fix for that was a clean reinstall.

I scavenged my search options.  I found the solution to my video driver issues, though not completely.  At least now I have my full 1280x800 resolution display.  Link:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

The only issue I'm having with that involves display artifacts when the framerate gets too high.  For example, scrolling down a webpage quickly.  A minor annoyance with general computer use, but open up a game and it would be a nightmare I'd imagine.


As for wlan?  Well, I tried a couple things.  First, what didn't work.  Then, as of right now, what only works halfway.
This didn't work:
[http://ubuntuforums.org/showthread.php?t=865971](http://ubuntuforums.org/showthread.php?t=865971)

Following those instructions did nothing for me, despite everyone's success.  However, I'm not surprised as not all devices behave alike.  With the install of the madwifi drivers, nothing happened.  My NIC still wasn't being picked up by the network manager.

Second method I found involved the mac atheros drivers compiled into a debian package. Link:
[http://ubuntuforums.org/showpost.php?p=5535562&postcount=3](http://ubuntuforums.org/showpost.php?p=5535562&postcount=3)

This method got ubuntu to realize my wlan NIC exists.  The button is blue up top as if everything is honkey dory.  Just one problem, though.  It can't pick up any wireless networks, it's borked.  I tried through the GUI and through "sudo iwlist scan."  Nada.  When I try to connect to my wireless network manually with the correct settings, it just hangs.

One last thing, too.  I haven't investigated much into it yet, but, the sound is scratchy and intolerable.
My chipset is nForce, not sure which revision.

That's where I am, now.  If anyone has had any similar issues or experiences, or if anyone has found some solutions, please share them here.  I would definitely appreciate it.  :)

---

### Post by issact on 2008-10-08
I was able to find out more specific chipset information.

nForce MCP77MV is the northbridge.  There really isn't a lot of information about this chipset, yet.


I hear there's troubles with nForce chipsets in general.  Any ideas?

---

### Post by issact on 2008-10-09
I just gave ndiswrapper an honest shot, using the original driver from HP for my wireless card.
Source:
[http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=2093&lc=en&dlc=en&cc=us&product=3747533&lang=en](http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=2093&lc=en&dlc=en&cc=us&product=3747533&lang=en)
It's further down the page;    	  
Atheros Wireless LAN Driver 06-2008 	2.00 B 	»  Version: 	20.64M

I extracted the package w/ cabextract:
```

athrext.cat   athrx.sys  data2.cab    netathr.inf   setup.exe  setup.iss
athrextx.cat  data1.cab  ISSetup.dll  netathrx.inf  setup.ini  SP39403.cva
athr.sys      data1.hdr  layout.bin   _Setup.dll    setup.inx

```

I got these two files for use:
netathr.inf
athr.sys


ndiswrapper gladly took these and convincingly said, "Okay, sir!  You're good to go!"

... :(

Restart the system, no go.  Next I try:

sudo gedit /etc/modules
added "ndiswrapper" on its own line.

I assume this is somewhat similar to Run in the registry or somesuch.

Restarted the system, nada.

sudo modprobe ndiswrapper doesn't show or tell me anything.


"ndiswrapper -l" returns:
```

netathr : driver installed
	device (168C:002A) present

```
Yet iwconfig only returns lo and eth0.


sudo ndiswrapper -m:
```

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

```

---

### Post by junfeng wu on 2008-10-24
> **issact said:**
> I just gave ndiswrapper an honest shot, using the original driver from HP for my wireless card.
Source:
[http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=2093&lc=en&dlc=en&cc=us&product=3747533&lang=en](http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=2093&lc=en&dlc=en&cc=us&product=3747533&lang=en)
It's further down the page;    	  
Atheros Wireless LAN Driver 06-2008 	2.00 B 	»  Version: 	20.64M

I extracted the package w/ cabextract:
```

athrext.cat   athrx.sys  data2.cab    netathr.inf   setup.exe  setup.iss
athrextx.cat  data1.cab  ISSetup.dll  netathrx.inf  setup.ini  SP39403.cva
athr.sys      data1.hdr  layout.bin   _Setup.dll    setup.inx

```

I got these two files for use:
netathr.inf
athr.sys


ndiswrapper gladly took these and convincingly said, "Okay, sir!  You're good to go!"

... :(

Restart the system, no go.  Next I try:

sudo gedit /etc/modules
added "ndiswrapper" on its own line.

I assume this is somewhat similar to Run in the registry or somesuch.

Restarted the system, nada.

sudo modprobe ndiswrapper doesn't show or tell me anything.


"ndiswrapper -l" returns:
```

netathr : driver installed
	device (168C:002A) present

```
Yet iwconfig only returns lo and eth0.


sudo ndiswrapper -m:
```

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

```
Hello Issac,

I installed these packages for ubuntu 8.04:
1) [compat-wireless-ath9k]("http://ubuntuforums.org/showthread.php?t=874097") for AR5009,
2) envy-gtk for setting up NVIDIA 8200M,
3) [alsa-driver-linuxant]("http://www.linuxant.com/alsa-driver/") to fix the broken sound.
They work for me. Give them a try. Good luck! :D

---

### Post by junfeng wu on 2008-10-24
> **junfeng wu said:**
> Hello Issac,

I installed these packages for ubuntu 8.04:
1) [compat-wireless-ath9k]("http://ubuntuforums.org/showthread.php?t=874097") for AR5009,
2) envy-gtk for setting up NVIDIA 8200M,
3) [alsa-driver-linuxant]("http://www.linuxant.com/alsa-driver/") to fix the broken sound.
They work for me. Give them a try. Good luck! :D

Forgot to tell you my laptop is also a CQ50z. I installed the i386 version of ubuntu 8.04 on it using the alternative CD.

---

### Post by issact on 2008-10-25
> **junfeng wu said:**
> Forgot to tell you my laptop is also a CQ50z. I installed the i386 version of ubuntu 8.04 on it using the alternative CD.

Thanks very much for the reply!

Video/Sound are working flawlessly, now.  I appreciate the help very much.

However, the driver for my wireless NIC are still defunct.  I used that script to compile the debian package and it was a no-go.  I mean, I now have access to wireless networks, however I can't connect to them.  It seems like it is smart enough to sniff the authentication method, but actually acquiring an IP from the router is another story entirely.

To rule out human error in WEP/WPA settings, I disabled wireless security entirely and my wireless NIC was still standing in the outfield, going duhhhhrrrr...

I used the latest script from that page, from 9/15/08.  Did you use an earlier version?  Is wireless connectivity working entirely for you?  And if so, could you be very amazing and email me the *.deb package that you were able to compile?  Or did you make install it from source?

*confused*

Thanks for any response, as you've already helped so much.  The video artifacts are gone!

---

### Post by junfeng wu on 2008-10-25
There are some *.deb files at the "ath9k" link of my earlier post. Scroll down that webpage a little bit to #5 and you will find them.

The orange light of the wireless button won't turn blue in ubuntu, even when my NIC is connected to a network. Actually the light of the button is controlled by software and it just needs some guys to work out an LED patch. Maybe we can get a patch for that later.

Your wireless connection problem is kind of weird. Are you sure the security setting has been turned off? A network without password does not have the security icon besides their strength bar in network manager, just like the "linksys" shown in the image below.

[IMG]http://yousefourabi.com/blog/wp-content/uploads/2007/10/vpn1.png[/IMG]

Actually I am a linux newbie. I am glad I could help but my knowledge is quite limited. If the wireless connection problem really exists for unprotected network, it will need some more experienced linux users to solve.

---

### Post by gsorian on 2008-10-25
Hola...

Are your model Compaq Presario CQ50-215NR?...

I was working with Novell SLED, Fedora 9, then openSUSE 11.0, then with the Ubuntu 64 (fails to recognize the processor), and all fails to recognize Wireless and Video (I'm working with vesa)... 

I'm working with x86... I know that we don't take the best of 64 X2 :(

So I will try all your posts... I will let you know how it works...

Gracias!...
...MeMo

---

### Post by gsorian on 2008-10-26
Hey!...

At last it worked...

Do you check if wireless was disabled (red/blue button)... due a unchange of color... you don't know if it works or not...

well no more steps than specified in three tutorials...

Now everything is working....

BTW... this was from a clean installation...
- I update all that update manager ask
- then install alsa package, from update manager...
- then install envy package, directly in console (no update-manager)
- Check for previously installed Nvidia software and uninstall...
- Ubuntu becomes by default with envy... don't use that, after you install the new envy, you will see two Envy in the Applications > System Tools... use the below one... this will recognize your video card and will download and install everything your distro needs.
- I installed the atheros driver:
[compat-wireless-ath9k-2.6.24-19-generic_20080806-mactel1_i386.deb]("http://launchpadlibrarian.net/16628473/compat-wireless-ath9k-2.6.24-19-generic_20080806-mactel1_i386.deb") (Check for new updates in the site... ([http://ubuntuforums.org/showthread.php?t=874097](http://ubuntuforums.org/showthread.php?t=874097))
- I add to the line...
ath9k
...to /etc/modules

Something weird... the wireless networks not found at first... why?, actually I don't have idea... but... I install first as manual wireless, (right now I'm connecting from a Hotel, temporally)... and use the name of the wireless network, with none security... and works... after that... I reboot... change again to "Roaming Mode"... reboot again... and voila!... the networks around the hotel were recognized and the Hotel one, gives me the IP normally and without problems...

...and that's all... sorry if you saw me repeat the info... but I think that should be useful...

Thanks for all guys...
we keep in touch. (gsorian@gmail.com)

---

### Post by gsub on 2009-01-13
Hi there.

I just got my compaq cq50Z. I installed ubuntu 8.10, 64 bit.

After reading this post, I was preparing myself for the worst. Here is my experience - 

Wireless: Works great, with one problem - the colour of the wireless connection stays red even when the wireless connection is active.

Graphics: I installed envyng (available through synaptic), and ran it. It recommended a driver for the graphics card, and I installed it. After a reboot, the graphics card seemed to be working just fine.

Maybe there's something in the new release of ubuntu that takes care of all this?

Either way, I <heart> Ubuntu

---

