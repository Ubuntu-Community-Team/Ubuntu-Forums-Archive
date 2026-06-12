---
title: "UNR on EEE 1000HE Can't load EEE.ko module"
date: 2009-06-13
forum: Hardware
---

### Post by Orbital_sFear on 2009-06-13
I have a plain install of UNR on a EEE 1000HE.  Everything works well but the stupid fan runs constantly which bugs me.

I found a module that lets you control the fan among other things: [http://code.google.com/p/eeepc-linux/](http://code.google.com/p/eeepc-linux/)

I downloaded it, Changed the &proc_root to NULL to make it compile and installed it.  After that I did the follow:
1. sudo cp eee.ko /lib/modules/2.6.28-13-generic/kernel/
2. sudo depmod -a
3. sudo modprobe i2c_i801
4. sudo modprobe eee
5. Seg Fault

I've tried a ton of different things and no mater what I do the thing seg faults.  I think it is an issue specific to UNR?  I've also gone to [http://www.statux.org/ubuntu](http://www.statux.org/ubuntu) and installed the module through apt-get.  If you do it that way, the module is called asus_eee; again, seg fault.

I think the issue is that i2c_i801 isn't doing what the eee module expects but I don't know what it needs.  Is anyone else seeing this problem and better you do you have a solution?

Thanks

---

