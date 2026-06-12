---
title: "Ubuntu  destroyed my Network Card - RTL8111"
date: 2010-03-22
forum: Hardware
---

### Post by Pastortom on 2010-03-22
Hi..

I just wanted to let people know that Ubuntu 10.04/9.10 64-bit can you destroy your network card.. 

That's at least my conclusion, and by all means, I hope Im wrong..

Ive got a Asus P7P55D motherboard with i5 CPU, 2x2gig rams, 2x9500GT gfx cards.. and this motherboard has the NIC RTL8111/8186B network adapter.. 

I started out with Windows 7 a couple of days ago, it worked like a breeze, but it was too slow for my taste..

So I decided to install Ubuntu.. 

I installed Ubuntu 10.04, and had huge troubles with my network card being given WRONG driver by the OS..

after a total of 12 hours of searching, I discovered 6-7 potential solutions to my problem.. and being as this was a software problem, i never took to consider that I might have to be very carefull so my hardware wouldnt be destroyed..

Anyways, 

after trying 10.04 a while, I resulted in trying 9.10.. but still, the same problem..

so I followed some guides etc.. and tried different things, but nothing..

I tried directly hooking my ADSL modem to my computer (and thereby skipping DIR-615 Dlink router) incase my router was the issue, but still nothing..

I reacted to the lights the NIC was giving..

Orange.. steady.. but slow..

I had never seen that before, and my experience with electronics made me look at this as a warning sign.. or perhaps a "too-late"-sign :P

I didnt know..

So i installed Windows Xp again, still same problem..

I installed Windows 7, still same problem..

And I wanna let you guys know, that for not 14 hours ago, I was playing Star Trek Onlin, and surfing the web, with Windows 7.. without any troubles..

I have checked the drivers, the bios settings, even updated the bios, and updated the drivers.. but still.. nothing.. 

I recall Ubuntu showing alot of weird addresses from the Network card.. like IP address being 192.234.0.231 and gateway being 253.0.3.123 etc.. really weird stuff.. I just thought it was a software malfunction. like a wrong driver.. but I guess I was wrong..

I hope, by all means I am wrong here, but I doubt it..

If you have experienced similar situations, and found a solution for it, I would be forever thankfull :)

Guess I have to go pick up a PCI-ethernet card...

NOW I could wish I never gave away the 30 PCI-ethernet cards i had lying around 3 weeks ago :P

=(

---

### Post by Sophont on 2010-03-23
That a driver destroyed your network card is highly unlikely.

It's way more probable that your card was gradually failing and it just happened while you did your Ubuntu tests.

There's one simple thing you can try (if you haven't already) - if your computer isn't a laptop.

Open the case, pull out the network card (touch grounded metal to make sure you're not statically (sp?) charged before you do that), then put it in again.

I remember a couple times where that made a difference because the card didn't sit right or a contact was oxydized (sp?).

---

### Post by Muzer on 2010-03-23
It's an onboard card as he said in the OP.

Make sure that when you re-installed XP/7 you correctly installed the proper drivers.

---

### Post by Pastortom on 2010-03-24
> **Sophont said:**
> That a driver destroyed your network card is highly unlikely.

It's way more probable that your card was gradually failing and it just happened while you did your Ubuntu tests.

There's one simple thing you can try (if you haven't already) - if your computer isn't a laptop.

Open the case, pull out the network card (touch grounded metal to make sure you're not statically (sp?) charged before you do that), then put it in again.

I remember a couple times where that made a difference because the card didn't sit right or a contact was oxydized (sp?).

Its onboard.. 


> **Muzer said:**
> It's an onboard card as he said in the OP.

Make sure that when you re-installed XP/7 you correctly installed the proper drivers.


I have.. Windows 7 has native drivers that works fine with this.. as I experienced from before installing Ubuntu..

It worked 100% fine for 3 months  (since I bought this PC and put it together) with Windows XP, I have also though tried to install Asus' official drivers, but no luck..

This network card has NEVER had any problems before, so it couldnt have been gradually failing.. 

And Ive never heard of completely new NIC's just failing one day when you suddenly wanted to format and install a new OS.. :P

By all means, I hope Im wrong, and theres a better explanation to what happened here, but I doubt it =/

---

### Post by TBABill on 2010-03-24
I had a similar experience recently while trying to install PCBSD on a partition. I downloaded, verified md5sum and began the install process. It popped the screens and seemed to install ok for about 5 seconds, then the entire laptop froze. No flashing, no movement of anything. I though....darn, a glitch. So I had to hard restart and realized I had fried the BIOS. It's a laptop and it would not even boot to the BIOS screen. I replaced the BIOS battery thinking it was a few years old...same result. I took every step I could find to bypass the BIOS and get up and running (pages of help ideas from various online sites and forums) but nothing would boot past the bios and recognize the CDROM, USB or anything. Black screen was best I could do (not a blank/off screen...it was showing black color, not just empty of color). 
 
It was either a really odd time to fail so hard or something in the install process of PCBSD interfaced with the BIOS and rendered it inoperable. I wanted to try and flash the BIOS to update/reset it, but couldn't get anywhere with the level of failure I encountered. I have installed over 30 distros on the same machine, have kept the fan clear and dust free, make sure to keep the laptop cool, etc. It just died right there in front of me.
 
I can't say it was PCBSD because it never finished. Most likely it was hardware failure that happened at that moment for no other reason other than it was its time, but I sure won't be installing PCBSD on any machine I own just out of caution it could happen again if it's a fluke in the install.

---

### Post by norseman-has-a-laptop on 2010-03-24
well think of it like this maybe it has nothing to do with the OS you have maybe its just a faulty product i cant tell you how many times something like this has happened to me with internal hardware. replace it if that doesn't work then you have an extra network card.
i really dont think it was ubuntu. i have similar problems with windows and macs but non of my linux computers have had this problem

---

### Post by Sophont on 2010-03-25
> **Pastortom said:**
> Its onboard.. 

Sorry - overlooked that.

> **Pastortom said:**
> 
This network card has NEVER had any problems before, so it couldnt have been gradually failing.. 

Sure it could. Stuff that breaks always works fine until it doesn't.

> **Pastortom said:**
> 
And Ive never heard of completely new NIC's just failing one day when you suddenly wanted to format and install a new OS.. :P

Certainly a creepy coincidence. But given a large number of installs over time it would happpen sooner or later. That looks meaningful from the point of view of the individual it happens to, but statistically it is expected given enough time.

> **Pastortom said:**
> By all means, I hope Im wrong, and theres a better explanation to what happened here, but I doubt it =/

The simplest explanation is often the best.

On the one hand we have a coincidence. On the other hand we have software somehow killing a piece of hardware. The latter is not impossible. But I assume that the manufacturer did not design a fail feature that allows for a special code sequence that overheats and melts a weak line somewhere. And the driver would be designed to work to specs. That makes destroying your NIC a very very very unlikely event.
If a recent kernel had an unfortunate driver that is capable of killing certain NICs we would probably get a lot of angry postings here.

Hardware does fail suddenly in a small percentage of cases. RAID Controller, several HDDs, a NIC or 2, motherboards, etc... - during the last 20 years I've seen them all fail. Worked perfect one day - gone the next.

Many years ago a not so old computer of mine suddenly did not turn on. Everything was fine before. One morning I switch it on - nothing.
Turns out the stupid floppy drive I hadn't even used in a while decided to go out with a bang and shorted the power pack.

All things considered coincidence is the most likely explanation by far.

---

### Post by dolbex on 2010-04-21
I have the exact same board and the same thing happen to me.  Had my computer for over a year.  Installed Ubuntu plenty of times on other machines, just not on this one and not from Windows.  Network card is dead.

---

### Post by yingwuzhao on 2010-04-29
I have the same problem, exactly the same symptoms. My mobo is p7p55d-e dulexe. Your network card is NOT dead!!

Simple power down you computer, and unplug every power sources, then wait for a couple of minutes, and start your computer again. The card will be alive again!

Try it and report back.

---

### Post by old_man_auz on 2010-04-30
I had the same problem.

My motherboard is a "Gigabyte 790XTA-UD4" with the same onboard network hardware as in the forum title. Network working fine in both Windows 7 and Kubuntu 9.10. I installed Kubuntu 10.04 overtop of Kubuntu 9.10 and the wired network wouldn't work. ALSO I couldn't connect to it with my wireless, which is a TPLINK wireless card of some sorts. I restarted back into Windows 7 to see if I could find some answers to my problems and BOTH the wired AND wireless hardware refused to work in Windows 7 as well.

I was beginning to panic, but as the guy said above, once I turned my computer off and unplugged everything from the wall for about 3 minutes and turned back on, the wired network is working again. I haven't tested the wireless yet.

---

### Post by elnur on 2010-05-01
> **yingwuzhao said:**
> I have the same problem, exactly the same symptoms. My mobo is p7p55d-e dulexe. Your network card is NOT dead!!

Simple power down you computer, and unplug every power sources, then wait for a couple of minutes, and start your computer again. The card will be alive again!

Try it and report back.

Thank you very much! I started thinking really bad about Ubuntu, but my network card is back alive.

---

### Post by peepingtom on 2010-05-01
Something like this happens when bad microcode/firmware is loaded on a chip by a driver. When that chip loses power, this firmware is no longer present, and new firmware can be loaded. A reboot is not the same as a hard reboot: [http://en.wikipedia.org/wiki/Booting#Hard_reboot](http://en.wikipedia.org/wiki/Booting#Hard_reboot)

You guys should post a bug report in Launchpad.

---

### Post by yingwuzhao on 2010-05-03
Now the problem has two aspects, one is in windows and the other is in linux.

For windows you want to roll back the network driver to the microsoft one, instead of using the one provided by Realtek, then turn on the feature "wake on lan" in device manage -> network card -> power management. 

For linux, you want to install the tool "ethtool" and in the console do:
sudo ethtool -s eth0 wol g

to also turn on the feature "wake on lan". Then the problem should be solved. If it still doesn't work, then under linux do the following:
sudo ethtool -s eth0 wol d
then do again:
sudo ethtool -s eth0 wol g

Best

---

### Post by satosh on 2010-05-16
My realtek nic rtl8111 (integrated on p7p55d-e) would only run in 10Mbps on either ubuntu lucid 64bit and win7. The cold boot (a couple of minutes off with no power plugged into the PC) worked. Thanks!

---

### Post by carsonrose on 2010-05-16
I have a Toshiba laptop that uses the RTL8111, I just tried the hard reboot, took the battery out of my laptop, then waited 4 or 5 minutes then put it back in. I still have no eth0. I see the green light solid and the orange light blinking.... but I cant get online. :(

---

### Post by slickvguy on 2010-05-16
FWIW, this happened to me today as well.
I have a GA-H55M-UD2H w/ onboard RTL8111D.
I installed Win7. No problems.
I installed Lucid, and networking was disabled. Well, I've been through this NIC/driver stuff before with other distros, so I thought it would be easy to fix. Unfortunately, after trying all the methods mentioned in various posts around the Internet (i.e. changing the driver to r8168 instead of r8169) - I cannot get it to work. 

Worse, when I booted into Win7, the previously working networking was now not working! As mentioned in other posts, the simple solution is to pull the PC plug for a minute or so in order to completely drain the motherboard of power. That worked. 

So not only does this f'n interface/driver combination not work in Lucid - but it puts the NIC in a state that Win7 can't pull it out of! I will look into this matter further over the coming hours/days and see what I can do about it. Yeah, I could just slap in a compatible PCI card - but I don't want to unless I absolutely have to.

---

### Post by slickvguy on 2010-05-16
> **carsonrose said:**
> I have a Toshiba laptop that uses the RTL8111, I just tried the hard reboot, took the battery out of my laptop, then waited 4 or 5 minutes then put it back in. I still have no eth0. I see the green light solid and the orange light blinking.... but I cant get online. :(

You removed the battery - but did you still have your laptop plugged into an AC outlet? If so, do whatever you have to do to make sure there's NO power going to the motherboard/NIC. Drain it. Also, try powering off/on the router. It's not damaged - it's just stuck in a bad state.

---

### Post by slickvguy on 2010-05-16
Success!

OK, I'm not 100% sure, but it now appears that it was the original driver (r8169) that put the NIC in a "dead state". Because after draining PC's power and verifying in Win7 that the NIC was working - I booted back into Lucid...and now the NIC is finally working (using r8168). :)

---

### Post by carsonrose on 2010-05-16
> **slickvguy said:**
> You removed the battery - but did you still have your laptop plugged into an AC outlet? If so, do whatever you have to do to make sure there's NO power going to the motherboard/NIC. Drain it. Also, try powering off/on the router. It's not damaged - it's just stuck in a bad state.

I unplugged it, then took out the battery.... still no luck! :(

---

### Post by slickvguy on 2010-05-17
Further update: I want to be clear, in case anyone stumbles upon these posts while searching the net. Earlier, my kernel automatically updated (since this was a fresh install) to 2.6.32-22 (from 21). And guess what? It also has the 8169 driver built in - but it works! 

The problem is that once a "bad" driver is used, it puts the NIC in a state that can't be initialize/reset until you pull the plug. So no matter what you try - it won't work. Further, it's obvious that BOTH driver numbers (8168 and 8169) can work. I guess you need the right version (i.e. code) of the driver (or is it something to do with the kernel and not the driver code?). I have r8168-8.018.00. I can confirm that one works. 

So now I'm back to using the r8169 and it works. So either it's a different version and/or other code was changed. Either way, I'm a very happy camper.

---

### Post by Geffers on 2010-05-17
> **Pastortom said:**
> Hi..

I just wanted to let people know that Ubuntu 10.04/9.10 64-bit can you destroy your network card.. 

That's at least my conclusion, and by all means, I hope Im wrong..

=(

This is a long shot due to date you posted problem but if not resolved try a Windows system restore to a known good date.

This sounds illogical but recently my wife's 6 month old HP laptop lost sound control, after trying the obvious I then booted an Ubuntu LiveCD, still no sound so OBVIOUSLY a hardware failure.

Got on to HP helpline (surprisingly helpful), he suggested a system restore, I told him this was a waste of time as a completely different OS had sound problems but he explained he had to follow procedure.

I complied with this waste of time and guess what...

IT WORKED  :confused:

I do not understand the logic but it worked, sound works now in Ubuntu as well.

Geffers

---

### Post by carsonrose on 2010-05-17
> **slickvguy said:**
> Further update: I want to be clear, in case anyone stumbles upon these posts while searching the net. Earlier, my kernel automatically updated (since this was a fresh install) to 2.6.32-22 (from 21). And guess what? It also has the 8169 driver built in - but it works! 

The problem is that once a "bad" driver is used, it puts the NIC in a state that can't be initialize/reset until you pull the plug. So no matter what you try - it won't work. Further, it's obvious that BOTH driver numbers (8168 and 8169) can work. I guess you need the right version (i.e. code) of the driver (or is it something to do with the kernel and not the driver code?). I have r8168-8.018.00. I can confirm that one works. 

So now I'm back to using the r8169 and it works. So either it's a different version and/or other code was changed. Either way, I'm a very happy camper.

Well, I stand corrected. I left the battery out of my laptop for about 10 minutes, nothing changed. I was still stuck with, what I though, was a bad NIC. Well, I left the laptop unplugged overnight, it some how drained everything there was............. I really thought I had drained it, but I guess not. I turned it back on this morning and it was dead, so I plugged it in............. VIOLA!!! 

THANKS GUYS!!! :guitar:

---

### Post by GenBattle on 2010-05-24
Also putting my name down for this problem. 

I would suggest the common factors are a 64-bit os/driver, dual-booting with Win7, and this realtek chipset (8168/8169/8139/8111) are to blame. It's also strange that the Asus P7P55 boards all seem to come up with this problem; but then they all share the same realtek chipset.

Have had no problem with 9.10, but as soon as i upgraded to 10.04 through the update system and restarted, bingo.

Will try the fix from [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448) tonight.

This is a very serious problem. I can imagine less technically inclined and less determined people would give up their hardware as completely bricked, when they just need to turn the power off and on. I myself was resigned to the fact that i needed a new motherboard or network card until i did some very extensive digging to find these threads on the Ubuntu forums.

It doesn't help when someone reports a problem like this and suggests a software fault causing hardware to be bricked, only to have someone come along and dismissively say that software cannot possibly brick hardware. This is not precisely bricking the hardware, but it does give the same appearance.

---

### Post by GenBattle on 2010-05-24
Restarting did indeed fix it.

Again, i can't stress enough how much of an issue this sort of failure is for Ubuntu. It not only bricked my network card under Linux, but also under windows, so i had no way of knowing whether or not my hardware had failed.

---

### Post by bingcrosby on 2010-05-31
Do these issues effect *.32-22 or was it just *.32-21?
If so, when will an iso be released with *.32-22 I can install directly to my new asus P7P55 PC (coming in a few weeks)? If I install the current iso from CD I presume I won't be able to update because the network card won't work.

---

### Post by sandrogalli on 2010-06-01
Hi, I can confirm that this is an issue for the Asus M4A785T-M onboard LAN, and is due to an incorrect driver loading with the 2.6.32-22-generic-pae kernel (may apply to other kernels also).

This is how I rectified the issue.

1. Check the model number of your ethernet controller:
```
$ lspci | grep Realtek
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/[COLOR="Red"]**8168B**[/COLOR] PCI Express Gigabit Ethernet controller (rev 03)
```

2. Check the driver your kernel is loading:
```
$ lsmod | grep r816*
[COLOR="Red"]**r8169**[/COLOR]                  91629  0
```

As you can see we have a [COLOR="Red"]**r8169**[/COLOR] driver for a [COLOR="Red"]**r8168**[/COLOR] chipset which is the cause of our issues.

3. Download the **8168** linux drivers from the [_Realtek_]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8111B/RTL8168B/RTL8111/RTL8168%3Cbr%3ERTL8111C/RTL8111CP/RTL8111D%28L%29%3Cbr%3ERTL8168C/RTL8111DP/RTL8111E%3Cbr%3ERTL8105E") website. Alternatively I have attached the correct driver to this post.

4. cd to Download directory and extract:
```
$ tar -xvf r8168-8.018.00.tar.bz2
```

5. Run script as superuser to autocompile driver:
```
$ cd r8168-8.018.00
$ sudo ./autorun.sh
```

6. [Optional] Test driver
```
$ sudo rmmod r8169
$ sudo modprobe r8168
$ sudo /etc/init.d/networking restart
```

Your network should be up and running with the new driver. To make the change permanent.

7. Blacklist r8169.
```
$ sudo gedit /etc/modprobe.d/blacklist.conf
```

Append the following lines:
```
# Blacklist Realtek RTL8111/8169 gigabit driver
blacklist r8169
```

Save and quit.

8. Update driver cache.
```
$ update-initramfs -u
```

REBOOT and see if the correct driver has loaded:

```
$ lsmod | grep r816*
[COLOR="Red"]**r8168**[/COLOR]                  91629  0
```

And everything should be just hunky-dory. ;)

---

### Post by ttguy on 2010-06-09
> **bingcrosby said:**
> Do these issues effect *.32-22 or was it just *.32-21?


I have this issue with 2.6.32-22.

And my system is not dual boot. So it is not related to dual boot installs.

I also had the situation where the 10.04 was working fine from 23 May up until something happened evening of 7th of June 2010 to break the network. My solution was to restore  9.10 - the Karmic Koala from a saved image.  This imediately restored network connectivity. I was thinking that I could just re do the upgrade to 10.04 and things would be fine. But  I found that as soon as 10.04 (as downloaded 9 June -  2.6.32-22) my network was dead again.

---

### Post by edkmho on 2010-06-11
Hi guys,

I have the exact problem with Realtek RTL8111D chipset on 2.6.32-22-generic kernel version. I have also installed the realtek driver 8.018. But it still once in a blue moon decided to stop working. By installing the driver and dual boot may not be the resolution. Hopefully someone can find a permanent solution to this.

My hardware is as follow:
Gigabyte P55-UD3P
Core i5 750
8 Gb Ram


Thanks.

---

### Post by LeonidShamis on 2010-06-30
Hi,

I've just experienced the same problem with ASUS P7P55D-E PRO motherboard which has Realtek® 8112L Gigabit LAN controller.
I've first installed Windows 7 and everything worked OK, and I started the Ubuntu 10.04 64-bit installation (with plan for a dual boot). The installation has not completed and when I returned to Windows 7 the network was dead.
BTW, the solution explained in this thread worked perfectly and I'm very thankful for your explanation.
I still have questions though: 
- Can I try installing the Ubuntu 10.04 again?
- Will it result in the same problem again?
- Is there a way to permanently fix this problem to allow Ubuntu 10.04 and Windows 7 (dual boot) work properly without a need of unplugging from the power after changing to another OS?
- If there is a permanent solution, how to apply it?

Thank you very much.

---

### Post by kismeras on 2010-07-13
> **sandrogalli said:**
> Hi, I can confirm that this is an issue for the Asus M4A785T-M onboard LAN, and is due to an incorrect driver loading with the 2.6.32-22-generic-pae kernel (may apply to other kernels also).

This is how I rectified the issue.

1. Check the model number of your ethernet controller:
```
$ lspci | grep Realtek
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/[COLOR="Red"]**8168B**[/COLOR] PCI Express Gigabit Ethernet controller (rev 03)
```

2. Check the driver your kernel is loading:
```
$ lsmod | grep r816*
[COLOR="Red"]**r8169**[/COLOR]                  91629  0
```

As you can see we have a [COLOR="Red"]**r8169**[/COLOR] driver for a [COLOR="Red"]**r8168**[/COLOR] chipset which is the cause of our issues.

3. Download the **8168** linux drivers from the [_Realtek_]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8111B/RTL8168B/RTL8111/RTL8168%3Cbr%3ERTL8111C/RTL8111CP/RTL8111D%28L%29%3Cbr%3ERTL8168C/RTL8111DP/RTL8111E%3Cbr%3ERTL8105E") website. Alternatively I have attached the correct driver to this post.

4. cd to Download directory and extract:
```
$ tar -xvf r8168-8.018.00.tar.bz2
```

5. Run script as superuser to autocompile driver:
```
$ cd r8168-8.018.00
$ sudo ./autorun.sh
```

6. [Optional] Test driver
```
$ sudo rmmod r8169
$ sudo modprobe r8168
$ sudo /etc/init.d/networking restart
```

Your network should be up and running with the new driver. To make the change permanent.

7. Blacklist r8169.
```
$ sudo gedit /etc/modprobe.d/blacklist.conf
```

Append the following lines:
```
# Blacklist Realtek RTL8111/8169 gigabit driver
blacklist r8169
```

Save and quit.

8. Update driver cache.
```
$ update-initramfs -u
```

REBOOT and see if the correct driver has loaded:

```
$ lsmod | grep r816*
[COLOR="Red"]**r8168**[/COLOR]                  91629  0
```

And everything should be just hunky-dory. ;)

I'm having the same issue with ethernet not working in Linux Mint 9 X64. It also causes the ethernet to stop working on Windows 7 Pro X64. I tried your fix but no luck. I ended up removing Mint and just using Windows 7. Are the developers aware of this issue? Does anyone know if there is a fix coming?

---

### Post by ttguy on 2010-07-13
As mentioned above I had this issue. And so I attempted to fix it  following the suggestions from sandrogalli.

I thought I should update this thread about my experience.

  I made the changes while running the  2.6.31-22-generic Ubuntu 9.10 - the Karmic Koala. I was on this version   - because I restored this version from an image after my network died on my Lucid install. The restore did not fix networking - see my previous post - and so  I tried following sadrogallis instructions under Karmic. 
 
11/6/2010
Get info about the installed network card 

```
 lspci | grep Ethernet 
 
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03) 
 
```get info about what driver is loaded - I have 8169 drivers for a 8168B card like  sandrogalli.  

Which he thinks is the problem and fixes as described below. 

But others just fix it by unplugging the pc for 3 mins 

```
 lsmod | grep r816* 
r8169                  32160  0  
mii                     5212  1 r8169 
 
```download the 8168 linux drivers and untar and install them 
```

tar -xvf r8168-8.018.00.tar.bz2 
 
 sudo ./autorun.sh 
 
$ sudo rmmod r8169 
$ sudo modprobe r8168 
$ sudo /etc/init.d/networking restart 
 

```At this point my networking is still down. So I UNPLUG the PC for one hour (posts say 3mins in enough) 
This is supposed to make the Network card forget everything and have to reload the drivers. 
When I restart I have networking back but  lsmod | grep r816* still reports r8169   
 
I then restore a disk image  to give 2.6.32-22-generic  Ubuntu 10.04 LTS - the Lucid Lynx  
When this boots up after the restore networking is working. 
$  lsmod | grep r816* reports the same ie I still  8169 drivers for a 8168B card  - but it is working 

```
r8169                  33980  0  
mii                     4381  1 r8169 
 
```12/6/2010 The 2.6.32-22-generic  Ubuntu 10.04 LTS - the Lucid Lynx  is still working - net work fine. 
13/6/2010 - install a bunch of updates 
kernal is still 2.6.32-22-generic 
networking still working after these

So I don't really know what actually fixed it. I don't seem to have changed my drivers. It may have just been having the modem off for long enough.

---

### Post by kismeras on 2010-07-13
@ TTGUY - My experience was the same as yours and my networking didn't work. Here is a quicker way to get things up and running again without waiting hours.

This is how i do it with my laptop, not desktop.
1.Power of the PC
2. Take battery out
3. Open lid, press and hold power button for 15 seconds. 
4. put the battery back in, plug in the power if you want and boot up. It should be working fine after that.

This does bring it back in Linux Mint too, but it just stops working again at some point. I decided to just run Windows on the laptop until there is a more permanent fix for this from Ubuntu. It's a brand new laptop and i don't want to risk permanent damage to the NIC.

---

### Post by kismeras on 2010-08-09
Quick question. Does anyone know if this is an issue with other Linux distros or just Ubuntu variants? 

I haven't seen any other forums with people having this issue other than Ubuntu and Linux Mint.

---

### Post by professordes on 2010-08-10
This still appears to be an issue (for me at any rate :) ) with the latest x86 -24 kernel in Lucid. I put an old HDD with Vista and Jaunty that had been sitting around onto a new i3 motherboard and then updated/upgraded everything in situ.

The problems (apparently dead ethernet after rebooting into Ubuntu) started after I had upgraded the driver in Vista to the one offered by Realtek and rebooted into Lucid. 

The suggested fixes - rolling back the driver and the WOL setting in Vista, powering off, restored connectivity. 

The MB is a Gigabyte  micro ATX GA-H55M-S2H and the ethernet chipset is definitely our RTL8111 friend....

---

### Post by Sylchat on 2010-08-15
Contributing to this post:

I have Asus P7P55D motherboard with Realtek "RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)", and Dual booting Windows 7 64 bits and Ubuntu 10.04 64 bits.

Network worked perfectly on both OSes when someday I realized that my transfer rate when copying a big file on Win7 from my SAN was really slow (1 MB/s). Back to Ubuntu, this was the same problem. As if my NIC was a 10Mb chip instead of a Gigabit chip... Same problem as Satosh:
> **satosh said:**
> My realtek nic rtl8111 (integrated on p7p55d-e) would only run in 10Mbps on either ubuntu lucid 64bit and win7. The cold boot (a couple of minutes off with no power plugged into the PC) worked. Thanks!

Anyway, I tried yingwuzhao's solution and now my LAN transfer copy is 36 MB/s (was 1MB/s) (Thanks!):
> **yingwuzhao said:**
> Simple power down you computer, and unplug every power sources, then wait for a couple of minutes, and start your computer again. The card will be alive again!

Also, I have read several posts on the internet, and I came up with the same conclusions that this realtek chip is crappy:
> **GenBattle said:**
> 
I would suggest the common factors are a 64-bit os/driver, dual-booting with Win7, and this realtek chipset (8168/8169/8139/8111) are to blame. It's also strange that the Asus P7P55 boards all seem to come up with this problem; but then they all share the same realtek chipset.

---

### Post by finalmike on 2010-08-28
Just for records sake, I just had this issue and unplugging for a few minutes and plugging back in fixed the issue. Thanks!!!

---

### Post by Fada.mahdi on 2010-09-26
Same problem here. I have Windows 7 Ultimate running. I partitioned Ubuntu, all my drivers work fine when running Ubuntu. But nothing works in Windows 7. its a direct result of Ubuntu. My sound, internet, and USB port drivers dont work at all in Windows now. I even removed Ubuntu yet still nothing works.

I have tried the power down method, no success. Now my computer is stuck. My only option is to try to wipe it out n reinstall my entire Windows 7 operating system again.

If anyone has any idea of a simpler way to fix this issue, please help me out.

Thanks!

---

### Post by rre12 on 2010-09-30
For the people who have just unplugged their computer for a few minutes and replug it back in. Did this permanently fix your connection problem? It seems that this only temporarily fixes my problem. Occasionally when I boot back onto Windows, my NIC card does not seem to be awake. So I had to redo the trick. This is very frustrating. I still think that this is the result of the wrong driver. Does anyone know if the dev team know about this major issue?

---

### Post by kwarde on 2010-10-09
Just had the same problem and unplugging the power brought back the network card.  Will see how it goes.  
Gigabyte board

---

### Post by shukle on 2010-10-12
This looks like bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573259](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573259) .
Yuo may want to pump the bug affects counters.

---

### Post by anty on 2010-11-25
Thank you so much!
I, too have the P7P55D-E motherboard and after a apt-get dist-upgrade the connection was gone and Windows 7 told me that there isn't a cable connected, too.

I draw the same conclusion as the starter of this thread, but removing the power cable for 2 minutes solved the problem!

---

### Post by linesma on 2010-12-13
> **sandrogalli said:**
> Hi, I can confirm that this is an issue for the Asus M4A785T-M onboard LAN, and is due to an incorrect driver loading with the 2.6.32-22-generic-pae kernel (may apply to other kernels also).

This is how I rectified the issue.

1. Check the model number of your ethernet controller:
```
$ lspci | grep Realtek
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/[COLOR="Red"]**8168B**[/COLOR] PCI Express Gigabit Ethernet controller (rev 03)
```

2. Check the driver your kernel is loading:
```
$ lsmod | grep r816*
[COLOR="Red"]**r8169**[/COLOR]                  91629  0
```

As you can see we have a [COLOR="Red"]**r8169**[/COLOR] driver for a [COLOR="Red"]**r8168**[/COLOR] chipset which is the cause of our issues.

3. Download the **8168** linux drivers from the [_Realtek_]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8111B/RTL8168B/RTL8111/RTL8168%3Cbr%3ERTL8111C/RTL8111CP/RTL8111D%28L%29%3Cbr%3ERTL8168C/RTL8111DP/RTL8111E%3Cbr%3ERTL8105E") website. Alternatively I have attached the correct driver to this post.

4. cd to Download directory and extract:
```
$ tar -xvf r8168-8.018.00.tar.bz2
```

5. Run script as superuser to autocompile driver:
```
$ cd r8168-8.018.00
$ sudo ./autorun.sh
```

6. [Optional] Test driver
```
$ sudo rmmod r8169
$ sudo modprobe r8168
$ sudo /etc/init.d/networking restart
```

Your network should be up and running with the new driver. To make the change permanent.

7. Blacklist r8169.
```
$ sudo gedit /etc/modprobe.d/blacklist.conf
```

Append the following lines:
```
# Blacklist Realtek RTL8111/8169 gigabit driver
blacklist r8169
```

Save and quit.

8. Update driver cache.
```
$ update-initramfs -u
```

REBOOT and see if the correct driver has loaded:

```
$ lsmod | grep r816*
[COLOR="Red"]**r8168**[/COLOR]                  91629  0
```

And everything should be just hunky-dory. ;)

I ended up having to follow your instruction, and it worked.  When I upgraded the kernel, it blacklisted the driver.  Thank you for this fix.  I was concerned, I have 3 machines running Ubuntu 10.10, and they were all affected.

---

### Post by anmg on 2010-12-31
I have checked my board ASUS P7P55D.
Chip is **RTL8112L** as mentioned in specification 

But this info according to AIDA64 report on W7x64:
**Realtek RTL8168D/8111D PCI-E Gigabit Ethernet Adapter (PHY: Realtek RTL8211/8212)	PCI**

Ubuntu is using driver:
**r8169 0000:02:00.0: eth0: link up**

So I do not switch system by reboot command, only shutdown.
After installing linux W7 sometimes do not load driver correctly even in case of reboot from windows to windows

I have downloaded driver from Realtek as recommends **sandrogalli**
After running script *autorun.sh*
following appeared in the logs
> r8169 0000:02:00.0: PCI INT A disabled
r8168 Gigabit Ethernet driver 8.020.00-NAPI loaded
r8168 0000:02:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
eth%d: RTL8168B/8111B at 0xffffc900050f4000, 90:e6:ba:30:e9:50, IRQ 46
r8168: eth0: link down
ADDRCONF(NETDEV_UP): eth0: link is not ready
r8168: eth0: link up
ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
r8168: eth0: link up

We'll check how it work now.

PS Update driver cache is compulsory!:  *sudo update-initramfs -u*
script *autorun.sh* renames r8169.ko to r8169.bak

As far as I understood r8169 is a defoult kernel driver for Realtek NICs and it may not fully support latest Realtek chips. That's why we have to compile driver supplied by Realtek to get fullt working device. Hope in next kernel version it will be fully fixed.


> **sandrogalli said:**
> 
As you can see we have a [COLOR="Red"]**r8169**[/COLOR] driver for a [COLOR="Red"]**r8168**[/COLOR] chipset which is the cause of our issues.

This is module names and does not mean anything

---

### Post by zigzag77 on 2011-01-08
Can we expect an official solution for Ubuntu 10.10 for the RTL8111 driver problem? 
Are the developers aware of this bug?

---

### Post by sarnold on 2011-01-10
Zigzag77, yes, the developers are aware: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573259](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573259)

Feel free to add details to the bug report: only _ONE_ user attached log messages. I suggest attaching a copy of your dmesg or /var/log/kern.log to the bug. Debugging without log files sucks. :)

---

### Post by zoey_s on 2011-01-29
Ubuntu (which I usually love) has really messed up things for my Toshiba Satellite Laptop too.  It was running beautifully; dual booting Windows XP and PCLOS, when I decided to replace PCLOS with Ubuntu 10.04.  Big Mistake!!  It ran fine for a day and then neither OS could get online.  My network is a Realtek RTL-8139/8139C/8139C+.  The command $ lsmod | grep r813* showed that Ubuntu wasn't loading the driver.  I booted into a PCLOS live cd and it loaded the necessary and correct driver, but couldn't connect to the internet.  I tried unplugging my laptop and removing the battery and when I put it back together again the laptop was messed up to where I couldn't get to grub.  At that point, I wiped the drive and did a clean install of Windows XP.  No internet for the fresh install.   I updated the Realtek driver, so now Windows shows that it is online; the little icon even blinks like it is connected, but I can't get online.  I can use wireless with the laptop, but that works only if I disable the cable connection.  I tried to set the driver to 'wake on lan' using the Windows device manager, but that option wasn't there.  I unchecked ' let Windows shut this down to save power', but it won't stay unchecked.  I know that this is an Ubuntu board, but I'm hoping that someone will be able to help me get XP back online.
       Thanks, zoey

---

### Post by xdevnull on 2011-01-30
I have a p7p55d-e pro and had the same problem.  I downloaded the drivers from realtek, unpacked and ran the autorun.sh and it fixed it -- apparently permanently as I can use both windows and ubuntu.  FYI windows definitely has something to do with the problem.  It is only after I logged out of windows and back into ubuntu that it was broken - and then broken for windows as well.  I'm not sure exactly what flag or setting it's doing but the realtek driver fixes it.

> **sandrogalli said:**
> Hi, I can confirm that this is an issue for the Asus M4A785T-M onboard LAN, and is due to an incorrect driver loading with the 2.6.32-22-generic-pae kernel (may apply to other kernels also).

This is how I rectified the issue.

1. Check the model number of your ethernet controller:
```
$ lspci | grep Realtek
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/[COLOR="Red"]**8168B**[/COLOR] PCI Express Gigabit Ethernet controller (rev 03)
```

2. Check the driver your kernel is loading:
```
$ lsmod | grep r816*
[COLOR="Red"]**r8169**[/COLOR]                  91629  0
```

As you can see we have a [COLOR="Red"]**r8169**[/COLOR] driver for a [COLOR="Red"]**r8168**[/COLOR] chipset which is the cause of our issues.

3. Download the **8168** linux drivers from the [_Realtek_]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8111B/RTL8168B/RTL8111/RTL8168%3Cbr%3ERTL8111C/RTL8111CP/RTL8111D%28L%29%3Cbr%3ERTL8168C/RTL8111DP/RTL8111E%3Cbr%3ERTL8105E") website. Alternatively I have attached the correct driver to this post.

4. cd to Download directory and extract:
```
$ tar -xvf r8168-8.018.00.tar.bz2
```

5. Run script as superuser to autocompile driver:
```
$ cd r8168-8.018.00
$ sudo ./autorun.sh
```

6. [Optional] Test driver
```
$ sudo rmmod r8169
$ sudo modprobe r8168
$ sudo /etc/init.d/networking restart
```

Your network should be up and running with the new driver. To make the change permanent.

7. Blacklist r8169.
```
$ sudo gedit /etc/modprobe.d/blacklist.conf
```

Append the following lines:
```
# Blacklist Realtek RTL8111/8169 gigabit driver
blacklist r8169
```

Save and quit.

8. Update driver cache.
```
$ update-initramfs -u
```

REBOOT and see if the correct driver has loaded:

```
$ lsmod | grep r816*
[COLOR="Red"]**r8168**[/COLOR]                  91629  0
```

And everything should be just hunky-dory. ;)

---

### Post by zoey_s on 2011-01-31
I installed the Realtek driver;  no joy.

I got XP online again by setting the network card under the advanced tab to linkspeed duplex mode  10 full.  
zoey

---

### Post by tstduke on 2011-02-07
I have an Asus P7P55d-e-pro board running dual boot Ubuntu 10.04 and Win 7. Exactly the same problem as others with no ethernet connection. 
 Unplugging all power for 3 minutes and then rebooting was the solution that worked for me also. Hope a fix is made available soon.

---

### Post by jocko on 2011-02-07
> **tstduke said:**
> I have an Asus P7P55d-e-pro board running dual boot Ubuntu 10.04 and Win 7. Exactly the same problem as others with no ethernet connection. 
 Unplugging all power for 3 minutes and then rebooting was the solution that worked for me also. Hope a fix is made available soon.
Same here with a gigabyte GA-P55-UD4 motherboard with a built-in RTL8111/8168B NIC.
I was starting to accept the idea of getting a new card when I finally found this thread... A cold reboot fixed it.

---

### Post by jazztickets on 2011-02-09
> **tstduke said:**
> I have an Asus P7P55d-e-pro board running dual boot Ubuntu 10.04 and Win 7. Exactly the same problem as others with no ethernet connection. 
 Unplugging all power for 3 minutes and then rebooting was the solution that worked for me also. Hope a fix is made available soon.

A fix will be released when the next version of Ubuntu comes out. Welcome to the wonderful world of Ubuntu.

---

### Post by ryannathans on 2011-02-17
Just letting ya all know that Ubuntu 10.04 LTS fryed my NICs almost 6 moths ago.

Gigabyte GA-P55a-UD5 (it has 2x RTL8111)

Had to buy another motherboard (exactly the same) and now wondering if it is safe to install ubuntu on it?

---

### Post by cacycleworks on 2011-02-18
> **sandrogalli said:**
> Hi, I can confirm that this is an issue for the Asus M4A785T-M onboard LAN, and is due to an incorrect driver loading

This is how I rectified the issue.
```
$ lspci | grep Realtek
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/[COLOR="Red"]**8168B**[/COLOR] PCI Express Gigabit Ethernet controller (rev 03)
$ lsmod | grep r816*
[COLOR="Red"]**r8169**[/COLOR]                  91629  0
$ tar -xvf r8168-8.018.00.tar.bz2$ cd r8168-8.018.00
$ sudo ./autorun.sh$ sudo rmmod r8169
$ sudo modprobe r8168
$ sudo /etc/init.d/networking restart
$ sudo gedit /etc/modprobe.d/blacklist.conf
[INDENT]# Blacklist Realtek RTL8111/8169 gigabit driver
blacklist r8169
[/INDENT]
$ update-initramfs -u
```
REBOOT and see if the correct driver has loaded:

```
$ lsmod | grep r816*
[COLOR="Red"]**r8168**[/COLOR]                  91629  0
```
And everything should be just hunky-dory. ;)

Yes!!!!! OMG thank you. I'm pretty experienced with Linux and this was totally vexing me.

> **kismeras said:**
> Quick question. Does anyone know if this is an issue with other Linux distros or just Ubuntu variants? 

I haven't seen any other forums with people having this issue other than Ubuntu and Linux Mint.

This affects all linuxes... I spent 2 full days ripping my hair out over this. My story is unique and interesting. I bought a used motherboard+cpu+ram from overclock.net. Motherboard is Asus Maximus III Gene. I got it, installed Fedora 14 (specifically the [Fusion remix]("http://fusionlinux.org/")) and all was well. 10.10's instability combined with Canonical's desire to dump Gnome have caused me to find a new distro. Fusion is awesome. It. Just. Works. And installs in about 1/3rd the time that Ubuntu does.

Then I work on my overclock and using a completely different hard drive, I install Windows Vista 32 bit to get all the HW monitoring tools and CPU-z sees my CPU at 4020MHz and doesn't report 2200MHz like linux does. (I hate it, so I always seem to have a license available) I get my overclock done then reinstall Fedora to dual boot with Vista. (Linux is my primary desktop)

No networking. But when I ran /etc/init.d/NetworkManager restart (Fedora's equivalent to Ubuntu's /etc/init.d/networking restart) it would come up. I tried putting it in /etc/rc.local, which did not work in either Linux. I went into the BIOS thinking that I broke something switching from IDE to ACHI mode. I tried acpi=off. I reinstalled a few times. I tried Cent-OS 5.5. I reran the CAT6 wiring. I tried a PCI ethernet adapter. Always the same. It would come up but I'd have to manually kick the networking after a boot-up. I automount remote directories, so I wasn't having it...

So I said screw it, I know Ubuntu so well, I can hack through anything. Plus, I was hoping that Ubuntu's VAST community would have found a solution. I found this page in my 2nd hour running ubuntu. Just for that, I'll probably hang out in Ubuntu-land for a while on this Desktop. I've got 10.04 LTS, so I'm hoping updates won't break this computer the way that 10.10 updates have broken others in my workplace. (They all get Fedora Fusion when that happens)

I say to everyone that the behaviors reported in this thread makes absolute sense from an embedded software / hardware standpoint. I did that professionally and have had the same situations happen to us. The "normal" way people code is to try as little as possible when programming a chip until it does what you want. And you ignore ALL other registers and settings. You know, all that stuff that shows up in lspci -vv and -vvv. More OCD/anal types will read the data sheet for the chip and decide which configuration for EACH and every setting is the best and program it that way. It's my professional opinion that the r8168 and r8169 are so similar as to be considered equivalent. Until someone who likes to be overly thorough (like me) comes in and sets EVERY register for a r8169 onto a r8168 and then it gets kinda mad.

Yaaay, awesome that this is the fix... Thanks!
Chris

---

### Post by Artemis3 on 2011-02-20
Nice rant. I have this same onboard NIC but haven't noticed anything yet. if it does, now i know to turn it off and unplug the lan for a while :)

And i do keep a 3com pci nic lying around just in case...

---

### Post by janpol on 2011-02-22
I had this issue with Slackware 13.1 64bit, Gentoo 64bit and Ubuntu 10.10 64bit, same symptoms as the OP (tried installing a Windows OS and had no connection over there either, and Windows 7 crashed after a while when this happened xD). But I think the OP panicked too quickly, I've noticed that this problem happens in a really random fashion, sometimes I had my connectivity back after a few hours, and sometimes after a few weeks :S (I had a usb wifi adapter, so I wasn't too worried about it).

In previous posts I've read that unplugging the power for two minutes solves the problem (never tried it), and also some people got it solved by installing the correct driver but I didn't try that either, I went for the easy fix. In my case, installing the 32bit version (with the PAE kernel, but the standard one should work too) solved the problem, so I thought that this was caused by a bug in the 64bit version of the driver (when I get the time, I'm going to take a look at this again).

I just wanned to point out that there's no reason to panic and think that your Ethernet card is dead, they don't even get really hot (like video cards), so I don't see how a driver could break it.

Regards!

---

### Post by jomom on 2011-02-22
Just had this happen with kernel 2.6.35-25-server, even though this 8169 driver is not available from the realtech site, it seems to keep getting snuck back into the kernel somehow.

---

### Post by cacycleworks on 2011-02-22
Did you blacklist it?

---

### Post by ryannathans on 2011-02-23
I am in need of installing linux once again on my desktop, however I have the affected NIC. 

What should I do to make sure I don't have to purchase another  motherboard again? Compile the new drivers and then blacklist the old?

I really don't want to buy another motherboard D:

---

### Post by cacycleworks on 2011-02-23
> **ryannathans said:**
> I am in need of installing linux once again on my desktop, however I have the affected NIC. 

What should I do to make sure I don't have to purchase another  motherboard again? Compile the new drivers and then blacklist the old?

I really don't want to buy another motherboard D:

Yes... do the steps I did in my post. You MUST have the files on a CD or usb stick... I was stupid and had them on our RAID (network share) so I had to go another computer with the usb stick to move it over. The install is super fast and as easy as the steps. Note: There will be an error thrown but it worked for me. Follow the steps, it's ok.

:) Chris

---

### Post by ankit singh on 2011-02-23
I also had this problem when i was dual booting winXP and ubuntu(don't know if that still exits,i am 100% ubuntu now,i had choose between XP and ubuntu because of this).I have a nvidia nforce NIC.When i installed ubuntu the NIC was working fine,and also was running fine in XP.However after subsequent boots ,NIC started working slower and slower in windows and then it finally completely ceased to work (only in windows and not in ubuntu,there was no performance decrement and it never stopped working in ubuntu).So as result connectivity on XP was completely lost.However i used to overcome this problem by reinstalling the NIC driver.Same was the problem with bluetooth dongle and my onboard sound card died on both XP and ubuntu

[SIZE="3"][SIZE="4"]Does running two different drivers for any hardware,destroys it?[/SIZE][/SIZE]

---

### Post by cacycleworks on 2011-02-23
> **ankit singh said:**
> [SIZE="3"][SIZE="4"]Does running two different drivers for any hardware,destroys it?[/SIZE][/SIZE]

Destroy? No. The real issue like I describe above is if obscure registers get set which other drivers (or other OS's drivers) don't know about or bother with ... AND at the same time, obscure register establishes a state where the card won't work as we want until the register is reset. 

Should all drivers be unable to twiddle that bit, then one could consider the hardware "bricked"; however this seem quite improbable as SOME driver knew about it to twiddle it! Plus... windows at least is very good about exposing advanced driver settings that we can experiment with. There, windwos is good for 2 things.

:) Chris

---

### Post by Nastybuzz on 2011-03-25
> **old_man_auz said:**
> I had the same problem.

My motherboard is a "Gigabyte 790XTA-UD4" with the same onboard network hardware as in the forum title. Network working fine in both Windows 7 and Kubuntu 9.10. I installed Kubuntu 10.04 overtop of Kubuntu 9.10 and the wired network wouldn't work. ALSO I couldn't connect to it with my wireless, which is a TPLINK wireless card of some sorts. I restarted back into Windows 7 to see if I could find some answers to my problems and BOTH the wired AND wireless hardware refused to work in Windows 7 as well.

I was beginning to panic, but as the guy said above, once I turned my computer off and unplugged everything from the wall for about 3 minutes and turned back on, the wired network is working again. I haven't tested the wireless yet.

this "unplugging" technique solved it for me, thank god. If i had to deal with wireless' instability anymore i was going to [insert awful deed here.] fyi this is my first post on ubuntu, CAUSE IM IN LOVE WITH UBUNTU AW YEA!:D

---

### Post by jazztickets on 2011-03-25
This is what irritates me about Ubuntu. You *know* that this issue won't be fixed until 11.04

---

### Post by ngoc on 2011-04-29
Hi guys,

I have the similar issue as you with a tiny difference. 

- dual boot wn7 x64 and buntu 10.04 x64 (did happen on 8.04 and 9.10)

I only lost my network's card on ubuntu. Win7 works as usual. There is nothing on ifconfig. The only way i found is to reboot ubuntu. I did not need to unplug the power.

One time !! after i let the computer power up, I've tried to reconnect via network manager, the connection was back.

Also, It changes nothing after changing the driver 8169 into 8168.

As some peole, i realise that my bandwith is slowing down sometimes. I was thinking it was my connection...

---

### Post by youngpatrick on 2011-05-03
I have compiled the correct linux driver 8.023.00 dated April 19, 2011 from Realtek web-site in Kubuntu 11.04/64bit system. It is ok for me to connect to Internet or my NAS. But the problem is the lan card transfer rate perform in 100mbps not in 1000mbps(gigabit). I have also tried to replace the cat6 lan cable. Unfortunately,it still work in 100mbps transfer rate. I wonder Realtek coded the win7 driver without any major issue but there are no bug-fix for linux system. I just only hope Realtek launch another linux driver for us to fix the issue :(


Patrick

_________________________
HP DM1-3000au w/AMD E350 CPU, 4G RAM, Netgear WNDR3700,

---

### Post by janpol on 2011-05-06
> **youngpatrick said:**
> I have compiled the correct linux driver 8.023.00 dated April 19, 2011 from Realtek web-site in Kubuntu 11.04/64bit system. It is ok for me to connect to Internet or my NAS. But the problem is the lan card transfer rate perform in 100mbps not in 1000mbps(gigabit). I have also tried to replace the cat6 lan cable. Unfortunately,it still work in 100mbps transfer rate. I wonder Realtek coded the win7 driver without any major issue but there are no bug-fix for linux system. I just only hope Realtek launch another linux driver for us to fix the issue :(


Patrick

_________________________
HP DM1-3000au w/AMD E350 CPU, 4G RAM, Netgear WNDR3700,
Does it run at 1Gbps in Windows? What about the other end of the cable? Does that device run properly at 1Gbps?

I think that you are trying to say that it works fine under Windows, but it doesn't hurt to ask :P

---

### Post by youngpatrick on 2011-05-20
> **janpol said:**
> Does it run at 1Gbps in Windows? What about the other end of the cable? Does that device run properly at 1Gbps?

I think that you are trying to say that it works fine under Windows, but it doesn't hurt to ask :P



On today I have re-installed Windows 7-64bits version on HP DM1-3000au to verify the Realtek RTL8168 Rev.6 gigabit lan card problem. After updating the Win 7 lan card driver downloaded either from HP or realtek web-sites, the problem is still there. The Netgear WNDR3700 router detect the signal at 100Mbps using cat6 cable I used. Certainly, the router can detect my desktop PC (built in Atheros AR8121 family chipset) and NAS in gigabits signal even though I connect its with cat5e lan cables. Surely, my linux desktop transfer the files from NAS in 65~ 94MBits/s via FTP service. That is I confirm my router is in good condition. I am curious whether using cat6e lan cable will fix the problem or not. Please advise.

Thanks,

Patrick

---

### Post by Bealer on 2012-03-17
This has just happened to me running 11.10.

I've tried the r8168 drivers and a hard reboot but no luck. I can see the eth0 device in Ubuntu, it just won't connect to anything.

---

### Post by ttguy on 2012-03-18
> **Bealer said:**
> This has just happened to me running 11.10.

I've tried the r8168 drivers and a hard reboot but no luck. I can see the eth0 device in Ubuntu, it just won't connect to anything.
if you can see eth0 then you do not have the problem that is the subject of this thread

---

### Post by cacycleworks on 2012-03-19
FWIW, on this same desktop I mention in the thread, 11.10 won't even boot up from CD or USB. I'm still using Ubuntu 10.04 LTS on it and thankfully, it's been there for me every day.

PC Linux OS installs easily and everything works without issue... probably end up switching. :P

Chris

---

### Post by wnelson on 2012-03-20
Did you do the following when compiling the r8168 drivers.

make clean; make; make install; depmod

Walt

---

### Post by cacycleworks on 2012-03-20
I either did sudo ./autorun.sh OR I read the download's INSTALL file (if there is one) and did that. I'm thinking I did exactly like the guy I quoted did.

---

### Post by Birdman2010 on 2012-03-20
I followed the instructions that I quoted below several times, but the steps corrupted my persistent file. I am running Linux Mint off a USB drive. The instructions below, though, did help point me in the right direction. It turns out that I simply have to "blacklist" the 8169 driver!

So, here are the steps that I followed. They seem to work even after rebooting my machine.


Google "Realtek" and download the Ethernet driver directly from the Realtek website.
Click Menu | Places | Downloads and right-click on the Realtek driver and select "Extract Here"
Open a terminal window and use these commands. The commands are case sensitive. "cd downloads" will NOT work:
cd Downloads
cd r8168-8.028.00 [Edit: the folder name will change with new versions. Type dir and hit enter to see available folders]
chmod +x autorun.sh [Edit: this makes the script executable]
sudo ./autorun.sh [Edit: this executes the script as root

Now, here are more critical steps. You have to "blacklist" the 8169 or it will be reloaded on your next bootup and KILL your Internet connection! (conflicting drivers)

In the terminal window, type this command:
sudo gedit /etc/modprobe.d/blacklist.conf

When you hit Enter, a editor window will open the blacklist.conf file for you to edit. Go to the very bottom and add these two lines
# Blacklist Realtek RTL8111/8169 gigabit driver
blacklist r8169

Close the editor window. It will ask you if you want to save the changes, hit Save .

Once I did these steps, my Realtek ethernet connection ran perfectly. More importantly, I was able to reboot and the Internet still worked. The key is that I had to blacklist the defective driver (8169).

> **cacycleworks said:**
> Yes!!!!! OMG thank you. I'm pretty experienced with Linux and this was totally vexing me.



This affects all linuxes... I spent 2 full days ripping my hair out over this. My story is unique and interesting. I bought a used motherboard+cpu+ram from overclock.net. Motherboard is Asus Maximus III Gene. I got it, installed Fedora 14 (specifically the [Fusion remix]("http://fusionlinux.org/")) and all was well. 10.10's instability combined with Canonical's desire to dump Gnome have caused me to find a new distro. Fusion is awesome. It. Just. Works. And installs in about 1/3rd the time that Ubuntu does.

Then I work on my overclock and using a completely different hard drive, I install Windows Vista 32 bit to get all the HW monitoring tools and CPU-z sees my CPU at 4020MHz and doesn't report 2200MHz like linux does. (I hate it, so I always seem to have a license available) I get my overclock done then reinstall Fedora to dual boot with Vista. (Linux is my primary desktop)

No networking. But when I ran /etc/init.d/NetworkManager restart (Fedora's equivalent to Ubuntu's /etc/init.d/networking restart) it would come up. I tried putting it in /etc/rc.local, which did not work in either Linux. I went into the BIOS thinking that I broke something switching from IDE to ACHI mode. I tried acpi=off. I reinstalled a few times. I tried Cent-OS 5.5. I reran the CAT6 wiring. I tried a PCI ethernet adapter. Always the same. It would come up but I'd have to manually kick the networking after a boot-up. I automount remote directories, so I wasn't having it...

So I said screw it, I know Ubuntu so well, I can hack through anything. Plus, I was hoping that Ubuntu's VAST community would have found a solution. I found this page in my 2nd hour running ubuntu. Just for that, I'll probably hang out in Ubuntu-land for a while on this Desktop. I've got 10.04 LTS, so I'm hoping updates won't break this computer the way that 10.10 updates have broken others in my workplace. (They all get Fedora Fusion when that happens)

I say to everyone that the behaviors reported in this thread makes absolute sense from an embedded software / hardware standpoint. I did that professionally and have had the same situations happen to us. The "normal" way people code is to try as little as possible when programming a chip until it does what you want. And you ignore ALL other registers and settings. You know, all that stuff that shows up in lspci -vv and -vvv. More OCD/anal types will read the data sheet for the chip and decide which configuration for EACH and every setting is the best and program it that way. It's my professional opinion that the r8168 and r8169 are so similar as to be considered equivalent. Until someone who likes to be overly thorough (like me) comes in and sets EVERY register for a r8169 onto a r8168 and then it gets kinda mad.

Yaaay, awesome that this is the fix... Thanks!
Chris

---

### Post by Bealer on 2012-03-29
> **ttguy said:**
> if you can see eth0 then you do not have the problem that is the subject of this thread

I do actually have the problem that this thread is talking about.

From the OP, I had everything working just like he did, and now get nothing, only an orange light from the adapter (indicating a slow connection). It doesn't work in Windows or Linux. 

I installed R8168, but still no luck in actually getting it to fully function. I can see eth0 via ethtool but can't get it to respond. Even hard power off's don't work.

The nic is either dead or in a completely dormant state. This all happened when using 11.10. On 11.04 I had been fine, I recently upgraded (in the last 3 weeks) to 11.10 and that's when it happened.

---

### Post by cacycleworks on 2012-03-31
I'd suggest running 10.04 live CD and attempt installing the driver again. Maybe that will unstick the controller.

---

### Post by Jan Greeff on 2012-06-04
When I read these posts I thought that my problems were solved, but alas! 

Both computers on my home network have accessed my HP 6313 all-in-one printer via the     existing connections recently. A pattern that has established itself     is that one seems to disconnect the other. 
    
    When computer no. 1 was running on Ubuntu 11.04 it could print, but only when no. 2 was powered off.     Then, when I installed 12.04 on machine no. 1 it could no longer     print or connect to the router, but no.2, running on Ubuntu 11.04  did manage to access the     router and to print when no. 1 was powered off. 
    
    So previous to Ubuntu 12.04, no. 1 lost contact with the printer     when no. 2 was running, now no. 2 loses contact when no. 1 is running.  
    
    The guys at launchpad are trying their best to help, but to no avail     as yet. Hopefully this will help them get on track also. 
    
    Does anyone have any ideas about where I should go from here?

---

### Post by cacycleworks on 2012-06-04
I'm wondering if you need a new router... I've recently had lots of unexplained phenomena cured by new network hardware, which particularly annoys me... shouldn't that stuff always work? :P

---

### Post by Skara Brae on 2012-06-04
This thread reminds me of a PC that I once had with Windows (Millennium?) and Mandrake (9?) in dual boot.
After a Mandrake session, internet wouldn't work in Windows. That was years ago; in 2004.

---

### Post by Jan Greeff on 2012-06-05
Thanks, could be but it is a new router and the old one did the same...the only difference being that I could print eventually after reinstalling the printer a few times, until I upgraded to 12.04 - since then there is NO printing being done on this machine.   I must add that the new router's manufacturer states that the software (which I obviously did not use) is not Linux compatible.

---

