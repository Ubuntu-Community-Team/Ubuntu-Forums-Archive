---
title: "Trying to run jackd - error message"
date: 2006-02-23
forum: Hardware &amp; Laptops
---

### Post by Ububurns on 2006-02-23
[I][SIZE="1"]## I have noticed quite a few people post a similar problem to the following.  
## However, as far as I have been able tell, it has not been solved.[/SIZE][/I]

I am unable to run jackd on my computer.  I was able to use it without needing to tweak, on my old PC.  I am using that PC's sound card in my current computer, so I am positive it is able to work - somehow.

The sound card in the works fine itself.  The ALSA driver seems to be loading, I am able to use media programs, all seems to be functioning well... except for  jack.

This unfortunately means that I am unable to use the programs I bought this newer computer for (eg: Ardour, Hydrogen, Zynaddsubfx, etc.)

Here is the output of jackd:

[I][SIZE="1"]Couldn't open hw:0 for 32bit samples trying 24bit instead
Couldn't open hw:0 for 24bit samples trying 16bit instead
Sorry. The audio interface "hw:0" doesn't support any of the hardware sample formats that JACK's alsa-driver can use.
ALSA: cannot configure capture channel
cannot load driver module alsa[/SIZE][/I]

I recently caught up with someone working on jacklab (a SUSE project) and they are of the opinion that I have an ALSA problem - but are unable to help any further.  After maybe a month of trying to make jack run, I am still where I started.

Any help would be greatly appreciated.

---

### Post by Ububurns on 2006-03-15
...Anyone have any ideas? Has anybody had this problem?

---

