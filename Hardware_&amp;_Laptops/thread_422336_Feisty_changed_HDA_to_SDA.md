---
title: "Feisty changed HDA to SDA?"
date: 2007-04-25
forum: Hardware &amp; Laptops
---

### Post by allwin on 2007-04-25
I have a fairly modern 80GB Western Dig IDE disk.  Under Edgy, it was called HDA.  Basically, I set up my hdparm.conf file to turn on 32 bit access and then DMA plus set it into a decent DMA mode.  Worked just fine.

After upgrading to Feisty...something...SOMETHING...now recognizes it as an ATA(SCSI?) disk.  Oh it boots and all that, system comes up fine, however when I try to use HDPARM to turn on 32 bit access etc,

sudo hdparm -d1 -c1 /dev/sda

it complains about "improper IOCTL" and refuses to do it.  To make matters worse, at boot time I am setting the system partition to WRITEBACK mode, and have hacked into FSTAB for the same reason.  Now, that tweak is not "sticking".  Grub sees it as HDA but something new in Edgy changes it over to SDA.

I need to know #1, is that the way it's supposed to be, and #2, how I can aim these two tweaks at /dev/sda...or maybe I don't need them any more?

This is not an external drive or anything!  The drive IS of a more modern vintage than the motherboard, which is a Dell XPS from 2002.  Dunno exactly what interface it supports (thought just IDE).

---

### Post by nubutu on 2007-04-26
See here, you are not the only one, but don't expect to find a solution yet...

[http://ubuntuforums.org/showthread.php?t=415057](http://ubuntuforums.org/showthread.php?t=415057)
[http://ubuntuforums.org/showthread.php?t=400356](http://ubuntuforums.org/showthread.php?t=400356)

---

### Post by huygens on 2007-04-27
This is a change in the recent kernel 2.6.19. The old IDE driver is being deprecated slowly, the new driver for SATA disk (which identifies disk as sd*) is the future standard. For now, it seems that hdparm is not 100% compatible with the new kernel. Some parameters can be changed, some cannot... Hopefully this will be fixed in the future.

The odd thing is that it is not constant that all user of Feisty have the new SATA driver or the old IDE driver... For example, I have 3 computers:
[LIST]
[*]laptop was upgraded from Ubuntu 6.10 to Feisty Herd 3 and on... The hard disk is now recognised as /dev/sda (though was hda before, and it is parallel-ATA). However, it still have the correctt DMA settings and all that, so no performance problem. The CD-burner is still recognized as /dev/hdc though... :confused:
[*]desktop was upgraded from Ubuntu 6.10 to 7.04 final. The two hard disks are still hda and hdb, so using the old IDE driver... :confused:. I have also installed on a dedicated partition the 64 bit version of Ubuntu 7.04, this is a fresh install of the RC release. The two hard disks are also seen as hd* instead of sd*... So it did not change, why? I have no clue...
[*]server (and old Duron computer), upgraded the Ubuntu Server Ed. 6.10 to 7.04 final. Same as with the desktop, it seems to be using the old IDE driver too. The disk is recognised as hda...[/LIST]So my installation on my server and desktop are consistent and similar to Ubuntu 6.10. However, my laptop installation is inconsistent with the other... Though I do not have to complain as it is working great and the default settings are correct (so I do not need to use hdparm).
But I just would like to understand (out of curiosity) why this is not the same on my laptop and other computers...

---

### Post by bomanizer on 2007-04-27
Any quick pointers on why are all my partitions showing on the desktop? Feels kinda uncertain to have the other system's partitions available.... ugh...

I'm not familiar at all on this whole sda-thingy... suggestions?

Thanks!

---

### Post by Zer0Nin3r on 2007-05-09
> **bomanizer said:**
> Any quick pointers on why are all my partitions showing on the desktop? Feels kinda uncertain to have the other system's partitions available.... ugh...

I'm not familiar at all on this whole sda-thingy... suggestions?

Thanks!

Heh..heh..So you don't want your other partitions to automatically mount when you boot up and I want my NTFS partitions to automatically mount when I boot up, but that doesn't happen.

I'm still able to mount them, manually, and it just asks for my password.  Now I'm just trying to figure out how to configure it so I don't have to do so each and every time I log in...

*UPDATE*
Was able to mount the drives automatically with a few setting and a little help from the program : pysdm and topic: [http://ubuntuforums.org/showthread.php?t=421095]("http://ubuntuforums.org/showthread.php?t=421095")

---

