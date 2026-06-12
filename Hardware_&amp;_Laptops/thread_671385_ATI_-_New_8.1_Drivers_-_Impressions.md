---
title: "ATI - New 8.1 Drivers - Impressions"
date: 2008-01-18
forum: Hardware &amp; Laptops
---

### Post by bcardarella on 2008-01-18
Just installed the 8.1 drivers...

The first impression was: Hooray! 1680x1050 is back. It was all downhill from there...

First off, I have an Alienware Area 51-m with the ATI Radeon Mobility 9700. It's not the best card out there but it seems that as the driver develop my card keep performing worse.


3D performance is horrible. Compiz+Fusion, AWN, nothing works.

2D performance is barely better. The say that scrolling in my browser window is a pain is an understatement. It drags, then finally goes. Moving window frames around is a complete joke.

I dare not even attempt to launch Aptana Studio...

These drivers are horrible. If you really need the 1680x1050 display then I suggest you use them but unless you want to wait while your screen catches up to your scrolling then I suggest waiting yet another month to see what crap ATI puts out.

If anybody with a 9700 Mobility is having good performance pleas post... hopefully there is a xorg.conf tweak that can be done to fix this.

As a side note in case anybody from ATI monitors these threads: your horrible driver support has actually prompted me to purchase a brand new computer with a Nvidia card. My Alienware laptop is more than powerful enough to handle what I need to do but because I have no other options for video cards and because ATI can't release a decent driver I'm force to upgrade. Thanks!

---

### Post by luisromangz on 2008-01-18
I am using the latest drivers, 8.1 which I downloaded a couple of hours ago, and they are performing very well, and they have solved the problems with screen artifacts that showed after a while in the bottom right corner of the screen.

I'm using a Mobility Radeon 200M, which is crap of course, but I don't expererience such problems...

---

### Post by DDM on 2008-01-18
I was glad to find that they released something today, since I had the widescreen problem on my laptop. Upgrading was easy, I just did ./ati-blah-blah.run --buildpkg Ubuntu/gutsy and dpkg -i *.deb and rebooted. Finally I have Compiz + Suspend + Zen Kernel all working at once (something my Nvidia GPU Desktop has been able to do since forever ago)

---

### Post by bcardarella on 2008-01-18
If others are having luck with the driver I'll try removing the module and reinstalling it... maybe the last installation didn't go through cleanly. I'll keep the thread updated.

---

### Post by snl2587 on 2008-01-18
Ah, so it works well with the 200M? I'll have to give it a try...

---

### Post by bcardarella on 2008-01-18
Completely removed fglrx, reinstalled from the 8.1 derived packaged (followed instruction: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)). No longer having the slow 2D performance reported earlier. However, Compiz refuses to start. Typing in FireFox is *extremely* slow. This almost seems as if the driver is not being used. I have my xorg.conf file's Device section set for 'fglrx'. amdcccle won't run. (tells me that no ATI card is installed or the driver is malfunctioning) But fglrxinfo spits out the proper information. I'm kind of stuck here, any thoughts?

---

### Post by bcardarella on 2008-01-18
It seems that the problem was that Compiz wasn't started... this resulted in slow typing. After some looking around I found this solution... I hope this helps somebody else:

[http://ubuntuforums.org/showthread.php?t=585252](http://ubuntuforums.org/showthread.php?t=585252)

So now 1680x1050 works, Compiz+Fusion, AWN working. Good scrolling... video playback is working. Seems to be okay. Still not 100% thrilled about the performance though, but at least things are back to working reasonably.

Configured properly I would say these are better drivers than the 7.12 set

---

