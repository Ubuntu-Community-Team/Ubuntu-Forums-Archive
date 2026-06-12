---
title: "broke my new hard-drive"
date: 2010-08-06
forum: Hardware
---

### Post by svaens on 2010-08-06
Hi guys, 

Having a problem here:

I just bought a new verbatim USB hard-drive, one of those small portable USB powered ones. 

It was working fine until I decided to create a truecrypt file on it. 

I was making a large file, and it had first reported it would take 3 hours to make. However, this later on reported 24 hours. So I decided to abort it. I hit the Abort button, but nothing happened. So, I did something maybe rash; I pulled it out. 

Now it;

1. Doesn't mount
2. Won't format

When I try to mount it, (it was formatted as ext3) I get the error:

Unable to mount location

DBus error org.gtk.Private.RemoteVolumeMonitorFailed:
An operation is already pending

When I try to format it, I get the error:

Error formatting volume

A job is pending on /dev/sdb1



How can I recover from this? 
I can't try another OS (i.e., windows) as it was formatted using ext3, and Ubuntu doesn't seem to be able to handle it anymore ... 

any ideas?

---

### Post by ronnielsen1 on 2010-08-06
I assume you're trying disk utility. Install gparted and try it

---

### Post by svaens on 2010-08-06
No, i first tried using gparted..
Both on Ubuntu and on puppy linux. 

iti makes this 'tick tick tick     tick tick tick ' repeated sound ... as soon as you initiate something with the drive, and it then will never stop until you unplug it. 
Ubuntu trying to shutdown then, can't. until you unplug it. 

Trying to format now with windows, and it is making the same ticking sound.

---

### Post by gasparov on 2010-08-06
- the two error messages you get of pending operations can or not be related to the hard drive problem, likely they are related because your system try to automount the drive but can't and keeps trying, when you do it manually it tells you that it is already trying.

- Hard drive clicking means failure most of the times but for usb powered it can mean that it doesn't have enough power from the usb to start up the thing, remember that when you turn on things usually they absorb more current than when they are acutally working. Suggestions are to change pc or eventually if your hard drive has one, insert the ausiliary power adaptor.  

- the output of dmesg can give a help

- If your hard drive is failing NEVER EVER use any tool to fix drives , copy the partition/drive with dd_rescue first then use the tools on the cloned partition. ( I know that this is not your case because it seems that the internal mechanics of your hard drive seems broken and you can't access it)

regards

---

### Post by svaens on 2010-08-07
seems like it was broken, no getting around it. 
At first I was hoping that it was just a case of some daemon getting in the way of the processes I wanted to run (due to some file system error)  but after I eventually managed to delete the partition, it still would not create a new one. 

Verbatim seems not to be the kind of quality I need ... it did, after all, last only 15 minutes. 

I've taken it back and gone for a (more expensive) seagate one. 
So far there is an immediate improvement in its initial working performance, not to mention that it did not crash after the first 15 minutes. 

Wish me luck!

---

