---
title: "Delete or Format?"
date: 2008-09-29
forum: General Help
---

### Post by coolclassic on 2008-09-29
I have a compact flash card for my dslr. What I would like to know is which is better either deleting files from card or formating the card to remove files. 

Does either methods degrade performance of card?

---

### Post by sh_son on 2008-09-29
[FONT="Trebuchet MS"]Hi,

If I would prefer format it, it will not reduce the performance of the memory stick as long as it's not a hard-drive.

There isn't much difference between deleting or formatting on flash storage devices, however it does on hard-drives.

So, yes, I prefer formatting it still; are you trying to install DSL (damn small linux)?[/FONT]

---

### Post by SuperSonic4 on 2008-09-29
Any effect will be negligible and deleting is easier than formatting although formatting will get rid of all the files

---

### Post by Excalibre on 2008-09-29
> **coolclassic said:**
> I have a compact flash card for my dslr. What I would like to know is which is better either deleting files from card or formating the card to remove files. 

Does either methods degrade performance of card?
Don't format it. Flash memory, unlike hard drives, has a limited number of write/erase cycles that it will do before it breaks down. It's usually a fairly high number, but why wear out your flash card sooner by formatting it, which basically erases a lot of stuff that doesn't need to be erased?

---

### Post by hyper_ch on 2008-09-29
it's about 1 mio writes to a new flash disk... good luck at hitting that limit.

---

### Post by rsambuca on 2008-09-29
A quick format makes way fewer writes to the drive.  To delete each file separately, each filename must be modified.  A quick format will just wipe the allocation table.

---

### Post by Iwannakillyou on 2008-09-29
I have been waiting for about 5 days now but the shipping times are 10-19 days. As soon as I get them I will let you know. I have not seen you on that forum for a long time now and I was wondering where you are? How did it go with the collection that you got? Here is the link to the beads again [http://www.liangdianup.com/beadscrafts_1.htm](http://www.liangdianup.com/beadscrafts_1.htm) and here is the link to the Swarovski beads [http://www.liangdianup.com/inventory/900020.htm](http://www.liangdianup.com/inventory/900020.htm) if those links don't work then you can goto [www.lducompany.com](www.lducompany.com) and click on the beads picture, that should take you right there. I hope you see this message and get back to me cause I miss talking to you :)

---

### Post by Excalibre on 2008-09-30
> **rsambuca said:**
> A quick format makes way fewer writes to the drive.  To delete each file separately, each filename must be modified.  A quick format will just wipe the allocation table.
Cool, I didn't know that.

---

### Post by ArtechnikA on 2008-11-03
> **rsambuca said:**
> A quick format makes way fewer writes to the drive.  To delete each file separately, each filename must be modified.  A quick format will just wipe the allocation table.

Continuing this theme...

Trying to format a CF card - quick or otherwise.  It's a 'generic USB adapter' and mounted as /media/EOS_DIGITAL.

gparted doesn't see it - just the 'real' disk devices.

so - first question - what do I use to format it?  This answer has ben surprisingly hard to find...

second question - it's a 32GB CF.  Formatting it with XP sets it to 8GB.  Formatting it with the target device (a Canon EOS) sets it to 8 GB.  How do I make the full 32GB accessable?

Thanks!

---

### Post by sdowney717 on 2008-11-03
I read some 8 gb flash drives were sold as 16 or 32 gb drives and when formated reveal their true identity.

---

### Post by ArtechnikA on 2008-11-03
> **sdowney717 said:**
> I read some 8 gb flash drives were sold as 16 or 32 gb drives and when formated reveal their true identity.

Can you point me to a link on that topic?  If i'm going to have a confrontation with the vendor, I'd like to have a little more to back up my position.  Thanks.

(Still not sure what I need to do to make this volume visible to gparted tho...)

---

### Post by solitaire on 2008-11-03
Most devices only do a "Quickformat" since a Full format on a Huge hard drive will take an hour or so.
Also a Quickformat can check for failed sectors on the device which may cause data to be lost. Just deleting items won't find bad sectors.

In general I only do a format of a Flash drive if I start having problems with it. But they are becoming so cheap you can just chuck it once that starts to happen...

---

### Post by sdowney717 on 2008-11-03
such as this here

[http://www.everythingusb.com/forums/showthread.php?threadid=12566](http://www.everythingusb.com/forums/showthread.php?threadid=12566)

I was bidding for one of these 16gb flash drives on EBAY, and I noticed one of the sellers was warning buyers that some drives were being hacked, sold as drives of higher capacity.

etc...
[http://translate.google.com/translate?u=http%3A%2F%2Fwww.digitimes.com.tw%2Fn%2Fmemberarticle.asp%3Fid%3D0000050613_B6TLI47WP40NCFW4Q9HFB&hl=en&ie=UTF-8&sl=zh-CN&tl=en](http://translate.google.com/translate?u=http%3A%2F%2Fwww.digitimes.com.tw%2Fn%2Fmemberarticle.asp%3Fid%3D0000050613_B6TLI47WP40NCFW4Q9HFB&hl=en&ie=UTF-8&sl=zh-CN&tl=en)

---

### Post by ArtechnikA on 2008-11-03
> **sdowney717 said:**
> such as this here
[http://www.everythingusb.com/forums/showthread.php?threadid=12566](http://www.everythingusb.com/forums/showthread.php?threadid=12566)
I was bidding for one of these 16gb flash drives on EBAY...

Thanks.  In this case, I am dealing with a (previously) reputable dealer and had no problems in the past, so I am expecting them to stand behind the product.  If not, I won't be shy about naming names...  Half the day is gone without a response to my email inquiry, but it's Monday, and I'm located in Eastern Standard Time, so they get the benefit of the doubt for a while...

---

### Post by ArtechnikA on 2008-11-16
Followup: I did get a response from FlashMemoryStore, who emailed an RMA form.  I returned the (seemingly defective) product and (with no further communication, like a shipping confirmation) received a replacement.

After a lot of experimentation (and just trying things in gparted, which is not completely intuitive...) I learned:

XP doesn't seem able to format a CF bigger than 8GB.  It doesn't even seem able to recognise a CF > 8GB.  (I don't have a 16GB to test, so maybe the limit is 16, not 8.  no matter...)

The Canon EOSD20 can't format a CF to bigger than 8GB, even with firmware 2.0.3 downloaded from Canons site yesterday and described as current.

gparted was able to create and format a FAT32 partition.  The Canon EOS-D20 will write to such a device.  what I don't know yet is: can it actually write out past 8GB?  That's a -lot- of pictures, so I may turn on RAW mode and make some BIG files...

Interestingly, the built-in CF reader in my Linux box also wanted nothing to do with the 32GB CF, but a (newer) $15 multi-card device could see it fine.

---

