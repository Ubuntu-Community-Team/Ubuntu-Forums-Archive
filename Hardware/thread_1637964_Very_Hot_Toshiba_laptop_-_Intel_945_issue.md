---
title: "Very Hot Toshiba laptop - Intel 945 issue?"
date: 2010-12-05
forum: Hardware
---

### Post by tpprynn on 2010-12-05
This is partly related to my other recent thread which was written in lack of understanding and put by me in a non-ideal category:

[http://ubuntuforums.org/showthread.php?t=1637561](http://ubuntuforums.org/showthread.php?t=1637561)

The 'acpi...' line has not solved things.

This is a Toshiba Equium L40 laptop with an Intel 645 chipset. It has always been fine with Linux till either Kubuntu 10.10 or 10.04 with Updates apllied.

I have watched the heat go beyond 87 degrees with the Performance setting, and it still goes at least that far with the acpi line added to /etc/default.grub.

I am leaving the laptop on Powersave till this is resolved in some way. The heat, by typing 

sensors 

into the terminal has gone down to 62. A terrible noise like a full on fan resulted after a period of heat, before any intervention into this. In some way it seems related to graphics drivers maybe, as turning the effects off was necessary yesterday. Kubuntu, Fedora KDE 14 and OpenSuse Kde 11.4 all disable effects by default, which seems a slightly underhand way of current distros avoiding this heat problem.

What do I need to do?

As a last resort, as I'm buying a bigger hard drive and will be reinstalling on it in about ten days, I might want to revert to 10.04 or Mint KDE 9 but somehow prevent the kernel updates that this issue seems to rest on. Does that make sense and is it possible with Kubuntu, i.e. to apply all updates but not newer kernels, at least until I read next year things have been put right. I don't want my flight from Windows to lead to a cooked laptop.

Thanks.

---

### Post by IcarusR on 2010-12-05
I have a tosh equium A100, with 945 chipset, which gets hot (both cpu cores > 64c) when doing cpu intensive stuff, such as transcoding video, fans come on & after job is finished temp usually drops.
Obvious thing to bear in mind..
Clean air vents out with air duster aerosol.
Make sure always has good ventilation.
Ambient temperature will have an effect, ie if you room temp is high then cpu will run hot.

My cpu is set at ondemand & I have all effects switched off, not interested in that stuff anyways.
As you are probably aware there are numerous threads here of boxes overheating. It seems that tosh boxes suffer badly.

You can 'hold' a package version, preventing upgrade.
In synaptic select package to be held, then go to 'package' menu & select 'Lock version' & this package will not be upgraded.

---

### Post by tpprynn on 2010-12-06
I don't know how relevant all the technical stuff I've read on this matter has been, but I do have to thank you for making me reconsider the more basic factor here. I've given my Toshiba a blast of compressed air (£5, Asda) round the back vent and the temperature has stayed at 48-60 degrees for a couple of hours. The laptop is also much quieter than it's been for a long time. Briefly last night it had reached 98 degrees...

Cheers.

---

### Post by yorktown48 on 2011-04-30
Ahhhh - Toshiba.

Simply put - If you do a search on Toshiba Laptop and Heat.   You will find you are not alone.    I believe Toshiba engineers do not place temperature high up on their list of issues to tackle.

I had a Toshiba laptop and dumped it.  The heat....was at a level where you could fry eggs.  And the system slowed down and that level.

Here is the 'worst' part.  You can look it up to confirm if it is true.    

The Fukushima plant....the one in Japan.  the one that is going through Meltdown.....that plant was built by Toshiba.

My impression is that Toshiba products and HEAT go hand in hand.

My suggestion....sell and get another machine.

---

### Post by IcarusR on 2011-05-04
yorktown48

Most recent toshes work well under windows without overheating. 
The problem is that toshiba tailor their products for their primary OS market & do not release specs so that the linux comunity can make the hardware work well under linux.
The other thing is that their model current life is very short, by this I mean that they release new models much more often than other manufacturers, so models become 'old' very quickly.

---

### Post by tpprynn on 2011-05-05
Several months on, my laptop is pretty constant at 55-57 degrees, still 5-10 degrees hotter than with Windows but very much in the safe region.

---

