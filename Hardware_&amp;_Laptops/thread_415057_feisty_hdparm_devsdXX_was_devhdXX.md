---
title: "feisty hdparm /dev/sdXX was /dev/hdXX"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by dc. on 2007-04-20
Hi,

feisty uses the new /dev/sdXX system instead of /dev/hdXX for IDE drives

How can I change now e.g. the acoustic management settings of my laptop's hard drive?

Hdparm does not seem to work with sdXX devices.

[FONT="Fixedsys"]dc@laptop:~$ sudo hdparm -d1 /dev/sda

/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
dc@laptop:~$ sudo hdparm -d /dev/sda

/dev/sda:
dc@laptop:~$ sudo hdparm -M /dev/sda

/dev/sda:
 HDIO_GET_ACOUSTIC failed: Inappropriate ioctl for device
dc@laptop:~$ [/FONT]



Thanks!

---

### Post by nubutu on 2007-04-22
Yes, somebody knows what to do? I find this quite annoying.

---

### Post by dc. on 2007-04-23
I still have no answer for this.
This is really annoying not to be able to use features your hardware has because of a change in software infrastructure.

---

### Post by nubutu on 2007-04-26
Hi

This is what I've been told in usenet:


"According to information on openSUSE mailing list [...] the following parameter;

hwprobe=-modules.pata

which you can copy/paste into your /boot/grub/menu.lst [...] returns the drives to their native IDE state, where hdparm should work as normal."


Nor the person who gave me the information neither myself have tried this yet, but I don't see any harm and it's very easy to change it back. Actually, I'm thinking you probably don't need to change your menu.lst, just pass the option to the kernel when booting should do the trick.

I'll have a go today afternoon and tell you the outcome.

PS. Another Debian user reported no problems using 2.6.20 kernel (in Debian) and stated this is a problem with the current Ubuntu release (although had not cited the information source).

---

### Post by robertobech on 2007-04-26
> **nubutu said:**
> Hi

This is what I've been told in usenet:


"According to information on openSUSE mailing list [...] the following parameter;

hwprobe=-modules.pata

which you can copy/paste into your /boot/grub/menu.lst [...] returns the drives to their native IDE state, where hdparm should work as normal."



I've tried adding it to grub during boot, but it didn't work.

---

### Post by nubutu on 2007-04-26
It didn't work for me either. Keep looking...

PS. And this is getting particularly annoying, not the least for the lack of information concerning it.

---

### Post by dc. on 2007-04-26
Thanks for posting in this thread!

I will try your suggestion but I don't have much hope because it didn't work for the others.

---

### Post by marrty on 2007-04-27
im a relative linux newbie, and i have the same problem.. my hda has become sda.. weird.

and my swap isnt active when i boot.. do i add...

/dev/sda2   none   swap   sw   0   0

into /etc/fstab?

im confused.. coz my partitions are now sda, but my fstab still says hda.. so do i change my fstab to sda's ? and add in the new sda2 line to mount my swap?

argh.. i love ubuntu, but if it wasnt for support from ppl who actually know what theyre doing (you guys), it would be nigh impossible to keep up!  :(

marty

---

### Post by Strannik on 2007-04-27
ok, i have just tried about 5 different "fixes" and nothing works at all. fiesty is a bit buggy...

---

### Post by Strannik on 2007-04-27
would be really nice to hear somebody from the team on this issue. I'm sure that there are probably a real lot of users that were supprised who have a regular ide drive and can't activate dma on it.

---

### Post by dc. on 2007-04-27
Rumors have it that the new drivers activate DMA automatically which I can confirm somewhat because my drive is set automatically to UDMA5, the highest transfer mode it supports.

Things are different though for non-standard options like the acoustic management I mentioned in my earlier post.

---

### Post by Strannik on 2007-04-27
hm.. its just really surprizing.. would be great if it would be written in the changelog or something..

---

### Post by dc. on 2007-04-27
Yes, definitely.

Did someone find an entry that deals with this problem in launchpad.net yet?

---

### Post by allwin on 2007-04-27
I did some research and experimentation.  First this is not construed as a "bug" this is supposed to be a "good thing" shearight!  Bottom line, Feisty wants to look at EVERYTHING in UUID form and not /dev/xxx form, so it's prolly a good idea to update Fstab to UUIDs if you can...and at least change hdxx to sdxx in fstab!  Second, there is a utility called SDPARM, but it is NOT equivalent to HDPARM at all.  Third, any tweaks you made from a previous version like Edgy need to be reviewed and updated, like the NOATIME and WRITEBACK mode of EXT3 being set, plus all your HDPARM tweaks.  If there's any consolation, it appears the new view of the hard drives is optimal, that is DMA is turned on and all that.  But as to setting other parameters, I surely don't know although you can find doc on SDPARM on Google, and there's hardly anything you can tweak (seems to me) with that.

---

### Post by nubutu on 2007-04-28
Some information:

[http://linux-ata.org/faq.html](http://linux-ata.org/faq.html)

---

### Post by dc. on 2007-05-04
bump

---

### Post by dc. on 2007-05-08
And there are new problems:

after a fresh boot hdparm shows that my harddrive runs correctly in udma5-mode:
DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5

however, after hibernating and resumeing

DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2 udma3 udma4 udma5


This is a serious bug!

---

### Post by SergeiFranco on 2007-05-12
I have an ITE RAID IDE controller and I get ~2Mb/s transfer rates - this is pathetic :(
Harddrives are PATA drives btw, my other on board PATA drive (through AHCI controller) works fine.
Also I have noticed I get from hdparm -i "Checksum: incorrect (0xe6), expected 0x1a" on both drives on that controller.
Here is someone's thread regarding same problem.
[http://ubuntuforums.org/showthread.php?p=2640646#post2640646](http://ubuntuforums.org/showthread.php?p=2640646#post2640646)
I actually don't think this is actually limited to ITE controller as there are a few bug reports on launchpad with similar transfer rates in Feisty.
Oh and other thing, when there is a transfer from affected drives it uses both of the cores close to 100%.
and form [http://linux-ata.org/faq.html:](http://linux-ata.org/faq.html:)
> Older, unsupported ioctls

Why does HDIO_SET_DMA fail? I want to use DMA!
Why does HDIO_SET_UNMASKINTR fail?

libata intentionally does not support all the HDIO_xxx ioctls that were supported by the older IDE driver. It is now preferred to use SG_IO as a generalized ATA command submission method, rather than creating a myriad of ioctls for each specific purpose.

The design decision was made only to support the HDIO_xxx ioctls that were heavily used by other programs. Generally the driver always programs the hardware to its maximum capability automatically, completely without user intervention. Therefore, for example, HDIO_SET_DMA is not needed for the vast majority of users because DMA is automatically enabled and used where available.
So what am I supposed to do to enable DMA then?

---

### Post by nubutu on 2007-05-12
You said it. This is just pathetic. I can't believe this kernel did pass through when only few days before the release of Feisty there was people with non-booting systems in launchpad. 

And I can't believe there are not any measures to give full backward compatibility with the old system. And even less that nothing was done so far, not even an explanation from somebody with certain authority on the subject, nothing, as far as I know.

This certainly makes me think about moving to Debian and forget about Ubuntu. I've got a life to live, a subject to study and so many things to do (like doing nothing at all). Getting tired of fixing stupid things I didn't even break.

Sorry guys.

---

### Post by dc. on 2007-05-13
Is there anything on launchpad regarding our issue?

---

### Post by nubutu on 2007-05-13
In the following thread someboy informed to have filed a bug report, which you can find below.

[http://ubuntuforums.org/showthread.php?t=400356&page=2](http://ubuntuforums.org/showthread.php?t=400356&page=2)

[https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/110636](https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/110636)

What I said about this kernel being quite problematic comes from things like these:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106063](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106063)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/103410](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/103410)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/82314](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/82314)

And I have to say that there actually was some notification about the issue:

[https://wiki.ubuntu.com/LibAtaForAtaDisks](https://wiki.ubuntu.com/LibAtaForAtaDisks)

---

### Post by dc. on 2007-05-28
Solved with 2.6.20-16-generic

---

### Post by lagartoflojo on 2007-05-30
I can't endorse that 2.6.20-16-generic solved this.
My PATA drive is still recognized as SCSI:
```
$ uname -r
2.6.20-16-generic
$ sudo lshw -C disk
  *-disk                  
       description: SCSI Disk
       product: HTS541080G9AT00
       vendor: ATA
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: MB4O
       (...)
```

---

### Post by meanmrmustard on 2007-05-31
I hadn't checked before upgrading to this kernel but I'm seeing /dev/hda now.



 uname -r
2.6.20-16-generic

~$ sudo lshw -C disk
            
   
  *-disk
       description: ATA Disk
       product: ST3500630A
       vendor: Seagate
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
      (....)

---

### Post by pestilence on 2007-06-11
The new ATA handling module sets automatically your disks, my laptop has an ATA disk which is now recognized as /dev/sda, DMA etc cannot be set through hdparm and the hdparm -v /dev/sda reports nothing. BUT still:
```

pestilence@pestilence-laptop:~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   1802 MB in  2.00 seconds = 901.58 MB/sec
 Timing buffered disk reads:   86 MB in  3.01 seconds =  28.56 MB/sec

```

Scores normaly...so don't worry if your disk cannot me manually set, it prolly is performing as it should be. Check hdparm -I /dev/sda and see what is set:
```

pestilence@pestilence-laptop:~$ sudo hdparm -v /dev/sda

/dev/sda:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 12161/255/63, sectors = 195371568, start = 0

```

But:
```

pestilence@pestilence-laptop:~$ sudo hdparm -I /dev/sda

/dev/sda:

ATA device, with non-removable media
        Model Number:       ST9100822A
        Serial Number:      3LG1L8KE
        Firmware Revision:  3.01
Standards:
        Used: ATA/ATAPI-6 T13 1410D revision 2
        Supported: 6 5 4
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:  195371568
        LBA48  user addressable sectors:  195371568
        device size with M = 1024*1024:       95396 MBytes
        device size with M = 1000*1000:      100030 MBytes (100 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 16
        Advanced power management level: unknown setting (0x8080)
        Recommended acoustic management value: 254, current value: 0
        **DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5**
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=240ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    SMART feature set
                Security Mode feature set
           *    Power Management feature set
           *    Write cache
           *    Look-ahead
           *    Host Protected Area feature set
           *    WRITE_BUFFER command
           *    READ_BUFFER command
           *    DOWNLOAD_MICROCODE
           *    Advanced Power Management feature set
                SET_MAX security extension
           *    48-bit Address feature set
           *    Device Configuration Overlay feature set
           *    Mandatory FLUSH_CACHE
           *    FLUSH_CACHE_EXT
           *    SMART error logging
           *    SMART self-test
Security:
        Master password revision code = 65534
                supported
        not     enabled
        not     locked
                frozen
        not     expired: security count
        not     supported: enhanced erase
HW reset results:
        CBLID- above Vih
        Device num = 0 determined by CSEL
Checksum: correct

```

As you can see the HD is set to udma5!

---

### Post by wallneradam on 2007-09-20
My Acer notebook has had the sam issue. I found a solution.

The problem is with the new "ata_piix" module. The solution is to blacklist this module and make a new initramfs:
[LIST=1]
[*]Create a file, "blacklist-local" in /etc/modprobe.d! (sudo touch /etc/modprobe.d/blacklist-local)
[*]Edit the file (sudo gedit /etc/modprobe.d/blacklist-local)
[*]Write the following line in it, then save it: 
blacklist ata_piix
[*]Edit /etc/initramfs-tools/modules (sudo gedit /etc/initramfs-tools/modules)
[*]Add the following lines and save it:
piix                                                                                                                                           
ide_generic                                                                                                                                    
ide_cd                                                                                                                                         
ide_disk
[*]Execute the following command: sudo update-initramfs -u
[*]Update all files has /dev/sda (or sdb...) in /etc and /boot. You need to change them to hda (hdb...). These should be only the fstab and menu.lst files. But if you use UUIDs you don't need to modify anything.
[*]Restart your system.
[/LIST]
Be sure all edited files has a final blank line (enter).

After these steps you got old good hda disks and you can use hdparm as well.

I hope I could help. Best regards: 
Adam

---

### Post by sugarland2k on 2007-10-23
I know this in an Ubuntu forum but I do run both Ubuntu/Kubuntu and SUSE 10.3.  For SUSE, I added the "hwprobe=-modules.pata" as detailed at [http://www.softwareinreview.com/cms/content/view/84/](http://www.softwareinreview.com/cms/content/view/84/)

First I tried this on the boot level as an extra command, then I added it though the boot module in Yast.  

SUSE sees drives as /dev/sda instead of /dev/hda, etc. and this is the problem?  

End result - My SUSE system runs much faster now.

Hopefully one of the gurus can explain this or advise on every better settings to speed up HD access.

The community makes Ubuntu the best!

---

### Post by daivwilson on 2008-01-11
> **wallneradam said:**
> My Acer notebook has had the sam issue. I found a solution.

Thanks wallneradam, this solution worked perfectly for me on a desktop PC.

---

### Post by vvvladut on 2008-04-11
> **daivwilson said:**
> Thanks wallneradam, this solution worked perfectly for me on a desktop PC.

It worked on mine too! Now I can use hdparm, but how do I make settings persistent on reboot?:(

---

