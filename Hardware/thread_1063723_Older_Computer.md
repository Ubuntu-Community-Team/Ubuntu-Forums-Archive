---
title: "Older Computer"
date: 2009-02-08
forum: Hardware
---

### Post by 00b00nt00 on 2009-02-08
A friend of mine has the following setup:

Intel i430tx mobo (Socket 7)
Cyrix MII PR300 downrated to PR266 CPU
256MB SDRAM
20GB Hard Disk
Radeon 7000 PCI graphics.

Basically, this system is running Win XP, which by itself, is no problem, but with all the security stuff installed, CPU usage hovers around 100%.

Obviously, this system is long in the tooth. Which version of Ubuntu would be most suitable for this machine? Or another distro if Ubuntu won't work.

---

### Post by hansdown on 2009-02-08
Hi 00b00nt00.

Try puppy linux or mepis.

[http://www.puppylinux.org/](http://www.puppylinux.org/)

[http://www.mepis.org/](http://www.mepis.org/)

I've been playing with mepis on an old hp box.It recognizes my sony walkman nwz-s615f right out of the box.

---

### Post by earobinson on 2009-02-08
I am not sure if xubuntu would work or not, but if your looking for a *ubuntu system then that is your best bet!

---

### Post by kestrel1 on 2009-02-08
The above should work well, but you could also try Xubuntu.
To be honest I am surprised that Win XP even runs on this system. Windows 98 would have found problems.

---

### Post by inigomontoya on 2009-02-08
+1 for puppy linux.  Vector would also be a nice choice.

---

### Post by 00b00nt00 on 2009-02-08
Thanks for suggesting Mepis and Puppy. Xubuntu takes an extraordinarily long time to boot on this computer (though the desktop is just about usable).

"To be honest I am surprised that Win XP even runs on this system. Windows 98 would have found problems."

You're having a laugh; this old computer will run '98 a lot faster than a modern system will run Vista!

---

### Post by snowpine on 2009-02-09
I agree with the Puppy suggestion. I've also had good luck with SliTaz on older hardware.

---

### Post by LaneLester on 2009-02-21
I have an old laptop that won't run Ubuntu. It works well with Puppy, but you have the limited non-Debian-type repositories. I'm downloading Mepis and hoping for better things. I particularly want to get NFS working on this box.

Lane

---

### Post by hansdown on 2009-02-21
Mepis is pretty good, without too much work to use it.

---

### Post by ymo on 2009-02-21
> **00b00nt00 said:**
> A friend of mine has the following setup:

Intel i430tx mobo (Socket 7)
Cyrix MII PR300 downrated to PR266 CPU
256MB SDRAM
20GB Hard Disk
Radeon 7000 PCI graphics.

I managed to get Intrepid Server and Jaunty Alpha-4 Desktop to run on a lower spec system than that:

IBM/Cyrix 6x86MX PR200
128MB SDRAM
S3 4MB video card

There does appear to be a problem with the Ubuntu installer when run on computers with Cyrix CPUs - it fails to automatically install a suitable kernel. See [http://ubuntuforums.org/showthread.php?t=1044091](http://ubuntuforums.org/showthread.php?t=1044091)

My system is not really suitable to run a GUI, yours with twice the RAM might be usable. The other distributions recommended earlier in this thread might be better choices.

---

### Post by LaneLester on 2009-02-21
Well, too bad. Mepis 7.0 won't boot on my old laptop.

Maybe I need a new laptop. ;)

Lane

---

### Post by 00b00nt00 on 2009-02-22
Thanks for the replies.

A bit off topic, but does anyone know the fastest CPU I can drop in an i430tx?
The original CPU was a P200MMX, and with the DIP switches set to their highest performing position, the MII 300 spits an error message after the POST (but not during), hence the 'throttle back'. I think this CPU needs a 75 MHz bus to operate at its highest speed, but alas, the i430tx only has a 66MHz bus.

---

### Post by kestrel1 on 2009-02-22
If you have the manual for the motherboard it should tell you hat it is able to take.

---

### Post by 00b00nt00 on 2009-02-23
The manual states that support only extends as far as a P233MMX. The lowest core voltage supported is 2.8 volts, which I think limits me to Cyrix. Unless there are any AMD processors which support this voltage.

---

### Post by sansa dude on 2009-02-23
i use ubuntu on my laptop which has worse specs than your friends my laptop only has a 10gb hard drive 256mbs of RAM most likely a worse video card and a pentium 3 processor and ubuntu works fine. it can be slow when opening a few programs at once but other than that its good. i also have another 20gb hard drive with windows 2000 on it

---

### Post by kestrel1 on 2009-02-23
If that is what the manual says I would be inclined not to try another processor. To be honest, even if you could get hold of a 233mhz CPU you wouldn't notice any difference.

---

### Post by 00b00nt00 on 2009-02-25
@ Sansa Dude

Screen re-draws are not the problem in Ubuntu - it just takes far too long for the computer to respond to mouse clicks.

I'll have a look in the bargain bins for a Cyrix MII PR300 that'll work at full speed on a 66MHz bus. You never know, I might get lucky.

---

### Post by kestrel1 on 2009-02-25
You may get luck, but you may be better off looking for a different motherboard & processor.

---

### Post by happycube on 2009-02-25
One major problem is that the 430TX chipset's L2 cache only covers the first 64MB of memory.  (only the 430HX with a wide tag ram could handle up to 512, alas)  This, sadly, will probably make running any modern OS (XP or any full-size Linux) a bit painful.

If the motherboard BIOS can handle it, the very early K6's worked at 2.8v-3.3v (hinting that running said early K6's on an even older 3.3v only mobo might actually work).  For some of the really popular boards, there are hacks/undocumented settings to get lower voltages (the later versions of the Asus 430HX board could go to 2.0v and people ran far later K6's on them)  But if it's a random board, you'll definitely need an early K6.

Forget about the manual and try to find the BIOS update history instead to see what types of chips are really supported.  Failing that do a search on the board and see what people have done with it.

But, if it's an ATX board, look into upgrading to a 440BX board and a suitable P2/P3/Celeron chip instead.  In the worst case (PC66 memory) you may be limited to a 66mhz bus speed, but anything aside from a cacheless Celeron will be much faster ;)

---

### Post by 00b00nt00 on 2009-02-25
Alas, it's a baby AT board, so I can't go down the ATX route. Intel's vanilla i430TX was the most inflexible of all the flavours - maximum 3.5x bus multiplier and minimum 2.8v core voltage.

I'll give Puppy and MEPIS a try, and suggest my friend get a newer PC.

He can't complain, it is a 12-year-old machine!

---

### Post by kestrel1 on 2009-02-25
Puppy should run OK on a machine with that spec. Not tried Mepis so couldn't say how that would do.

---

