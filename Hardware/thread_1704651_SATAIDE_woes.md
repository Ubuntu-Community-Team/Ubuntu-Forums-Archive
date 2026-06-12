---
title: "SATA/IDE woes"
date: 2011-03-10
forum: Hardware
---

### Post by SeanCly10 on 2011-03-10
Hi all,

I've got an issue with this computer I'm working on, and I'm hoping some kind soul will be able to point me in the right direction. :)

I'm moving the contents of an older machine into a newer one, one with a newer motherboard and faster processor. This board is an Abit NF7-S2, carrying 2 SATA plugs and 2 IDE plugs. The pertinent components from the older machine are my SATA main drive, running Ubuntu, and an IDE secondary drive. In the older machine, although it took some work, I did manage to get the SATA and IDE drives to co-exist with the SATA as boot drive, which is what I want to do with this new setup.

Here's my issue. If I switch the CMOS jumper and blank out the BIOS to factory settings, then I can plug up the SATA drive and it will boot fine into Ubuntu as many times as I restart it. If I add anything on IDE, then the thing will either go into an endless reboot loop or freeze for what seems like ages on 'Detecting IDE drives...' before it evidently times out and reboots again. After that, removing the IDE drive and putting it back to SATA only does no good, it will stay in that endless reboot cycle until I reset the CMOS again.

I'm at my wits end with this thing. I'm convinced that I'm missing something small or too obvious to think about, but I can't figure it out. I've set everything in the BIOS exactly as the manual says it. I'm lost.

Might anyone have any ideas about where I might be going wrong?

---

### Post by Yellow Pasque on 2011-03-11
Make sure your PATA drive is jumpered to Master. Also, make sure your SATA drive is jumpered to force SATA150 mode, as some older SATA controllers choke when seeing a SATA300 drive (though they should theoretically just fallback to SATA150 speed).

I'm not sure if abit still provides BIOS updates, but check to see if you have the latest.

---

### Post by SeanCly10 on 2011-03-11
> **Temüjin said:**
> Also, make sure your SATA drive is jumpered to force SATA150 mode, as some older SATA controllers choke when seeing a SATA300 drive (though they should theoretically just fallback to SATA150 speed).

Does anyone have a handy rock I can pound my head against? AAARRRGGGHHH!!!

Jumped on Western Digital's website, found the jumper settings for the Caviar Blue in there, stuck on a jumper I found in a box, switched the rig on, and the bloody-minded thing lit up like a Christmas tree. Fully reassembled and running like a scalded dog inside of 20 minutes.

I'd have never in this world thought of that one, hoss. I didn't think this board was old enough to have that problem...hell, the mobo I had before was 5 years older than this one, and I didn't have to jumper the drive. Just goes to show you, cover ALL your bases.

Praises are raised to you in Alabama tonight, man. Thank you, a whole helluva lot.

-Sean

---

