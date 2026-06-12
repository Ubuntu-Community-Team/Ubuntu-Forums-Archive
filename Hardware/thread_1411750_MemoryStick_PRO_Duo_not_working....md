---
title: "MemoryStick PRO Duo not working..."
date: 2010-02-20
forum: Hardware
---

### Post by Lîtus on 2010-02-20
Hi everyone!

(First of all, sorry but my english is very poor...)

I'm trying to mount a Memory Stick PRO Duo (via Memory Stick Duo adaptor). I'm using Ubuntu Karmic Koala in a Toshiba Satellite a200 1gb with a built-in card reader. I think that I was able to do that before but I can't remember how nor even if I really did it... 

So the problem is that when I put my card in the card reader nothing happens... I tried to insert a SD card and it works (ubuntu pops up a new window and all that stuff), but when I remove it and insert my MemoryStick I get nothing...

dmesg says:
```
$ dmesg | grep memstick
[ 6481.076351] memstick0: switching to 4-bit parallel mode
[ 6481.076549] memstick0: interface error, trying to fall back to serial
[ 6481.092490] mspro_block: probe of memstick0 failed with error -62

```
What does it means? How can I fix that error 62? (and what kind of error is that, by the way...)
When I remove the card, I'm not able to use my card reader again... (but doing "$ toshset" I can fix it)

Thanks guys!!

---

### Post by biabrasil on 2010-02-22
Hey, I got the same issue on my Ubunt 9.10 running on HP Pavillion dv2000.
Does anybody know what is the problem? Please help us.

Thanks a lot,
Bianca Brasil

---

### Post by Viglen on 2013-01-15
3 years ago... 
anyway a similar thread was here [http://ubuntuforums.org/showthread.php?p=9937993](http://ubuntuforums.org/showthread.php?p=9937993)

---

