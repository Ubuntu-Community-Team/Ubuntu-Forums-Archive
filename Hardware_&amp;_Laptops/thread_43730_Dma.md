---
title: "Dma"
date: 2005-06-23
forum: Hardware &amp; Laptops
---

### Post by jefffq on 2005-06-23
I tried to turn DMA on, and it didn't work.

---------------------
jef@exodus:~$ sudo hdparm -d1 /dev/hdc

/dev/hdc:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)
---------------------

I really have no idea where to go from here. Everywhere I look it says that that should work. I'm assuming the right stuff is on in the kernel, as no Ubuntu users mentioned having to do that.

---------------------
jef@exodus:~$ lspci | grep -i ide
0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
---------------------

The drive is a regular Maxtor PATA 160GB drive.

I get the exact same results for my two optical drives (CD/DVD).

I also have two SATA drives, I don't have a clue what to do with those. Hdparm doesn't even mention DMA for them.

Any help?

Thanks in advance!

---

### Post by afonic on 2005-06-23
Have a look here:
[http://www.ubuntuforums.org/showthread.php?t=19519](http://www.ubuntuforums.org/showthread.php?t=19519)

(post #5 did it for me)

---

### Post by jefffq on 2005-06-23
Thank you very much, afonic, for that link. The 5th post fixed it for me as well. Now I have to figure out the SATA.

---

### Post by afonic on 2005-06-23
[QUOTE=jefffq]Thank you very much, afonic, for that link. The 5th post fixed it for me as well. Now I have to figure out the SATA.[/QUOTE]
 You're welcome.

Just add the SATA drives in the hdparm list as well and DMA will work. They should be sda and sdb if you have 2 of them (and not hda and hdb, your CD-ROMs may have those).

---

### Post by jefffq on 2005-06-24
You are right about the devs that my SATA drives are, and that my opticals are hda and hdb, smart cookie you are to have figured that.

What is this "hdparm list" that I add my SATA drives too? Do you mean just in hdparm.conf around the bottom where you tell it what to do to your drives at boot? Probably .....

But, hdparm doesn't seem to work for SATA.

```

root@exodus:~ # hdparm /dev/sda

/dev/sda:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 14946/255/63, sectors = 122942324736, start = 0

```

See, no DMA mentioned. I've searched this and found out that hdparm supposedly doesn't work for SATA, and you need to use blktool. blktool also doesn't set DMA on my drives, it says it's the wrong ioctl.

```

root@exodus:~ # blktool /dev/sda dma
HDIO_GET_DMA: Inappropriate ioctl for device

``` 

For all I know, DMA is already working on my SATA drives, I haven't noticed copying files stopping music or anything, with them. But I don't even have a way to find out.

Maybe I need to do a similar procedure as that one in the link you gave me, but for my SATA controller. I wouldn't know what to put, though.

I hahve no idea if this helps at all, but ...

```

root@exodus:~ # lspci | grep -i sil
0000:01:0d.0 Unknown mass storage controller: Silicon Image, Inc. (formerly CMD     Technology Inc) SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02) 
```

---

