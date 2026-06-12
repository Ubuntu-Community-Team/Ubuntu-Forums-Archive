---
title: "64bit Natty and Intel Sandy Bridge (ThinkPad T420)"
date: 2011-08-01
forum: Hardware
---

### Post by mejo on 2011-08-01
Hello,

After running 64bit Natty on a ThinkPad T420 with integrated i915 graphics for some time, I'll try to summarize my experiences and list solutions as well as issues that still do exist.

EDIT: I posted a list for 64bit Oneiric on a ThinkPad T420 [here]("http://ubuntuforums.org/showthread.php?p=11353524#post11353524").

First, most of the hardware worked out of the box.

Below follows a list of issues with a fresh Natty installation, that I was able to solve:

[LIST]
[*]CPU fan running all of the time: fix thinkfan configuration, solution described [here]("http://ubuntuforums.org/showpost.php?p=10866947&postcount=9") and [here]("http://ubuntuforums.org/showthread.php?t=1748475")
[*][suspend to RAM crashing]("https://bugs.launchpad.net/ubuntu/maverick/+source/pm-utils/+bug/625364"): seems to be fixed by [new kernel]("http://kernel.ubuntu.com/%7Esarvatt/lp761065/natty/"), solution described [here]("http://ubuntuforums.org/showthread.php?t=1748475&page=9") and [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/761065/comments/38")
[*]power saving measurements: [TLP]("https://launchpad.net/%7Elinrunner/+archive/tlp") ([docs in german]("http://thinkpad-wiki.org/TLP_-_Linux_Stromsparen")), [new kernel]("http://kernel.ubuntu.com/%7Esarvatt/lp761065/natty/"), [force pcie_aspm]("http://www.phoronix.com/scan.php?page=article&item=linux_2638_aspm&num=2")
[*]make tp_smapi kernel module work on t420: patch module source as described [here]("http://ubuntuforums.org/showpost.php?p=11044346&postcount=11")
[*][Active Protection System]("http://www.thinkwiki.org/wiki/Active_Protection_System") (with [HDAPS]("http://www.thinkwiki.org/wiki/HDAPS")) is working with [patched tp_smapi kernel module]("http://ubuntuforums.org/showthread.php?t=1752993") as well
[*][some]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/761065") [i915]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/792849") [graphics]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/794658") [issues]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/780053") apparently were fixed by the [new kernel]("http://kernel.ubuntu.com/%7Esarvatt/lp761065/natty/") as well
[/LIST]

Unfortunately, still some issues persist:

[LIST]
[*]microphone mute key is not working: [bugreport]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408903")
[*]issues with external monitor and docking station: described [here]("http://ubuntuforums.org/showthread.php?t=1752993")
[*]the [kernel patch]("http://kernel.ubuntu.com/%7Esarvatt/lp761065/natty/3.0-rc3-i915-Fix-gen6-SNB-GPU-stalling.patch") that fixes many of the issues above still didn't make it into Natty updates. It seems to be applied to the [2.6.38-11 kernel]("https://launchpad.net/ubuntu/+source/linux/2.6.38-11.47"), but that one still is in Natty proposed updates, and wasn't accepted to Natty updates yet. It seems like a regression was found in 11.47, and thus we need to wait for [11.48]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/818175")
[*]many small issues with unity, but I guess these are not specific to my hardware
[*]another hardware-independent, but very annoying issue: thunderbird freezing at quit from time to time: [bugreport]("https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/689453")
[/LIST]

I believe that a lot issue can be solved by using newer kernels, xorg intel video drivers and mesa. It would be much appreciated, if ubuntu developers could give Sandy Bridge support a higher priority. A lot of people will use this technology together with ubuntu in future. And some of the issues described above even may result in damaged hardware, thus they should be considered as critical.

---

### Post by ultimatebuster on 2011-08-15
I applaud this movement.

A comprehensive guide with how to get the T420 working with ubuntu as much as possible (hardware related only) would be awesome too, as I'm going to be testing out that laptop 3 days from now..

My current IdeaPad Y460, excellent with Windows (except for.. you know.. the Windows part.. which isn't excellent..).. always have a problem with Ubuntu.. Hopefully I can move to the T420 if it doesn't have too many issues.

Also what about the Active Protection System and Thinklight?

---

### Post by mejo on 2011-08-16
> **ultimatebuster said:**
> 
A comprehensive guide with how to get the T420 working with ubuntu as much as possible (hardware related only) would be awesome too, as I'm going to be testing out that laptop 3 days from now..

You should find all relevant information about how to setup Ubuntu 11.04 Natty on a ThinkPad T420 in my notes above. Unfortunately I don't have enough time to write a step-by-step tutorial right now.

I missed a note about external monitor and docking station in the list above. Will have to do further investigation before adding it to the list though.

> **ultimatebuster said:**
> Also what about the Active Protection System and Thinklight?

Didn't dig into the topic Active Protection System yet, but according to the thread **[Ubuntu 11.04 on Thinkpad T420 with HDAPS Working]("http://ubuntuforums.org/showthread.php?t=1752993")** it works with patched tp_smapi kernel module ([step-by-step tuturial for patching tp_smapi]("http://ubuntuforums.org/showpost.php?p=11044346&postcount=11")).

The thinklight works out of the box. You can turn it on and of with the respective hotkey (<Fn> + <PageUp>).

---

### Post by ultimatebuster on 2011-09-01
It took a lot of config to get all the thing work.. Unfortunately I didn't have foresight to record all the things I did to get it working... -.-

I also had to config grub's boot option to disable something in order to lower the temperature to around 40-45C. Don't remember what it was, but the CPU was constantly spinning at around 50-55C before (very unthinkpad)

---

### Post by mejo on 2011-09-02
> **ultimatebuster said:**
> I also had to config grub's boot option to disable something in order to lower the temperature to around 40-45C. Don't remember what it was, but the CPU was constantly spinning at around 50-55C before (very unthinkpad)

Do you mean the boot option 'pcie_aspm=force'? Whatever boot options you added, you should be able to find them either in /etc/default/grub or at least in /boot/grub/grub.cfg.

---

### Post by rewyllys on 2011-09-02
> **mejo said:**
> Do you mean the boot option 'pcie_aspm=force'? Whatever boot options you added, you should be able to find them either in /etc/default/grub or at least in /boot/grub/grub.cfg.
Mejo, do you mean that the "pcie_aspm=force" option needs to be disabled on the T420?  

I'd like to know, because I'm currently awaiting the arrival of a T420 (in about 2 weeks).

Thanks in advance for your answer

---

### Post by mejo on 2011-09-02
> **rewyllys said:**
> Mejo, do you mean that the "pcie_aspm=force" option needs to be disabled on the T420?

No, this option is not enabled by default. Adding the boot option to GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub (and running update-grub afterwards) will decrease power consumption of the system. It is a partial workaround for the [infamous power consumption bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131").

---

### Post by ultimatebuster on 2011-09-04
Yes I had to do that (the boot option thing).

Also is anyone experiencing flaky wireless while ethernet is completely fine (and other wireless devices are fine)?

---

### Post by mejo on 2011-09-15
Since some weeks, I discover system freezes every now and then. Not  sure, what causes them, but if I remember correctly, every time they  happen, I listen to music with banshee, and firefox is running.

The freeze is a hard freeze that I'm only able to solve by pressing the  power button for several seconds. Neither change to the console works,  nor does waiting for minutes help anything. The music doesn't stop, but  plays the last second in an endless loop.

I'm running up to date Ubuntu 11.04 with most recent 2.6.38-11-generic amd64 kernel.

Does anybody else discover these kind of hard freezes on a T420? I'm a  bit worried whether I might discover hardware issues. The laptop is  merely half a year old.

---

### Post by ultimatebuster on 2011-09-29
> **mejo said:**
> Since some weeks, I discover system freezes every now and then. Not  sure, what causes them, but if I remember correctly, every time they  happen, I listen to music with banshee, and firefox is running.

The freeze is a hard freeze that I'm only able to solve by pressing the  power button for several seconds. Neither change to the console works,  nor does waiting for minutes help anything. The music doesn't stop, but  plays the last second in an endless loop.

I'm running up to date Ubuntu 11.04 with most recent 2.6.38-11-generic amd64 kernel.

Does anybody else discover these kind of hard freezes on a T420? I'm a  bit worried whether I might discover hardware issues. The laptop is  merely half a year old.


I'm experiencing the same freezes. What kernel modules do you have loaded? I'm pretty sure this has to do with pluggin the computer into power or off power. If you didn't do it and still get those freezes, I believe it's because the thinkpad's power connector is a little bit flaky. It sometimes disconnects by itself and reconnects immediately (happened to me a couple of times.)

Try this: 

[http://www.robertbeal.com/1248/ubuntu-10101104-freezing-battery-power](http://www.robertbeal.com/1248/ubuntu-10101104-freezing-battery-power)

I used this for another laptop. Going to try on my thinkpad

---

### Post by mejo on 2011-10-02
> **ultimatebuster said:**
> I'm experiencing the same freezes. What kernel modules do you have loaded? I'm pretty sure this has to do with pluggin the computer into power or off power. If you didn't do it and still get those freezes, I believe it's because the thinkpad's power connector is a little bit flaky. It sometimes disconnects by itself and reconnects immediately (happened to me a couple of times.)

Try this: 

[http://www.robertbeal.com/1248/ubuntu-10101104-freezing-battery-power](http://www.robertbeal.com/1248/ubuntu-10101104-freezing-battery-power)

I used this for another laptop. Going to try on my thinkpad

Thanks for sharing your experiences. I don't think that the freezes I discovered are related to power issues, but I'll keep an eye on it. Actually I plug and unplug the power connector very often while the laptop is running, and didn't ever discover a freeze while doing that. Thus I doubt that my freezes are related to power connector issues.

The good news is, that I didn't have hard freezes in the last two weeks at all. Not sure whether this is related to the kernel update (running 2.6.38-11.50). If the freezes ever happen again, I'll consider to try the workarounds from your link.

---

### Post by ultimatebuster on 2011-10-02
> **mejo said:**
> Thanks for sharing your experiences. I don't think that the freezes I discovered are related to power issues, but I'll keep an eye on it. Actually I plug and unplug the power connector very often while the laptop is running, and didn't ever discover a freeze while doing that. Thus I doubt that my freezes are related to power connector issues.

The good news is, that I didn't have hard freezes in the last two weeks at all. Not sure whether this is related to the kernel update (running 2.6.38-11.50). If the freezes ever happen again, I'll consider to try the workarounds from your link.

Don't bother. I don't think it works as it seems unrelated.

Also are you experiencing issues with unpluggin VGA? I get hard freezes via that as well.

---

### Post by mejo on 2011-10-03
> **ultimatebuster said:**
> Also are you experiencing issues with unpluggin VGA? I get hard freezes via that as well.

No, I don't use external monitors yet either. Up to now I'm not able to connect the hard freezes to a special task or action. They happened while listening to music with banshee or while browsing the internet with firefox.

I'll give the docking station a try soon, let's see whether I discover hard freezes there as well. Last time I tried, the output of external monitor was flawed, and USB keyboard over docking station didn't work either. I'm curious whether that changed, as I'd like to use external keyboard/monitor/mouse.

---

### Post by ultimatebuster on 2011-10-06
Quick tip: If you unplug the VGA and your desktop is black with only the mouse movable. close the lid to put the laptop to sleep and open it back up. That solves it.

---

### Post by mejo on 2011-10-06
I added a new thread about the T420 with docking station here: [http://ubuntuforums.org/showthread.php?p=11313961](http://ubuntuforums.org/showthread.php?p=11313961)

---

### Post by mejo on 2011-10-16
> **mejo said:**
> After running 64bit Natty on a ThinkPad T420 with integrated i915 graphics for some time, I'll try to summarize my experiences and list solutions as well as issues that still do exist.

Now that I upgraded to Ubuntu 11.10 Oneiric Ocelot, I'll share my experiences again. First I have to say that all in all the upgrade went pretty smoothly. Below is a summary of the issues that one needs to address manually:


[LIST]
[*]While the auto modus for the fan seems to work much better in Oneiric, thinkfan didn't run after the upgrade. This is due to changed paths to temperature sensors. For me the coretemp paths changed from /sys/devices/platform/coretemp.X/temp1_input to /sys/devices/platform/coretemp.0/tempX_input, X being ascending diggits.
[*]The HDAPS driver needs to be [patched]("http://ubuntuforums.org/showthread.php?t=1752993") again, due to a [bug in tp_smapi]("https://bugs.launchpad.net/ubuntu/+source/tp-smapi/+bug/875787").
[*][Several]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131") [power]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/818830") [regressions]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/834037") in newer kernels can (at least partly) be addressed by adding the boot options "pcie_aspm=force" and "i915.i915_enable_rc6=1" to GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub.
[*]Setting 'model=thinkpad' for snd-hda-intel module as described [here]("http://ubuntuforums.org/showthread.php?p=11395285#post11395285") enabled microphone/line in and headphone/line out connectors of the docking station.
[/LIST]

The following issues have been addressed in Oneiric and are fixed:


[LIST]
[*]Issues with external monitor and docking station: described [here]("http://ubuntuforums.org/showthread.php?t=1752993")
[/LIST]
 
This leaves the follwing things that still don't work in Oneiric:


[LIST]
[*]Issues with the graphics mode when switching between docked and undocked state with running system.
[*]The microphone mute key is not working: [bugreport]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408903")
[/LIST]

---

### Post by JurB on 2011-10-23
> **mejo said:**
> [Several]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131") [power]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/818830") [regressions]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/834037") in newer kernels can (at least partly) be addressed by adding the boot options "pcie_aspm=force" and "i915.i915_enable_rc6=1" to GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub.
That seems to help, i now get 16-17w in powertop (was 24-25W), temperatures are 45-50°C (was 50-55°C). It did mess up conky, battery-time now shows "unknown".   

> **mejo said:**
> The microphone mute key is not working: [bugreport]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408903")
Weird, mine work just fine...

---

### Post by mejo on 2011-10-23
> **JurB said:**
> 
> 
The microphone mute key is not working: [bugreport]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408903")

Weird, mine work just fine...


You're sure that your _microphone_ mute key works? It really mutes the microphone? Or are you talking about your audio output mute key?

---

### Post by JurB on 2011-10-24
> **mejo said:**
> You're sure that your _microphone_ mute key works? It really mutes the microphone? Or are you talking about your audio output mute key?
My bad, i meant audio output...

---

### Post by amdemas on 2011-10-26
For audio out and mic for when docked

Try adding this line 

[I]options snd-hda-intel model=thinkpad 

[/I]*to **/etc/modprobe.d/alsa-base.conf*
[I]
to the bottom of the list of options. 

[/I][I]

Then reboot. 

It worked for me with t420s. 

I am having an issue with the fan noise still and have tried thinkfan but cant get it....any help?
[/I]

---

### Post by mejo on 2011-10-26
> **amdemas said:**
> For audio out and mic for when docked

Try adding this line 

[I]options snd-hda-intel model=thinkpad 

[/I]*to **/etc/modprobe.d/alsa-base.conf*
[I]to the bottom of the list of options. 
[/I]* It worked for me with t420s.*[I]

[/I]Great, thanks a lot for the hint. Indeed it works like a charm for me on T420.
> **amdemas said:**
> *I am having an issue with the fan noise still and have tried thinkfan but cant get it....any help?*

See e.g. [http://ubuntuforums.org/showpost.php?p=10866947&postcount=9](http://ubuntuforums.org/showpost.php?p=10866947&postcount=9) there I described how to get thinkfan working on 11.04. On 11.10. the paths to sensors changed, see [http://ubuntuforums.org/showpost.php?p=11353524&postcount=16](http://ubuntuforums.org/showpost.php?p=11353524&postcount=16)

---

### Post by amdemas on 2011-10-26
Great Ill give that a shot....i am now having another issue with my trackpad...it doesnt work so i try fn+f8 and no go it doest indicate anymore now of my hotkeys for the fn key work now except the sleep key.

I have no idea what happened lol

Any help?

---

### Post by mejo on 2011-10-27
> **amdemas said:**
> Great Ill give that a shot....i am now having another issue with my trackpad...it doesnt work so i try fn+f8 and no go it doest indicate anymore now of my hotkeys for the fn key work now except the sleep key.

I neither have issues with my trackpad, nor with my hotkeys. They all work as expected.

---

### Post by Guitar John on 2011-10-27
> **mejo said:**
> Now that I upgraded to Ubuntu 11.10 Oneiric Ocelot....

You upgraded, rather than doing a clean install?  

Reason I'm asking is that the next version of Ubuntu is an LTS.  I'll be staying put with that version, and I'd rather not have to do another clean install if I don't have to.

FWIW, I'm running 11.10 on a ThinkPad X100e.  Everything works, so far.

---

### Post by mejo on 2011-10-27
> **Guitar John said:**
> You upgraded, rather than doing a clean install?  

Reason I'm asking is that the next version of Ubuntu is an LTS.  I'll be staying put with that version, and I'd rather not have to do another clean install if I don't have to.

FWIW, I'm running 11.10 on a ThinkPad X100e.  Everything works, so far.

Yes, I upgraded from 11.04 to 11.10. Upgrading from one Ubuntu release to the next one is officially supported by Ubuntu and shouldn't cause major trouble.

---

### Post by amdemas on 2011-10-27
> **mejo said:**
> [/I]Great, thanks a lot for the hint. Indeed it works like a charm for me on T420.


See e.g. [http://ubuntuforums.org/showpost.php?p=10866947&postcount=9](http://ubuntuforums.org/showpost.php?p=10866947&postcount=9) there I described how to get thinkfan working on 11.04. On 11.10. the paths to sensors changed, see [http://ubuntuforums.org/showpost.php?p=11353524&postcount=16](http://ubuntuforums.org/showpost.php?p=11353524&postcount=16)


Sorry to be such a n00b...but where do i get the kernel module "coretemp" and after that how do i reload it?

Thanks

---

### Post by mejo on 2011-10-27
> **amdemas said:**
> Sorry to be such a n00b...but where do i get the kernel module "coretemp" and after that how do i reload it?

Thanks

coretemp is compiled as module in default Ubuntu kernel. All you need to do is following the step-by-step tutorial I linked. See 'modinfo coretemp' for more information.

---

### Post by coverup1128 on 2011-11-01
> **JurB said:**
> That seems to help, i now get 16-17w in powertop (was 24-25W), temperatures are 45-50°C (was 50-55°C).

I received T420 a week ago. Thank you for the detailed posts - helps a lot. 

So far have been playing with Live CDs. Using Jupiter, Natty used far less watts than Oneiric for me. Using Natty with WiFi on and FF running, I went as low as 9-10W. But when CD spun or when using skype, power consumption could jump to as much as 17W. 

Using Oneiric, I never went below 13W. Also, the fan was barely heard in Natty, while sung Oneiric it was always spinning at around 2000 rpm.

---

### Post by lddm on 2011-11-13
HI!
I'm using 11.04 in a T420 for a week now and I'm only having a annoying problem. When I connect a external monitor to the VGA or DP (via DP-HDMI adapter) I can't configure to use only the external monitor and leave the laptop screen turned off. I'm not sure if I'm making myself clear, the idea is to use only the external monitor and leave turned off the laptop included screen. When I configure the "internal" monitor to be turned off the video output also goes off.
Does anyone have experienced the same problem?
Greetings.

---

### Post by coverup1128 on 2011-11-28
Yes, the same problem here when using Monitors or Fn+F7. But xrandr in the terminal works fine.

---

