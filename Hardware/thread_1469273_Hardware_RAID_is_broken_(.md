---
title: "Hardware RAID is broken :("
date: 2010-05-02
forum: Hardware
---

### Post by ownaginatious on 2010-05-02
Hello everyone,

I recently purchased a SATA/RAID card (Model VANTEC UGT-ST310R) to be used to RAID together a few drives in my computer.

Unfortunately, there appears to be something wrong. I'm able to set up the hardware RAID fine in the card's BIOS, but when I reboot, I am greeted with this message (very top):

[IMG]http://i643.photobucket.com/albums/uu157/ownaginatious/3186eb84.jpg[/IMG]

When I check fdisk, I see that my system has not properly detected my new RAID, and rather thinks I just have two messed up hard drives (The ones in RAID are t 1.5 TBs):

[IMG]http://i643.photobucket.com/albums/uu157/ownaginatious/b7061485.jpg[/IMG]

Does anyone know what's going on here? I know the card is supposed to be linux compatible, because there are comments of people having gotten it to work with Ubuntu before.

I'm thinking this is something to do with my hardware due to the random addressing problem, but I'm not sure. It's an A8N-VM motherboard with an AMD 3000+ Processor, if it matters.

Can anyone help me out?

Thanks,

Dillon

P.S. Sorry for the hugeness of my images :p

---

### Post by arsenic23 on 2010-05-02
Depending on your controller it may have something to do with those drives being drastically different sizes.

---

### Post by ownaginatious on 2010-05-02
Oh no, they're both the same size (2 identical Seagate 1.5 TB drives: /dev/sda and /dev/sdb). The 500 GB is a different hard drive not part of the RAID.

---

### Post by arsenic23 on 2010-05-02
> **ownaginatious said:**
> Oh no, they're both the same size (2 identical Seagate 1.5 TB drives: /dev/sda and /dev/sdb). The 500 GB is a different hard drive not part of the RAID.

Oh, oops, hehe, I confused myself as to what I was looking at.  Sorry.

So you set the raid on blank drives and then installed your OS?  Or did you setup the raid to use as storage alongside your OS?  Where is grub installed?  What drives are(is) you OS on?

---

### Post by ownaginatious on 2010-05-02
The OS is located on a separate 60 GB drive (not pictured) and GRUB is there too. So the RAID is in addition as extra storage to the OS.

---

### Post by arsenic23 on 2010-05-02
Oh, OK.  I see what's going on here after looking up your card.  That's not a true hardware raid card.  You'll still have to set it up in your OS before it will function correctly.  It will still show the two /dev/sd* drives as messed up, but you will have to link them together to form third item that will be the actual raid.  I had one setup back in Dapper.

If you lspci you should be able to get an idea of what chips the card is based up, then you can look up setting it up in Ubuntu.  Though I'm assuming you can boot fine.

---

### Post by arsenic23 on 2010-05-02
If your having trouble looking it up here's a good place to start:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by ownaginatious on 2010-05-02
Ahh, that makes a lot more sense now. I think I'll just go with mdadm. It seems a lot more straight forward, and according to a lot of posts I've read, it's a lot less of a headache to deal with if a drive should fail.

Thanks for your help!

---

