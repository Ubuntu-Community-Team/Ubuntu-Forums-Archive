---
title: "Intel HD 3000 Graphics support for xorg?"
date: 2011-04-13
forum: Hardware
---

### Post by tbessie on 2011-04-13
Hi all...

So I just bought a new Thinkpad T420 with Sandy Bridge chipset and Intel HD 3000 onboard graphics.

I noticed, however, that performance is pretty laggy, and there is nothing provided for "Additional Drivers" (i.e. proprietary drivers, usually for graphics).

Does anyone know the current state of support for this graphics setup?  I found this site: [http://intellinuxgraphics.org/](http://intellinuxgraphics.org/) but I'd have to compile the latest drivers for myself, which I'd rather not bother with if there are prebuilt packages out there somewhere.

Looking at Synaptic Package Manager, it shows the latest version of the Intel graphics drivers available don't even appear to cover this generation of chips.

Does anyone know when full support of Intel HD 3000 (etc) graphics will become part of Ubuntu, even as a backport?

- Tim

---

### Post by wolfen69 on 2011-04-13
You could install the xorg-edgers ppa and install the latest intel drivers via synaptic.

```
sudo add-apt-repository ppa:xorg-edgers/ppa
```
then 
```
sudo apt-get update
```

Or, you could try out ubuntu 11.04, as I hear the drivers are updated.

---

### Post by tbessie on 2011-04-14
> **wolfen69 said:**
> You could install the xorg-edgers ppa and install the latest intel drivers via synaptic.

```
sudo add-apt-repository ppa:xorg-edgers/ppa
```
then 
```
sudo apt-get update
```

Or, you could try out ubuntu 11.04, as I hear the drivers are updated.

Thanks for the suggestions - I took a look at the xorg edgers "statement" [https://edge.launchpad.net/~xorg-edgers](https://edge.launchpad.net/~xorg-edgers) - doesn't make it sound very safe (if I want a working system).

I might just try out the 11.04 beta.  In fact, I'm running one copy of Ubuntu on the bare metal, and another in VirtualBox, so I'll try it out in VirtualBox first to see if I like it and how stable it is.  Of course, that's not the best test since it won't necessarily be using the native drivers for most things, but it'll give me an idea of it.

- Tim

---

### Post by tbessie on 2011-04-16
Well, I just updated to the 11.04 development release, and I can say three things:

1. Graphics seemed to work better (I could get the higher resolution I needed), although that might be due to a setting I missed the first time

2. Graphics on the laptop screen itself was often filled with lots of scary-looking vertical lines at various points, so there are things still to fix

3. I hate the new desktop interface

- Tim

---

### Post by Wlo on 2011-04-18
Do you have switchable graphics?  If so go into the BIOS and set graphics to Discrete rather than Optimus.  This will mean Ubuntu will always use the full blown gfx card rather than the onboard one.  You'll use more power though.

---

### Post by mastablasta on 2011-04-18
> **tbessie said:**
> Well, I just updated to the 11.04 development release, 
 
 
well it means "you used" the edgers PPA as it will be part of 11.04 as stable and then new edgers will be out there.

---

### Post by VogonZarniwoop on 2011-04-18
> 3. I hate the new desktop interface

If you mean Unity, don't worry, not so many people like it :D.  But you can change back to Gnome classic, or I'd recommend installing Kubuntu.  KDE 4.6 is shaping up pretty nicely these days.  There are a few rough edges such as the network manager still crashes if you look at it funny, but generally speaking it's a decently usable desktop and hasn't succumbed to the "dumb it down for the thumb-typing crowd" philosophy that seems to be infesting everything else these days.  It has come a long ways since the early 4.x releases.

---

### Post by no.human.being on 2011-04-30
I'm having Ubuntu 11.04 (Alternate installation, because I needed to set up full disk encryption with dm-crypt) installed on a Lenovo Thinkpad T420 device with an Intel Core i3 2310m inside, which features an integrated Intel HD Graphics 3000 graphics processor on the same die.

First question I have is: How can I find out, which graphics driver is used for the HD Graphics? It seems not to be used as a VESA device, since "glxinfo | grep direct" yields "direct rendering: Yes" so it seems that some Intel-specific device driver is in use, I'd just like to know the exact name of the module.

Now to the real problem: When I connect an external monitor via the DVI-D output on the notebook's docking station (connecting one to a DisplayPort on the docking station or the notebook itself would probably yield the same results, but I cannot verify this since all the monitors I'm using are DVI-only) both, the internal and external screens show a black image with only a mouse pointer on it. I'm able to move the pointer around from one monitor to the other, but that's all. It does not display anything and it will also not respond to a click in the top left corner for example (where the system menu sits), so it's most likely not only a problem related to the frame buffer not getting redrawn. I can shut the system down using magic sysrq (switching to a console with Strg + Fx would probably also work), but that's all. No X11.

When I boot the system with the external monitor connected, it will show a black screen as soon as X11 is started. The GDM login does not show up.

Anyone knows, how to fix this issue, so that I can use the notebook with an external monitor? Anything I need to change in a configuration file or any additional packages I need to install? Or is it just that X.Org or Unity (don't know exactly, whether this is an X11-related or a Unity-related problem) simply don't support SandyBridge hardware well enough, so I'll have to wait until a patch arrives?

Thank you very much.

---

### Post by fjgaude on 2011-04-30
You can see the driver used with this command:

```
sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 18
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:fb800000-fbbfffff memory:e0000000-efffffff ioport:ff00(size=8)
```

The **i915** seems to be what Unbuntu 11.04 is using with my box.

---

### Post by mgbaron on 2011-05-02
Hi everyone,

I just took delivery of my new ThinkPad 420s this morning with Intel HD Graphics 3000 acceleration and I'm seeing the same problem as no.human.being.  When I connect my 1920x1080 monitor via DisplayPort --> hdmi, on the connected monitor I only see the title bar and mouse pointer, the rest of the screen is black.

Also, the desktop search seems really sluggish.  Not the search itself, but the GUI which lags several seconds behind my typing and sometimes hangs up unpredictably.

Any help would be greatly appreciated.

Matt

Not sure if this is helpful:
```

>sudo lshw -C video
[sudo] password for matt: 
  *-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:49 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:4000(size=64)
```

---

### Post by no.human.being on 2011-05-03
The problem still exists when in a classic GNOME session instead of Unity. It even exists when Compiz is disabled. So the 'i915' module seems to be faulty. Could someone please verify, whether this bug appears on notebooks from other vendors (not Lenovo systems) or even desktop systems as well, when the internal Intel HD Graphics is used? If so, we might file a bug report to the developers of the 'i915' module. If not, then it might be something specific to the hardware used within Lenovo systems and not a problem with the Intel HD Graphics.

---

### Post by brianjhu on 2011-05-04
Another T420 with the external monitor (Acer V223w connected via VGA) issue in 11.04. I can make the laptop screen be the "dead" one if I move the external to the left of the laptop. Also, the "good" monitor shows a black bar for the top 15% or so.

---

### Post by donalgodon on 2011-05-04
so, is this a driver issue related to Sandy Bridge?

I do notice that the picture quality via HDMI is not as good as it is over Win-doze 7 with the ATI drivers in my Dell Sandy Bridge laptop with HD3000 graphics.

---

### Post by WilliamAnderso on 2011-05-04
Hello. I'm also having similar problems with 10.04 on my laptop; however, my laptop refuses to recognize it when an external monitor is connected. Honestly, I'd be happy with laggy/fuzzy performance. Here's the information on my video controller;

wanderso@araran:/etc/brightscope$ sudo lshw -C video
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
       resources: memory:c0000000-c03fffff memory:b0000000-bfffffff(prefetchable) ioport:6000(size=64)

I piped the full output of sudo to a file with neither monitor port plugged in, the monitor connected to the analog port, and the monitor connected to the HDMI port, and none of the lshw output changed for any of that. Incidentally, the monitor is a Samsung SyncMaster SA350 and the laptop is a HP Pavilion dv6-6013cl if that helps.

---

### Post by arkban on 2011-05-04
I recently purchased a T520 with an i7 and also am similar having issues. I find that videos (Totem, VLC) can freeze Gnome, requiring a hard-reboot. Also sometimes when opening new tabs in Firefox.

I'm running Linux Mint 10 (built on Ubuntu 10.10). I'm adding my "sudo lshw -C video" in case it might the investigation in someway:
```

  description: VGA compatible controller
       product: Sandy Bridge Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:48 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:5000(size=64)

```

---

### Post by le_gudeg on 2011-05-08
Same problem here, got external monitor plugged and the screen were just blank. The left palm rest are also bit hotter.

---

### Post by no.human.being on 2011-05-17
It just seems to magically work now. At least on classic GNOME. Haven't tested on Unity yet, since I prefer classic GNOME anyways. However, you need to run in a dual-view configuration (internal AND external monitor running). If you disable the internal panel, the framebuffer output device seems to get disabled, so no output to external display either.

I'm glad to see such an improvement.

---

### Post by egon.olsen on 2011-06-08
> **no.human.being said:**
> ...However, you need to run in a dual-view configuration (internal AND external monitor running). If you disable the internal panel, the framebuffer output device seems to get disabled, so no output to external display either.


@ [no.human.being]("http://ubuntuforums.org/member.php?u=1185897"), what exactly did you mean with "dual-view configuration". Did you refer to the xorg.conf setup in this way or having the external screen connected all the time?
I am running the edgers ppa drivers on the intel-next-proposed kernel on my i7 T420 with on hd 3000 graphics and things have not improved. I was running standard kernel before. The system still is very unreliable. Random crashes ~1-2 a day, sometime x not refreshing when disconnecting external screen, etc.

Tried Mint Katya, as I read somewhere things were better there - they weren't. Some problems with Fedora 15. It is awefull. Shame to have spend so much money. I have been using Ubuntu for 6 years now but I fear I have to go back to Windows, soon. I cannot have the system crash midway through my work.

---

### Post by ShakataGaNai on 2011-06-09
Want to chime in saying that I have much the same problem.  I have a brand new Dell Latitude E6320 running 11.04.  It's got an i7 & the HD 3000.

I've not tested the HDMI yet, but when I plug the VGA in, half my on board screen goes black and the external monitor only shows the title bar.  I can mouse onto the external screen and such like that, but it isn't useful.

Output:
```
root@WMF331:~# lshw -C video
  *-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:e1400000-e17fffff memory:d0000000-dfffffff ioport:4000(size=64)
root@WMF331:~# uname -ra
Linux WMF331 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by wangston on 2011-06-29
[LEFT]me too. thinkpad t420, i7, intel hd 3000, and no dual monitor with 11.04

interestingly, 10.10 seems to work okay. i'm not sure how to figure out what changed between 10.10 and 11.04, whether it's possible to revert just the drivers to the 10.10 version, or what the likelihood is of a future update fixing it.

i'm thinking i will downgrade to 10.10, and if that proves unworkable, go back to windows and maybe try again with 11.10?
[/LEFT]

---

### Post by donalgodon on 2011-06-30
Hope somebody gets on this, because it's a real show-stopper for many folks.

---

### Post by Grelf on 2011-06-30
I'm RMA'ing my shiny new System 76 latop because of this issue.

Unless a fix comes out before they get me the RMA information. ;)

---

### Post by anewbie on 2011-07-02
I just built a z68 system with asrock extreme4 and it seemed to run fine with 11.04. Is there a specific issue I should be looking forward to encountering ?

---

### Post by no.human.being on 2011-07-06
> **egon.olsen said:**
> @ [no.human.being]("http://ubuntuforums.org/member.php?u=1185897"), what exactly did you mean with "dual-view configuration". Did you refer to the xorg.conf setup in this way or having the external screen connected all the time?

No. You can use the internal panel only or you can use both, the internal panel (notebook) and the external monitor. If you disable the internal panel (either by disabling it in "System --> Settings --> Screen" or by closing the laptop lid) the external monitor gets disabled as well. There is no way to use external only, like one might sometimes like to when the notebook is docked. So you're definitely forced to using both, internal and external display, in dual-view, or refrain from using the external display device at all. Seems the video controller is somehow "linked" to the internal display, so that internal display disabled => video controller disabled => no picture at external monitor either.

You can disable the external screen (by disconnecting it or simply disabling it under "System --> Settings --> Screen") and use the internal display only, but you cannot disable the internal panel and use external only. If you try to, the whole graphics device gets suspended, so that there's no signal for the external display device either.

Sorry if this was a bit unclear at first. English is not my first language.

---

### Post by kgolick on 2011-07-08
Can you guys explain for a newb how did you made this to work? I purchased today a Intel I5 2500k + a H67 chipset mainboard, with Intel HD graphics 3000 and i can't select more than 1024 x 768 screen resolution. 
I'm using ubuntu 11.04

*-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:49 memory:fe000000-fe3fffff memory:e0000000-efffffff ioport:f000(size=64)

Thank you!

---

### Post by Gecko123 on 2011-08-07
I have similar problems with an external monitor (VGA and HDMI) as described by many other users in this thread. The last post is four weeks old. Is there any development in this direction?

Kind regards

---

### Post by AbsoluteHeero on 2011-08-12
i have a similar problem.

whenever i play The Longest Journey with my 32" HDMI TV hooked on my DEll xps15, everything works fine, great FPS and all that. But as soon as I unplug my TV and just want to play on my laptop screen i can't see the cutscenes from the game. to view them i absolutely have to play in "windowed" mode and ALSO I have to click and drag  beginning outside the "windowed" game (desktop) and then inside of it, and i have to keep moving the mouse in order to see the video properly. If i stop moving the mouse, the video freezes.

so i'm left wondering, is this a screen problem rather than my Intel HD 3000. or both. I Freaking don't know.


please help

---

### Post by JamesAng on 2011-08-16
Hi all,

I'm using E3-1235 with C206 chipset.
Also encountered the same issue with HD3000 graphic driver.

Is there any update on this issue to resolve the lack of support for the HD 3000 iGPU?

Thanks.

---

### Post by talthing on 2011-08-18
This fix worked great !

Samsung Series 3   (i2357 chip)  Ubuntu 10.04.3  (kernel 2.6.38 )

Intel HD 3000 controller not recoginzed Ubuntu 10.04
(symptom: main menu - administration - preferences - monitors shows 'unknown'
unable to configure any external monitors)

Fix:

Step 1 - update kernel to 2.6.38

Step 2 - add repository
sudo add-apt-repository ppa(colon)xorg-edgers/ppa

Step 3 download updates
sudo apt-get update

Step 4 launch update manager and install updates

Step 5  reboot


Check: main menu - Administration - preferences - monitors
you should see 'Laptop'

---

### Post by homeyclaus on 2011-09-21
For some systems, turning on the semaphores in the kernel intel graphics driver helps. In others, it can make it worse, but it's worth a shot, since the results have been promising.

Adding i915.semaphores=1 to the kernel command line (do this by typing 'e' at the GRUB screen and adding it to the line with the text vt.handoff in it).

To make the change permanent, you need to edit /etc/default/grub and add it like this:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.semaphores=1"

Lastly, today's kernel update for 11.04 also has some intel lockup fixes in it.

Hope that helps!

---

### Post by drivindisco on 2011-12-01
Has anyone got any news on this issue? I am running 11.04 on thinkpad e520 core i3-2310m and hd 3000 graphics. Not even sure if these are the same issues, but I'm having glitching of the graphics with in application windows.  When I use gedit or the terminal in particular, the text will jumble up and entire lines will go black. It makes it really hard to use as I normally notice this happening when doing coding assignments for school, since I'm constantly popping back and forth between them and scrolling a lot.  

Also, overall the graphics performance (with or without compiz enabled0 is significantly diminished from using Windows 7 64-bit pro. Programs seem to open slowly and gnome seems to take longer than usual to start on boot. I really hate to use windows and prefer using Ubuntu, but I am almost at my wits end with this. I purposely bought this laptop, b/c it was "ubuntu certified." It may be due to the "newness."

Any help would be greatly appreciated!

---

### Post by MoreOrLess on 2011-12-01
[http://www.phoronix.com/scan.php?page=article&item=intel_sna_september&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_sna_september&num=1)

Unfortunately, you'll probably have to wait until Precise/12.04 to get SNA by default. Until then, there's always the xorg-edgers PPA if you're feeling adventurous..

---

### Post by sonsnix on 2011-12-02
I added the xorg-edgers PPA and did an "sudo apt-get update" and upgrade.
I'm not sure though whether the new driver version is in use, lshw still gives me driver="i915" but no specific version.

My issue is, that WebGL doesn't work in Chrome. It will always say "your browser seems to support WebGL, however your graphics card doesn't seem to..." or something like that.

Any tips on WebGL?

---

### Post by cjhcv on 2012-02-13
> **talthing said:**
> This fix worked great !

Samsung Series 3   (i2357 chip)  Ubuntu 10.04.3  (kernel 2.6.38 )

Intel HD 3000 controller not recoginzed Ubuntu 10.04
(symptom: main menu - administration - preferences - monitors shows 'unknown'
unable to configure any external monitors)

Fix:

(...)

Check: main menu - Administration - preferences - monitors
you should see 'Laptop'

Hi,

I'm having the same problem here with a desktop running 10.04.3 LTS. I just did the proposed fix but monitor still shows as UNDETECTED and cannot go beyond 1600x1200 when native resolution is 1900x1080 (DELL 2405FPW). My config is i5 2500k on GA-Z68A-D3H-B3 (so Intel HD 3000), and connection is through DVI. After applying the fix I get:

$sudo lshw -C video
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
       resources: memory:fb800000-fbbfffff memory:e0000000-efffffff(prefetchable) ioport:ff00(size=64)

$uname -a
Linux 2.6.32-38-generic #83-Ubuntu SMP Wed Jan 4 11:12:07 UTC 2012 x86_64 GNU/Linux

I installed before 11.10 and it got to native resolution ok, but due to some stuff I'm back to using 10.04.3 LTS and planning to use it for a long while.

Any ideas? Thanks,

Carlos

---

### Post by GusPS on 2012-03-06
I'm facing the same problem. There's still no solution I guess. I've filled this launchpad bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/912397](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/912397)

Here is another thread: [http://ubuntuforums.org/showthread.php?t=1465764&page=2](http://ubuntuforums.org/showthread.php?t=1465764&page=2)

---

### Post by KarthikShenoy on 2012-05-03
Hi all ,
Intel recently released the drivers(23-Apr-2012)
[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=13815&ProdId=3231&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=13815&ProdId=3231&lang=eng)
Worth a look.
PS no arguments about Unity being problematic. Most of the people who use windows in workplace will have hard time getting used to both of the different UI.
Hope Unity pays off in the iOS battle :):):)

---

### Post by MonkeyPaw on 2012-05-03
I'm using the HD 3000 with my i3 2125 on 12.04, and the graphics are just great. Unity runs in 3D, scrolling is fast, and I don't see any artifacting or glitches. That's running with no special mods or drivers. Couldn't be happier.

---

### Post by GusPS on 2012-05-03
> **KarthikShenoy said:**
> Hi all ,
Intel recently released the drivers(23-Apr-2012)
[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=13815&ProdId=3231&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=13815&ProdId=3231&lang=eng)
Worth a look.
PS no arguments about Unity being problematic. Most of the people who use windows in workplace will have hard time getting used to both of the different UI.
Hope Unity pays off in the iOS battle :):):)

I only see the 23-feb-2012 version. I'm using the edgers PPA, which I believe has the latest intel driver version, but although that, it doesn't work. I'm starting to think this is not a video driver problem. Maybe a display that receive an invalid turn on/off directive.
I test a lot of things. More info in the link I left on previous posts.
Thanks!.

---

### Post by MrTKusa on 2012-06-26
> **MonkeyPaw said:**
> I'm using the HD 3000 with my i3 2125 on 12.04, and the graphics are just great. Unity runs in 3D, scrolling is fast, and I don't see any artifacting or glitches. That's running with no special mods or drivers. Couldn't be happier.

I have an HP Pavilion DM4 with the HD3000 on the i3-2330.  I have installed 12.04 but then ran into the Black screen after first reboot.  I have set the GRUB file to GRUB_CMD_LINUX="nomodeset" and I can logiy question is n without going through recovery.  My question is: Is there something better I could do to utilize my Intel HD 3000 graphics better?

Any help would be so appreciated.   BTW: I am a Linux noobie so please explain it as to a child :lolflag:

---

### Post by GusPS on 2012-06-26
Hi. See this LP bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/912397](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/912397)

What have worked on my PC is the drm_kms_helper.poll=0 kernel param.

---

