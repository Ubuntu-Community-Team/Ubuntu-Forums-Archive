---
title: "Screen goes solid color, MMIO error"
date: 2016-10-31
forum: Hardware
---

### Post by jeff162 on 2016-10-31
I'm having an issue with my Samsung R-580 laptop. I think it's a hardware problem but I'm not sure where to go with it. I have installed Ubuntu 14.04.

Basically, after a either a few seconds or a few minutes, the screen goes solid gray or blue and any disk IO (if any is going on) stops. It's then completely frozen and I can't even get a tty. Except once.

The one time I got to a tty the screen mostly contained a message like this, 
```

MMIO_Error then some hex digits, a few zeroes, x, more zeroes. .
```

I couldn't get a pic of the exact error before the screen blacked out and I haven't been able to get a tty since. Sorry if that's not enough.

I tried several different Linux distros, Ubuntu, Debian, Arch, and some more obscure ones on various hard drives and USB sticks and the result is always the same.

I ran Memtest and the memory passed two full rounds of tests once and some of the other times it would crash. 

So I'm pretty sure it's not an issue with the memory, it has 2 sticks and they both pass Memtest separately.

I'm not sure where to look from here, whether it's an issue with the motherboard or the CPU. I really have no real way to test either. Also, I can't really find anything on the googs.


Any help in tracking this down is very appreciated.

---

