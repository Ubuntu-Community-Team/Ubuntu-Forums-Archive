---
title: "Mobo, CPU upgrade imminent - what will happen when I do?"
date: 2005-11-13
forum: Hardware &amp; Laptops
---

### Post by Rebajas on 2005-11-13
Hi Everyone,

I am soon going to be ditching my big beige box for something based around a Mini-ITX motherboard. I am worried though that I'll have problems if I just transplant my hard drive from one machine to another.

Will Ubuntu (Breezy) just shrug, find the device drivers for the new machine architecture and carry on OR will it cough, splutter and die?

I'm not keen to do a fresh install as I am quite happy with my current setup and don't much fancy shifting all my data either.

What experiences have others had with this particular scenario?

Regards.

---

### Post by teaker1s on 2005-11-13
you may wish to install a different kernel before you change so you have either option in grub list if you change cpu type

---

### Post by Rebajas on 2005-11-15
That's all? If that is all the trouble I will have then I'l be mightily impressed.

I'll be keeping the old box anyway so I assume that if things don't work out I can just put the HD back in the old machine, make changes and then transplant back to the new machine?

Regards.

---

### Post by kosmic on 2005-11-15
ok you just need to have atentio to the kernel you have before you transplant the disc to the other computer, if you have the K7 kernel and you are putting the disc in a mini-itx computer it will not boot, to be sure you can boot just install the kernel i386 and all will go fine.
 
 
The problems that may arrive is some hardware that can't be detected just donwload the modules for them if they are available and where you go ;)

---

### Post by Rebajas on 2005-11-17
That all sounds cool - I dare say I will post if I have any problems but that can wait until I actually upgrade.

Actually it will be a downgrade, but I just just can't stand the noise any more :)

R.

---

### Post by teaker1s on 2005-11-18
buy a quiet fan

---

### Post by Bartender on 2005-11-18
Hi, rebajas -
I don't know squat about Ubuntu, but couldn't help commenting after reading your complaint about noise - gotta second teaker's suggestion; quieter fans would prob'ly be the easier path unless you have a unique situation of some kind, such as a box filled to the rafters with SCSI HDD's or an overclocked P4 EE, etc.

Have you poked around under the hood to identify the noisemaker(s)?  Start by replacing the noisiest fan.
 
A week ago I ditched the horribly noisy Intel retail P4 heatsink & fan and replaced with a schnazzy Zalman CNPS9500.  Zalman's website lists compatible boards and my ASUS P5GDC-V was listed but I was nervous about the installation and whether it would fit inside the Antec Sonata case.  Everything went fine.
The new fan is connected to the same receptacle on the MB as the OEM unit.  Zalman includes a speed control which I used to throttle it down to nearly silent running.  ASUS PCProbe (a utility included with ASUS boards to monitor fans and temps) tells me I'm running a coupla degrees C cooler than before.  Not much of an improvement thermally but I'll take it, and the reduction in noise is very nice.
If the noise is mostly coming from the PSU fan(s), take a peek inside after unplugging the unit of course (careful now - don't get near those big capacitors) to ascertain how easy it would be to replace them.  EndPCNoise specializes in quiet fans but Directron, NewEgg, etc. works too.  Very quiet fans usually push less air than noisy ones so this could be an issue if you have a very high output PSU and your new fans don't move enuf air.  CFM data is available on websites for new fans but figuring out your old fans' output might be tough.  I'm in the process of replacing a failing PSU fan in a Pentium III computer with a Nexus 80mm from EndPCNoise.  Your existing PSU fans will often (at least older ones are this way) have just two wires - black and red - while the typical replacement fan will have 3 wires and a loom of some kind that usually includes 3 pin and 4 pin plugs to cover the widest range of applications.  Just cut the plug off the new fan (which will of course void the warranty), solder and heatshrink red-to-red and black-to-black, then tape off the yellow wire so the cut end doesn't touch anything.  I'm not sure but imagine that newer PSU's with controllable fan speeds will have the third yellow wire so in that case make sure to connect all of them.  
Case fans would be the easiest to replace.
If you knew all of that already....never mind

---

