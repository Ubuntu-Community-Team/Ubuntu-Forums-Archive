---
title: "PATA + SATA problem?"
date: 2007-06-08
forum: Hardware &amp; Laptops
---

### Post by Matakoo on 2007-06-08
Hi,

I hope someone can shed a little light on this weird problem. 

Here's the deal - I got a new computer assembled, and tried installing Kubuntu 7.04, 64 bit on it. However, I ran into problems almost immediately. The live-cd stopped with various error messages such as:

ATA: abnormal status 0x7f on port 0x00018007
hda: lost interrupt
Failed to set xfermode (err_mask=0x4)
dma_timer_expiry: dma status=0x24

I first thought it was my harddrive that was developing a fault (ATA-disk) so I replaced it with another one. Same problem. I then disconnect the SATA disk (my /home disk) to see if that's the culprit. Nope. Same problem.

I then try to install Vista to see if I get the same problem. No, now everything works (apart from having to download some drivers). 

After some more experimenting, it turned out that everything works in Kubuntu as well if I make sure my DVD-burner (ATAPI) is disconnected. Everything is installed, updated, and configured to my liking. 

I then turn off the computer, just to plug in the burner again to see if I can now get it to work. Guess what? The computer freezes during boot.

Since Vista works properly with the same hardware, I've ruled out that it's a hardware problem. I'm not quite sure where the problem is, but I have a feeling it might be related to the new "treat everything as scsi" method. Especially since everything worked in another computer but a computer that only had ordinary ATA. Apart from SATA and ATA, there's also a real scsi-card in this computer (only a streamer attached to it though, and no disk) and a memory-card reader (which, of course, is also treated as scsi even though its connected through USB).

Any ideas how to fix this, anyone?

---

### Post by reiki on 2007-06-08
What motherboard did you use?

I have both PATA and SATA and this one is working. 

How many IDE (PATA) connectors on the motherboard?
How many SATA connectors?

Does BIOS detect all drives when you are booting up?

What is your boot order?

---

### Post by Matakoo on 2007-06-08
> **reiki said:**
> What motherboard did you use?

I have both PATA and SATA and this one is working. 

How many IDE (PATA) connectors on the motherboard?
How many SATA connectors?

Does BIOS detect all drives when you are booting up?

What is your boot order?

Well, the motherboard is an Asus P5GD2-Premium. And yes, the BIOS recognizes all drives (when they're all plugged in that is). PATA and SATA alike.

There are all-together 3 PATA-connector, and all three are used. I prefer to not have both master and slave on the same channel if at all possible, so I have a DVD-ROM connected to one connector, DVD-burner to another, and my boot-drive on yet a third.

As for SATA, there are 8 connectors divided up between two controllers (one Silicon Image, one Intel, both integrated on the motherboard), although I have disabled the Silicon Image one in the BIOS.

The boot-order is just the DVD-ROM first, and the PATA-HD second. That's it.

And apart from this "small" problem of not being able to boot when the burner is connected, everything works great. And it was easier to get everything to run using 64bit than I thought it would be :)

---

### Post by reiki on 2007-06-08
OK look at your PATA connectors. I have a P5LD2 and on mine there is one PATA connector by itself and then 2 PATA connectors together. The one PATA that's by itself is the only connector that you can use for ATAPI drives (your optical drives). The 2 PATA connectors that are paired up next to each other can have hard drives connected to them but not optical drives. Look in your manual. It should tell you if this is the case with your P5GD2 as well. I suspect this is where your problem is. Since you have 2 optical drives, you may want to put them BOTH on that single PATA as master and slave. Connect your ATA hard drive to one of the paired PATA connectors (preferably the first one of the pair although I'm not sure that matters) and then connect your SATA hard drive to a SATA port. 

Having 2 optical drives as master/slave won't slow anything down. They are both "slow" devices. I agree that you don't want to slave an optical drive to a hard drive as that WILL slow the hard drive down.

Anyways... try it this way and see if that helps. Mine exhibited exactly the same kind of goofy errors.... "I think I see everything, I'll start using everything. OOOooops.... that ain't supposed to be there..."

---

### Post by Matakoo on 2007-06-09
> **reiki said:**
> Having 2 optical drives as master/slave won't slow anything down. They are both "slow" devices. I agree that you don't want to slave an optical drive to a hard drive as that WILL slow the hard drive down.

True. I guess old habits die hard...since I used to get a lot of coasters on older hardware if I had anything more than the writer on one channel. On recent hardware it shouldn't be a problem.

> **reiki said:**
>  Anyways... try it this way and see if that helps. Mine exhibited exactly the same kind of goofy errors.... "I think I see everything, I'll start using everything. OOOooops.... that ain't supposed to be there..."

Indeed it did! I have no idea why I didn't try that in the first place...but the important thing is that it works now! Thanks a lot!

---

### Post by reiki on 2007-06-09
Glad to help. :)

---

