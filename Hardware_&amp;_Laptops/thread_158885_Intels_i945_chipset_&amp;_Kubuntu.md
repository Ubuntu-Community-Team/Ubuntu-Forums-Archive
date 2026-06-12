---
title: "Intels i945 chipset &amp; Kubuntu"
date: 2006-04-11
forum: Hardware &amp; Laptops
---

### Post by Elif Tymes on 2006-04-11
Hello all, I'm a relative newcomer to the Linux field. THis is my first "real" install of linux, since messing with mandrake 8 back in the day, almost 5 years ago.

Since then I've been an XP junky, switched to Mac OS X for about two months(then my G3 ibook I was using died) and have been loath to return to XP. Guess it's my rebellious nature, eh?

Anyway, here's my 'Issues'

Hardware:

Dell Inspiron 9400 WIth Intel Core Duo @ 1.66Ghz
2x512MB DDR2 533 RAM

Integrated Intel i945 graphics chipset
Intel Wireless ABG Mini-PCI card: 3945ABG 


I start installing Ubuntu Linux off of the CD

It completes that just peachy, it reboots, and attempts to start installing more packages, it runs through that just fine.

Then I have to configure my display settings. I allow it to autodetect, which it does and tells me to use i810. Ok, no problem from me. I then default through the rest. I.E. 1024x768@60hz is default resolution, default options are selected for the video card, etc.

Now, I finish my installation, reboot, and come to a blue screen with nasty characters all around it. It tells me "Eh... no... Display can not be found... Screen cannot be found"

I can understand that, it means my kernel doesn't support the graphics chipset, I can live with that. I switch it from i810 to VESA, and force the resolution down to 800x600.

This appears to work. I can now get into x11.

However, my beautifull 1900x1200 resolution is going to waste, so I find a workaround.

[https://wiki.ubuntu.com/i915Driver](https://wiki.ubuntu.com/i915Driver)

It tells me to download the .deb file, and install it. 

This is where I run into problems: How the heck do I install it? I tried double clicking it, even tried to figure out how to force apt to install it to no avail.

Any assistance would be delectable.

(P.S. I tried updating to the SMP kernel, but it hangs on PCMCIA... I'll try and work on that while you guys respond)

---

### Post by alex0o0 on 2006-04-12
dpkg -i packagename.deb

---

### Post by Elif Tymes on 2006-04-12
[QUOTE=alex0o0]dpkg -i packagename.deb[/QUOTE]


Yep, I figured that out last night. Now however it hangs when trying to get the battery state?

Don't know why.

---

### Post by Elif Tymes on 2006-04-13
Woo. Ok, forced it to deactivate the pcmcia device from.

Now, I still can't get the drivers installed for i945gm.

I'm a complete Linux novice, so any help would be greatly appreciated.

---

### Post by Miguel on 2006-04-14
Hi Elif

I might be a bit crazy to recommend this to a newbie but... ¿could you try the development version of ubuntu? If there is something that improves with new versions  in linux it is hardware support, particularly on the laptop camp. If you have the bandwidth, and a 700MB CD-RW, you could have a go at the (K)Ubuntu Dapper Drake live CD.

I am suggesting this basically because you are using hardware that didn't exist when the last stable ubuntu was released. And it is not like we got great support from all hardware manufacturers, you know.

For your lockups, you could try to install (or boot) passing the option "noapic" (or similar). Some folks do need to use this parameter even to get the thing installed.

---

### Post by mscman on 2006-04-14
What errors exactly are you getting when you try to install the drivers?
Also, I highly recommend what the previous user suggested about trying out the Dapper testing release.  I'm using a Toshiba M45-S331 with the 915 chipset.  Not only did it fix some graphics issues, but also fixed ALL of my networking problems.  Keep in mind though that it can be an ambitious undertaking using a development version.  However, in my experience with it, Dapper is to the point now that it is (for me) more stable than Breezy.  Might be worth a shot before you waste a ton of time trying to fix something too complicated for someone new to Linux...

---

### Post by Elif Tymes on 2006-04-15
Well you guys, I've gotten to the point where I've accepted the fact htat there is no driver support (as of yet) for my VGA chipset. This isn't a huge issue to me, as the most challengning game I play is "Konquest" and a few rounds of hextris...

The only issue is VESA doesn't support 1900x1200 resolution, so I'm stuck with 1600x1200, which isn't terrible...

As for networking: That's where I'm going now, trying to get some wireless drivers installed, and that's going halfway decently. Have the new 1395abg chipset from intel, which isn't exactly supported yet(intel did release a new chipset)

So I'm gonna probably either A) Switch to dapper, or B) Stick with what I've got until dapper is released with support. My biggest gripe(as of now) is merely the lack of wireless, which I should get fixxed soon.

---

### Post by dragonflyFZX on 2006-04-18
hi elif,

i have a dell latitude d620 with the same chipset as yours.  I ran into the same difficulties, and i am a beginner, too.  Please look at my post on [http://www.ubuntuforums.org/showthread.php?t=160521]("http://www.ubuntuforums.org/showthread.php?t=160521") cause it now works fine.  I do have to admit i am running dapper. 

I am now trying to get the wifi going.  If you get it up, please tell me, cause again, i have the same!

---

### Post by artivisual on 2006-05-10
I've been trying to get wifi working on the d620. I downloaded the intel windows drivers from the intel site after following the instructions from the ndisinstall howto. That didn't work as the driver won't load. The hw is recognized by the card but doing a modprobe on ndisinstall module returns a error in the message log.

Then I tried downloading the native driver from sourceforge for the intel 3945 ABG (what the lspci returns is identified as this manufacturer model on one of the links I've read).  That's going nowhere as it can't be compiled standalone. 

The next step would be for me to compile the 802 module in the kernel and compile the intel native driver as well. That would require to know how to build the kernel in ubuntu which is again another road block.

The joys of installing linux on brand new laptops I guess...

---

### Post by dragonflyFZX on 2006-05-12
Are you running dapper?  My wifi works out of the box on kubuntu dapper these days.

---

### Post by Seamus_X on 2006-10-19
Have you tried the i810 driver instead of the vesa?  It supports the i9xx video chipsets fine.  I even get direct rendering.
<snip>
Section "Device"
        Identifier      "Intel Corporation Mobile Integrated Graphics Controller
"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection
<snip>

---

