---
title: "Hardware or software problem???"
date: 2012-12-13
forum: Hardware
---

### Post by johnspeedster on 2012-12-13
I have been using 12.04 on my Dell Inspiron 1525 for 6 or 8 months now and installing updates as they come along.  Yesterday morning the laptop did not boot first time in fact I had to hit the power button several times before it booted then ran fine all day. Today it would not boot at all. Put in the live cd and it booted immediately. I read a number of threads that gave various ideas so turned off the computer to start checking hardware. Since then, no way can I get any sort of action. Is it hardware or software? Holding down fn key while hitting the power button gives me two solid lock LEDs and one - number 9 - is flashing. Have checked docking station, removed and replaced RAM chips, and done the static off and on trick all to no avail. Power light comes on, cd drive whirs briefly, then the power light goes off -sometimes it does stay on though. Has it done a post check? I don't know. 
Any ideas would be greatly appreciated.
Merry Christmas BTW.

---

### Post by agillator on 2012-12-13
It could be either but I would lean toward hardware from your description. What happens with a live cd? Can you open the BIOS? If a live cd boots then it is probably software. If you cannot open the BIOS then it is more probably hardware.

---

### Post by johnspeedster on 2012-12-13
No, the live cd will not boot. Just the same result with battery or power, power light comes on, cd drive makes a half hearted attempt at starting, then the power light either goes straight off, or sometimes stays on until I hold the button down for off. Many thanks for such a prompt response!

---

### Post by grahammechanical on 2012-12-13
> Has it done a post check? I don't know. 

That is the key question. At what point is the machine failing to boot. A number of steps take place before the OS begins to load. The BIOS runs its Power On Startup Tests. Then it looks for an operating system on the first listed boot device. If it cannot find an operating system on the first device it will look to the second listed device, and so on. At some point it will load the Grub menu or give an 'Operating system not found' type message.

If Grub cannot find a suitable operating system to load it will give an error message. If Grub tries to load an OS but there are problems it usually drops to a Grub command line.

Are you getting any of this? Is there a power supply problem? Is there a loose connection at the power on switch?

Regards.

---

### Post by johnspeedster on 2012-12-13
Just to check that, I noted the time it stayed on after I pushed the power button. On five tests - the latter three without the live cd - it stayed on for only 6, 4, 3, 3, 3 seconds. I think my next step will be to borrow a pair of RAM chips from a friend and give that a try. Would that be safe all round? Could also then swap my hard drive over to the other laptop. I guess those two should be definitive tests. 
Thanks again for your help for a Kiwi chap down under.

---

### Post by agillator on 2012-12-13
There are a lot of things it could be. Trying things at random may not be the best troubleshooting procedure. At this point, I think I would give Dell a call and see what they suggest. If they aren't any help then I suppose there are some things we can try. From what you have said I gather you are comfortable with opening up your computer, replacing components when necessary, and that voiding a warranty is not an issue. Just out of curiosity I assume you are purposely trying to avoid the expense of a repair technician?

---

### Post by johnspeedster on 2012-12-13
Right on all accounts agillator! Cost is a factor, and time just before Christmas. Also, I have my daughter's identical laptop here as well to fix for her. She is using Vista and has had a couple of crashes. Last time I fixed it after booting up with Ubuntu, this time it sat in a drawer for a month before I touched it. Took the bottom panel off and cleaned the filthy filter. It runs fine now! I won't tell her if I use it for spare parts..... Just tell her she needs a new one! LOL. Not really! 
Anyway, I will call Dell and report back on anything they suggest.
Thanks again.

---

### Post by johnspeedster on 2012-12-14
Well Dell tell me it is the Motherboard. B...... My service centre tell me it is a minimum $400NZ to replace. For an extra $289 I can get a new HP i5 3210 so I think that is my way forward. Unless of course anyone has any other ideas as to what I could try next.
Thanks again - what a great service!

---

### Post by agillator on 2012-12-14
I agree that your best move is to replace the computer. But, of course, hang on to the old one. Spare parts can be hard to come by and expensive. That's the thing about computers in general, laptops in particular, these days. They are almost disposable items. I'm also glad to hear Dell was helpful. I may be in the market for a new laptop shortly and your experience certainly puts them on my short list.

---

