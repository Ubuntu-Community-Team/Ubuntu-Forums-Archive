---
title: "Rediculusly short battery on ubuntu"
date: 2010-07-14
forum: Hardware
---

### Post by balloooza on 2010-07-14
I am an extremely advanced linux user, and I juat bought a new laptop, the inspiron 1464 from dell, I fixed a susspend issue, but I am unable to fix the battery.

On the windows install I get 4 hours of battery but on ubuntu I am getting under 2 hours.

here is my lspci
```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

Does anyone have ideas?

-mark

---

### Post by balloooza on 2010-07-14
New information:

What I have been able to fix: wifi
install powertop```
sudo apt-get install powertop
``` then wait for it to suggest to fix wifi, but DO NOT let it fix HD audio, it makes an annoying popping noise constantly.
that brings the battery up to 3 hours estimate.


I think that other thing to blame is the intigrated grapics because in windows I tried turning the graphics to mamimum performance and I was down from an estimated 3 hours at 70 percent to 1 and 45 so that is somthing to look into, tomorrow...

---

### Post by IcarusR on 2010-07-14
Yep as you've discovered linux drivers are not as 'good' as windows ones, probably due to the lack of demand for 'good' linux ones & the cost involved in development for the relatively small & free market.

Some sites with info on powersaving...

[http://lesswatts.org/]("http://lesswatts.org/")

[http://www.spencerstirling.com/computergeek/powersaving.html]("http://www.spencerstirling.com/computergeek/powersaving.html")

[http://www.thinkwiki.org/wiki/How_to_reduce_power_consumption]("http://www.thinkwiki.org/wiki/How_to_reduce_power_consumption")

Also disable any unused hardware in BIOS ie serial & paralell ports if present.
Switch off any unused services with something like BUM. (it's in the repos)

---

### Post by balloooza on 2010-07-14
Thanks, I will try

As much as I love the linux, I know that hardware companys are in the buisness of profit not world happiness, I cant blame them for not supporting linux.

one day we will take over... or at least have 4% market share, I think jolicloud is going to make that happen, I just installed the 1.0 release, WOW, speechless.

---

### Post by balloooza on 2010-07-14
that first link was helpful, I will be trying some of the patches this weekend, and some tonight, I will keep posting, and then create a guide, and maybe a sh script to walk the user through setting all the options, and making sure they backup all the old stuff.

---

### Post by IcarusR on 2010-07-14
> one day we will take over

I like your optimism' but people were saying that back in the eighties !! 

Jolicloud, whilst looking similar to UNR looks interesting. Might give it a whirl on my netbook when I get it back together.

---

### Post by IcarusR on 2010-07-14
Compiling a customised kernel may also help.

---

### Post by cgroza on 2010-07-14
> **IcarusR said:**
> I like your optimism' but people were saying that back in the eighties !! 

Jolicloud, whilst looking similar to UNR looks interesting. Might give it a whirl on my netbook when I get it back together.

that was a long time ago. Linux has changed and i believe it has the potential to get over 5% in the next years. Believe me, once it gets above 5 % this percent will grow a lot faster!

---

### Post by cubicsilver on 2010-07-14
I had the same problem with my laptop.  After installing powertop, I discovered that I had about 1200-1800 wakeups per second.  Load balancing ticks etc.  So after some digging I ended up trying nolapic, and my wakeups went down to 30-50.  I tested my battery life and it's very close to the same as windows 7.  

Worth a shot?

I also installed laptop mode tools too.  But I'm not sure if it makes a difference.

---

### Post by balloooza on 2010-07-14
> Jolicloud, whilst looking similar to UNR looks interesting. Might give it a whirl on my netbook when I get it back together.
Ironic, I just put my netbook back together, I was relocating my touch controller, but it ended up being open for 2 weeks.

> I had the same problem with my laptop. After installing powertop, I discovered that I had about 1200-1800 wakeups per second. Load balancing ticks etc. So after some digging I ended up trying nolapic, and my wakeups went down to 30-50. I tested my battery life and it's very close to the same as windows 7. 

How did you do nolapci, did you get rid of the tics too.

---

### Post by cubicsilver on 2010-07-14
It's a just a kernel parameter that you would enter at startup.  
Easiest way is to edit the grub config.

```
gksudo gedit /etc/default/grub
```

Change GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nolapic"

save and exit

then update grub

```
sudo update-grub
```

reboot

run powertop again

---

### Post by balloooza on 2010-07-14
Will nolapic work with the 4 thread 2 core i3 processor, I have read that nolapic is not good for multicore, what was the significance of changing this option, how much battery did it save for you.

Thanks, will try it.

mark

---

### Post by Foreigner99 on 2010-07-14
Hi,

I'm not an advanced user, I'm a beginner, especially with Ubuntu. Looks like I have a very similar problem of a "faulty" battery in my quite new Acer Aspire One. Does anyone have a suggestion how to fix it?

Thanks.

---

### Post by cubicsilver on 2010-07-14
I'm not sure about multicores... I have a single core, but I notice no performance difference.  Except a small delay of seeing my battery icon when I plug or unplug my laptop.  

I have a Gateway LT31

Amd L110 processor
2 gigs ram
500 gig hard drive
ati x1270 graphics
atheros wireless n
11.6inch screen
Web cam

Everything works out of the box on this thing.  Except the scaling on the processor, that took a modified bios update to fix.

I would imagine that the acer aspire one would perform the same with nolapic because it's a single core too.  Try it and see what happens.

---

### Post by balloooza on 2010-07-14
Hey, welcome to the forums.

I would start off by going to software center and installing powertop.

then head over to a terminal in the accecories menu and run it with sudo like this
```
sudo powertop
```

then you can see all the things causing the "inturrupts" or things that are making your processor wake up, and then you can use the "suggestions" it makes simply by hitting the letter of the thing it recommends at the bottom of the screen.

---

### Post by balloooza on 2010-07-14
Hey, welcome to the forums.

I would start off by going to software center and installing powertop.

then head over to a terminal in the accecories menu and run it with sudo like this
```
sudo powertop
```

then you can see all the things causing the "interrupts" or things that are making your processor wake up, and then you can use the "suggestions" it makes simply by hitting the letter of the thing it recommends at the bottom of the screen.

---

