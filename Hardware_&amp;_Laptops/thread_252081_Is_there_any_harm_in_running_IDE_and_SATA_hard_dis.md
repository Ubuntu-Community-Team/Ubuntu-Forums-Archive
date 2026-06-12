---
title: "Is there any harm in running IDE and SATA hard disk drives on the same system?"
date: 2006-09-06
forum: Hardware &amp; Laptops
---

### Post by Roasted on 2006-09-06
My instructor said he advises against it, though I have a feeling it's just a matter of his personal opinion for whatever reason as opposed to a "true" hazzard.

Any harm in doing this?

---

### Post by kidders on 2006-09-06
In actual fact, it's often a good thing. If you think about it, your disk buses are only so wide.

The classic example is software RAID. Throwing 4 disks on the same SATA bus is always daft because (depending on the type of RAID you use, of course), when you access one of them, you'll tend to access all of them. The smarter approach would be to use two IDE and two SATA devices, thus splitting the load a little.

Granted my example only applies to systems with lots of disks in them, but it is certainly true to say that such systems will always underperform if one I/O bus is unnecessarily overloaded.

---

### Post by HAARP on 2006-09-06
No. Why should there be? If it was harmful, the BIOS wouldn't allow it in first place (usually)

---

### Post by Roasted on 2006-09-07
Will using IDE along with SATA downclock the speed of anything? Or will running IDE and SATA run the exact same as just running SATA alone?

Another question. I have an IDE drive with XP with a few games on it wine and cedega don't support. I primarily work out of my SATA drive with Linux. If I plug both in, will grub take care of dual booting?

---

### Post by Roasted on 2006-09-07
slow server = dbl post. :<

---

### Post by kidders on 2006-09-07
The SATA interface is considered to be faster than IDE, so your IDE disk will be slower. I'm not sure what you mean by "downclock the speed of anything" ... the answer is probably no though. Are you referring to the fact that your kernel needs to load extra stuff to manage both interfaces, maybe? If so, the effect will be totally imperceptible.

Regarding your other question, grub is fine for dual booting :-)

---

### Post by HAARP on 2006-09-07
Well, you've got to tell grub first that Windoze exists..

---

### Post by neptune39 on 2006-09-07
I think he means will having the slower ide in the raid bring down the collective speed overall, like you only as fast as the slowest piece kind of thing.

---

### Post by Roasted on 2006-09-07
Nah, I just got the vibe from my instructor that IDE and SATA on the same board was not a good idea... So I was skeptical to try it myself, since Windows is on my IDE drive sitting on the bookshelf behind me. I was just questioning whether or not it was safe...

---

### Post by futz on 2006-09-09
> **Roasted said:**
> Nah, I just got the vibe from my instructor that IDE and SATA on the same board was not a good idea... So I was skeptical to try it myself, since Windows is on my IDE drive sitting on the bookshelf behind me. I was just questioning whether or not it was safe...

Sounds like your instructor is a computer noob. Where some people get these crazy ideas I'll never know... Lack of experience is my guess. Those who can, do - those who can't do, instruct others. (or something like that :mrgreen: )

Mix and match and don't worry about it. They work just fine together. I have many SATA and IDE drives in at least eight computers I can see from here in the swamp. I've never had any problems or performance issues whatsoever.

---

