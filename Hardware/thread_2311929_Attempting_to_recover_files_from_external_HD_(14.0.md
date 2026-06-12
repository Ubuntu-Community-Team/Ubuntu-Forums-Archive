---
title: "Attempting to recover files from external HD (14.04)"
date: 2016-01-31
forum: Hardware
---

### Post by justin80 on 2016-01-31
Well, the title states it all, really. I'm fairly new to this, and I've tried a variety of commands to resolve this, but quite frankly, i'm at a loss. 
To start, i feel the commands don't even acknowledge the external drive as removing it changes the results in no way whatsoever. 

What information would i need to provide for assistance here? 
Thanks in advance, and I apologize for the awful "formatting" of my message.

---

### Post by fkkroundabout on 2016-01-31
so how old is the hard drive ? are you saying the hard drive has failed, and is generally undetectable, and you want to recover data that you can't currently access ?

plug the hard drive in, open a terminal, and type
```
ls /dev/sd*
```

then unplug the hard drive, and input the same code. tell us the output of both

---

### Post by justin80 on 2016-01-31
The hard drive is the original one from my laptop, so an estimated... 7 months of use... 
Yes. Impact induced crash led to its failure, and it's undetectable, even from within my enclusre (Light is red, along with clicking sounds that state it's generally bad)
It shouldn't be impossible to recover some data, in theory... 


Unless i input the command incorrectly, i don;t think results were what they should be...
Both were the same. 
In my case it appears as /dev/sda (This also does not change, regardless of whether the enclosure  connected or not.)
ANd... strangely i get denied access... on both occasion. 

"bash:  /dev/sda: Permission denied"

---

### Post by Vladlenin5000 on 2016-01-31
I strongly advice you to stop (immediately) whatever you're trying to do because you really don't know what are you doing and sooner than later you will make things even worse.
*sda* is how Linux system usually label the first HDD or SSD drive, whatever that is. If you replace let's say the one and only internal laptop drive, that new drive will become *sda*...

> _Impact induced crash_ led to its failure, and it's _undetectable_, (...)
It shouldn't be impossible to recover some data, in theory...

No, sorry, that doesn't even register as a good April Fools day joke.
An undetectable drive (by BIOS/UEFI or external adapter) CANNOT be recovered with software because the OS aren't even aware of the existence of such drive. Recovery in that scenario, if possible, can only be done (or tried) by specialized services and a huge fee (really huge).

---

