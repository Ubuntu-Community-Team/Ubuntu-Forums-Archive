---
title: "Ubuntu on Dell Studio 17"
date: 2008-07-31
forum: Hardware
---

### Post by appleno on 2008-07-31
Howdy Folks!
I'm having no end of problems with the above combo, mainly due to the ATI video card and WiFi.
If I install the 32Bit ubuntu, I can get the wireless to work with the windows drivers and ndiswrapper, but with the 64Bit version, ndiswrapper will cause the kernel to hang.

The other problem I'm seeing is with the ATI Radeon card - It's terrible. I just get a black screen if using Driver "radeonhd", and if I install the fglrx driver, again I get kernel crashes (even with building the official ati driver).

Finally, the touchpad doesn't do VertTwoFingerScroll, despite the manpage saying it is supported.

Has anybody tried ubuntu on this new dell machine? (I don't think dell bothered :) )

thanks for reading!

---

### Post by kentonspr on 2008-08-01
I've got it running on my Studio 15. I'm using Kubutnu w/KDE4.1.

I was getting some grief with the 64 bit system, so I switched to 32. I've got wireless working using the ndiswrapper and I've got the closed ATI drivers working as well. So far so good on my end. 

The touchpad scrolling doesn't work for me or most of the capacitive touch buttons, but I'm working on getting all of that taken care of.

---

### Post by coffeeaddict22 on 2008-08-07
My Studio 17 is working fine.  I've got the 32 bit version; wireless running fine on ndiswrapper.  Hadn't had any video card issues at all, running the proprietary drivers off the repository.

Bought a wireless mouse with it- fingers are too fat for prolonged touchapd use, so can't comment on the scrolling issue. The fingerprint reader would be nice, but only 'cause I'm getting lazier...

---

### Post by exit3219 on 2008-08-07
I'm interested in the Studio 15. Do you mind posting the lspci?

---

### Post by sunnycloud on 2008-08-23
Hi everybody,

I'm planning to buy a Dell Studio 17 and I would say that feedback on ubuntu running on it is rather scarce on the web!  This is about the only post I found about it.  I would particularly like to be reassured about the **ATI Mobile Radeon 3650HD** graphic card.

All feedback will be greatly appreciated :)

---

### Post by sunnycloud on 2008-08-24
Anybody outhere...  ? :-?

---

### Post by davekra on 2008-08-24
I've got Hardy working on my Dell 1735.  Took a couple weeks.  Using ndiswrapper and Radeon vesa driver.  It also worked with the Radeon fglrx but it seemed that when I tried to shutdown it took almost 20 seconds to get the shutdown screen.  It still takes longer than I'd like but it's ok.

One thing that newbies should be told is to right click on the menu and "edit menus".  There are many tools that aren't displayed by default.  One in particular is the "control center".  I'm no Unix guru but along with 4 co-workers we support almost 140 Solaris servers.  But dealing with video drivers and network drivers that don't work is humbling.  We run Solaris on Sun machines so all the driver stuff is already figured out.  None of them have video cards, just terminal connections.

Anyway, if anyone wants a printout of some system setting just let me know.

Thanks for all the great info on the boards.
davidk

lspci output:
:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobilitiy Radeon HD 3650
01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

---

### Post by sunnycloud on 2008-08-25
> **davekra said:**
> I've got Hardy working on my Dell 1735.  Took a couple weeks.  Using ndiswrapper and Radeon vesa driver.  It also worked with the Radeon fglrx but it seemed that when I tried to shutdown it took almost 20 seconds to get the shutdown screen.  It still takes longer than I'd like but it's ok.


Thanks for the tip davekra, I'll be sure to try this on mine (arriving in a couple of weeks :)) and I'll give feed back as well of my experience.

---

### Post by janascii on 2008-08-25
I'm going to be purchasing the studio 17 this week hopefully( just need to make sure the bank doesn't block the purchase).  Anyway I'll post on here about my progress once I get it in.  I've been fighting with graphics drivers long enough that I should be able to figure it out.

---

### Post by davekra on 2008-08-26
Ok, I just reloaded my machine.  Bad choices on partition size and gparted had a small problem.

The networking found the wireless card with no additional drivers.  The grafix card was found as generic and I had too enable the ATI driver in "Hardware Drivers".  Both ATI and WL are "in use".  Right click on the applications menu and "edit menus".  Under "other" enable "screens and graphics".  Go to Applications, Other, Screens and graphics, Graphics card.
Click on Driver and select fglrx.  Go back to the Screen tab and select Generic, LCD Panel 1920x1200.  Select Widescreen monitor and click ok.  You'll have to reboot and it may come up in reduced resolution.  Just go back and select the Generic LCD panel again.

Good luck,
davidk

---

### Post by pelle.k on 2008-08-30
Bump. I'm interested in how everything works out for ya. With these workarounds, is it stable? How about suspend/hibernate?
I greatly appreciate your input!

BTW, why don't you guys install from the dell iso's?
[http://linux.dell.com/wiki/index.php/Ubuntu_8.04](http://linux.dell.com/wiki/index.php/Ubuntu_8.04)

---

### Post by XxLeekxX on 2008-08-31
I've had nothing but trouble with Radeon HD 3650 (I also have Dell studio 17).  I'm just using the restricted driver because the closed source drivers of ATI are just plain horrible.  I heard recently that ATI is going to add more support, but I honestly do not have time to wait.  For wireless, I had to upgrade my kernel for wifi to work.  This is even a bigger dillema for installing closed source driver, because the closed driver conflicts with the kernel (which is 2.6.24-21-generic).  Since i'm using open source driver, my suspend and hibernate modes do not work.  But on the bright side, my wow on wine is having great frame rates.  So in short: if you're getting studio 17 with Radeon HD 3650, expect problems.

---

### Post by pelle.k on 2008-09-01
Hmmm. Maybe you should've gone with ndiswrapper and the standard kernel?
I had a chat with a bloke at the arch linux forums, and his studio 17 is just working just peachy (arch being bleeding edge and all of that), so maybe intrepid will be a better fit for the studio 17?

---

### Post by XxLeekxX on 2008-09-02
I would use Ndiswrapper but I don't know where to get the driver from.  I went to the dell support site and downloaded it (R186036.exe) but it won't work.  I searched in the driver disc that was provided, but still no success.  I even downloaded the driver from HP site (sp39243.exe).  It works but the signal is extremely weak.  If anyone can tell me where to get driver, I'd greatly appreciate it.

---

### Post by pelle.k on 2008-09-02
Did you blacklist the "in kernel" driver? (bcm43xx)
btw, take a look at this guide; [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
From the lspci from davekra one week ago (if you have the same hardware) step 2b seems to be appropriate. btw, the driver in that step is gone from the ftp server, but i think this is the same one; [http://h50176.www5.hp.com/local_drivers/24256/sp33008.exe](http://h50176.www5.hp.com/local_drivers/24256/sp33008.exe)

---

### Post by XxLeekxX on 2008-09-02
Yes I've done that, and I've also tried the driver you provided, but it does not work.  I guess I'll have to keep looking.  BTW: my card is BCM4322 Rev 01

---

### Post by pelle.k on 2008-09-03
Oh. Then the driver i pointed to wouldn't work (most likely), because i thought you had a 4312.

BTW, **did you blacklist b43 AND ssb** when you tried loading ndiswrapper drivers (reboot required), because i just read that bcm43xx is blacklisted by default anyway (replaced by b43 and ssb obviously...)

And last of all, did you try the native driver? (blacklisting b43 and ssb still required)
```
wget http://www.broadcom.com/docs/linux_sta/hybrid-portsrc-x86_32_5_10_27_6.tar.gz
tar -xvf hybrid-portsrc-x86_32_5_10_27_6.tar.gz
cd hybrid-portsrc-x86_32_5_10_27_6
make -C /lib/modules/$(uname -r)/build M=$(pwd)
sudo modprobe ieee80211_crypt_tkip
sudo insmod wl.ko

```

---

### Post by XxLeekxX on 2008-09-03
I think so, I followed this guide as I was installing the HP driver (the one I said gives low signal) [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

The guide I'm using right now to enable BCM4322 is [http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

I'm forced to upgrade kernal to 2.6.24-21-generic.  So When I'm installing the ati driver, there is trouble because there is no support for this kernal.

---

### Post by pelle.k on 2008-09-03
Allrighty then. tough luck!
Might i suggest you install envyng-gtk, and install the ati driver through that?

---

### Post by davekra on 2008-09-03
Ya know...even though I had success loading my 1735 I'm having problems now.  I initially loaded it on a drive I bought from Newegg.  Trying to boot with the Live cd and the original Dell hdd fails.  It seems the drive is either not being found or the adapter is having trouble negotiating an interface speed.

Does Dell do anything to their drives that would only let Vista load?  This is happening on two drives from Dell.  I requested a replacement because the first was not being seen by the bios.  The replacement is being found but still wont let Ubuntu Live load.

Anyone got any ideas?

Thanks,
davidk

---

### Post by XxLeekxX on 2008-09-03
Yeah Pelle.K I've also already tried envy, haha (kernel problem again :P).  Thanks for your help I really really grateful.  Oh and dave, I'm not a pro or anything, and hopefully someone will comment on my advice I'm about to give you.  But you could try installing the dell Ubuntu ISO that Pelle.k suggested: [http://linux.dell.com/wiki/index.php/Ubuntu_8.04](http://linux.dell.com/wiki/index.php/Ubuntu_8.04)

---

### Post by davekra on 2008-09-04
I'll give the Dell image a shot.  
It's strange though that Hardy loaded fine with the non-dell drive.  If the Dell drive is hdd1 or 2 it has problems.  And two separate drives had the problem...that's why I thought, maybe, Dell is doing something to try to keep us from leaving the evil empire that is Microsoft.  
Booting Ubuntu from the first drive, with the Dell one as hdd2, gives errors about that second drive.  The interface is responding slow, or if it does find the drive it says the speed is restricted.  

Anyway, if anyone thinks of anything else please let me know.
Thanks,
davidk

---

### Post by tom72 on 2008-12-19
Hey all,
I thought I might give an update to this thread. I recently bought a Dell Studio 17 (the 1737 in fact) and installed Ubuntu 8.10 on it. Everything worked out of the box. The laptop has two 256GB hard drives of which I used the unused one to install Ubuntu on (dual boot with Vista).
Wifi, graphics card etc, worked out of the box. The only thing not working is using a headset. I tried to manually install the latest ALSA stuff (by using the beta drivers from the ALSA website) but that somehow didn't work. It's still possible to use a headset although it doesn't prevent sound output from the built-in speakers.
Apart from that everything else works perfect.

/t

---

### Post by pelle.k on 2008-12-19
Well, thankyou very much tom72. Appreciate you taking the time to give us an update.

---

### Post by ProfDecoy on 2008-12-21
That's good news tom72.  I recently had to send my Inspiron E1705 back to Dell for repairs on multiple issues, and they're sending me a Studio 1737 as a replacement because they don't have the parts to fix my '1705.  The two drive on it is nice, not sure if my replacement is coming with two HDDs or not (probably not).  This might be an interesting adventure.

I was concerned that I might have issues with 8.10 on the new system (it's coming with Vista on it, ick.  I was dual booting Ubuntu 8.04 and XP on the old system).  At least Dell says that this system will support 4GB of RAM unlike the 1705 (which only officially supported 2GB, but would recognize 4GB installed but would only make 3GB available).  Would be nice if it could take 8GB like my Laditude 630 from work (Which will probably see 8.10 or 9.04 on it in the coming months).

---

### Post by Leuenberg on 2008-12-29
> **tom72 said:**
> [...]The only thing not working is using a headset.

I'm trying to remove this crappy Vista on my own Studio 1737 and configuring a Linux/XP dual boot. And the headset is also not working properly with XP... guess we'll have to wait for a proper driver.

---

### Post by tom72 on 2008-12-30
> **Leuenberg said:**
> I'm trying to remove this crappy Vista on my own Studio 1737 and configuring a Linux/XP dual boot. And the headset is also not working properly with XP... guess we'll have to wait for a proper driver.
Yeah thats really annoying. After doing the first, fresh install of Ibex on the 1737 I read through the various threads here helping with the audio drivers on laptops. I installed the latest ALSA drivers manually and followed the steps outlined in one of those threads but that didnt work. The sound was totally gone afterwards. After playing around for a couple of hours I resigned - even uninstalling and installing the original ALSA drivers didnt work so I reinstalled Ubuntu and I'm now scared as hell of trying out any 'manual' sound installations.

---

### Post by rogde on 2009-03-22
Hi Guys. I installed ubuntu intrepid on my Studio 1735 yesterday, before I had used preinstalled Vista for half a year. I'm totally new to Linux, but still it all worked out relatively smoothly, thanks to the good Ubuntu wikis on the web. The basics are sorted, but there are a few big BUTS:
[LIST]
[*] I can't get my **Bluetooth headset** Sony-Ericsson HBH-PV708 to run. Did u have any probs with the Bluetooth adapter?  "sudo hciconfig hci0 revision" is mising the "SCO mapping: HCI" info. Any experience with that? 
[*] I can't get GoogleEarth to run. It seems to be a problem with the ATI driver. Can't figure out solution yet. I suspect its a driver bug. Which driver do you use? The** ATI FGLRX **one or are there better ones? Any ideas?
[*] I can't get Windows stuff (**Sketchup**) proper with WINE. But as I want to use only one OS I would like to run all my graphics software here. How do you run your win apps?
[*] Fortunately I don't use wireless, so I don't have to worry at least about that for the moment
[/LIST]
I was really keen to try Ubuntu out, and surprised how easy it was to get the basic thing up and running. But I'm pretty frustrated now about this stuff. Any help / experiences appreciated.

---

### Post by pelle.k on 2009-03-22
> I can't get GoogleEarth to run. It seems to be a problem with the ATI driver. Can't figure out solution yet. I suspect its a driver bug. Which driver do you use? The ATI FGLRX one or are there better ones? Any ideas?
It is a driver bug. Turn off desktop effects, or try the free "radeonhd" variant. The "radeonhd" is not very fast in intrepid, but should be much improved in jaunty, while the propreitary fglrx probably suffers from the same problems it always has, until ATI starts building it on the same technology as the "radeon(hd)" developers are. I dont knwo if this problem is fixed in recent fglrx versions though.
> I can't get Windows stuff (Sketchup) proper with WINE. But as I want to use only one OS I would like to run all my graphics software here. How do you run your win apps?
Wine does run certain windows applications (you may try a more recent version from winehq), but for more advanced applications i prefer virtualbox (the "non-free" version) directly from Sun (yes, they have debs/repo).
> ortunately I don't use wireless, so I don't have to worry at least about that for the moment
It's not that hard, actually. But because of some of the chipsets dell use, the free drivers don't work. However with jaunty, more chipsets may be supported. I find ndiswrapper to be fairly easy to setup with ndisgtk though (for use with windows wireless drivers).

---

### Post by cknight on 2009-06-16
Just another update for folk out there considering this laptop.  Got mine about a month ago, wiped Vista within a day and installed Jaunty 9.04.  Wireless, sound, backlit keyboard (oh so excellent), touchpad, suspend, hibernate, in-built webcam and multi-head display all worked out of the box.

My only caveat is that I'm using the open source ATI driver.  I did play around very briefly with the closed source fglrx driver, but found it a bit buggy.  Specifically:

[LIST][*]window maximizing and minimizing had a delay on it (however, this post may provide a fix: [http://ubuntuforums.org/showpost.php?p=7376252&postcount=6](http://ubuntuforums.org/showpost.php?p=7376252&postcount=6)) [*]Screen wouldn't power on after suspend resume (though I bet this can be relatively easily fixed)[*]Account switching can cause kernal crashes, screen freezes and screen blanks[*]General lack of snappiness[/LIST]

As I don't use compiz, I've stuck with the open source driver, which I've been very happy with.  All in all, its a great laptop which I've been very happy with and impressed at Ubuntu's performance on.

---

### Post by pelle.k on 2009-06-17
> As I don't use compiz, I've stuck with the open source driver
If you do feel you're missing out on some things (docky / awn / window shadows), you can activate the "gnome compositor" even with the open-source driver. It hasn't got a desktop cube, nor cool minimize/maximize effects, but you can run, say docky, and you also get window shadows :)
You **HAVE TO** disable it before activating compiz in the future though. If you don't compiz will just throw an undescriptive error at you.

Open gconf-editor ("configuration editor" in the "system tools" menu), navigate to **/apps/metacity/general** and activate **compositing_manager**.

---

### Post by cknight on 2009-06-17
> **pelle.k said:**
> 
Open gconf-editor ("configuration editor" in the "system tools" menu), navigate to **/apps/metacity/general** and activate **compositing_manager**.
Cheers for that.  It works a charm.  The extra gloss is rather nice and I'm not seeing any performance degradation, so it stays :)

---

### Post by cknight on 2009-06-17
> **appleno said:**
> Finally, the touchpad doesn't do VertTwoFingerScroll, despite the manpage saying it is supported.

The Studio 17's come with Alps touchpads.  This is not the same as Synaptics touchpads, though the Alps can use the synaptics drivers just fine.  The "AlpsPS/2 ALPS GlidePoint" touchpad doesn't have multi-touch, which is a shame, though it has a really nice feel to it and superior to my previous synaptics touchpad.  

However, I have successfully configured my touchpad to do vertical two finger scrolling. See [this post]("http://ubuntuforums.org/showthread.php?p=7474290#post7474290") on cofiguration of the Alps Glidepoint touchpad.

---

### Post by Denimaka on 2009-10-02
Hi folks, 
So, I am going to buy Dell Studio 17 soon, what is your advice after having so much experiences working with this machine?

I used to play with Ubuntu, Fedora, Open SUSe on my previous Compaq Presario laptop, and it was quit easy. Now I do know what to buy, AMD or Intel, HP, Compaq or Dell? 
Please helpppppp :confused:

I really need asap comments, coz I hate Windows and unfortunately now i am with it

---

### Post by tom72 on 2009-10-03
Ubuntu 9.04 works without any problems on my machine (Dell Studio 1737). Installation went without any trouble and I have never experienced any serious issues. The only minor thing I've come across was that when I closed the laptop while it was running it didn't recover from hibernation (panel stayed black). Apart from that I'm happy with my Dell Studio

Tom

---

### Post by TidyBhoy on 2010-03-23
Giving up on ubuntu... Very regretably! I've found it a constant annoyance on my Studio 17! Especially graphics issues! I'll check back every now and then cause the tireless work people do makes ubuntu get better and better! But for now I'll hold off a while! Till ubuntu improves or I buy a better laptop ha!

---

### Post by voldemorte on 2010-06-05
I plan on buying a Dell Sudio 17 but I have not opted for the ATI Graphics, instead I've opted the Intel HD graphics.
I want to know whether there are any Graphics driver issues with this option. I want compiz enabled with all its eye-candy in all its glory.
Please reply if anyone uses such a configuration or if I'll face any likely problems with graphics drivers for Intel HD.
Is it necessary to add that I'm a newbie to linux?

Thank you in advance.

---

