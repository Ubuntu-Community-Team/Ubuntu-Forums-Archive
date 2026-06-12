---
title: "Dell Latitude D630 PP18L: 8GB RAM?"
date: 2011-10-16
forum: Hardware
---

### Post by sks24 on 2011-10-16
I just purchased a Dell Latitude D630 PP18L, which is a 32 bit machine.  It now has 2GB of RAM in it, but Crucial (.com) says it will take 2 4GB RAM modules, for a total of 8GB of RAM.  However, I read that XP Professional will only address a little over 3GB of RAM (I think 3.25GB)

Would a 32 bit Linux distribution like Ubuntu address more than 3.25GB of RAM?  Or is there something basic to the 32 bit architecture which prevents it from using more than that much RAM?

Assuming that is so - that the limit is @3.25GB - what advantage would there be to installing more than 4GB of RAM in such a machine?  Crucial says it will take 8, but what would be the point of putting all that RAM in the machine?  

And, again, might Ubuntu be able to utilize the full 8GB of RAM which this machine will take?  

Thanks in advance for your help,
Scott

---

### Post by diasf on 2011-10-16
A pae kernel can address more than 4Gb afaik, but are you sure the motherboard will support it?

---

### Post by sks24 on 2011-10-16
Thanks diasf,

I don't know if the motherboard will support it.  I guess the think to do at this point would be to boot to Ubuntu with the machine and then run "lshw" and post the hardware configuration here?  I'm just thinking that somebody could then tell me whether it might work.

Could anybody tell me if there a sticky of guide anywhere in this forum or elsewhere about installing a pae kernel (howto & so forth) and what the implications of doing so are?  I'm just thinking that there has to be a hitch: the OS updating being a bit tricky, maybe?  Things like that.

Thanks,
Scott

---

### Post by 2F4U on 2011-10-16
> **sks24 said:**
> Thanks diasf,

I don't know if the motherboard will support it.  I guess the think to do at this point would be to boot to Ubuntu with the machine and then run "lshw" and post the hardware configuration here?  I'm just thinking that somebody could then tell me whether it might work.

Could anybody tell me if there a sticky of guide anywhere in this forum or elsewhere about installing a pae kernel (howto & so forth) and what the implications of doing so are?  I'm just thinking that there has to be a hitch: the OS updating being a bit tricky, maybe?  Things like that.

Thanks,
Scott

This site confirms that the D630 can take up to 8GB of RAM

[http://en.wikipedia.org/wiki/Dell_Latitude#D-Family](http://en.wikipedia.org/wiki/Dell_Latitude#D-Family)

And this author says that he installed a 64 bit Linux

[http://www.nathansheffield.com/wordpress/2008/installing-ubuntu-linux-on-a-dell-latitude-d630/](http://www.nathansheffield.com/wordpress/2008/installing-ubuntu-linux-on-a-dell-latitude-d630/)

So, what you could try is download the 64bit version and see if it boots. If the machine is 32bit, it won't boot.

---

