---
title: "partition not possible! unable to install ubuntu"
date: 2009-02-05
forum: Installation &amp; Upgrades
---

### Post by eskararriba on 2009-02-05
hello everybody, 

I've got a huge problem with the installation: I had a wubi install before and tried to migrate to a real partition using Gparted, but it wouldn't let me do the partition (claiming errors on the hard drive) - I defragmented the hard drive and ran CHKDSK, everything turns out to be fine. 

Now (after three days of trying) I finally deleted the wubi install to do a new clean install with the ubuntu liveCD- but again, partition is impossible. 

Any ideas what may be the problem? Or even a solution?

thanks a lot!

(I got an HP DV2000, the hard disk is a Samsung HM250JI ATA, abou 90 GB occupied and 130 free space)

---

### Post by wolfen69 on 2009-02-05
i have seen this before. the only solution i found was to buy a new hard drive unfortunately. hopefully someone knows something i don't. good luck.

---

### Post by |{urse on 2009-02-05
yeah, if you've gotten the same problem with the live install try writing zeroes (low level format) to the hard disk before installing (you will have to reinstall windows, then install ubuntu)

If you feel up to that, check out a livecd made for low level formatting called DBAN

[www.dban.org](www.dban.org)

---

### Post by eskararriba on 2009-02-05
hi, 

I already deleted ubuntu, and my documents are saved on an external hard drive. the computer is rather new and I haven't had any problems with it, so I'm not too fond of buying a new hard drive... hm, don't you think formatting it completely, re-install vista and then ubuntu would be a possible way to do this...?

---

### Post by eskararriba on 2009-02-05
ok, I decided to make an ubuntu full install, so I don' t have to format partitions - I didn't like windows anyways, and never used it ... d'you think it works if I choose the second option (full install) of the liveCD?

DBAN sounds as a somewhat radical thing to do... I would do so, but will it be possible to re-install windows from the recovery disk / ubuntu from the liveCD afterwards...?

---

### Post by caljohnsmith on 2009-02-05
When you tried to install Ubuntu to its own partition, you said "partition is impossible". What do you mean? Does the Ubuntu installer show you the partitions, but then gives you some sort of error when you try to make partitions? Please be as specific as possible about the problem. Also, from your Live CD, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
sudo fdisk -lu
```
And please post the output.

---

### Post by eskararriba on 2009-02-05
hi, 

when I try to do the partition, gparted and/or liveCD both show me the C: drive (and a D: drive, which is for recovery), start the disk check, start the shrinking process and after 20 minutes or so show an ERROR message, saying that shrinking is not possible.

when I run the sudo fdisk command (which I cant post as I haven't got a connection with the liveCD) it just shows me the basic details of my hard drive (250 GB, heads, etc.)

---

### Post by avtolle on 2009-02-05
Well, if you have Vista, you would need to use its tool for shrinking the partition before trying to partition with Gparted.

---

### Post by eskararriba on 2009-02-05
and again:

I decided to do a full install, deleting windows (won't miss it, so no problem), and it worked perfectly ... I think. Now I can post the outcome of the command (sudo fdisk -lu), which is:


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x89254f32

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   470543849   235271893+  83  Linux
/dev/sda2       470543850   488392064     8924107+   5  Extended
/dev/sda5       470543913   488392064     8924076   82  Linux swap / Solaris


Do you see anything weird up there? Are there any tests I should run? Is vista REALLY gone?

thanks again

---

### Post by ElizabethJoan on 2009-02-05
> **caljohnsmith said:**
> When you tried to install Ubuntu to its own partition, you said "partition is impossible". What do you mean? Does the Ubuntu installer show you the partitions, but then gives you some sort of error when you try to make partitions? Please be as specific as possible about the problem. Also, from your Live CD, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
sudo fdisk -lu
```
And please post the output.

I have a somewhat similar problem, but mine is that when I get to the Partition Disks menu, there is nothing there. I click forward and it tells me that I have make a selection, but there is nothing to select.

When I enter that code into a terminal, there is no output.

EDIT: I forgot to mention that I am running Vista, so would I instead have to partition my hard drive through a different method as was mentioned above?

---

### Post by caljohnsmith on 2009-02-05
ElizabethJoan, are you trying to install Ubuntu to a SATA drive?

---

### Post by ElizabethJoan on 2009-02-05
I actually had no idea, but I looked it up, and yes, it's a SATA drive.

---

### Post by caljohnsmith on 2009-02-05
OK, that might be the issue then. How about going into your BIOS and set your SATA drive to use "AHCI" mode, and if for some reason your BIOS doesn't have AHCI available, you could instead try "RAID" if that is available. Once you've done that, boot your Live CD again, but at the first main menu press F6 for special boot options, and then add:
```
pci=nomsi
```
To the end of the long string of boot parameters. Then try booting Ubuntu by choosing the "try Ubuntu without making changes", and let me know if that works or not.

---

### Post by ElizabethJoan on 2009-02-05
Alright, I'll be back in a bit with the results.

---

### Post by jrusso2 on 2009-02-05
This thread reminds me of too many cooks.

---

### Post by ElizabethJoan on 2009-02-05
> **ElizabethJoan said:**
> Alright, I'll be back in a bit with the results.

There was no option for either ACHI or RAID.
There was only something called "SATA Native Support" or something like that, which was enabled, with the option to disable it.

---

### Post by caljohnsmith on 2009-02-05
What BIOS options do you have for your SATA drive? Just "SATA Native support"? Do you have anything about IDE-legacy mode or any other options available? If you don't have any other BIOS options, you could try disabling the SATA native support, and then check to see if Ubuntu can see the drive by doing "sudo fdisk -lu" again in Ubuntu.

---

### Post by ElizabethJoan on 2009-02-05
There were no other options in BIOS.
I disabled the Native Support and Ubuntu can see the drive now. I'll try to install now and let you know if it is successful or not.

EDIT: Disabling it worked. Woot! Thank you for your help. :)

---

### Post by |{urse on 2009-02-06
> **eskararriba said:**
> hi, 

I already deleted ubuntu, and my documents are saved on an external hard drive. the computer is rather new and I haven't had any problems with it, so I'm not too fond of buying a new hard drive... hm, don't you think formatting it completely, re-install vista and then ubuntu would be a possible way to do this...?

Did you install Veeeeeesta yourself? Was it pre-installed? If it was pre-installed there is probably some odd proprietary partition (which is probably the whole problem anyways) i would say yes absolutely. Formatting it completely is what DBAN does by the way. format that sucker, reload veeesta (if you insist) then install ubuntu.

[www.dban.org](www.dban.org)

^^ sorry for the 10hrs later reply.

lol veeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeesta! (in an outrageous hispanic accent)

---

### Post by caljohnsmith on 2009-02-06
> **ElizabethJoan said:**
> There were no other options in BIOS.
I disabled the Native Support and Ubuntu can see the drive now. I'll try to install now and let you know if it is successful or not.

EDIT: Disabling it worked. Woot! Thank you for your help. :)
Glad to hear that worked OK; cheers and enjoy your new Ubuntu install. :)

---

