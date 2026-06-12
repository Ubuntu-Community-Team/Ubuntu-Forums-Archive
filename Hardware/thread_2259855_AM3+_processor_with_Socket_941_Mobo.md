---
title: "AM3+ processor with Socket 941 Mobo"
date: 2015-01-07
forum: Hardware
---

### Post by fugu2 on 2015-01-07
Does anyone know if I can buy a replacement processor that is an AMD AM3+ and cram it into a socket 941 motherboard and have it still work? looking to fix an older computer and I'm just trying to weight my options

---

### Post by QIII on 2015-01-07
No.

They would be both physically and electrically incompatible.

---

### Post by fugu2 on 2015-01-07
Alrighty then. Thank you for your help. I'm probably going to just look at buying a barebone system with newer processor/mobo combo.

---

### Post by mörgæs on 2015-01-07
According to my standards AM3+ is new. Why do you want to let go of it?

---

### Post by QIII on 2015-01-07
The AMD FX (their current flagship) processors are AM3+.

The APUs (CPU with on-die GPU) currently use versions of the AM, FM and possibly FT sockets.

FX CPUs are far more powerful, but require a separate GPU.  The APUs are a decent low-power compromise.

---

### Post by Yellow Pasque on 2015-01-08
As far as I'm aware Socket 941 is just another name for Socket AM3. If you have a motherboard with an AM3 socket, you may be able to use an AM3+ (i.e. a Bulldozer core-based) CPU if the BIOS supports it (check your mobo's CPU support list).

@QIII; you're probably thinking of Socket 940, which was an older socket for Opterons and is incompatible with AM2, even though they both have 940 pins and the same physical pin layout. Socket 940 CPU's had a DDR memory controller and Socket AM2 CPU's had DDR2.

---

### Post by QIII on 2015-01-08
You can use a 941 pin AM3 CPU in a 942 pin  AM3+ socket, but not the other way around on the 942 pin AM3+s unless you want to bend the extra pin on your AM3+ CPU and have a significant emotional event.

Some later "AM3" boards actually have a 942 pin socket, but the pin holes are smaller than the pins on the AM3+ CPUs.

Also, the circuitry on those mobos generally do not supply adequate current for the AM3+ processors.

If the physical socket is white, no AM3+ processor.  If it's black, it'll fit, but if it was sold as an AM3, the OEM will not have improved some of the other, older technology.

(By the way, I only know this because I was "future proofing" some AM3 machines with AM3+ mobos for when I could get around to replacing the AM3 CPUs with AM3+ CPUs.)

---

### Post by Yellow Pasque on 2015-01-09
> If the physical socket is white, no AM3+ processor. If it's black, it'll fit
That's what I was referring to. I was not suggesting bending a pin as it probably wouldn't work anyway even if you could get it into the socket. My understanding is that the boards with a black socket will work with AM3+ chips as long as the BIOS supports them. Again, checking the mobo's CPU support list is the best way to figure out if the board supports AM3+ chips.

> Some later "AM3" boards actually have a 942 pin socket, but the pin holes are smaller than the pins on the AM3+ CPUs.
From the accounts I've read, the two CPU's are mechanically compatible if the board has a black socket (i.e. it doesn't have the extra pin blocked off).

---

