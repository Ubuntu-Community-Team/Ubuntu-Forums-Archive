---
title: "Does Linux have problems recognizing the right transfer mode for an IDE DVD-RAM ?"
date: 2006-12-25
forum: Hardware &amp; Laptops
---

### Post by rlgc79 on 2006-12-25
Hello,

Today I found a solution to a problem that has been bugging me for some time, and I wonder whether it is a Linux kernel bug. 

Both the BIOS configuration of my motherboard (an ASUS A8N-E) and Windows list my DVD-RAM (a MATSUSHITA/PANASONIC SW-9585) as UDMA2 compatible, and everything works as expected. On the other hand, if I enable DMA on Linux (any distribution, Ubuntu included), the transfer mode is automatically set to UDMA5, and strange things happen (the computer freezes,  random read/write errors etc). My workaround is to install Ubuntu with DMA off (passing ide=nodma to the kernel), and then I manually enable DMA and force the transfer to UDMA2 by adding the following lines in /etc/hdparm.conf

/dev/hdc {
        dma = on
        transfer_mode = 66
}

Then the computer behaves as expected.

My questions are the following: 
1) Why does Linux not set the transfer mode to UDMA2 automatically?
2) How can I force UDMA2 when booting a live CD??

Thanks

---

### Post by po0f on 2006-12-25
rlgc79,

What do you mean by if you enable DMA?  It should automatically set the right mode with no user intervention.  I've never had a problem with the kernel picking the wrong DMA mode for any of my drives, optical or not.  Now, if you went playing with the settings...  :)

---

### Post by rlgc79 on 2006-12-26
> **po0f said:**
> rlgc79,

What do you mean by if you enable DMA?  It should automatically set the right mode with no user intervention.  I've never had a problem with the kernel picking the wrong DMA mode for any of my drives, optical or not.  Now, if you went playing with the settings...  :)

Dear po0f,

For example, after a clean Ubuntu install (both on dapper and edgy)

sudo hdparm -d1 /dev/hdc, 
followed by sudo hdparm -i /dev/hdc returns:

[PHP]
/dev/hdc:

 Model=MATSHITADVD-RAM SW-9585, FwRev=B100, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6

 * signifies the current active mode
[/PHP]

which is clearly the wrong transfer mode. The only way to set the correct transfer mode is to force UDMA2, e.g.,
sudo hdparm -X udma2 -d1 /dev/hdc    ](*,) .

This is annoying when I try to install from the live CD because I have to turn DMA off to succeed, which slows down the installation.

---

### Post by po0f on 2006-12-26
rlgc79,

Reboot up and check your DMA settings without the `hdparm` command, you should find that the kernel has already set it up for you.

---

### Post by rlgc79 on 2006-12-26
Po0F,

After rebooting, the transfer mode is back again to UDMA4.   Note that this problem happens with any distribution, not only with Ubuntu. The only workaround is to add 

/dev/hdc {
dma = on
transfer_mode = 66     <==== without this line the computer goes awry
}

to hdparm.conf .

I've been googling for this problem, and it seems that I am not alone. I read posts in Ubuntu and CentOS forums describing similar problems I face when installing Ubuntu/Fedora/Gentoo/Suse with DMA on.  Windows correctly set the transfer mode to UDMA2, so that is why I think there might be a problem with the combination Linux Kernel+Panasonic SW-9585+Asus A8N-E. 

Bug or not, is there a way to force UDMA 2 with the live CD?

---

### Post by po0f on 2006-12-26
rlgc79,

You could boot with DMA disabled and re-enable it when it finally boots up.  That's the only way I see of working around this.

---

