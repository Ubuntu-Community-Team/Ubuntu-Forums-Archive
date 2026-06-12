---
title: "Medion 97400 - first time user"
date: 2006-05-04
forum: Hardware &amp; Laptops
---

### Post by markus_nagler on 2006-05-04
Hello,

I have to switch to a Medion 97400 Notebook (German: [http://www.medion.de/md97400/sued/ausstattung.html](http://www.medion.de/md97400/sued/ausstattung.html)) after some years on a mac. I would like to run Ubuntu on it, but my Linux experience is very limited.
I tried the Ubuntu Live CD on my mac, I'm fine with command line stuff, and I used to have some Free BSD (IIRC) stuff on my mac. Plus, I know someone using Ubuntu albeit on a desktop machine.
So, my first question would be: _is there anything I absolutely need to do before I remove the pre-installed Windows XP?_ (besides downloading & burning an Ubuntu installation CD)

---

### Post by danielph on 2006-05-04
[LIST]
[*]Firstly have a good backup or 2 of everything you would need to recover the system back to it's current state. XP disks, drivers, data, configuration etc Just in case there is a problem.
[*]Consider running the machine as a dual boot as there will most likely times you still want to use windows at first.  Ubuntu can install itself and leave Windows in another partition.
[*]Export files you may need for the transistion into a format that ubuntu can read - things like the bookmarks from your browser, contacts, email, word docs, etc. Firefox can read HTML bookmarks, check Evolution and Thunderbird for what they can import.
[*]If you are using a wireless it maybe worth having a cable in case it does not work first time.
[*]Check the hardware compatibility list
[*]Search the forum for known issues with your hardware[/LIST]
Dapper is out in a few weeks, you may want to wait.

I cant think of much more at the moment, only to say welcome and enjoy.

Someone else may have more to add.

Dan

---

### Post by markus_nagler on 2006-05-04
[QUOTE=danielph][LIST]
[*]Firstly have a good backup or 2 of everything you would need to recover the system back to it's current state. XP disks, drivers, data, configuration etc Just in case there is a problem.
[*]Consider running the machine as a dual boot as there will most likely times you still want to use windows at first.  Ubuntu can install itself and leave Windows in another partition.
[*]Export files you may need for the transistion into a format that ubuntu can read - things like the bookmarks from your browser, contacts, email, word docs, etc. Firefox can read HTML bookmarks, check Evolution and Thunderbird for what they can import.
[*]If you are using a wireless it maybe worth having a cable in case it does not work first time.[/LIST]
[/quote] All of the above is fine, as my data are on a Mac that continues to be available. I certainly won't want to run Windows.

> [*]Check the hardware compatibility list
[*]Search the forum for known issues with your hardware.
Dapper is out in a few weeks, you may want to wait.
Could you define "hardware"? There's a bewildering array of "stuff" under System (when running the pre-installed WinXP), which of that is important?
My search for experiences with Medion Laptop produces only very scarce results, none with the precise model I'm using (AFAIK only sold from today).
Waiting for Dapper isn't really an option as I need the machine up and running soon. Just out of curiousity: will the upgrade to Dapper require a complete reinstall or will it be comparably painless, i.e. a regular upgrade with some hardware and software problems that are ironed out over the following 6 months?

---

### Post by danielph on 2006-05-04
What I mean by hardware is - Video, Sound, Multimedia, DigitalCameras, WebCameras, WiredNetworkCards. WirelessNetworkCards, Printers. Scanners, Motherboards 
and Mouse. The website for your machine or the documentation that came with it should have this listed. From the link you posted the video card is ATI Mobility&#8482; Radeon® XPress 200M Graphics card for example. Being so new it most likely has not been tested on Ubuntu. This does not mean it will not work. Will it work with 3D and all resolutions, well I can't answer that. Doing a quick search on this forum or google for this card will reveal more.

[http://www.ati.com/products/radeonxpress200m/specs.html](http://www.ati.com/products/radeonxpress200m/specs.html)

Some manufactures are not so friendly towards Linux, they may not write drivers or the source is closed. This makes it harder, but not impossible to get stuff working. Some are very friendly. For example Nvidia for video drivers, and Belkin have started using a Ralink chipsets in some of their wireless cards which are supported in many distributions of Linux. 

Also check out [https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport) is a place to start and maybe the manufactures of your chipsets / hardware and this is a link to a Medion 95264 [https://wiki.ubuntu.com/LaptopTestingTeam/Medion95264?highlight=%28medion%29](https://wiki.ubuntu.com/LaptopTestingTeam/Medion95264?highlight=%28medion%29)

The chances are most of this stuff will work and if it doesn't there is normally a way to get it working. This forum is a great help if you do have problems.

As for Dapper uprade well once the dapper official release is made, you should be able to upgrade to it through the update manager. There are known issues with automatix, which should be removed first (if you have installed it). From limited experience with dapper distribution upgrades through the dapper release cycle it works well. 


Regards


Dan

---

### Post by markus_nagler on 2006-05-04
Thanks for the clarification on the hardware. I went through the core components and came up with potential problems for the following:

> [list][*]audio: Realtek ACL650 AC'97 > bug #2090 > seems fixable, I'll cross that bridge when I come to it

[*]network: ULi PCi Fast Ethernet > no info on wiki > forum: [http://ubuntuforums.org/showthread.php?t=148812](http://ubuntuforums.org/showthread.php?t=148812) > ???

[*]WL-network: Winbond W89C33 mPCI 802.11 WLAN Adapter > no info on wiki > forum yields this: [http://ubuntuforums.org/showthread.php?t=164869](http://ubuntuforums.org/showthread.php?t=164869) which is no help to me

[*]graphics: ATI Radeon Xpress 200M > not mentioned on wiki; > forum yields: [http://ubuntuforums.org/showthread.php?t=164852](http://ubuntuforums.org/showthread.php?t=164852) > uh oh![/list]
I nonetheless went ahead:

**A. Installation history**

1. attempt: screen went blank; force restart through power button
2. attempt : [http://ubuntuforums.org/showthread.php?t=165796](http://ubuntuforums.org/showthread.php?t=165796)
typing "linux acpi=off noapic nolapic vga=771" at the prompt. Works.
*
3. X-server does not work. Detailed output does not contain any error messages. I only get a centered white square on a blue background with lines made from nonsense letters. "Detailed output" is basically just version numbers etc.
> Following the advice here [http://ubuntuforums.org/showthread.php?t=164852](http://ubuntuforums.org/showthread.php?t=164852)
However, I had to use "sudo nano /etc..."
_I do not understand the instructions linked to further down that thread. Help would be appreciated._
This gets me to the login screen, however right before it comes up, the lower half of the screen is filled with vertical white lines for half a second.

4. Ubuntu runs, graphic are ok. However, _no network_
> checked the router, enabled notebook's MAC address. Still, pinging the router from the notebook does nothing at all > presumably the ethernet card is not properly configured/recognised.
A change to a static IP address makes ping work, but with 100% packet loss.

**B. Areas of immediate concern:**
- network, see #4 above.
- playing an audio disc worked, but correlated with the system becoming unresponsive, i.e. Application, Places and System no longer "pull down" etc. Almost as if the system was under heavy load. The phenomenon persisted after removing the audio disc. Tried to reproduce without success.
- trackpad and mouse are over-responsive. No idea where to fix that. Changing System/Preferences/Mouse had no discernible effect.

**C. What test should I perform to ensure everything is working smoothly?** I will certainly try out a few programmes, but perhaps there's a list to go through.



**((FWIW: the options around partitioning are a bit unclear. Irrelevant in my case, as I plan to erase everything and do a clean install anyway, once I've verified it's working.))*

---

### Post by danielph on 2006-05-04
> 4. Ubuntu runs, graphic are ok. However, _no network_
> checked the router, enabled notebook's MAC address. Still, pinging the router from the notebook does nothing at all > presumably the ethernet card is not properly configured/recognised.
A change to a static IP address makes ping work, but with 100% packet loss.I am no expert on Linux troubleshooting but I'll try and help. Before checking your driver, it is worth checking that the configuration for the netcard is good.  Can you ping yourself or ping loopback 127.0.0.1? If so, can you ping another computer other than the router? Can the router except ping's or are they disabled? Have you got the correct subnet mask etc. Are there any pointers in the system log (System, Administrator)? Does the card stop and start ok (System, Administrator, Networking). You may like to try Network Tools in the same place.

Some commands you may like to try. Open up terminal (Application, Accessories) and type ifconfig. Do the results look as you would expect? Also you can have a look at routing info with Netstat -r.

My ifconfig:
```
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17576 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17576 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:519226 (507.0 KiB)  TX bytes:519226 (507.0 KiB)

ra0       Link encap:Ethernet  HWaddr 00:11:50:66:F3:79
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:fe66:f379/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2876665 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2920844 errors:198 dropped:198 overruns:0 carrier:0
          collisions:66061 txqueuelen:1000
          RX bytes:1965566161 (1.8 GiB)  TX bytes:1816118336 (1.6 GiB)
          Interrupt:193 Base address:0x8000

```

Good Luck

---

