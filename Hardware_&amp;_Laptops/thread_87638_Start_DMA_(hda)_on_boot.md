---
title: "Start DMA (hda) on boot"
date: 2005-11-08
forum: Hardware &amp; Laptops
---

### Post by jipke on 2005-11-08
I've read several topics about this issue now. Still haven't found a solution. 

I've added:
/dev/hda {
	dma = on
}

and

/dev/hdc {
	dma = on
}
to /etc/hdparm.conf

hda=harddisk
hdc=cdrom0

After a reboot, DMA is enabled for my Toshiba cd drive. But somehow, DMA for hda isn't. 

sudo hdparm /dev/hda

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 78165361, start = 0



I have to start DMA manually typing 'sudo hdparm -d1 /dev/hda' in a terminal:

/dev/hda:
 setting using_dma to 1 (on)
 using_dma    =  1 (on)

Am I forgetting something? Do I have to add some extra code to /etc/hdparm.conf to make DMA for hda work after boot?

Thanks in advance.

---

### Post by tseliot on 2005-11-08
This is not the right place to ask questions.

There is no need to put this 

/dev/hda {
dma = on
}

as DMA should be enabled by default for your harddisk.


If you want a kernel which has DMA enabled by default (also for your cdreader) you have recompile your kernel:  everything is explained in my guide (which is aimed at newbies): [http://www.ubuntuforums.org/showthread.php?t=85064]("http://www.ubuntuforums.org/showthread.php?t=85064")

---

### Post by Zxaos on 2005-11-08
Have you tried setting the keepsettings variable with hdparm?

sudo hdparm -k1 /dev/hda 
sudo hdparm -K1 /dev/hda

(keep settings, and keep features).

This might help.

---

### Post by jipke on 2006-03-26
I know this is an old topic, but I still haven't found a solution to keep DMA enabled by default. 

[QUOTE=tseliot]
If you want a kernel which has DMA enabled by default (also for your cdreader) you have recompile your kernel:  everything is explained in my guide (which is aimed at newbies): [http://www.ubuntuforums.org/showthread.php?t=85064]("http://www.ubuntuforums.org/showthread.php?t=85064")[/QUOTE]

I've followed your instructions (great howto btw) and compiled a custom kernel. DMA is now enabled for cdrom and dvd. Unfortunately, my harddisk still won't use DMA automaticly; I have to start it manually (sudo hdparm -d1 /dev/hda), after which it works fine.

This is the content of my /etc/hdparm.conf:
```

#/dev/discs/disc0/disc {
#	mult_sect_io = 16
#	write_cache = off
#	spindown_time = 240
#}

#/dev/discs/disc1/disc {
#	mult_sect_io = 32
#	spindown_time = 36
#	write_cache = off
#}

#/dev/cdroms/cdrom0 {
#	dma = on		   
#	interrupt_unmask = on
#	io32_support = 0
#}

/dev/hda {
	mult_sect_io = 16
	write_cache = off
	dma = on
}

#command_line {
#       hdparm -q -m16 -q -W0 -q -d1 /dev/hda
#}
/dev/cdrom {
       dma = on
}
```

As you can see, DMA should work by default.

In one thread on this forum I found that changing the order or adding a '#' to ide-cd, ide-disk and ide-generic in /etc/modules should make a difference. Unfortunaly it doesn't. 

Current content of /etc/modules:

```
lp
mousedev
psmouse
via82cxxx
#ide-cd
#ide-disk
#ide-generic

```

I'm running out of idea's here. Anyone?

Thanks in advance!

---

