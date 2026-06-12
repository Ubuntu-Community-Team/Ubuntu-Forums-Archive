---
title: "PC Won't Boot, Frozen on Intel Logo"
date: 2008-05-23
forum: Hardware
---

### Post by AlexMono94 on 2008-05-23
Just rebooted and my PC won't load up GRUB, BIOS or anything. It's frozen on the Intel Inside logo and I can't boot from a CD or DVD. Any ideas?

---

### Post by Zorael on 2008-05-23
Can you hit ESC when the logo shows to see verbose self-test output?

Could be an improperly seated PCI card/HD/RAM stick/fluffy bunny, could be a busted RAM stick, could be a busted motherboard, etc etc.

---

### Post by AlexMono94 on 2008-05-23
Nope, escape or any other key does nothing. =[

---

### Post by Zorael on 2008-05-23
I'd try basic troubleshooting.

Remove all unnecessary hardware. That means HDs, all expansion cards except your videocard, all RAM sticks except one (document which sockets they were in though). Just enough to get it to self-test but not necessarily boot. Do your very best to get it to show verbose self-test text (usually by mashing ESC), or failing that, get into the setup and see if you can enable Verbose Boot or something there.

If it worked, shut it down, add one more peripheral, power on.

---

### Post by AlexMono94 on 2008-05-23
After searching the net I found that it's most likely static or a dead motherboard battery. What d'you think?

I'll try basic troubleshooting when I have the time (and the confidence =P).

---

### Post by Zorael on 2008-05-23
Well, as far as I'm aware, the battery just makes sure your bios settings aren't wiped upon loss of power. Don't quote me on that, though.

---

### Post by SmokinJuan on 2008-05-23
> **Zorael said:**
> Well, as far as I'm aware, the battery just makes sure your bios settings aren't wiped upon loss of power. Don't quote me on that, though.

I HAD to quote you on that because in my experience, you're right.  Bad CMOS batteries just make you set the date & clock upon every boot when they fail.

Alex, a few months ago I had the same problem, though I'm not sure if I got the the manufactures boot screen (Compaq in my case).  I executed the basic troubleshooting technique Zoreal mentioned and found the problem to be a USB hub (of all things).  It was a Vakoss 7 port hub.  I had installed the hub with the machine on and it worked fine, but upon reboot, nothing.
Good luck.

---

### Post by AlexMono94 on 2008-05-24
> **SmokinJuan said:**
> I HAD to quote you on that because in my experience, you're right.  Bad CMOS batteries just make you set the date & clock upon every boot when they fail.

Alex, a few months ago I had the same problem, though I'm not sure if I got the the manufactures boot screen (Compaq in my case).  I executed the basic troubleshooting technique Zoreal mentioned and found the problem to be a USB hub (of all things).  It was a Vakoss 7 port hub.  I had installed the hub with the machine on and it worked fine, but upon reboot, nothing.
Good luck.

Well I haven't made any modifications to this PC. I just rebooted and then it could even boot properly. Thanks for the help but I think it's best if I take this for repair because it could be anything and I don't wan't to fiddle around with the insides. :(

---

### Post by Zorael on 2008-05-24
> **AlexMono94 said:**
> Well I haven't made any modifications to this PC. I just rebooted and then it could even boot properly.
Things break. :>

---

### Post by AlexMono94 on 2008-05-24
I've found the offending compenent, my hard drive. Unplugged it from the motherboard and it booted fine into a Hardy live CD. So I think it's time to get a new hard drive (I was thinking about getting a new one anyway :) ).

I should've known considering I just installed Hardy and it took ages to partition the disk.

Thanks for all the help but is their any possibility their could be a problem with the motherboard where I plug the hard drive in? What are the symptoms of a dead hard drive?

Thanks

---

### Post by AlexMono94 on 2008-05-26
Bump

---

### Post by TheLions on 2008-05-26
> **AlexMono94 said:**
> I've found the offending compenent, my hard drive. Unplugged it from the motherboard and it booted fine into a Hardy live CD. So I think it's time to get a new hard drive (I was thinking about getting a new one anyway :) ).

I should've known considering I just installed Hardy and it took ages to partition the disk.

Thanks for all the help but is their any possibility their could be a problem with the motherboard where I plug the hard drive in? What are the symptoms of a dead hard drive?

Thanks
it probably hangs because your motherboard can't detect drive's type, size and other parameters...

try waiting more then 5 minutes to see if would skip the drive detection.

---

