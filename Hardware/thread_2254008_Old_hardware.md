---
title: "Old hardware"
date: 2014-11-24
forum: Hardware
---

### Post by blaz3 on 2014-11-24
Lubuntu Live can boot, but when i try to put my Wifi password in it freezes!

Windows works ok, so why Linux don't? 
Even if i press ALT+TAB to get more info, it's nothing special there no error i think. 

Before replacing CPU from Sempron 2800+ 1.6GHz to Athlon 64 3200+ 2.2GHz  on board Gigabyte Nforce 3 250 and 1.5GB of RAM,
Lubuntu did work.

Is there maybe s solution or is my system just a no go situation?

---

### Post by mörgæs on 2014-11-24
Hi, welcome to the fora.

Wifi can be tricky in a live boot. I recommend installing and updating using a wired connection, adding wifi functionality as the last step.

---

### Post by blaz3 on 2014-11-24
I have tried without Wifi on and it's the same, it works about 30 seconds.

---

### Post by Dragonbite on 2014-11-24
Double check the media and maybe re-install it on the USB?

I know it sounds dumb, but dumb sometimes works.

---

### Post by mörgæs on 2014-11-24
Which BIOS version do you use?

---

### Post by blaz3 on 2014-11-25
I use Rufus to boot from USB flash key, i can't install because it works just about 30 seconds before freezing. BIOS is final version.

---

### Post by mörgæs on 2014-11-25
If it all works using the old CPU then all I can imagine is that the new CPU itself is failing or that BIOS settings need to be revised.

---

### Post by blaz3 on 2014-11-25
CPU is good, but looks like not supported properly, older CPU did not have SSE3 support, but this one has now.

What is command to run without frame buffer, because i was able to run Slackel a Greek distro, this one did not use frame buffer for Geforce 6600GT, maybe here is the problem with this GPU.

---

### Post by mastablasta on 2014-11-25
> **blaz3 said:**
> CPU is good, but looks like not supported properly, older CPU did not have SSE3 support, but this one has now.

that new CPU is supported just fine. 

did you apply the paste properly when replacing the CPU? is the CPU running at optimal temp?

---

### Post by blaz3 on 2014-11-25
Sure,  it's low power anyway.

---

### Post by Dragonbite on 2014-11-25
Could try a different distribution's liveusb and see if it continues to freeze after 30 seconds.  If so, then something with the hardware, if not then it is software (driver? who knows)...

Just thinking this could help narrow down where the issue is, and rule out (bad) hardware issues.

---

### Post by blaz3 on 2014-11-25
Slackel Fluxbox runs ok but this one use just VGA without any 3D support  i think. I can draw empty square on screen if i move a window.

I could run Lubuntu with just VGA, what is the parameter in boot menu older distros have use that?

---

### Post by mörgæs on 2014-11-25
If you mean running in VESA mode there's info in the link in my signature.

---

### Post by blaz3 on 2014-11-26
It's no good, i have added vga=791 at the and it's not doing anything and also freezing at the end. Input was correct, so no go i guess.

I don't have any AGP Radeon card to try if Geforce is the problem here, but i did try with another Geforce card and there was no change what so ever?

---

### Post by sudodus on 2014-11-26
> **blaz3 said:**
> Lubuntu Live can boot, but when i try to put my Wifi password in it freezes!

Windows works ok, so why Linux don't? 
Even if i press ALT+TAB to get more info, it's nothing special there no error i think. 

Before replacing CPU from Sempron 2800+ 1.6GHz to Athlon 64 3200+ 2.2GHz  on board Gigabyte Nforce 3 250 and 1.5GB of RAM,
Lubuntu did work.

Is there maybe s solution or is my system just a no go situation?

Maybe something makes your new CPU and graphics card/chip incompatible.

If you are lucky, you might find a driver that works, if you try several different linux distros for old computers. I would start with ***Wary Puppy, Tiny Core ***and*** Knoppix***. All of them are good at recognizing old hardware. Knoppix is not a light as the other two, but might still be worthwhile because of its hardware recognition.

---

### Post by blaz3 on 2014-11-27
Yes Slacko 5.7.0 works, but i want something that looks good, maybe i will try Mint with XFCE.

---

### Post by blaz3 on 2014-11-27
I think i have solve the problem.

I was thinking about previous CPU frequency then i have setup CPU manually with multiplier and it worked i can run now every distro now, no more freezing at boot. Well this CPU (AMD socket 754) don't use yet any power regulation so that's that. 

I hope this can help someone else to.

---

### Post by mörgæs on 2014-11-27
Good, please mark the thread 'solved'.

---

