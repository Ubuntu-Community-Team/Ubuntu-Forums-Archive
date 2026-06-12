---
title: "How Does hdparm Work?"
date: 2006-02-06
forum: Hardware &amp; Laptops
---

### Post by wsmoser2004 on 2006-02-06
I initially started searching these forums to determine how to make my hard drive spin down after 30 minutes, but I've come across lots more that I can do with **hdparm**...trouble is, I don't know what's safe and/or how to use some things.  Here's my output from **sudo hdparm /dev/hda**:

```

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 8192 (on)
 geometry     = 65535/16/63, sectors = 78140160, start = 0

```

First, I'd like to get the hard disk to spin down after 30 minutes.  I've tried **sudo hdparm -S 241 /dev/hda** but after 2.5 hours the disk was still spinning (I wasn't using the computer, obviously).  I also have laptop-mode enabled, but it's NOT laptop-mode-tools, which I believe is different.  The laptop-mode I have does not spin down the disk as far as I can tell.

I've read the man page for hdparm, and there's also a -B option...but the man page isn't very descriptive about what to set the value to.  It just says that the range is 0-255, but doesn't specify what the numbers in between mean.  Currently, I believe it is set to 128 (according to **sudo hdparm -i /dev/hda**).  Anybody know how to set this flag?

Also, I read a HOW-TO on these forums about how to speed up the hard disk by changing the MultCount variable, but it warned of catastrophic data loss, so I'd rather not take that route.  However the HOW-TO also mentioned changing the IO_support variable but didn't specifically say that this was dangerous.  Currently mine says 16-bit, which sounds slow to me.  Is it dangerous to change this?  And if not, what should I change it to?

Thanks!

---

### Post by GTvulse on 2006-02-06
[quote=wsmoser2004]However the HOW-TO also mentioned changing the IO_support variable but didn't specifically say that this was dangerous. Currently mine says 16-bit, which sounds slow to me. Is it dangerous to change this? And if not, what should I change it to?[/quote]

It is not dangerous, but you should change the BIOS settings first, from 16 bit to 32 bit. Afterwards, you can edit [font=monospace]/etc/hdparm.conf[/font] to increase IO_support to 32:
```

/dev/hda {
        io_support=32
}

```

---

### Post by wsmoser2004 on 2006-02-06
Thanks dradul...

Hmm...I don't seem to remember a setting in the BIOS to change from 16-bit to 32-bit.  It's been a while since I've been in there, so perhaps it's there and I've missed it.  But thanks, I'll try it.

---

