---
title: "Ubuntu 11.04 compatability with HP dv6t laptop."
date: 2011-05-12
forum: Hardware
---

### Post by PhantmKllr on 2011-05-12
I'm in the market for a new laptop, and this time around, I think that I'm going with an HP.

The model I'm looking at is an HP Pavilion dv6t Special Edition, with an Intel 2nd generation i5-2540M processor, and the Intel HD Graphics 3000.

I'd like to know if anyone has had experience with Ubuntu and this HP laptop model, or the Sandy Bridge chipset in general. I'm specifically worried about the graphics and the WiFi. I'm not sure how well the new HD Graphics 3000 will work with Ubuntu. Also, I don't even know if the WiFi will work, as I don't know what wireless card ships with the laptop.

---

### Post by erikschmitz on 2011-05-12
I have an HP DV6T-6000 Quad Edition, which is very similar. Mine has the Radeon 6770M in it. Wireless works fine in Ubuntu. The HD 3000 works well too... it runs Unity and can do compiz effects. 

The Radeon causes all kinds of problems, actually, due to the switchable nature and a race condition with the open source driver..

---

### Post by screaminj3sus on 2011-05-12
My sandy bridge laptop works great for the most part (Asus U52F, Intel I5 460M) I had sound and suspend didn't work by default but were easily fixable. Graphics wise intel graphics have been perfect.

---

### Post by dl330 on 2011-05-24
> **erikschmitz said:**
> I have an HP DV6T-6000 Quad Edition, which is very similar. Mine has the Radeon 6770M in it. Wireless works fine in Ubuntu. The HD 3000 works well too... it runs Unity and can do compiz effects. 

The Radeon causes all kinds of problems, actually, due to the switchable nature and a race condition with the open source driver..

Did you end up just disabling the Radeon graphics card within the BIOS?

---

### Post by erikschmitz on 2011-05-25
no, my bios does not have any options to disable the radeon.

instead, I put "blacklist radeon" in /etc/modprobe.d/blacklist.conf

then added the following to rc.local

```
modprobe radeon
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```

this disables the radeon during boot (to avoid a race condition), then renables it at startup and turns the radeon card off to stop it from using power.

---

### Post by lawrencesilva on 2011-06-25
hi there! would just like clarify: when you said "renables it at startup and turns the radeon card off to stop it from using power." 

did you mean natty renables Intel HD Graphics  and disables the radeon 6770m at startup?  

if that would be the case, will ubuntu gui still use the radeon gpu or just let it sit there and do nothing?

any comment from you, would be greatly appreciated.

thanks in advance man!  

-lawrence

> **erikschmitz said:**
> no, my bios does not have any options to disable the radeon.

instead, I put "blacklist radeon" in /etc/modprobe.d/blacklist.conf

then added the following to rc.local

```
modprobe radeon
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```this disables the radeon during boot (to avoid a race condition), then renables it at startup and turns the radeon card off to stop it from using power.

---

### Post by Yellow Pasque on 2011-06-25
The radeon will not be used, but it will not consume battery either.

---

### Post by lawrencesilva on 2011-06-25
oh that's a bummer, is there another way around? i mean, can i set it to exclusively use the radeon gpu and turn off the intel hd graphics instead?

thanks!!!

> **Temüjin said:**
> The radeon will not be used, but it will not consume battery either.

---

### Post by sgtguthrie on 2011-06-29
> **lawrencesilva said:**
> oh that's a bummer, is there another way around? i mean, can i set it to exclusively use the radeon gpu and turn off the intel hd graphics instead?

thanks!!!

I would like to know this too...

---

### Post by cbennett926 on 2011-08-06
Hey, I know this has been dead for a while but, if you keep it all intel how does this work? I am looking at this exact laptop as well

---

### Post by egandt on 2011-09-21
I have this same notebook, and lets just say its not looking for for Ubuntu on it.  First off it will only use a SVGA driver, it does not find the Intel or the ATI card as present on the system, so the X experience is useless.  I can not find any way to force it to use one or the other card, as they are both present, but neither works :-(

/sys/kernel/debug/vgaswitcheroo/switch does not exist on this system at all, so no hope playing with that, I've black listed and uninstall the ATI drivers, that did nothing to help either.

Simple put the X display on this notebook is completely useless at this time, I'm still playing around to see if it can be fixed, but I'm not counting upon it.

ERIC

---

### Post by sgtguthrie on 2011-09-21
> **egandt said:**
> I have this same notebook, and lets just say its not looking for for Ubuntu on it.  First off it will only use a SVGA driver, it does not find the Intel or the ATI card as present on the system, so the X experience is useless.  I can not find any way to force it to use one or the other card, as they are both present, but neither works :-(

/sys/kernel/debug/vgaswitcheroo/switch does not exist on this system at all, so no hope playing with that, I've black listed and uninstall the ATI drivers, that did nothing to help either.

Simple put the X display on this notebook is completely useless at this time, I'm still playing around to see if it can be fixed, but I'm not counting upon it.

ERIC

I also have this laptop, and have no problems after following the instructions in post 5 of this thread, have no problems. It's worked for every distro i've tried except pclinuxos. 

The problem is that when hp put the laptops together, they modified the Radeon driver. For this reason, the fgrlx driver from ati doesn't work, as linux thinks it's a different model than it is. Ati says that because hp modified the driver, hp would have to release a linux driver for it, which I believe they have no intentions of doing. 

Either way, the sandy bridge graphics work just fine, so once you disable blacklist the Radeon card, and disable switcheroo, you should be good to go. 

Like I said, post 5...

---

### Post by egandt on 2011-09-21
Good to hear it is possible to get it to work, my current key issue stems from the fact that the SVGA driver is being used.  
I'm trying to get it to use the Intel driver right now, but that is causing problems as well. Its all really annoying and poorly implemented as I want to be able to switch from Intel to ATI in windows and get just one working in Linux, best case would be to have both, but that seems like an unlikely option.  
My current plan is to manual create an xorg (and boy do I hate doing that), as using -configure setups up both, and then neither work.  

ERIC

---

### Post by sgtguthrie on 2011-09-21
I would just do a fresh install of ubuntu, and then DON'T install any proprietary drivers once you boot (you may have to try booting a couple times due to a race condition). Then follow the instructions in post 5, reboot, and vouala! You're good to go using the Intel sandy bridge graphics.

---

### Post by mysticmatrix on 2011-10-01
> **sgtguthrie said:**
> I would just do a fresh install of ubuntu, and then DON'T install any proprietary drivers once you boot (you may have to try booting a couple times due to a race condition). Then follow the instructions in post 5, reboot, and vouala! You're good to go using the Intel sandy bridge graphics.

I was trying to install Ubuntu Natty through Wubi today. The installation used to hang on the Radeon driver, but went sucessfully when I started in safe graphics mode. Now, I have a installed Ubuntu on my laptop, but it again is not starting due to the stupid Radeon thing.

Even booting in safe mode hangs up due to Radeon driver. Is there any way that I can disable loading of Radeon driver at startup and then blacklist it later? Kernel still seems to respond, since I can use SysReq+B to reboot my laptop.

---

### Post by sgtguthrie on 2011-10-01
> **mysticmatrix said:**
> I was trying to install Ubuntu Natty through Wubi today. The installation used to hang on the Radeon driver, but went sucessfully when I started in safe graphics mode. Now, I have a installed Ubuntu on my laptop, but it again is not starting due to the stupid Radeon thing.

Even booting in safe mode hangs up due to Radeon driver. Is there any way that I can disable loading of Radeon driver at startup and then blacklist it later? Kernel still seems to respond, since I can use SysReq+B to reboot my laptop.



I think I hear more problems with wubi than anything else. I don't see the point myself. If you're doing that, and don't want to just dual boot; it works fine in virtualbox...

---

### Post by SeijiSensei on 2011-10-01
[BIOS upgrade to enable Radeon card]("http://ubuntuforums.org/showpost.php?p=11244073&postcount=2")

[How to dual-boot Ubuntu on dv6tse]("http://ubuntuforums.org/showpost.php?p=11299287&postcount=5")

I don't have any info on how to get the fingerprint reader working though.

I plan to compile this stuff into a single posting in the near future.

---

### Post by mysticmatrix on 2011-10-01
> **SeijiSensei said:**
> [BIOS upgrade to enable Radeon card]("http://ubuntuforums.org/showpost.php?p=11244073&postcount=2")

[How to dual-boot Ubuntu on dv6tse]("http://ubuntuforums.org/showpost.php?p=11299287&postcount=5")

I don't have any info on how to get the fingerprint reader working though.

I plan to compile this stuff into a single posting in the near future.

Seiji,
 Can I get the specs of your laptop. Mine has Intel HD + AMD 6770M, along with a Ralink Wifi. I couldn't care less about using my ATI card in linux, the driver support of ATI on linux has always been insufficient. I am already on latest BIOS (F1.A for the Intel Model), and using fixed mode.

  I was able to install via Wubi, but I guess I will try a dedicated install some time later, tough I don't see how that will make any difference. Things that were not working were Wifi and Intel GPU. The system was not booting with trace-calls referring to Radeon module. But, I was still able to boot to graphics after that. Kernel does not seems to die after boot, as SysReq still functions. 

  Please update this thread if you make a detailed install post anywhere. It would be much appreciated.

---

### Post by SeijiSensei on 2011-10-01
The computer is off at college with my daughter, but here's what our order from HP says:

HP Pavilion dv6t Select Edition customizable Notebook PC

    * • steel gray
    * • Genuine Windows 7 Home Premium 64-bit
    * • 2nd generation Intel(R) Dual Core(TM) i5-2410M (2.3 GHz, 3MB L3 Cache) with Turbo Boost up to 2.9GHz
    * • 1GB GDDR5 Radeon(TM) HD 6770M Graphics [HDMI, VGA]
    * • FREE Upgrade to 6GB DDR3 System Memory (2 Dimm)
    * • 640GB 7200RPM Hard Drive with HP ProtectSmart Hard Drive Protection
    * • No Additional Office Software
    * • No additional security software
    * • 30% OFF! High Capacity 6-Cell Lithium-Ion Battery (standard) - Up to 5.75 hours of battery life +++
    * • 15.6" diagonal High Definition HP BrightView LED Display (1366x768)
    * • SuperMulti 8X DVD+/-R/RW with Double Layer Support
    * • HP TrueVision HD Webcam with Integrated Digital Microphone and HP SimplePass Fingerprint Reader
    * • Intel 802.11b/g/n WLAN with Wireless Display Support
    * • Standard Keyboard with numeric keypad

I never use WUBI; I always install Ubuntu in a dual-boot arrangement, which as my other posting suggests is a pain in the butt with an HP machine.  The Intel wifi card is supported out-of-the-box on Ubuntu.  The only real issue I had, other than installation, was getting the ATI card to work with the proprietary driver.  Once I upgraded the BIOS and switched to fixed mode, I could install the driver using the Additional Drivers applet.

---

### Post by mysticmatrix on 2011-10-07
Hmnn, I have the same specs except

Core i7 2630QM
ATI 6700M 2 GB
750 GB 7200 RPM HDD
RaLink Wifi module
Blu-ray drive

I tried loading Ubuntu 11.10, and everything seemed to work pretty fine. I was able to turn off the ATI cards and rely exclusively on Intel on-board, which is completely good for me. I already use fixed graphics, so I would try to install fglrx on it later. However, the laptop seemed to run pretty hot. I was helpful to turn off ATI, but still processor did not seem to go in lowest frequency a lot. Perhaps that can be tweaked later.

As of now, I am waiting for the final release of 11.10. I also found some handy advice on another forum regarding switching graphics, etc. I will make a post once I figure out more stuff.

---

### Post by Antarell on 2011-10-07
Heya, I have a DV6-6023TX, and have found that you don't need to blacklist the radeon module. I have been running Xubuntu and then Ubuntu 11.10 quite happily for a couple of weeks. (see [here]("http://help.stedman.net.au/2011/10/xubuntu-1110-on-hp-dv6-6023tx.html") for what I found get's it working. The only thing I have found is sometimes when it wakes up from sleep the backlight is off, a quick Fn-F3 get's it back up.

---

### Post by jozeph78 on 2011-10-14
Wow another good one to try tonight. This has been so much effort, all futile efforts at that. 

God I really wish ATI would just respect people's desire to use Linux and make decent drivers. =(

---

### Post by sgtguthrie on 2011-10-14
> **jozeph78 said:**
> Wow another good one to try tonight. This has been so much effort, all futile efforts at that. 

God I really wish ATI would just respect people's desire to use Linux and make decent drivers. =(

The problem here isn't ati, it's hp. Notice your linux box probably shows your ati card model incorrectly. As I understand it, hp modified the ati driver on this device, so any linux drivers ati releases won't work. They say hp needs to release a linux driver because of the modification. Hp has no intentions of doing this... So ya, it's complicated. :-)

---

### Post by jozeph78 on 2011-10-15
That would explain a lot then guthrie. I didn't know it was so device specific.

---

### Post by sgtguthrie on 2011-10-15
Ya, I wish i could find the articles I got this from as a reference, but i just can't find it.  If I stumble across them, i'll post in this thread.

---

### Post by rmp5s on 2011-11-17
I just recently got an HP DV6TQE like some others here have but I bumped up to the i7-2720QM and also got the ATI 6770.

Good to know I'm not the only one who notices this thing running REALLY hot.  I've had it get up to 92C in ubuntu and I had it sitting on a glass table when I first got it and it got so hot it blue screened the stock windows build.  I think it's just the way the CPU is.  I wasn't even doing anything...it happened overnight.  The stock windows build was garbage so I put 11.10 on it and it's been very smooth sailing ever since.  How can I tell what hardware the thing is actually using?  I'm curious.

Am I wrong for kinda feeling like such powerful hardware is going to waste running this OS?  It's a pretty lightweight OS and, yea...it's SCREAMING FAST on here but it just seems like overkill.

---

