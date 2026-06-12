---
title: "64-bit kernel sees only 3.2 of 4GB"
date: 2009-12-19
forum: Hardware
---

### Post by koanhead on 2009-12-19
I have an ASUS A8N-SLI motherboard with an Athlon 64 X2 processor. 
     "uname -a" outputs the following:
          ```
Linux hostname 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:02:15 UTC 2009 x86_64 GNU/Linux
```

     I have 4GB RAM installed in 4 1GB modules. The motherboard BIOS is the latest version as far as I can tell (but still four years old.) The motherboard only sees 3.2GB at POST. The BIOS setup has a pair of options which change this- essentially a "hardware" and a "software" version of PAE. (I don't recall the exact wording, but I will come back and post it after I reboot the machine later today.) If either of these is enabled, then the board sees all 4GB at POST and all 4GB is available for Ubuntu to use. Unfortunately, enabling either or both of the aforementioned options causes both onboard LAN adapters to stop working.

     The board also exhibits other flaky behavior which I won't go into yet but which I suspect may be BIOS-related. I've been considering using coreboot / LinuxBIOS on this machine to work around these issues, and I wonder if anyone here has experience or advice on the subject.

---

### Post by Dark_Stang on 2009-12-20
I can't recommend reflashing your the BIOS of your computer with 3rd party firmware, unless you're prepared to eat the cost of a new board. That being said, sounds like your board has some problems. Do you see any physical damage? Extended capacitors?

---

### Post by koanhead on 2009-12-20
I examined the machine when I got it back in July, and again a few weeks later when I installed some new drives. I didn't notice any obvious physical damage at that time. I will check it out again probably tomorrow- the machine is busy with a time-consuming operation until then. At that time I will get the exact phrasing of the BIOS options I mentioned as well. If I can I will try to get a picture of the innards although I don't expect that will be very useful.

---

### Post by Dark_Stang on 2009-12-20
It's hard to see a bad cap in a 2d picture. So I'll post some links so you can see exactly what I'm talking about.

First pic. Notice the bulges.
[http://www.badcaps.net/images/caps/kt7/image004.png](http://www.badcaps.net/images/caps/kt7/image004.png)

Second pic. Corrosion and bulges.
[http://www.windows-help-central.com/image-files/bad_capacitors.jpg](http://www.windows-help-central.com/image-files/bad_capacitors.jpg)

Third pic. Notice the good capacitors in the front to the left. No corrosion, no bulging. Now look at the cap that has actually exploded... which is bad, btw.
[http://www.mikerepairscomputers.com/blog/wp-content/uploads/2009/07/Bad_Capacitor_01.jpg](http://www.mikerepairscomputers.com/blog/wp-content/uploads/2009/07/Bad_Capacitor_01.jpg)

If you see bad capacitors your motherboard is failing. It may work for now, to a point, but it is going bad. My parent's main desktop has several bad capacitors, and they know it. It gives them random problems all the time. I told them to just run it into the ground and then get a new desktop.

---

### Post by lukeiamyourfather on 2009-12-20
Its unlikely that failing hardware would cause this particular problem so looking for bad capacitors on your motherboard is a waste of time. Bad capacitors are more likely to cause random restarts or it just plain won't boot up.

Make sure the BIOS options for software and hardware memory hole or memory remapping are enabled. If both of those options are not enabled then the motherboard (and the operating system) will be unable to recognize the entire 4GB of installed memory.

A quick Google revealed the manual for your motherboard and shows an option in the Advanced tab of the BIOS, chipset, DRAM configuration, and finally "DRAM Over 4GB Remapping" which is disabled by default. Enable this and it should work. Cheers!

---

### Post by koanhead on 2009-12-20
Thanks- this was the BIOS option to which I alluded in my OP. In my experience, enabling either option has the same effect as enabling both, which is that the system sees all 4GB (yay!) but both onboard LAN adapters stop working (boo!)
Also, according to the instructions in the BIOS setup screen, those two options should only be used with a 32-bit OS IIRC.

---

### Post by lukeiamyourfather on 2009-12-20
> **koanhead said:**
> Thanks- this was the BIOS option to which I alluded in my OP. In my experience, enabling either option has the same effect as enabling both, which is that the system sees all 4GB (yay!) but both onboard LAN adapters stop working (boo!)
Also, according to the instructions in the BIOS setup screen, those two options should only be used with a 32-bit OS IIRC.

Not sure what to say about the NIC not working. Maybe a bug or maybe you accidentally disabled them in the BIOS? Glad its seeing all 4GB now though. Cheers!

---

### Post by koanhead on 2009-12-26
Actually it's not seeing all 4GB just at the moment, since I need to be able to use one or both of the LAN adapters in order to post here :)
I'm still trying to figure out why those two desirable conditions are mutually exclusive. I suspected a BIOS issue (BIOS firmware is the most recent available, hence my question about coreboot) but now I'm wondering if RAM timings / voltage may play a part. Going to pull the lid off later today and make sure that the RAM sticks are all the same type and look up the correct specs for them and check those against what the BIOS says.

---

