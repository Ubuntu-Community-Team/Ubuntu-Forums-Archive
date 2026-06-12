---
title: "Hard drive failure question"
date: 2009-08-30
forum: Hardware
---

### Post by Zeikcied on 2009-08-30
I know this forum is mainly for compatibility issues, but I don't know where else to ask this.  I'm hoping people more versed in computer hardware than I can help ease or confirm my hard drive worries.

The hard drive that came with this computer is a 200 Gig Seagate drive (ST3200826AS).  For various reasons recently, I've become rather worried about the health of the drive.  The drive has always made a loud noise when the computer turns on after being off for a while.  I always thought it was the CPU fan going wild for some reason, but on reflection the fan never ever got that loud.  Now I believe that's the Seagate drive spinning up.  This has relevance for the first reason I suspect drive issues.

1. Kubuntu froze, so I shut down the computer using the Power button and started it back up.  Usually the drive doesn't make the noise when I power it back on that fast, and it has always made the noise before Grub displays.  But this time it started making the spin-up noise when the Kubuntu loading screen came up.  I panicked and shut down the computer again, and booted it once more.  It didn't happen that time.

2. I've experienced several freezes that seem to occur when files are deleted or moved between partitions.  I thought it was an ext4 bug in the Jaunty kernel, so I followed a workaround in the bug list to install the Karmic kernel.  But then I had a freeze happen when I was using the Karmic kernel. :(  It only happened once, and maybe I accidentally hit the wrong kernel version in Grub, but that also worried me.

3. The most worrying part is the hard drive temperature.  Using GSmartControl, I've been looking at the drive's SMART stats for a while now.  The drive seems to operate between 51 and 54 degrees Celsius.  It seems to fluctuate a lot.  My CPU temp is usually around 40 to 45 degrees, and my other hard drive typically runs around 45 degrees.  The other hard drive (a WD drive) is only two bay slots above the Seagate drive, and I would think that if it's an environmental issue, that the WD drive would be a lot hotter.  The "Worst" value listed on GSmartControl for the Seagate drive temp is 56, but I have no idea when that happened.  I've ran two self-tests via GSmartControl (one short and one long) and neither returned any errors, but I don't know if those tests can catch everything.

Like I said, I don't know much about computer hardware.  I really don't know much about drive failure.  I did buy an external drive, which I actually got before I started suspecting drive failure, and I've tried to back up every day or every other day.  But I've been worrying about this for a month now, and I would really like a more educated opinion.

---

### Post by pietjanjaap on 2009-08-30
Check seagate website, they have a program to check your drive.

The max temp of your hd is also on seagate website, normally is 50, best is 40(make your pc really hot with hdtune(do surface control)and occt([http://www.ocbase.com/perestroika_en/](http://www.ocbase.com/perestroika_en/)) to stress your pc.
At the same time check your temps and voltages. Voltages may only go down or up bij 5%.

If the sound is clicking then your power supply is maybe not strong enough. Check voltages wenn the pc is running stress test.
Test your hd in another pc if clicking is also there.

If you buy a pc then run tests on the pc:
Check wat is the max temp of your cpu and gpu.(search internet).
In the bios of your pc, check the temp protection off cpu, enable this and put in de max temp you found.
In bios check protection of fans, enable this.
Check how fast the cpu, memory is running, search on internet if it is ok.
Run memtest86 from cd, the whole night, 0 errors is ok.
Hdtune run surface check on the hd.

Then run: and check voltages and temps off everything(install from your mainbord firm the software to check the voltages and temps).
occt
prime95

Now you know if anything gets to hot(install more fans).
Now you know if you have a good(maybe)power supply, if a power supply goes up and down with voltages, then it can damage a lot.

---

