---
title: "Problem with Seagate 500gb Freeagent"
date: 2010-12-05
forum: Hardware
---

### Post by itsbatmansilly on 2010-12-05
hi, new here and let me preface by saying i have scoured the web and tried many solutions for this problem including various scripts, rules.d changes etc to no avail lol.

i have a Seagate Freeagent 500gig drive. when i use it via usb on my netbook using an ubuntu 10.10 live disk on the flash drive, it works pretty much fine. when i connect it to my desktop however, which is running 10.10 off of the HD, it does not see the seagate at all. doesnt mount, doesnt acknowledge its existance in anyway whatsoever, even with fdisk, gparted etc.

what the heck can i do here? any help would be appreciated as i am currently having to ftp my music from my hard drive to the seagate in order to transfer it lol

---

### Post by wilee-nilee on 2010-12-05
Do you have windows machine to see if it shows?

How is it formatted?

How you tried a bootable partitioner on its own?

Can you desribe in more detai the steps you have taken?

Can you remember unplugging it without using a disconnect through the computer first? say during a data transfer.

---

### Post by itsbatmansilly on 2010-12-06
> **wilee-nilee said:**
> Do you have windows machine to see if it shows? **it does show on a windows 7 machine** 

How is it formatted?  **have tried many ways, currently fat**

How you tried a bootable partitioner on its own? **yes and still no go**

Can you desribe in more detai the steps you have taken? [B]well i tried to wonk about with power management, no go, tried the sdparm method described [http://www.linuxquestions.org/questions/linux-hardware-18/ubuntu-compatibility-issues-with-seagate-free-agent-pro-external-hdd-687233/]("http://www.linuxquestions.org/questions/linux-hardware-18/ubuntu-compatibility-issues-with-seagate-free-agent-pro-external-hdd-687233/") there, created a new UDEV rule as suggested [here]("http://ubuntuforums.org/showthread.php?t=494673") and still no go
[/B]
Can you remember unplugging it without using a disconnect through the computer first? say during a data transfer. **nope dont think i did**.

all i can say is ugh lol

---

### Post by wilee-nilee on 2010-12-06
> **itsbatmansilly said:**
> all i can say is ugh lol

Should be formatted as a ntfs probably, that way the share between Linux and Windows is a up to date type of shared use. Fat anything is not a good choice for a 500 gig drive.

If it was a ntfs you could run a chkdsk.

If it was me and I have several externals one 2 terrabytes all NTFS. I would back thte stuff up on that one through the windows 7 then reformat it to a NTFS and reload it and call it a day.

With a quick look on the web through your link it looks like the free agent may have some compatibility problems anyway, here is my 2 terra model.
[http://www.amazon.com/gp/product/B002BH4ONE/ref=oss_product](http://www.amazon.com/gp/product/B002BH4ONE/ref=oss_product)

Edit nothing but not compatible with Linux on these freeagent hard drives, I'm surprised at this to be honest.

I'm sure you must have come across this the link is a hack for the power problem, which seems to be part of the whole conundrum.

---

### Post by itsbatmansilly on 2010-12-06
tried ntfs as well in the beginning but will try again as you are right it is a better option anyway!

---

