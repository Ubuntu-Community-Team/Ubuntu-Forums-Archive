---
title: "Display issues with HP 6710b laptop (Intel GMA X3100 UMA  video card)"
date: 2007-05-23
forum: Hardware &amp; Laptops
---

### Post by smylie on 2007-05-23
Hi 

I've just got this laptop (insurance replacement, would not have been my first choice =). I'm unable to start up X at all on this computer.
I've been able to install feisty using the text based install on the Alternate CD, and starts up fine, displays splash screen etc, but drops back to command prompt every time X is about to load.

I've tried editing the xorg.conf to use both the VESA and I810 drivers, but get messages like this:

(WW) I810: No matching Device section for instance (BusID PCI:0:2:1). (may not be exact that's from memory =)

I've tried emerging the xserver-xorg-video-intel package, and changed the driver in xorg.conf to "intel".  X seems to start up at this point (the screen seems to initialise), but just goes black and the computer becomes mostly unresponsive. Caps-Lock key still toggles the caps-lock led, but I'm unable to use Control-Alt-Backspace to crash out of X to try something else. At this point I need to boot back off the rescue CD so I can change the the xorg.conf driver away from intel so the laptop doesn't boot straight back into the same problem = /

According to wikipedia ( [http://en.wikipedia.org/wiki/Intel_GMA#GMA_X3100](http://en.wikipedia.org/wiki/Intel_GMA#GMA_X3100) ) the X3100 uses the Mobile 965GM chipset which is supported under linux (as of May 2007). 

Does that mean I just have to wait for this to be included in the ubuntu repositories? 

Thanks
Dave Smylie

---

### Post by smylie on 2007-05-24
Further information from a few more hours digging round . . .

the wikipedia states that the  965GM chipset is supported from version 2.0 onwards - this is the version in the feisty repo's so the driver should support it. Sure enough, in Xorg.log it detects it.

(II) intel(0): Integrated Graphics Chipset: Intel(R) 965GM
(--) intel(0): Chipset: "965GM"


(EE) GARTInit: Unable to open /dev/agpgart (No such file or directory)
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?

the intel_agp module wasn't loaded automatically - i modprobe'd it (and chucked it into /etc/modules), and no errors came back on command line or dmesg.

However - /dev/agpgart is still missing and the above error still remains.  I have specified 128M VideoRam (i believe the max for these cards) 

Section "Device"
        Identifier      "Generic Video Card"
        Driver            "intel"
        VideoRam    128000
         BusID           "PCI:0:2:0"
EndSection

However, the log shows it's only picking up 8M

(EE) GARTInit: Unable to open /dev/agpgart (No such file or directory)
(WW) intel(0): /dev/agpgart is either not available, or no memory is available for allocation.  Using pre-allocated memory only.
(**) intel(0): VideoRam: 7676 KB

I'm not sure of whether that's caused by /dev/agpgart being missing or because I need to configure the bios to allocate the videocard memory. (I had to do that for my old computer, but in the bios of this one, there's no mention of the video card at all)

Any one got any ideas on where I could go from here? (With the current goal being to work out why my /dev/agpgart is gone . . .)

Cheers
Dave

---

### Post by bimbo on 2007-06-09
You might want to take a look at [http://www.intellinuxgraphics.org/install.html](http://www.intellinuxgraphics.org/install.html) if you didn't already.

However, since I'm actively considering that very notebook (the 1680x1050 version) to run Ubuntu on myself, could you comment on build quality and overall impression?

---

### Post by neptho on 2007-06-09
Try adding the following to your /etc/modules:

```
intel_agp
agpgart
```

Then reboot and see if it loads AGP support.

---

### Post by smylie on 2007-06-09
I've actually been very disappointed with this laptop so far.

I had to use to use the Alternate Install CD as it couldn't start X winders in the normal live cd. Even with the Alternate Installer, I couldn't get X to run afterwards. I needed to get the latest intel video drivers from their git repository and compile those + my own custom kernel. (Which also meant had to work out how to do the Intel wireless custom compile as well, which was a real pita .. . . )

Literally took about 4 days to get this laptop into a useable state, which is seriously not cool.


Anyway, having finally got X to run, compiz / beryl won't work, and the monitor is blurry. (see [http://ubuntuforums.org/showthread.php?t=464907](http://ubuntuforums.org/showthread.php?t=464907) )

About the only thing that has impressed me is that suspend and hibernate worked out of the box - first laptop I've seen do that.

I think the main problem is that the laptop is too new - the first version of the video driver was only released about 3 or 4 weeks ago, so it's not incorporated into any distributions yet. This should change, (and hopefully one of the newer drivers will resolve my screen issues).

I'm about to give gutsy gibbon a try shortly - will let you know how it goes . . .

Cheers
Dave Smylie

---

### Post by bimbo on 2007-06-09
Sounds like maybe the driver doesnt actually use the truly proper resolution?

Maybe you need 915resolution like with 915 and 950 chipsets?

But other than the issues with X (which should sort out themselves over time, I can deal with that) does it feel solidly built?

The fact that suspend and hibernate works is a very good sign already ;)

---

### Post by smylie on 2007-06-09
> **bimbo said:**
> Sounds like maybe the driver doesnt actually use the truly proper resolution?

Maybe you need 915resolution like with 915 and 950 chipsets?

But other than the issues with X (which should sort out themselves over time, I can deal with that) does it feel solidly built?

The fact that suspend and hibernate works is a very good sign already ;)
That's what I thought - but it is (as far as I can tell) running at the right resolution - everything is the size I'd expect, and xdpyinfo etc return that it's running at 1650x1080 so go figure . . .

Unfortunately 915resolution doesn't support the chipset on this card (yet?). I'm not sure if it ever will given the new intel modesetting drivers can supposedly do everything 915resolution can do . . . 
(Having said that, I just used the 915resolution binaries from the fiesty repo's - it's possible a newer version does support it).

But yeah, apart from the screen, it's pretty good. The internal speakers are adequate, the touch sensitive audio controllers work out of the box, (volume, mute etc), card reader works. Haven't tried bluetooth yet, but I'm not anticipating any issues there. 

However, the screen is a HUGE downer. I would recommend **strongly** against this laptop until these issues are sorted.

Cheers
Dave Smylie

---

### Post by ramjet_1953 on 2007-06-09
You could always try the new Intel driver;

Copy and paste this into a terminal:

[COLOR="Red"]sudo apt-get install xserver-xorg-video-intel[/COLOR]

After it has done it's thing just re-boot.

Hopefully, it will have done the right thing.

Regards,
Roger :cool:

---

### Post by bimbo on 2007-06-10
How about noise? there are some reports about it spinning the fan near constantly? 

Some older HP notebooks can control the fan from software according [http://www.debianhelp.org/node/3731#comment-8166](http://www.debianhelp.org/node/3731#comment-8166) I wonder if that works on the 6710b too, must see if I can get one for testing somewhere...

---

### Post by smylie on 2007-06-10
> **bimbo said:**
> How about noise? there are some reports about it spinning the fan near constantly? 

Some older HP notebooks can control the fan from software according [http://www.debianhelp.org/node/3731#comment-8166](http://www.debianhelp.org/node/3731#comment-8166) I wonder if that works on the 6710b too, must see if I can get one for testing somewhere...
Yeah - the fan is pretty loud when it's going. It isn't constant, but does seem to be going more often than not. It hasn't been enough of an issue for me that I've looked into seeing weather or not I can control it . . .

---

### Post by smylie on 2007-06-10
> **ramjet_1953 said:**
> You could always try the new Intel driver;

Copy and paste this into a terminal:

[COLOR="Red"]sudo apt-get install xserver-xorg-video-intel[/COLOR]

After it has done it's thing just re-boot.

Hopefully, it will have done the right thing.

Regards,
Roger :cool:
Hi ramjet - thanks for the suggestion, but i'm already using the latest intel drivers from the git repository.

---

### Post by bimbo on 2007-06-10
Thanks for the comment on fan noise. I don't think this is an option for me, then :(

---

### Post by smylie on 2007-06-10
> **bimbo said:**
> Thanks for the comment on fan noise. I don't think this is an option for me, then :(
I really wouldn't consider the fan noise to be an issue (it's no better or worse than any other laptop I've tried).

If you can live with the screen quality, you can certainly live with the fan =)

---

### Post by bimbo on 2007-06-11
Well on my current Toshiba, fan barely ever (unless I keep it at full load for 1+ min) spins on.

On a T60 I recently used, I at least had the option to override fan control but otherwise it would have disturbed me a lot (though there mostly the ATi GPU was at fault, the thing runs HOOOOT).

If I can convince Lenovo to give me international warranty on a T61, I'm gonna buy that one for sure as price is about the same as are specs.

---

### Post by albertonym on 2007-06-27
How did you solve /dev/agpgart problem? (Unable to open /dev/agpgart (No such file or directory)). I've got intel_agp module loaded but agpgart is definitely missing, although I tried building it in and building as module in the kernel.  

> **smylie said:**
> 

Anyway, having finally got X to run, compiz / beryl won't work, and the monitor is blurry. (see [http://ubuntuforums.org/showthread.php?t=464907](http://ubuntuforums.org/showthread.php?t=464907) )

Cheers
Dave Smylie

---

### Post by smylie on 2007-06-29
> **albertonym said:**
> How did you solve /dev/agpgart problem? (Unable to open /dev/agpgart (No such file or directory)). I've got intel_agp module loaded but agpgart is definitely missing, although I tried building it in and building as module in the kernel.
I had to compile one of the later versions of the kernel to get the /dev/agpgart to appear.
However, having said that, I believe that the current fiesty kernel is recent enough to fix this problem.
Try (at a console obviously):
```

$ sudo apt-get update
$ sudo apt-get upgrade

```

That should bring down a whole heap of updated stuff, hopefully including a newer kernel.

Let me know how you get on 
Cheers
Dave Smylie

---

### Post by albertonym on 2007-06-29
Thanks for your reply. I upgraded my kernel to 2.6.21.1 and it solved the problem.

> **smylie said:**
> I had to compile one of the later versions of the kernel to get the /dev/agpgart to appear.
However, having said that, I believe that the current fiesty kernel is recent enough to fix this problem.
Try (at a console obviously):
```

$ sudo apt-get update
$ sudo apt-get upgrade

```

That should bring down a whole heap of updated stuff, hopefully including a newer kernel.

Let me know how you get on 
Cheers
Dave Smylie

---

### Post by J-Red on 2007-06-30
Hey, I have the same laptop and am still having trouble getting it to work. I did:
```
sudo apt-get upgrade
sudo apt-get update

```

and added 
```
intel_agp
agpgart
```
into etc/modueles

I also did:
```

sudo apt-get install xserver-xorg-video-intel
```

But it still won't work. Can anyone help me with what else I should do?

---

### Post by J-Red on 2007-07-01
*bump*

---

### Post by balleyne on 2007-07-01
I've solved J-Red 's issues and attempted to detail our [solution]("http://www.blaise.ca/blog/?p=14") on my blog.

---

### Post by Voland666 on 2007-07-07
Get the latest X3100 driver released by Intel here:

[http://ubuntuforums.org/showthread.php?t=494943](http://ubuntuforums.org/showthread.php?t=494943)

Hope this helps

---

### Post by s_raghu20 on 2007-08-09
Hi there,

any updates from anybody on the compiz compatibiliy of the driver.

Current behaviour is fine, in the sense that it displays things nicely and normal happy flow runs fine. Only exception that I encountered being the Suspend-Resume thing. It breaks the system.

any clues from anyone ?

regards
raghav..

---

