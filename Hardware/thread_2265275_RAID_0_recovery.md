---
title: "RAID 0 recovery"
date: 2015-02-13
forum: Hardware
---

### Post by bettymorlock on 2015-02-13
Hello, 

I have a acer [aspire s7 191]("http://www.myfixguide.com/manual/acer-aspire-s7-191-disassembly/") laptop that has failed.  It only has one ssd msata drive but I keep being told that it is configured in a RAID 0 configuration.  The ssd has some files on it that I desperately need to recover, and I have run into some issues doing so.  I bought a msata to sata converter off of newegg to get it to work with my desktop(windows 7) and It seems to recognize it just fine the piece is [here]("http://www.amazon.com/gp/product/B007PPZ2I8/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1").  I have tried to boot up into ubuntu to get it to work and I get::

```
**WARNING:  there appears to be one or more degraded RAID devices **

....one or more of the RAID devices are degraded:

mdo: inactive sda3[0](s)
        57989120 blocks super 1.2
```

It also gives me the option to start the degraded RAID but times out before I am able to type an answer.  I also do not want to lose sensitive data on the disk.  


I also have tried to read the disk using [DiskInternals Linux Reader]("http://www.diskinternals.com/linux-reader/") and the only thing it will let me open up is the "boot" portion of the disk where grub is stored.

is there anything I am doing wrong or is there somthing I can do to just pull the contents of my desktop off the drive?  pls help.


_**[COLOR=#ff0000]::EDIT::[/COLOR]**_
I have concluded that this is was a hardware based RAID 0 from the controller inside the labtop.  so I guess the issue is that I no longer can use the controller because the labtop is dead, so is there a way to read the data without using the hardware based RAID device?

---

