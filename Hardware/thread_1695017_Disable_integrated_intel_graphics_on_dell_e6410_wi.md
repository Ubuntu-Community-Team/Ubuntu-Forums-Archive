---
title: "Disable integrated intel graphics on dell e6410 with nvidia nvs3100m"
date: 2011-02-25
forum: Hardware
---

### Post by arkangelboss on 2011-02-25
Hi all,

I've been looking for a solution for weeks, but with no luck. While I've been able to overcome the working problems and boot correctly on the discrete graphics, I can see that the integrated graphics in the core i5 is uselessly working, draining power and causing problems with the turbo and drivers as described by other users.

Is there a way I can completely disable such an annoying piece of silicon and let the system go ignoring it?

Regards.

---

### Post by Yellow Pasque on 2011-02-25
Only in the BIOS would you find such a setting assuming your vendor included it. A lot don't, so you're basically screwed if you don't have one (make sure it hasn't been included in a BIOS update).

---

### Post by arkangelboss on 2011-02-25
Unfortunately I have no way through the bios. It's a shame in a business class laptop.
Any OS level solution would be great.
Thanks

---

### Post by Yellow Pasque on 2011-02-25
[http://www.google.com/search?q=%22vga_switcheroo%22](http://www.google.com/search?q=%22vga_switcheroo%22)

---

### Post by arkangelboss on 2011-02-25
> **Temüjin said:**
> [http://www.google.com/search?q="vga_switcheroo"](http://www.google.com/search?q="vga_switcheroo")

from what I can understand this tool/procedure is aimed at hybrid gpus. My case is much simpler: only the discrete gpu is cnnected to output, while the integrated stays there laughing to me. I don't need it to be on at all. I think there is some big mess in the engineering behind this iussue, but I also hope to find a workaround.

Thanks.

---

### Post by Yellow Pasque on 2011-02-25
:lolflag:

---

### Post by arkangelboss on 2011-03-03
Any other suggestions? Anyone? It would be great to fix such a messy condition, the i915 also suffers from the [turbo problem]("http://ubuntuforums.org/showthread.php?t=1594981&highlight=i915+failed+symbols") and slows the boot down... I really don't want it to stay up and laughing.

Thanks.

---

### Post by mtron on 2011-03-03
you need a acpi_call to turn this beast off. Have a look at [http://linux-hybrid-graphics.blogspot.com](http://linux-hybrid-graphics.blogspot.com) and the mailing list at [https://launchpad.net/%7Ehybrid-graphics-linux](https://launchpad.net/%7Ehybrid-graphics-linux) if there is already a known call for your model available else you need to do some digging in the dsdt file of your hardware.

EDIT: arr seems it's the other way around in your case... sorry

---

### Post by arkangelboss on 2011-03-04
> **mtron said:**
> you need a acpi_call to turn this beast off. Have a look at [http://linux-hybrid-graphics.blogspot.com](http://linux-hybrid-graphics.blogspot.com) and the mailing list at [https://launchpad.net/%7Ehybrid-graphics-linux](https://launchpad.net/%7Ehybrid-graphics-linux) if there is already a known call for your model available else you need to do some digging in the dsdt file of your hardware.

EDIT: arr seems it's the other way around in your case... sorry

You are right mtron, there seem to be many possible approaches to turn off a discrete gpu in an hybrid setup, while nobody cares turning an integrated (and non-functional) off. Although, I will try to learn something from the sources you have suggested.

Any other ideas are welcome!

Thanks.

---

### Post by arkangelboss on 2011-03-21
Anybody else with other ideas?

---

### Post by nbubis on 2011-06-25
Hi, 

I'm having the opposite problem on the E6410 - namely the intel GMA is not detected. I've posted a new thread here:

[http://ubuntuforums.org/showthread.php?t=1790103](http://ubuntuforums.org/showthread.php?t=1790103)

It seems the options you have are the ones I need and vice versa - maybe we can figure this one out together. Can you post your boot options?

```
cat /var/log/dmesg | grep BOOT_IMAGE
```

---

### Post by arkangelboss on 2011-06-26
Hello nbubis, 

here is the BOOT config you requested: 
> [    0.000000] Command line: BOOT_IMAGE=/vmlinuz-2.6.38-8-generic root=UUID=53d5d9d7-0844-465e-b7d1-* ro nouveau.modeset=0 acpi_osi=\"!Windows 2009\"
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.38-8-generic root=UUID=53d5d9d7-0844-465e-b7d1-* ro nouveau.modeset=0 acpi_osi=\"!Windows 2009\"I had to add the nouveau.modeset=0 to force NVIDIA on first boot after installing ubuntu 10.10, while the acpi_osi=\"!Windows 2009\ to make the advanced keyboard functions working (volume, brightness, ecc).

Regarding your problem, my information suggests the INTEL is NOT CONNECTED to any output frame buffer, so DELL simply didn't put the connections to the video output. That's what is making me angry ](*,) there is a USELESS piece of silicon constantly draining power at no use (almost, because the memory controller is ATROCIOUSLY fitted IN the integrated card).

Till now I had no luck in deactivating the Intel graphics, but it has not given me bigger problems apart from slowing the boot down around 10 secs. I also don't think I will ever solve this issue because the memory controller and the IGP are probably power dependent on each other...

---

### Post by nbubis on 2011-06-26
This doesn't make any sense:

We both have the same laptop with intel + nvidia, yet yours shows up in lspci whereas mine doesn't. If indeed "DELL simply didn't put the connections to the video output" - why would it show up on your machine?
alternatively, if it's not showing up in lspci (by me) it would seem that it's not draining power since it's not connected.

---

### Post by arkangelboss on 2011-06-28
> **nbubis said:**
> This doesn't make any sense:

We both have the same laptop with intel + nvidia, yet yours shows up in lspci whereas mine doesn't. If indeed "DELL simply didn't put the connections to the video output" - why would it show up on your machine?
alternatively, if it's not showing up in lspci (by me) it would seem that it's not draining power since it's not connected.

Well, the answer is that the i915 actually doesn't show up in my lspci too, but I'm almost sure it's on because of the Arrandale architecture: the memory controller is placed in the same piece of silicon as the graphics, and the OS knows about the i915 on boot.

I'm looking for accurate information about this so I may be wrong, of course.

---

### Post by nbubis on 2011-09-04
Hi all, Just had an interesting discussion with DELL support. Dell answers in blue.

> Hello, I'd like to ask a technical question regarding the E6410, with an NVIDIA 330M card. I'd like to know if Dell has disabled the built in Intel card in the BIOS, since it appears not to be accesiable.

[COLOR="Blue"]In line with your concern, the integrated Video Card is being disabled every time a video card such as NVIDIA is being address to the system.[/COLOR]

Ok. I don't think this is a hardware problem - I think this is a BIOS issue, but I'd like to confirm this.

[COLOR="blue"]Yes, this is not a problem. It is working as designed.[/COLOR]

Ok. so you are confirming that I cannot activate the intel graphics card??

[COLOR="blue"]However, Intel card will still function as video accelerator.
Yes, you will have to use only one video card.[/COLOR]

I'm not understanding . Assume I can shut off the NVIDIA card (through my operating system), can I or can I not accelerate graphics through my intel card?

[COLOR="blue"]Yes, that is possible, but your computer was designed to work properly with NVIDIA since the motherboard was designed to use Video Card and not the integrated one.[/COLOR]

Yet once I deactivate the NVIDIA card, the intel card does not seem to be connected. Is the only way to activate it turning the NVIDIA card off through the BIOS?

[COLOR="blue"]It is not advisable to do that.[/COLOR]

Again, so If I deactivate the NVIDIA card (through my OS), the intel card should be connected and running? this does not seem to be the case.

[COLOR="blue"]Yes, that is not possible since the Intel is only designed to help nvidia in processing graphics or videos. May I know why you would like to use Intel card instead of Nvidia?[/COLOR]

I would like to switch off the NVIDIA while not using it to save power and lower system temperature. I still need some video acceleration to use basic desktop effects. This is possible on similar (non-optimus) laptops such as the Lenovo's T410.

[COLOR="Blue"]I am very sorry to inform you that the option you want is not available.[/COLOR]
	
Can you explain where the problem is (software / bios / hardware)?

[COLOR="Blue"]No problem on the hardware or BIOS, it is just not an option for your system.
However, I suggest that you download an update for the Intel driver through Intel web site.[/COLOR]

I understand this is Intentional, I am trying to understand whether or not this can be fixed (say by a new intel or NVIDIA driver, an option in my linux OS etc..).
	
[COLOR="blue"]It may be possible if you will try to download and updates for your Intel Video Card. But again, there is no assurance that it will work 100%, but you can try.[/COLOR]

Ok. So you are saying that the intel card is not disconnected in any way. That is important.

[COLOR="blue"]Yes[/COLOR]

What do you guys make of this?

---

### Post by mrv on 2011-09-06
Interesting thread(s). So indeed we are all in the same boat apparently in that NVIDIA is currently forced into use, although there are a few mentions about i915 during boot but not in lspci. So far none of my attempts in using the acpi_call, byo-switcheroo or ironhide/bumblebee have worked, and the latter I guess are simply because E6410 is not "Optimus" ie. dual working graphics laptop? However, I haven't yet tried anything manual, just checking eg. test_off.sh etc.

I'm not interested in hybrid graphics anyway, and all I would like to do is that I'd like to turn NVIDIA off (and Intel on) by any means possible, since it really feels like the machine is draining battery a lot, and I like Intel graphics better anyway regarding (free) driver support. And yes this is my work laptop so I didn't have a choice to have Intel-only laptop since this was the only E6410 available. It doesn't of course hurt if the nvidia is on reserve.

I posted my DSDT data (as instructed on the launchpad page) on the Launchpad bug report and reported it on the linux-hybrid-graphics mailing list. You can of course compare yours to mine, or maybe point out if you can make out something out of it ie. some possibly interesting bits two poke via acpi_call.

It's good if switching to Intel is at least theoretically possible, although I wasn't yet really convinced about the Dell discussion above.

ps. I tried briefly the nvidia proprietary driver as well, somehow at least on 11.10 it was a pain to install so that it'd actually work - and then magically on another jockey attempt it worked... in the end it didn't seem to give more battery life, and the tools mentioned didn't work any better, so I reverted to nouveau which even has 3D acceleration working in 11.10

---

### Post by arkangelboss on 2011-09-06
I can confirme that the e6410 is not an optimus notebook, so there is no hardware supporting the switch betweet cards. 

Moreover, what appears to me is that there is actually no electrical connection between the Intel card and any video output: I didn't find any evidence the integrated card can produce video output, but it has to stay on (I can just figure out that's because of the memory controller built into it).

The question is: is there any way to turn the graphics off and leave the memory controller on?

---

### Post by mrv on 2011-09-06
Ok, I thought Optimus was about being able to use both at the same time, and that not having it wouldn't rule out switching between them.

---

### Post by nbubis on 2011-09-06
arkangelboss & mvr - 

one thing we could test is disabling the nvidia card through the bios, and use a install disk to see whether or not the intel card gets detected. I have a hunch this a intel driver problem.

---

### Post by mrv on 2011-09-06
> **nbubis said:**
> one thing we could test is disabling the nvidia card through the bios, and use a install disk to see whether or not the intel card gets detected. I have a hunch this a intel driver problem.

I haven't seen such an option in the E6410 BIOS?

Anyway, I'll try nouveau.perflvl_wr=7777 nouveau.perflvl=0 for now to underclock the nvidia and thus lessen power drain. It seems to work.

---

### Post by arkangelboss on 2011-09-06
> **mrv said:**
> I haven't seen such an option in the E6410 BIOS?

Anyway, I'll try nouveau.perflvl_wr=7777 nouveau.perflvl=0 for now to underclock the nvidia and thus lessen power drain. It seems to work.

I couldn't find a way to disable the Nvidia card through the bios too. 

@nbubis: maybe I was too interested in getting rid of the Intel... Now I think it would be a good thing to have it REALLY working. In this [thread]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/561802") people says many bugs with the Intel driver have been solved in recent kernels, so if your proposed scenario was possible (INTEL is connected and capable of producing video output, NVIDIA can be disabled) we could have something interesting to test. Unfortunately I have no evidence other than Dell words for the first and no evidence at all for the latter.

@mrv: I am using the official Nvidia driver supported in Natty, I had to force nouveau.modeset=0 when installing Maverick because of a black screen bug. Is it possible to implement the Nvidia downclock with the official driver on?

---

### Post by mrv on 2011-09-06
> **arkangelboss said:**
> 
@mrv: I am using the official Nvidia driver supported in Natty, I had to force nouveau.modeset=0 when installing Maverick because of a black screen bug. Is it possible to implement the Nvidia downclock with the official driver on?

Well the default driver for Nvidia in Ubuntu is the open nouveau driver, so it's at least as official as the separately installable nvidia driver :) On Oneiric, there seems to be finally no black screen problem with the default driver, so I just installed Ubuntu from the 11.10 beta 1 CD when I got this laptop.

When I was checking out the proprietary driver, I saw some clock options in the nvidia-settings, but somehow they were disabled. As I had quite a difficulty in installing the drivers in the first place, and I didn't have any obvious need for them, I went back to the default nouveau driver.

The underclocking (nouveau.perflvl_wr=7777 nouveau.perflvl=0 ) to the lowest power level does have a visible performance penalty, though, but still snappy enough for me I think. I use the somewhat lighter Unity 2D now since it's quite great now in 11.10 and doesn't actually look much at all different from Unity 3D anymore. However, the default 60Wh battery now finally seems to last well over 3h of work, while before it seemed to drain the battery in something like 1.5h even. The laptop is used so actually it's more like 50Wh battery nowadays. I guess though that it really should be ca. 4-5h optimally on this laptop, so maybe there is more to be done.

---

### Post by arkangelboss on 2011-10-25
Thanks mrv, I have a look at the nouveau driver in 11.10__

---

### Post by nbubis on 2012-07-21
Just wondering:
Did any of you (arkangelboss & mrv) get anywhere on this issue in the last year? The short battery life is driving me nuts, and I was wondering if you have perhaps found a solution.

Thanks!

---

### Post by arkangelboss on 2012-07-23
> **nbubis said:**
> Just wondering:
Did any of you (arkangelboss & mrv) get anywhere on this issue in the last year? The short battery life is driving me nuts, and I was wondering if you have perhaps found a solution.

Thanks!

Nope... I studied the issue for a while, but the issue seems inescapable: the natural way to go would be to power off the intel video chip altogether (since it is not connected to the output anyway), but there is no option at the bios level to do so.

Cutting power to the graphic chip also appears to mean we power off the memory controller, which shares the same silicon...

No luck until now...

---

### Post by nbubis on 2012-07-24
What about powering off the nvidia? any luck with that?
I'll be trying to underclock the nvidia card, I'll post results if that helps any.

---

### Post by arkangelboss on 2012-07-24
> **nbubis said:**
> What about powering off the nvidia? any luck with that?
I'll be trying to underclock the nvidia card, I'll post results if that helps any.

The nvidia has to stay on because it is the only card connected to video out.
It would be nice to change the powermizer settings in order to make the nvidia stay down in clock and energy: I have only been able to find a way to disable powermizer, but this leaves the card on high performances.

If you have any suggestions they are certainly welcome!

---

