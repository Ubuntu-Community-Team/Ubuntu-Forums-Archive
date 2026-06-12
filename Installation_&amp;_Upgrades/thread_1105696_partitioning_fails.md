---
title: "partitioning fails"
date: 2009-03-25
forum: Installation &amp; Upgrades
---

### Post by kyeohti on 2009-03-25
I just found out about this site and wanted to see if anyone can help me get ubuntu installed before I resolve to keep Windows for another generation...  I replaced my only hard disk recently and the first OS I put on the new disk was SUSE 11.  It installed fine, but I was having a hard time understanding how to not only tweak hardware but notice even the simplest of stats...  Like how much RAM is installed...  A friend introduced me to ubuntu and I liked the layout much better but I tried several times without avail to install ubuntu.

   I'm convinced that the partition stage is that which fails because it finishes very fast and successive installation attempts always showed a map of the partioning from before ubuntu installation began.  I was choosing "Guided" and "100% ubuntu" in the beginning and later I tried various custom partition choices just to see if I could provoke any kind of a unique response, which I couldn't.

   SUSE 11 found and partitioned my Veloci RAPTOR serial ATA hard drive without any prompts of glitches so I'm stumped by what I might have missed with ubuntu.  I'm not possitive which version of ubuntu I'm using but it's the most recent I could find last week in an iso image format.  I don't get any error messages at all during the installation until I try to boot without the CD.  Then I get a "Gave up waiting for device /root" which is of course my hard drive which isn't partioned for ubuntu.

    Suggestions welcomed.

Thanks,

Kyeohti

---

### Post by kyeohti on 2009-03-28
A friend of mine uses LILO to boot into his ubuntu so I thought I'd try using a boot loader as well.  The discussions I found suggested that LILO might be a bit out of date compared to GRUB so I started with GRUB 0.95.  All I see though on the GRUB Super Disk is partition selection and restore tools.  I'm expecting a tool which can CREATE and manage partitions so that the OS doesn't have to  Is LILO the better choice or is my logic fundamentally flawed?  It's been slim pickin too finding a site with a GRUB downloadable file as well.  Something about GRUB 2.0 being the new focus but that's in alpha stage and I don't want to invest in alpha phase software if I can avoid it.

Thanks,

Kyeohti

---

### Post by kyeohti on 2009-03-30
In case anyone cares, I fixed it.  I had to change the SATA bios from Enhanced to Compatible protocol and then partitioning finally worked.

Regards,

Kyeohti

:popcorn:

---

### Post by dandnsmith on 2009-03-30
Good to know you solved it.

Is that 'compatible with IDE'?

---

