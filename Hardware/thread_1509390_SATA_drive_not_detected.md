---
title: "SATA drive not detected"
date: 2010-06-14
forum: Hardware
---

### Post by c.webster on 2010-06-14
I'm already running Ubuntu 9.10 on a SATA drive without any problems.  I bought a new SATA drive and have sucessfully wired it up.  My BIOS doesn't recognise it.  The only SATA option in the BIOS set-up screen is as follows:

On chip IDE Device > SATA RAID ROM > enabled.

Do I have to do something within Ubuntu for the drive to be recognised?  If you can help, please bear in mind I'm an idiot who won't understand his kernels from his RAIDs (whatever they are).

---

### Post by xsandz on 2010-06-14
You said that BIOS is not recognising your new device. So i reckon there is no prob with Ubuntu and your new device. You may try a thing. If u have another running SATA port , u can swap the ports with your old running device and check what happens. If older one gets undetected then it will suggest that the prob is with the SATA port. Can you please let me know your mobo detail?

---

### Post by c.webster on 2010-06-14
Thanks for the quick reply.

When you say "swap ports", do you mean the SATA slot on the motherboard?

What do you mean by 'mobo details'?

---

### Post by phoenixflames on 2010-06-14
If its a desktop try putting the new drive without the old one and try it in your BIOS. If it works try both and make sure one says "Master", preferably the bootable one (there is a jumper cable in the sata pins) and the new one "Slave" and is there a long wire to HD to motherboard?:confused:

---

### Post by psusi on 2010-06-14
> **phoenixflames said:**
> If its a desktop try putting the new drive without the old one and try it in your BIOS. If it works try both and make sure one says "Master", preferably the bootable one (there is a jumper cable in the sata pins) and the new one "Slave" and is there a long wire to HD to motherboard?:confused:

No there is not.  Master/slave is for IDE, SATA has no such thing, since you can't connect two drives to the same cable.

---

### Post by cascade9 on 2010-06-14
> **psusi said:**
> No there is not.  Master/slave is for IDE, SATA has no such thing, since you can't connect two drives to the same cable.

True, but there are some motherboards that have 'master' and 'slave' SATA ports. No idea why they did that....

---

### Post by psusi on 2010-06-14
> **cascade9 said:**
> True, but there are some motherboards that have 'master' and 'slave' SATA ports. No idea why they did that....

Because the controller can be configured in the bios to pretend to be an ide controller instead of AHCI SATA.  In that mode, it pretends that the drives on the respective sata ports are IDE master/slave.

---

### Post by phoenixflames on 2010-06-14
Update the BIOS maybe?

---

### Post by xsandz on 2010-06-15
yeah mobo means Motherboard details :P ...and as far as i am concerned that there is no issue of master-slave in SATA ports ...and yes I am talking about SATA ports of motherboard

---

### Post by phoenixflames on 2010-06-17
If you have an eSATA port then use it or even look for a usb to Hard drive converter

EDIT: Btw there is a SATA with master/slave its called PATA

---

### Post by nerderello on 2010-09-18
This is how I **solved** a similar problem.

My mobo has two SATA ports on it, but I'd always run IDE (PATA) style hard disks, so, as it's my birthday, I bought a new 500 gb SATA hard disk.

I plugged it in, powered the PC up, and.... Well, it took ages to do a POST and when I had a look in the BIOS (F2 from the POST screen on my mobo) the old hard disk (IDE) was there but my new SATA disk wasn't.

I booted up Ubuntu 10.04 (on my old IDE hard disk), it came up fine although the hard disk access light was on permanently. And when I looked in the SYSLOG I saw (every second or so) these three messages:

> [B]ata3: SATA link down (SStatus 0 SControl 310
ata3: EH complete
ata3: hard resetting link[/B]I have no idea how an operating system can "see" a device that the BIOS cannot, but that seems to be what was happening.

After a bit of research I discovered that:

[LIST=1]
[*]SATA v1 (speeds up to 150) is not the same as SATA v2 (speeds up to 300), but more importantly SATA v2 is not as backwardly compatible as it should be.
[*]My mobo has two SATA v1 (upto 150 - 1.5 Gb/s) ports.
[*]The Seagate hard disk is a SATA v2 (300 - 3Gb/s) the interface shown on the site that  I bought it from as **SATA/30**0 .
[*]My mobo (ASROCK **AM2NF3-VSTA**) was refusing to deal correctly with the fast hard disk.
[/LIST]

**_The solution_**
The solution was to force the hard disk to operate at the slower speed. 

This was done by putting a **jumpe**r across the two pins furthest away from the data connector (if you look at my Seagate 500gb hard disk - with the circuit board bits uppermost -, it has (left to right) a four pin jumper block, the SATA data socket, the SATA power socket. And the jumper needs to be put over the two pins furthest away from the SATA data socket. A picture of this can be found at : [http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=206571&NewLang=en](http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=206571&NewLang=en) ).

Once I had put the jumper on and re-connected the drive, I booted the PC, went into the BIOS and there, as bold as brass, was the new SATA drive.

I have since loaded (installed afresh) Ubuntu 10.04 onto my new SATA drive and it works a treat (nothing special to do, just treated it like a normal drive).

Hope this helps someone else who naively thought that as both the mobo and the hard disk said SATA they would simply work out of the box.

Nerderello

---

