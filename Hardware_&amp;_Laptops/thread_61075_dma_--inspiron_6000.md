---
title: "dma? --inspiron 6000"
date: 2005-08-30
forum: Hardware &amp; Laptops
---

### Post by cham0169 on 2005-08-30
i am running ubuntu hoary on an inspiron 6000. it seems that hard drive access just isnt as zippy as it should be. so therefor think immediately, DMA?? hmm..

in the hdparm.conf file i added something about:

/dev/sda {
    dma = on
}

and 

/dev/scd0 {
    dma = on
}

was this not right? when i boot up ubuntu i get an error early in the boot that it could not set device DMA because of a wrong ioct1  -- er something like that. any ideas ubuntuans?

---

### Post by frodon on 2005-08-30
Read these 2 threads :
[http://www.ubuntuforums.org/showthread.php?t=30949&page=1&pp=10&highlight=enable+DMA](http://www.ubuntuforums.org/showthread.php?t=30949&page=1&pp=10&highlight=enable+DMA)
[http://www.ubuntuforums.org/showthread.php?t=49926&highlight=hdparm](http://www.ubuntuforums.org/showthread.php?t=49926&highlight=hdparm)

I think the answer of your problem is in  ;-) (read the whole threads)

---

### Post by cham0169 on 2005-08-31
i have tried damn near aeverything to get dma enabled. i changed the 
S07hdparm to S29hdparm -- didnt help
when i run 'sudo hdparm -d1 /dev/sda' i get the following error:
************************
cham0169@cooter:~$ sudo hdparm -d1 /dev/sda
/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
***********************
it is a sata drive. i have read through every thread on here and people come so close to the sata situation, but no one ever answers it. also, my cdrw+dvdrom im having the same problems

what the crap is an Innappropriate ioctl for device?

edit, according my fstab, my cdrom is mounted from /dev/scd0
but when i run hdparm on that, it says it isnt found

when ripping audio cds, i get 5x tops. seems like i should be better

---

### Post by ACK!! on 2005-08-31
[QUOTE=cham0169]i have tried damn near aeverything to get dma enabled. 

....
edit, according my fstab, my cdrom is mounted from /dev/scd0
but when i run hdparm on that, it says it isnt found

when ripping audio cds, i get 5x tops. seems like i should be better[/QUOTE]

Trying doing this like I just did for my hard drive:

sudo hdparm /dev/hda

/dev/hda:
 multcount    = 16 (on)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 16383/255/63, sectors = 40007761920, start = 0

So for you that would be hdparm /dev/sda for example.

What is the output?

Oh yeah I think you got your cdrom setting wrong by just a bit:

/dev/scd0 {
dma = on
}

first don't include the 0 at the end of the device name and second are you sure its not a sdc device like this:

/dev/sdc {
dma=on
}

as an example.

---

### Post by cham0169 on 2005-08-31
/dev/sda:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 8192 (on)
 geometry     = 4864/255/63, sectors = 40007761920, start = 0


 -- 

cham0169@cooter:~$ sudo hdparm /dev/scd
/dev/scd: No such file or directory

---

### Post by ACK!! on 2005-08-31
[QUOTE=cham0169]/dev/sda:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 8192 (on)
 geometry     = 4864/255/63, sectors = 40007761920, start = 0


 -- 

cham0169@cooter:~$ sudo hdparm /dev/scd
/dev/scd: No such file or directory[/QUOTE]

Do not see anyone setting DMA on for sda devices:
one post after a search eve said --
the scsi device dont give you the same access to the hardware as ide. even if it is the same hardware. look at the code you will see what i mean

Your hdparm post says nothing about DMA on/off status nothing.
Did you include all of the output?

Someone please correct me and help if possible.

Oh yeah I found that Debian unstable has a sdparm package for configuring these devices.

[http://packages.debian.org/testing/admin/sdparm](http://packages.debian.org/testing/admin/sdparm)

Below is a link that has a couple of debs listed.
[http://sg.torque.net/sg/sdparm.html](http://sg.torque.net/sg/sdparm.html)

Not sure if it will work if installed under Ubuntu but small individual utils usually work better than large gui apps if the gcc libc stuff matches than say the large GUI apps with tons of dependencies.

Check that out.

If you need help with a startup script to get this going on startup we should be able to do that too.

I do not see any discussion of this going in Ubuntu.

Now here is the other part.  

Are you sure that is the correct device for the dvd/cdrom device?  


The naming convention you are using appears superficially at least to be off.

Usually the cdrom/dvd device would be hdc or sdc but scd at all.  That just sounds wrong and other users of the same laptop listed the device as a hdc device.

---

### Post by cham0169 on 2005-09-01
i installed sdparm and it seems like its working. however i dont know exactly how i can use it to enable dma. i cant seem to find anything that allows me to do that with sdparm. 

also, with the cd/dvd is there a way i can list what it is? 

according to fstab, this is whats mounted:
/dev/scd0       /media/cdrom0   udf,iso9660 ro,user,noauto  0       0

---

### Post by ACK!! on 2005-09-01
[QUOTE=cham0169]i installed sdparm and it seems like its working. however i dont know exactly how i can use it to enable dma. i cant seem to find anything that allows me to do that with sdparm. 

also, with the cd/dvd is there a way i can list what it is? 

according to fstab, this is whats mounted:
/dev/scd0       /media/cdrom0   udf,iso9660 ro,user,noauto  0       0[/QUOTE]

You can put in a cdrom and do a df -k at the command prompt.

Honestly I wish someone with one of these disks would reply since I don't have one therefore I am shooting in the dark so to speak.  

The DMA setting might NOT even apply to your brand of scsi disk.  Do you get anything different from a sdparm /dev/sda output?

From an example on the sg utils page I see that:

$ sg_map
/dev/sg0  /dev/sda
/dev/sg1  /dev/scd0
/dev/sg2  /dev/scd1

so the setting appears to be correct for your cdrom.  If you put in a CD and the system reads it fine then what do you get if you just run sdparm /dev/scd0?

You might also try this:

(WCE = write cache enabled which can help speed)
sdparm --get=WCE /dev/sda
WCE         1  [cha: y, def:  1, sav:  0]

If it does not look like what I show above (which means its enabled) then of course its disabled.  If it shows nothing at all you don't have the option (sorry).

So .... if you got this option you can also do a:

sdparm --set=WCE /dev/sda 

Which might help speed.

Sorry I cannot be of any more help.

---

### Post by cham0169 on 2005-09-02
no worries, i appreciate the help. it seems this sata guy just doesnt wanna help me out. hm... it'll get figured out

---

### Post by mlord on 2005-09-03
If your disk is showing up as /dev/sda, then DMA is already enabled.  No need to fiddle with it.

-ml
(hdparm author)

---

### Post by shazer on 2005-09-04
[QUOTE=cham0169]i am running ubuntu hoary on an inspiron 6000. it seems that hard drive access just isnt as zippy as it should be. so therefor think immediately, DMA?? hmm..

in the hdparm.conf file i added something about:

/dev/sda {
    dma = on
}

and 

/dev/scd0 {
    dma = on
}

was this not right? when i boot up ubuntu i get an error early in the boot that it could not set device DMA because of a wrong ioct1  -- er something like that. any ideas ubuntuans?[/QUOTE]

Hey dude, 

SATA is already optimized natively.  Make sure that you have SATA, scsi cdrom and drive support compiled in the kernel.I use Gentoo linux and all I had to do was the following:

change, in include/linux/libata.h
#undef ATA_ENABLE_ATAPI /* define to enable ATAPI support */
to
#define ATA_ENABLE_ATAPI /* define to enable ATAPI support */

Recompile the kernel and after rebooting all I had to do was point the fstab file to /dev/sr0.  I use udev and the 2.6.12-r10 kernel.  If you can modify that file and recompile the kernel you should be ok.  let me know if that helps.  if not, you should try Gentoo Linux, it's rock solid and it has great support for my inspiron 6000.  Now I play my dvd's my menu support using VLC media player.  Good luck.

---

### Post by ACK!! on 2005-09-04
[QUOTE=shazer]Hey dude, 

SATA is already optimized natively.  Make sure that you have SATA, scsi cdrom and drive support compiled in the kernel.I use Gentoo linux and all I had to do was the following:

change, in include/linux/libata.h
#undef ATA_ENABLE_ATAPI /* define to enable ATAPI support */
to
#define ATA_ENABLE_ATAPI /* define to enable ATAPI support */

Recompile the kernel and after rebooting all I had to do was point the fstab file to /dev/sr0.  I use udev and the 2.6.12-r10 kernel.  .....[/QUOTE]

I thought if he was seeing the devices as a /dev/sda and a /dev/scd0 then it was already compiled in.

Is this not correct?

---

### Post by userguy on 2005-09-05
[QUOTE=mlord]If your disk is showing up as /dev/sda, then DMA is already enabled.  No need to fiddle with it.

-ml
(hdparm author)[/QUOTE]

Great reply. That's about as good an answer as one could hope for.

---

