---
title: "Hybrid Intel + Mobility Radeon HD 5650/5750 / 6530M/6550M"
date: 2014-09-29
forum: Hardware
---

### Post by QuimNuss on 2014-09-29
I couldn't get the graphics drivers to work properly and I'm stuck with OpenGL 1.4 (I'd need 2.1).

From lspci I got

VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Madison [Mobility Radeon HD 5650/5750 / 6530M/6550M]
VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)

I guess it is using the Intel card, [8086:0046], but it _should_ support opengl 2.1 (check 0046 at [http://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units](http://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units)). What can I do to use the appropriate driver?

I thought I'd try to use the ATI card, I've tried installing both flgrx drivers suggested on the 'additional drivers', but that gets me to 'low resolution mode' on reboot. I haven't tried fixing it since I'm not very optimistic when it comes to this...

Now I'd like to nail the problem down and be able to use at least OpenGL 2.1, any help would be much appreciated, as well as if somebody is able to tell me if that's even possible.

Thanks!

I'm on ubuntu 14.04.

lshw

        *-display
             description: VGA compatible controller
             product: Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:44 memory:e0000000-e03fffff memory:d0000000-dfffffff ioport:6050(size=8)
   *-display
                description: VGA compatible controller
                product: Madison [Mobility Radeon HD 5650/5750 / 6530M/6550M]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:46 memory:c0000000-cfffffff memory:e6400000-e641ffff ioport:5000(size=256) memory:e6440000-e645ffff

$ lspci -vnn | grep VGA -A 12
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02) (prog-if 00 [VGA controller])
	Subsystem: COMPAL Electronics Inc Device [14c0:004d]
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at e0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 6050 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
--
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Madison [Mobility Radeon HD 5650/5750 / 6530M/6550M] [1002:68c1] (prog-if 00 [VGA controller])
	Subsystem: COMPAL Electronics Inc Mobility Radeon HD 5650 [14c0:004d]
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at e6400000 (64-bit, non-prefetchable) [size=128K]
	I/O ports at 5000 [size=256]
	Expansion ROM at e6440000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: radeon

---

### Post by QuimNuss on 2014-10-02
Summary of what I tried so far:

I've managed to power on/off the cards using switcheroo. How? By activating the modeset=1 on grub, rebooting, switching to a tty and stopping the lightdm. Then all the switcheroo commands seem to work (their status changes and says i915 driver is off).

[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

Then I tried installing the ATI proprietary driver from the repositories as well as from the ATI site, on both cases getting the low-resolution mode and almost an irresponsive keyboard and mouse (I kind of managed to make it work sometimes by starting on recovery mode).

When using the ATI proprietary driver from the site I pretty much followed these steps: [http://askubuntu.com/questions/487761/installing-ati-catalyst-14-20-beta-on-ubuntu-12-04-throws-error](http://askubuntu.com/questions/487761/installing-ati-catalyst-14-20-beta-on-ubuntu-12-04-throws-error) up to 5., since I didn't have that error and the packages were build and the pop-up suggested me to install them, which I did (I had to do that several times as missing dependencies were missing)

I've tried powering off the integrated card on all cases just in case that helped making the system believe it isn't hybrid and only had the ATI card, but I always end up in low graphics mode anyway.

On low graphics mode, I've tried aticonfig --initial, the switcheroo things, ... nothing worked.

WARNING: After installing the proprietary driver I was unable to get a responding system (it got stuck loading unity: menus and mouse were there but nothing happened) following my life saving commands (purge fglrx, reinstall xorg, reconfigure it, reboot).

I'll try with archlinux next week or with a fresh ubuntu install, which it must have some tweak on OpenGL as I was able to play some games I'm not able to now.

Summary: anytime I try to use fglrx or fglrx-updates I get the low graphics mode and I'm unable to log in. Even with radeon, the system doesn't seem to use the ATI card as I only get opengl 1.4. I haven't seen any difference on the battery life estimate by switching the card on an off using switcheroo.

Any help is much appreciated.

---

### Post by QuimNuss on 2014-10-22
I've solved it... I'm so ****ing excited. The 4 nights of crawling the web and understanding how graphics work payed off... I'm still amazed.

Ok so I managed to get the discrete card working on Linux Mint 14.04 Qiana.

What I did:
Updated fresh install
changed the /etc/default/grub from quiet splash to modeset=1
update-grub

added the lines
echo ON > /sys/kernel/debug/vgaswitcheroo/switch
echo DIS > /sys/kernel/debug/vgaswitcheroo/switch

at /etc/rc.local

Then reboot.

Then I went to tty with ctrl+alt+f1, sudo su and checked that both cards were up with

# cat /sys/kernel/debug/vgaswitcheroo/switch

stopped mdm (lightdm on ubuntu or kdm gdm on others) with

service mdm stop

then turned off the intel card 

echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

it said i915 is off and with cat like before we can see

```
  
0:DIS:+:DynPwr:0000:01:00.0
1:IGD: :Off:0000:00:02.0
2:DIS-Audio: :Pwr:0000:01:00.1

```

and then

service mdm start

to bring the window manager up again. And voilà!

pol@baldrik ~ $ glxinfo | grep OpenGL
OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD REDWOOD
OpenGL core profile version string: 3.3 (Core Profile) Mesa 10.1.0
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 10.1.0
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:

So I believe what was that the DIS card is on slot 0 (I don't know how that happened)

Also, last week I was looking at the wrong string on glxinfo (grepping glx version instead of OpenGL) which is always 1.4 (unfortunatelly the same OpenGL version I was able to run on the intel card :S, hence the stupid mistake)

I had problems with modeset.i915=0 modeset.radeon=1 and combinations, always getting the 'vga_switcheroo: client <number> refused to switch' . modeset = 1 worked.

So probably now if I add the echo OFF > /sys/kernel/debug/vgaswitcheroo/switch on rc.local I will always start with the integrated graphics card. However, if using switcheroo to power the cards and move them around works, then I'll leave the OFF for the integrated card by default and switch graphics when I need them. I still have to try this.

I haven't managed to get the fglrx driver or the amd catalyst to work, I've tried all sorts of things. Different debian-based distros (ubuntu 12.04, 14.04, mint, debian). The problem was essentially that fglrx claims to not support muxless cards.

I haven't found a clear way to know if you have a muxed or a muxless card. Muxed or muxless essentially means that you have a physical switch or a bios switch for the cards (muxed) or that you switch by software (muxless). The later have higher rate of success on working. THe internet claims that atis over 6xxx (included) are muxless and below 4xxx (included) are muxed. I had 5xxx so that grey zone... ( [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide) )

I was reassured when inspecting the log of /var/log/XOrg.log upon installing fglrx reported

> 
[    32.664](WW) PowerXpress feature is not supported on A+I Mux platform. Please uninstall fglrx driver.
[    32.664] (EE) this is a Muxless PX A+I platform, we doesn't supported it
[    32.664] (EE) No devices detected.


(the *we doesn't supported it* is real, (sic))

[http://ubuntuforums.org/showthread.php?t=2228404](http://ubuntuforums.org/showthread.php?t=2228404)

So at least you can know wether your card is muxless by looking at XOrg.log when installing fglrx and look for the (EE) strings.

The post [http://ubuntuforums.org/showthread.php?t=1930450&page=82](http://ubuntuforums.org/showthread.php?t=1930450&page=82) didn't work for me, any of the interesting comments (namely: 503 536 815 834 857)

I haven't tried with ubuntu 13.04 because it is discontinued and I would've had problems getting the packages. The 12.04 gave me an error when installing the generated packages (missing some networking driver when runing initrms or initramfs... I can't remember exactly)

I tried with xorg-edgers and some other ppa, I'll post how to revert the changes tomorrow.

And also some piece of information many people get wrong. vga_switcheroo is related to the opensource radeon driver. If you are using another driver that 'file' won't exist. Also you need to be root to see ir and autocomplete won't work, so use the first two sections of the guide:

[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

(How to switch and using vga_switcheroo)

In that guide is missing that you have to put the grub to modeset=1, though. Otherwise if I recall correctly is not the kernel that decides what gpu to use and you won't be able to switch, or something like that. (Kernel Mode Setting KMS [http://ubuntuforums.org/showthread.php?t=1744188](http://ubuntuforums.org/showthread.php?t=1744188))

I'll post more information I've gathered and embellish this post tomorrow.

Hoorray!

ps. fingers crossed that this will still work upon reboot :S

---

### Post by QuimNuss on 2014-10-22
Ah, and maybe it's important to say that there's no xorg.conf anymore. aticonfig --initial messes that one pretty much. What I saw is that it simply neglected the intel card and created a xorg.conf with no reference to the intel card.

But with radeon and intel, there's no xorg.conf no more.

Also, if the modeset of the intel card is set to 0 the X server fails to start. I can't tell why since I didn't save the log.

---

### Post by QuimNuss on 2014-10-22
Ah, one more thing. Now that I know that vgaswitcheroo works, there are plugins/applets to add an icon to the applet bar to switch cards within a click. I'm not sure it will work here since I believe I had to stop and start mdm for the changes to be in effect, but it's worth a try, it's pretty neat.

Thanks to Nicola and  Alexislavie for their inspiring posts and the community in general. Special thanks to cutting edge Gentoo users, some pretty neat stuff there regarding this problem. And this guy too [http://airlied.livejournal.com/70348.html](http://airlied.livejournal.com/70348.html).

---

### Post by QuimNuss on 2014-10-22
goddamit it didn't work on reboot...

but I'm getting there... stay tuned.

---

### Post by youzava on 2014-10-23
don't give up! I've been busy for a long time with this and I won't give up either! 

Have you considered looking in the direction of a specific amd/intel kernel? Maybe we can compile one.

---

### Post by QuimNuss on 2014-10-23
Hello brother in arms,

I haven't recompiled the kernel before, but that's a good idea. I'll switch to ubuntu tonight since there switcheroo worked all the time, for some reason it now stopped working on Mint (keeps saying client 0 (or 101) refused to switch) no matter if I'm root, mdm is stopped or what modeset I have inputted in grub. Also sometimes the keyboard doesn't work, sometimes the cursor doesn't work... stuff like that.

But now that I know that it is possible that shed some light in the issue. I can't rembmer if switching changed the order of the cards on switcheroo. Maybe that was the reason of the success, having the discrete card first. I have no idea how to control that if it's not throught switcheroo. I've tried blacklisting i915 and radeon and modprobing them on rc.local, but that didn't seem to change anything.

So, how do we recompile the kernel and what do you suggest we try? Do you also have 5xxx? I feel 5xxx cards are kind of neglected out there.

cheers!

---

### Post by youzava on 2014-10-24
Hey I installed 14.10 and the latest kernel 17.10 and after a lot of work I am now figuring out how to configure the open source driver for gaming.
phoronox forums have a lot on that. They say there are a lot of graphical improvements to be made with 3.18
DRI_PRIME=1 
xrandr --listproviders
xrandr --setprovideroffloadsink
DRI_PRIME=1 glxgears
I wonder why no one tries to help us on this forum..

The oibaf ppa is something to look out for.

---

### Post by QuimNuss on 2014-10-24
The oibaf repos didn't work for me. What kernel is 17.10? I have 3.2 so I don't know what you mean.

What do the commands you posted do?

I've managed to get the default opensource driver (radeon) to work correctly through vgaswitcheroo. Putting the commands in rc.local does not work, probably because X server is already running when they are issued althought I had read rc.local was ran after each runlevel, not true. That's what happened in Linux Mint.

So right now my procedure is to switch to a terminal, stop lightdm (or mdm or kdm) run the command
```
echo DIS > /sys/kernel/debug/vgaswitcheroo/switch
```
and start lightdm. Then the discrete is on and the integrated is off and I can do nice 3d stuff. The acceleration is baaarely enough for game emulation, but it works fine for pc games like TF2 (Haven't tried yet, but it worked already with the integrated one, so...).

---

### Post by QuimNuss on 2014-10-24
I'll post as solved although I couldn't max out the graphic card.

---

### Post by QuimNuss on 2014-10-24
It's important to note that the switcheroo commands only work if you're root. Sometimes I got different output when running the commands as sudo instead of root.

Long story short:
replace nomodeset for modeset=1 in file /etc/default/grub
```

sudo su
vim /etc/default/grub
update-grub
reboot

```
upon reboot, switch to a terminal with ctrl+alt+f1, stop the window manager with
```
sudo service lightdm stop
```
turn off the integrated card and on the discrete with
```
echo DIS > /sys/kernel/debug/vgaswitcheroo/switch
```
restart the window manager
```
sudo service lightdm start
```

And voilà. ```
glxinfo | grep OpenGL
``` should report your discrete card, as well as
```
cat /sys/kernel/debug/vgaswitcheroo/switch
```

If you want to turn off the discrete do the same but use
```
echo IGD > /sys/kernel/debug/vgaswitcheroo/switch
```

The status of the card it's not saved between sessions and both are ON by default. I think the discrete card is completelly ignored when both are on (at least glxinfo uses the intel one when both are on). I haven't yet searched how to change the 'default' state or keep the last status, but it's definitely possible, I'll find out later on.

---

### Post by Tinek on 2014-10-28
Hey!

I'm glad to finally see someone with the exact same config and troubles!

On my side I'm not trying to get anything from the radeon discrete card cause the only gpu-intensive application I'd use are still Win-hosted but the overheating is really a pain in the...

I'm now (since a few days) using Xubuntu 14.10. And I think that I've not been able to get the laptop under 90°C since 13.10.

So far I've tried :
- fglrx drivers (never worked since 10.04)
- acpi_calls back in the day (don't work since 11.4)
- vga_switcheroo stopped working from 13.10
-I thought of underclocking through rovclock to improve autonomy but the soft is too old by now and doesn't support our cards anymore.
- new power management routines (dynpm...) never worked for me.

Like you I found the way to get vgaswitcheroo working (but on 14.10) but that's pretty random (and not working anymore since 2 days). 

I'll try later later on a fresh install and keep you updated.

---

### Post by QuimNuss on 2014-10-28
Great!

You can try if vga_switcheroo works from a liveCD/LiveUSB.

---

### Post by Tinek on 2014-10-29
I won't give up on this one!

After a fresh install I had some really nice results. I mean less than 10w consumptions and a global 45°C. 
This thanks to the improvements made in latests radeon drivers and through tlp, which handle fairly well the radeon power management.

Sadly upon reboot, system gets random again. Try to pass a lot different grub parameters about power management, but I'm still booting 1/10. Not an option for me.
Looks like both the i915 and radeon drivers are fighting during boot time to get the priority, and there I don't have the knowledge to do much. 

The only I can think of solving that would be to start the laptop with no radeon module and the load it back after, but that's definitely not the aim of that thread!..

Will give it a try under 14.04 (and keep on digging the web for 14.10), as it's supposed to be more stable.

And I would strongly suggest you to keep on digging around the PRIME technology, if you don't want to bother with the switching thing. It would allow you to have some windows rendered by one or the other gpu :
-ati for game.
-system default for the rest.
that would not be a long term solution but might help you to get the results you're looking for!

Good luck!

---

### Post by Tinek on 2014-10-30
PRIME informations may be founf here : [https://wiki.archlinux.org/index.php/PRIME](https://wiki.archlinux.org/index.php/PRIME)

Cheers

---

### Post by Tinek on 2014-10-31
Update for me :

System finally usable through acpi_call (after 4 re-installation!), ie ATI disabled.
For  those that it might help full system is Acer Aspire 4820TG with  i5/HD5650, Xubuntu 14.10, latest (regular) everything as of 10/31/14.

The  dpm use only leads to bad power management and it seems that there is some  kind of weird struggle between the i915 and radeon drivers that prevents from booting and keeping the system stable.
I hope I'll have the time to fill a bug report soon to help improvements on stability/usability on a spare install, just don't really know how procced/start from.

---

### Post by QuimNuss on 2014-11-05
** WARNING **

On reboot today I got a black screen after a certain delay with the following message on dmesg:
[...]
[   47.313515] snd_hda_intel 0000:01:00.1: Start delayed initialization
[   47.418106] snd_hda_intel 0000:01:00.1: CORB reset timeout#2, CORBRP = 65535
[   47.418220] snd_hda_intel 0000:01:00.1: no AFG or MFG node found
[   47.418299] snd_hda_intel 0000:01:00.1: no AFG or MFG node found
[   47.418352] snd_hda_intel 0000:01:00.1: no AFG or MFG node found
[   47.418380] snd_hda_intel 0000:01:00.1: no AFG or MFG node found
[   47.418403] snd_hda_intel 0000:01:00.1: no codecs initialized
[   47.418425] snd_hda_intel 0000:01:00.1: initialization error
[   53.195954] systemd-logind[1060]: Failed to start unit [email]user@1000.servic[/email]e: Unknown unit: [email]user@1000.servic[/email]e
[   53.195961] systemd-logind[1060]: Failed to start user service: Unknown unit: [email]user@1000.servic[/email]e
[...]

I don't know if it's related to modprobing in and out snd_hda_intel but it's likely. After 3 reboots and modprobing in and out, adding the line 'sleep 10' before exec lightdm on file /etc/init/lightdm.conf (see [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/969489](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/969489)) seems to have fixed it, although the message in dmesg is still there. So proceed with caution. I'm trying to find out how to get rid of those messages as we speak.

(maybe it's better to use rmmod and insmod instead of modprobe -r and modprobe... I don't know what's the difference.)

*****
Some more info on vga_switcheroo:

If, once lightdm has been stopped you still get 

```
client 101 refused to switch
```

The 101 refers to snd_hda_intel so you can solve this by removing the module, switching switcheroo and then reload the module:

```
sudo su
modprobe -r snd_hda_intel
echo DIS > /sys/kernel/debug/vgaswitcheroo/switch
modprobe snd_hda_intel
```

This happens because sound is also on the intel chip, so it refuses to switch it off while in use.

I'm getting better and better at this.

---

### Post by topdawg7793 on 2014-12-27
Something tells me you're close...

I too have a 4820tg and have tried on-and-off over the last couple years to get my card working in Ubuntu and I just haven't ever had luck! The driver on AMD's official site lists the Mobility Radeon 5000 series as being supported but every time I try to install their driver my computer goes into low graphics mode. I haven't had luck with switcheroo since 12.04 (currently on 14.04).

I would really love to at least be able to turn my discrete card off so my computer isn't always operating at a million degrees...I'll make an effort tomorrow and see if I can figure something out and I'll post here. Glad I'm not the only one with these issues!

UPDATE: Nvm on the switcheroo, it's definitely working. echo OFF > /sys/kernel/debug/vgaswitcheroo/switch seems to have turned off my discrete gpu as my computer isn't producing as much as heat as it normally does. cat /sys/kernel/debug/vgaswitcheroo/switch shows the discrete gpu is off as well. Welp, progress..Still can't get it to switch to my discrete though.

---

### Post by simon75 on 2015-01-05
Woah !!! Hi there, just found this post! I had the same problem, I'm using a mobility hd radeon 5450...  and it really seems like 5xxx series are in between everything 

I can confirm that vga_switcheroo seems to be the only solution to use the discrete card and that proprietary driver are just messing up more. 
I am stuck though. Vga switcheroo works fine, switching on/off and switching gpu, but when I restart lightdm after switching for the DIS something is not going right. I get the default wallpaper of ubuntu and my cursor, but nothing else is showing up. no loggin prompt 

I'm pretty new to all this and I just want to be able to run my discrete card. I'm assuming lightdm is looking for the ATI card when it boots to render his things and then it just can't find it and do nothing ? 
I know you guys have a lot to work on for yourself, but I you can think of where I should start looking it would be really nice to share it. Either there is some config for lightdm referring to the ati card that I need to change, or there is another ways to start lightdm and reconfigure it at the same time so it can detect the "new" hardware he will have to use ? Or maybe it is possible to log in X even if lightdm is messed up through the terminal, so X boot and hopefully he fixes whatever is happening ?

Anyway, thank you for the thread, your explaination are as clear as source water, and I think I would have never figured out what that modeset=1 was reffering to without you !

---

### Post by Tinek on 2015-02-04
@topdawg7793

Yeah, sure vgaswitcheroo works. The thing is that it always mess up at one point and unless you're some kind of script-killer-guy you won't be able to automate the things this method need at every screen update (means : log out, reboot, back from sleep etc...) and then x will fail.

The only way that worked for me permanently on the 4820tg (5656/i5) is acpi_call that disable the power input of the card through acpi. You will never be able to use it as long as you make the calls, but that's what I want.

ps : glad to finally hear from someone with the exact same laptop and exact same story ;)

@simon75

Actually I don't think the whole 5xxx serie is forgotten at all, but some of them like so. And I've read somewhere that there also might be an architecture thing but can't recall.

I'd say the same thing about switcheroo than above.

If you only want to use the discrete (=ATI) one permanently then you might try to have a look in your bios. usually you can choose between the modes :
- Hybrid (discrete + integrated)       <= the one default, and messing for us
- Discrete

(- Integrated, sadly, is a rare option in bios. If you're some kind of gambling dude, a russian hacker (I think) did put up a hacked bios for Acer TimelineX series that enables this option and lot more, the problem is if you mess up motherboard is dead)

As far as I saw if you choose integrated, everything runs fluently and you even may be able to install proprietary drivers.

Cheers,

---

### Post by magico on 2015-02-22
Amazing information and for the first time since I have Ubuntu in this laptop (4 years), I'm able to have the discrete card working

> 
$ glxinfo | grep OpenGL
OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD REDWOOD
OpenGL core profile version string: 3.3 (Core Profile) Mesa 10.3.2
OpenGL core profile shading language version string: 3.30


But this was not so easy as indicated because in my case, the initial setup of the discrete card was

> 
$ sudo cat /sys/kernel/debug/vgaswitcheroo/switch
1: DIS: : DynOff:0000:01:00.0
2: DIS-Audio: : DynOff:0000:01:00.1


Having "DynOff" makes the screen go black and you have to switch again to IGD to continue working.

After a few hours of trial and error, I've found that putting this in grub

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.runpm=0"

Allows the discrete card to be set initial to "Off" only.

After that, all the initial instructions worked perfectly!!!

---

### Post by QuimNuss on 2015-02-22
Nice, I didn't know about this option. I've looked up what does that mean, with the very interesting result [1]:

radeon.runpm=0 means Disable Radeon power management in newer Linux kernels, which is enabled by default.

Moreover the google result states that then the discrete card can be switched on/off by default by setting the switcheroo commands on the /etc/rc.local. I will try that tomorrow.

[1] [http://www.mostthingsweb.com/2014/07/disable-radeon-power-management-newer-linux-kernels/](http://www.mostthingsweb.com/2014/07/disable-radeon-power-management-newer-linux-kernels/)

---

### Post by brian50 on 2015-02-23
Hi, I'm using the same graphics card on my acer 4745G laptop.
I found that the only different between DIS and IGD graphics card, is my laptop can wake from I suspend it.

when I use glxinfo test the OpenGL implementation , two cards were same at 60fps.  

I think the discrete card should higher than the integrated.

sorry for my non native english.

---

### Post by QuimNuss on 2015-02-24
You probably mean glxgears and you probably have vertical sync activated (which syncs with the screen framerate of 60 fps)

Try with:
[FONT=Courier New]
vblank_mode=0 glxgears
[/FONT]

---

### Post by Tinek on 2015-05-05
Hi guys,

On my side, after a fresh install of Mint Rebecca, everything is running flawlessly... Radeon drivers are handling perfectly that card for the first time (except hdmi audio that crashes the pulseaudio server atm).

Do you have those results too?[SIZE=2]

Cheers

[SIZE=1]... Looks like it's the end of a dark age ...[/SIZE][/SIZE]

---

### Post by QuimNuss on 2015-05-07
Man, I am totally trying this. If you are right it is indeed the end of a dark era.

Did it work out of the box? I mean, you install Mint, then you go to drivers and then install fglrx? But you said radeon, so did you do something else?

I've starte a LiveUSB session with rebecca, and out of the box reports

[FONT=Courier New]
mint@mint ~ $ glxinfo | grep OpenGL
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Mobile 
OpenGL version string: 2.1 Mesa 10.1.3
OpenGL shading language version string: 1.20
OpenGL extensions:
[/FONT]

Let me know! tremendously interested.

---

### Post by QuimNuss on 2015-05-07
[FONT=Courier New]mint@mint ~ $ dmesg | egrep 'drm|radeon'
[    6.531861] [drm] Initialized drm 1.1.0 20060810
[    6.569794] [drm] radeon kernel modesetting enabled.
[    6.569976] radeon 0000:01:00.0: enabling device (0006 -> 0007)
[    6.576428] [drm] initializing kernel modesetting (REDWOOD 0x1002:0x68C1 0x14C0:0x004D).
[    6.576553] [drm] register mmio base: 0xE6400000
[    6.576608] [drm] register mmio size: 131072
[    7.765876] radeon 0000:01:00.0: VRAM: 1024M 0x0000000000000000 - 0x000000003FFFFFFF (1024M used)
[    7.765977] radeon 0000:01:00.0: GTT: 1024M 0x0000000040000000 - 0x000000007FFFFFFF
[    7.766074] [drm] Detected VRAM RAM=1024M, BAR=256M
[    7.766135] [drm] RAM width 128bits DDR
[    7.766652] [drm] radeon: 1024M of VRAM memory ready
[    7.766716] [drm] radeon: 1024M of GTT memory ready.
[    7.766788] [drm] Loading REDWOOD Microcode
[    7.767132] [drm] GART: num cpu pages 262144, num gpu pages 262144
[    7.782914] [drm] PCIE GART of 1024M enabled (table at 0x000000000025D000).
[    7.783133] radeon 0000:01:00.0: WB enabled
[    7.783196] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000040000c00 and cpu addr 0xffff88022f026c00
[    7.783301] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000040000c0c and cpu addr 0xffff88022f026c0c
[    7.784147] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x000000000005c418 and cpu addr 0xffffc9000931c418
[    7.784250] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    7.784319] [drm] Driver supports precise vblank timestamp query.
[    7.784411] radeon 0000:01:00.0: irq 43 for MSI/MSI-X
[    7.784429] radeon 0000:01:00.0: radeon: using MSI.
[    7.784523] [drm] radeon: irq initialized.
[    7.801515] [drm] ring test on 0 succeeded in 1 usecs
[    7.801639] [drm] ring test on 3 succeeded in 1 usecs
[    7.987801] [drm] ring test on 5 succeeded in 1 usecs
[    7.987869] [drm] UVD initialized successfully.
[    7.988198] [drm] Enabling audio 0 support
[    7.988298] [drm] ib test on ring 0 succeeded in 0 usecs
[    7.988400] [drm] ib test on ring 3 succeeded in 0 usecs
[    8.139022] [drm] ib test on ring 5 succeeded
[    8.197087] [drm] radeon atom DIG backlight initialized
[    8.197165] [drm] Radeon Display Connectors
[    8.197225] [drm] Connector 0:
[    8.197281] [drm]   LVDS-1
[    8.197339] [drm]   DDC: 0x6560 0x6560 0x6564 0x6564 0x6568 0x6568 0x656c 0x656c
[    8.197431] [drm]   Encoders:
[    8.197489] [drm]     LCD1: INTERNAL_UNIPHY
[    8.197548] [drm] Connector 1:
[    8.197606] [drm]   HDMI-A-1
[    8.197661] [drm]   HPD1
[    8.197717] [drm]   DDC: 0x6440 0x6440 0x6444 0x6444 0x6448 0x6448 0x644c 0x644c
[    8.197809] [drm]   Encoders:
[    8.198450] [drm]     DFP1: INTERNAL_UNIPHY1
[    8.198512] [drm] Connector 2:
[    8.198569] [drm]   VGA-1
[    8.198628] [drm]   DDC: 0x6430 0x6430 0x6434 0x6434 0x6438 0x6438 0x643c 0x643c
[    8.198723] [drm]   Encoders:
[    8.198778] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    8.198957] [drm] Internal thermal controller with fan control
[    8.364624] [drm] radeon: dpm initialized
[    9.703607] [drm] fb mappable at 0xC045E000
[    9.703661] [drm] vram apper at 0xC0000000
[    9.703714] [drm] size 4325376
[    9.703764] [drm] fb depth is 24
[    9.703814] [drm]    pitch is 5632
[   14.179857] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[   14.179887] radeon 0000:01:00.0: registered panic notifier
[   14.179930] [drm] Initialized radeon 2.36.0 20080528 for 0000:01:00.0 on minor 0
[   14.180475] [drm] Memory usable by graphics device = 2048M
[   14.221791] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   14.221886] [drm] Driver supports precise vblank timestamp query.
[   14.260297] fbcon: inteldrmfb (fb1) is primary device
[   15.086147] i915 0000:00:02.0: fb1: inteldrmfb frame buffer device
[   15.096033] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 1
[/FONT]

---

### Post by Tinek on 2015-05-07
Hi QuimNuss,

I should have been a little more specific... What works out of the box is the power management of the discrete card through radeon. And for me that was the goal.

As my system is quite stable, I can do a bit of testing for you! Tell me if you want me to paste some commands outputs, I don't know what you could be interested in.

I didn't get that you had to install fglrx actually, are you sure you have to?

Cheers,

---

### Post by QuimNuss on 2015-05-07
Hey Tinek,

No I don't think the fglrx drivers will work... they haven't ever so far. Since Mint wasn't using the discrete card out of the box I wondered if you had done something else.

So what you have is that the discrete card isn't powered so the fans don't run like crazy, right?

I will see how well is the switching working on Rebecca. I don't think there's anything I'd like to test that I can't test myself, but thanks for offering!

and thanks for the heads-up!

---

### Post by QuimNuss on 2015-07-22
Hey!

So I'm getting back to this. How did you install radeon?

---

