---
title: "Optical drive non-responsive after killing kio"
date: 2011-11-01
forum: Hardware
---

### Post by mdjames on 2011-11-01
A couple days ago running Kubuntu 10.04 on a Dell Optiplex 780, while in the midst of changing CDs that I was ripping music from, I was alerted that the optical drive (DVD - R/W) was in use by another application.  I searched around, found nothing using the drive and opted to halt the offending application, which if I remember correctly was audio-kio or something.  I realize now that was probably a stupid move.  The drive now doesn't respond in any way.  The activity light flashes continuously.  Curiously, it remains in this state whether I'm running Kubuntu or Windows.

examining the contents of /dev ....
```

:/dev$ ls
adsp             disk      hidraw1  loop4   net                 psaux  ram14  ram9    sda3        sg1       tty0   tty17  tty25  tty33  tty41  tty5   tty58  tty9     usbmon3  vcs3   vcsa4
audio            dri       hpet     loop5   network_latency     ptmx   ram15  random  sda4        shm       tty1   tty18  tty26  tty34  tty42  tty50  tty59  ttyS0    usbmon4  vcs4   vcsa5                    
block            dsp       input    loop6   network_throughput  pts    ram2   rfkill  sda5        snapshot  tty10  tty19  tty27  tty35  tty43  tty51  tty6   ttyS1    usbmon5  vcs5   vcsa6                    
bsg              ecryptfs  kmsg     loop7   null                ram0   ram3   root    sda6        snd       tty11  tty2   tty28  tty36  tty44  tty52  tty60  ttyS2    usbmon6  vcs6   vcsa7                    
bus              fb0       log      lp0     oldmem              ram1   ram4   rtc     sdb         sndstat   tty12  tty20  tty29  tty37  tty45  tty53  tty61  ttyS3    usbmon7  vcs7   vga_arbiter              
char             fd        loop0    mapper  parport0            ram10  ram5   rtc0    sdb1        stderr    tty13  tty21  tty3   tty38  tty46  tty54  tty62  urandom  usbmon8  vcsa   zero                     
console          full      loop1    mcelog  pktcdvd             ram11  ram6   sda     sequencer   stdin     tty14  tty22  tty30  tty39  tty47  tty55  tty63  usbmon0  vcs      vcsa1                           
core             fuse      loop2    mem     port                ram12  ram7   sda1    sequencer2  stdout    tty15  tty23  tty31  tty4   tty48  tty56  tty7   usbmon1  vcs1     vcsa2                           
cpu_dma_latency  hidraw0   loop3    mixer   ppp                 ram13  ram8   sda2    sg0         tty       tty16  tty24  tty32  tty40  tty49  tty57  tty8   usbmon2  vcs2     vcsa3

```It seems to me that my cdrom drive is no longer available as a device.  The optical drive was never mounted by fstab, only hard disks and some SAMBA shares are in there.

Have I nuked my optical drive or what??  I've read on some other forums that checking the cables inside is a good idea, but I can't imagine they've come loose, as I've never had the case open.  I'd greatly appreciate any direction you might be able to point me in to get this resolved...

Thanks for reading.

---

### Post by Redblade20XX on 2011-11-02
Does your BIOS still detect the cd drive? If not, your drive probably went bad.

- Red

---

### Post by mdjames on 2011-11-15
Thanks for the reply.  My BIOS did, recognize the drive though wasn't happy with it. What I did was shut down the machine with plug pulled for about 15 minutes.  After starting up again, all was normal.

---

