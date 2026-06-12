---
title: "Acer Aspire 5735z"
date: 2008-11-26
forum: Hardware
---

### Post by mattfromseattle on 2008-11-26
I have the Acer Aspire 5735z laptop as well, but I can't even seem to get it to boot using the live disc. I've tried in versions 8.04 and 8.10, as well as digging out an old version 7 disc. I'm able to get to the main screen of the CD where you can choose installation, but once I select to install, it goes through the loading screen and then goes black with a blinking _ cursor in the top left.  If I boot it as a live disc, I get:

"Buffer I/O error on device..."

And then it continues to reprint this message and a couple slight variations until I shut down the laptop.

With the version 7 disc, I was able to get past the load screen, but I started receiving errors that the screens could not be found. While I wasn't surprised by this since it was a brand new laptop, I am surprised I'm having this much trouble with the newest release of Ubuntu. Any thoughts? I know I probably haven't provided enough detail, but I am at a loss.

On a side note, OpenSUSE 11 was successfully able to be installed and the only problem I had was the wifi. Fedora 8 does not install and gives me the same issue as Ubuntu. Thanks in advance for any suggestions!

---

### Post by mattfromseattle on 2008-12-01
So I downloaded and successfully installed Fedora 10 over the weekend and it worked flawlessly, even my wifi.  So now I'm even more confused about Ubuntu not even loading the live CD portion on my laptop.  Anyone have success with this laptop?

---

### Post by dbius on 2008-12-12
Hi!

**[COLOR="Red"][SIZE="4"]UPDATE!!![/SIZE][/COLOR]**

Isn't necessary do the steps below, only install **linux-backports-modules** which contains the newest wifi drivers too, (and this method) use dkms, so if you do a kernel upgrade you don't have to reinstall anything!!!

Whith steps below after a kernel upgrade you have to reinstall the downloaded package!

------------

My friend bought one of this laptop. He gave me to install Ubuntu.

I could install Ubuntu 8.10 Intrepid (32 bit) without any problem, the only thing that is not worked, was the wifi.

I found, that the laptop has Atheros AR928X chip.

I searched via google about this chip and finally now the wifi is working too!!!

The solution that worked for me I found [here]("http://wireless.kernel.org/en/users/Drivers/ath9k")

So downloaded from [here]("http://wireless.kernel.org/en/users/Download#DownloadlatestLinuxwirelessdrivers") [this]("http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2")

I followed the instructions from there, but at ***sudo make unload*** gave me error, that it couldn't remove one module, the **mac80211**.

First I had to remove the **ath9k** module manually (because the mac80211 module was used by this module):

```
sudo rmmod ath9k
```

After this step with **sudo make unload** it could remove the necessary modules.

The next and final step was **sudo make load**

But I saw that the ath9k module wasn't loaded, so I had to load it manually:

```
sudo modprobe ath9k
```

Now the wifi is working!!! :guitar: And the wifi button light also ;)

So I suggest you to try it!


here is some information from the working wifi:

```
potyesz@ubuntu-laptop-potyesz:~$ lsmod |grep ath
ath9k                 250160  0 
mac80211              213296  1 ath9k
rfkill                 17176  2 ath9k
led_class              12164  2 acer_wmi,ath9k

```

```
potyesz@ubuntu-laptop-potyesz:~$ dmesg | grep ath
[   14.447520] ath9k: 0.1
[   14.510284] ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.524286] ath9k 0000:03:00.0: setting latency timer to 64
[   14.958447] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   15.108618] Registered led device: ath9k-phy0:radio
[   15.123008] Registered led device: ath9k-phy0:assoc
[   15.137112] Registered led device: ath9k-phy0:tx
[   15.166473] Registered led device: ath9k-phy0:rx

```

```
potyesz@ubuntu-laptop-potyesz:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:13:F7:2F:14:14
                    ESSID:"nanasi28"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=8/100  Signal level:-91 dBm  
                    Encryption key:off
                    IE: Unknown: 00086E616E6173693238
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 07064E4C20010D14
                    IE: Unknown: 2A0104
                    IE: Unknown: 32041224606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000005211aca5db
                    Extra: Last beacon: 4ms ago

pan0      Interface doesn't support scanning.
```

The wifi is working also after reboot!


Good luck :)

dbius

ps: sorry for my English

---

### Post by lexus_ on 2008-12-22
Hi everybody!

I have bought Acer 5735Z couple days ago. Under Ubuntu 8.04 version it realy didn't work properly. Microphone, build-in web camera didn't work and even it was not possible to watch any movie (system just hanging without any response to mouse or keyboard!)
 When I upgraded to 8.10, then it became possible to watch movie. But I still have problem with Microphone and build-in camera.

Have somebody faced with same problem?

---

### Post by dbius on 2008-12-22
> **lexus_ said:**
> Hi everybody!

I have bought Acer 5735Z couple days ago. Under Ubuntu 8.04 version it realy didn't work properly. Microphone, build-in web camera didn't work and even it was not possible to watch any movie (system just hanging without any response to mouse or keyboard!)
 When I upgraded to 8.10, then it became possible to watch movie. But I still have problem with Microphone and build-in camera.

Have somebody faced with same problem?

Built-in webcam worked for me under Ubuntu 8.10 "out of the box" so I didn't do anything with it. (I tried it with Skype).

Microphone: has got this laptop a built-in microphone?? Because skype worked for me only with an external (jack) microphone.

And what's the matter with the wifi at you? Works for you or not?

---

### Post by lexus_ on 2008-12-22
Thanks dbius for quick response. Wifi works good without any problem under 8.04 and 8.10. I have tried external microphone and it works now - under 8.10 (it didn't under 8.04)
   About Skype... I have tested my webcam there and it doesn't work. But good to know if it works for you :)

---

### Post by dbius on 2008-12-22
> **lexus_ said:**
> Thanks dbius for quick response. Wifi works good without any problem under 8.04 and 8.10. I have tried external microphone and it works now - under 8.10 (it didn't under 8.04)
   About Skype... I have tested my webcam there and it doesn't work. But good to know if it works for you :)

It'strange... did you an update you used skype?

---

### Post by lexus_ on 2008-12-23
> **dbius said:**
> It'strange... did you an update you used skype?

Yes, I downloaded skype two days ago from skype.com. Actually issue with webcam has been solved Today just after subscription to medibuntu repository and load updates. Source page [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by dbius on 2008-12-23
> **lexus_ said:**
> Yes, I downloaded skype two days ago from skype.com. Actually issue with webcam has been solved Today just after subscription to medibuntu repository and load updates. Source page [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

Congratulation ;)

hmmm... I used medibuntu repo too but I didn't recognize that this was necessary for a working webcam :)

---

### Post by LittleM@n on 2009-01-18
I have an Acer Aspire 5730Z, so very close to the 5735;
I wanted to install a linux operating system on it and i have choosen  ubuntu 8.10, because I understand that it's the best linux for notebooks.

Giving the fact that I am an old Windows user, I am a total noob and have no ideea how to use the linux, especially how to install new drivers. In windows it's very simple, you just run the exe, or you use device manager to reinstall a driver from a given location.
How do I install the driver for my Atheros AR928X? Because the wireless network doesn't work. It can see the wireless networks, also with the power for each of it, but is unable to connect :(
What steps do I have to make, where do I have to go, etc...
Please, can someone explain for me? ;;)

Also, why the System->Administration->Hardware Drivers is empty? What does this represents in fact?

Thank you!

---

### Post by lexus_ on 2009-01-20
About your problem with WLAN. Sure, you can find answer here
[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros]("https://help.ubuntu.com/community/WifiDocs/Driver/Atheros")

*Also, why the System->Administration->Hardware Drivers is empty? What does this represents in fact?*
Usually it represents some non open source available drivers for your system.

---

### Post by lexus_ on 2009-06-04
Is somebody installed Ubuntu 9.04 on Acer Aspire 5735z? How it works? Is it WiFi working too?

---

### Post by dbius on 2009-06-04
> **lexus_ said:**
> Is somebody installed Ubuntu 9.04 on Acer Aspire 5735z? How it works? Is it WiFi working too?

Yes, it works out of the box. I upgraded my Friend's Ubuntu from 8.10 to Jaunty, and the wifi works without problems.

---

### Post by rallymania on 2009-07-16
Just installed 9.04 on a 5735 last night 
had no problems with devices being detected (picked up wlan, sound... everything)
my only config issue is when you shut down it doesn't actually power off, i just get left with a flashing underscore cursor.
pressing and holding power button does switch it off so it's no drama, i'd just like to figure out how to fix it properly (it's going to be used by the misses you see)
 
(pretty new to linux, but not shy of the terminal if required)
anyone got some clues as to what i can try, or osmewhere i can learn about power config settings?

---

### Post by arma0012 on 2010-02-08
G'day,

I'm also using an acer 5735, and am using 8.10 out of the box and have had no issues either. 

Can anyone tell me if they know of any way to turn all the lights off? Or how to get the bluetooth button to do something else (since some models don't have bluetooth but still have the button) ?

Cheers,
Sam

---

### Post by Asymptotic on 2010-07-04
Hi, I just tried to install Ubuntu 10.04 LTS on to this laptop and now im really scared. My machine will no-longer boot from the live CD, it will also not Boot from the Vista Recovery CD it Will not boot the Windows 7 installer CD...
The Screen is not showing any information at all (although I think this may be because the computer doesn't stay on long enough to power the monitor) additionally I cannot get in to the Bios to change the boot order so I can't make a bootable flash.
I've tried plugging in an external monitor to see if this changes anything without luck.

This is my dads work laptop that I was supposed to borrow then give back to him, looks like it may be permabroke.

Im going to DL Fedora and see if that works but in the mean time can anyone give me any other suggestions of what I might try?

Cheers

***Update: Ubuntu 9.04 Live CD isnt being read either

***Update2: Fedora 13 is not booting from a live CD either.

---

### Post by MosaicDave on 2010-07-08
You know, very much the same thing happened to me: Just yesterday, I installed 10.04 onto an Acer Aspire 5735Z, and things were basically working (except for WiFi - see below).

This morning, however, when I tried to boot the machine, nothing would happen...  well, almost nothing: the power light would come on, it would stay on for maybe 10 seconds, then it would shut back down - no POST, no chance to enter the BIOS, nothing.  Weird.

Well, I unplugged everything and took the battery out for a few minutes.  Then plugged everything back in and it's working again normally.  As a matter of fact, I'm typing this message on the 5735Z right now.  Very strange; I wonder if it will happen again...

However: the WiFi doesn't work.  I can see other access points under the network browser, or whatever it's called, but I can't connect to anything, at least not with WPA2.  I haven't tried at all to fix this yet, though - just beginning with this machine.  There do seem to be plenty of references to this as I search around; probably it won't be too hard.

Well, at least the wired network connection works, which is all I need for the time being...

--dave

> **Asymptotic said:**
> Hi, I just tried to install Ubuntu 10.04 LTS on to this laptop and now im really scared. My machine will no-longer boot from the live CD, it will also not Boot from the Vista Recovery CD it Will not boot the Windows 7 installer CD...
The Screen is not showing any information at all (although I think this may be because the computer doesn't stay on long enough to power the monitor) additionally I cannot get in to the Bios to change the boot order so I can't make a bootable flash.
I've tried plugging in an external monitor to see if this changes anything without luck.

This is my dads work laptop that I was supposed to borrow then give back to him, looks like it may be permabroke.

Im going to DL Fedora and see if that works but in the mean time can anyone give me any other suggestions of what I might try?

Cheers

***Update: Ubuntu 9.04 Live CD isnt being read either

***Update2: Fedora 13 is not booting from a live CD either.

---

### Post by PaulW21781 on 2010-07-14
I'm having the same issue with the boot hangs...  Have to remove the battery and power supply for a second to get it working again.  Also the graphical flickering, its like a slight distortion every minute or so, reminds me of how my old nVidia card in my desktop played up when I had a dodgy PSU...

Also, I checked the Acer site for a BIOS update, its listing 1.08 as the latest (from [here]("http://www.acer.co.uk/acer/service.do?LanguageISOCtxParam=en&miu10einu24.current.attN2B2F2EEF=3734&sp=page15e&ctx2.c2att1=17&miu10ekcond13.attN2B2F2EEF=3734&CountryISOCtxParam=UK&ctx1g.c2att92=122&ctx1.att21k=1&CRC=2980211862"))

But checking the laptop here, it's reporting System Bios V1.11 :confused:

Also I found another link to another page on Acer, [http://support.acer-euro.com/drivers/notebook/as_5735.html](http://support.acer-euro.com/drivers/notebook/as_5735.html)

So I'm truly puzzled why mine has 1.11 showing, 1.08 is on acer under 5735Z (and also 5735 I checked), yet another Acer page shows v1.10...

I've tried emailing Acer customer support, but that failed "due to an unknown error"

Everything is fine with 10.04 on my other 2 Acer's though (7720G and 3500)

Meh...

---

### Post by MosaicDave on 2010-07-14
> **PaulW21781 said:**
> Also the graphical flickering, its like a slight distortion every minute or so, reminds me of how my old nVidia card in my desktop played up when I had a dodgy PSU...

BTW, I also notice a weird little occasional flicker in the video on this 5735Z - as though 100-200 rows of the display get corrupted, just for a single frame, or part of a split second; this happens every couple of minutes or so.

At first I attributed this to some kind of flaky internal connector, but since others appear to see similar things, I'm guessing I need to update the video driver somehow.  At this point, however, I haven't tried to figure out how to get the right driver installed; I'm just using the stock install from the 10.04 live CD; I'm only using this machine very occasionally at this point.

Previously this machine had Vista on it; I rarely used it as it was kind of an extra machine here, but I don't think it had this video problem under Vista.

The WiFi also isn't working right for me here under 10.04; it won't connect to any access points, though they show up in it's list.  I seem to remember being unable to get WiFi working under Vista, but I'm not sure about that; it was a long time ago, and generally under Vista nothing appears to work right anyway (hence Linux)...

--dc

---

### Post by MosaicDave on 2010-07-14
By the way: It occurs to me just now, that maybe the whole thing about sometimes needing to pull the battery to get it to cold boot, is maybe actually a video driver problem?

Hmmm...

--dc

---

### Post by PaulW21781 on 2010-08-07
> **MosaicDave said:**
> The WiFi also isn't working right for me here under 10.04; it won't connect to any access points, though they show up in it's list.  I seem to remember being unable to get WiFi working under Vista, but I'm not sure about that; it was a long time ago, and generally under Vista nothing appears to work right anyway (hence Linux)...

--dc

Not a solution for many, but I gave up trying to get the buggy Atheros card to work properly, so replaced it with a spare Intel 4965AGN card.  Needless to say, no more issues which works for me!

---

### Post by Ian Goodacre on 2011-01-26
Re display flicker: I am running 5735Z with BIOS 1.11. I'm running Debian rather than ubuntu, but also had the display flicker problem. For me it was solved by adding "i915.powersave=0" to the boot flags.

I also have the boot problem: often system will not boot. The fan and disk activity lights come on briefly, twice, then the power goes off again. The BIOS screen never appears. If I add boot option "acpi=off" then booting is reliable but the newer intel graphics driver requires acpi - with acpi off the intel driver (i915) doesn't load and I end up with the VESA driver and one lousy choice for screen resolution.

Update: following the advice at [http://www.lesswatts.org/projects/acpi/debug.php](http://www.lesswatts.org/projects/acpi/debug.php) I have discovered that with the boot option "pci=noacpi" the intel graphics driver loads and the boot problem occurs much less frequently, but it still occurs.

---

### Post by arma0012 on 2011-01-26
I was having the boot problem as well for a while (its been fairly ok recently). You can get it to boot by removing the plug and battery, depressing the power button for a few seconds (I assume to remove any relic power), then replugging and starting again.

I hate this machine.

---

### Post by elundmark on 2011-12-20
**Ubuntu 11.10 & Acer 5735Z FTW!**

I bought mine this summer for $~120, best money I've ever spent. had some issues with the Wireless Switch button in the beginning, but that was w/ Beta 2. Everything works flawlessly regarding the hardware, Unity 3D, graphics, even 720p Flash video runs really smooth.

Haven't tested the modem or the external vga port though.

Also, if your considering this laptop, I've had an irritating problem with bootups lately: After about 3 restarts, it won't boot, just spins up over and over. But if I remove the AC and the battery for a few seconds it boots fine. Annoying though. But I guess it's one of those things only a few have problems with.

... and the screen Q is excellent btw, crisp, bright, and 16:9 :)

---

