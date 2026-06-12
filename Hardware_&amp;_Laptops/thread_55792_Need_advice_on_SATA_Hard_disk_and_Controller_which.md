---
title: "Need advice on SATA Hard disk and Controller which is 100% Linux Compatible"
date: 2005-08-10
forum: Hardware &amp; Laptops
---

### Post by ganja_guru on 2005-08-10
My drive (Seagate 200GB SATA) was a blacklisted drive in the kernel(along with the silicon Image 3112 controller), but performance was four times slower cause of the blacklist..so I edited out the line. Unfortunately,after 3 months, I now have a drive with a couple of bad blocks..shit..dont know if its cause of the hack or cause of the heat(where i live, temp reaches 40C)..

Anyway I need your advice on what controller and SATA drive I should buy which is 100% Linux Compatible..I'm upgrading very soon so any names of those motherboard controller's is also helpful. Presently I use a Silicon Image 3112 controller(PCI).


p.s - are nvidia sata controllers on those MSI FX64 boards any good with linux? 

Thanks.

---

### Post by greyhound4334 on 2005-08-10
Hey Guru,

Sorry I can't help.  But I was planning on getting one of those 200GB Seagate SATA drives myself, and so I wanted to see what you meant about "blacklisted".  Can you point me to where I can read more about this?

You may have saved me from making an expensive mistake!

Thanks!

---

### Post by ganja_guru on 2005-08-10
Yeah...this is from the kernel's sata_sil.c (for any Silicon Image controller)..the support for sil is bad enough, but Nvidia controller support is worse(no RAID AFAIK)
The best thing to do at the moment is to buy two WD RAPTORS and a 3ware 8006-2LP.. no other option comes even close..

/**
 * sil_dev_config - Apply device/host-specific errata fixups
 * @ap: Port containing device to be examined
 * @dev: Device to be examined
 *
 * After the IDENTIFY [PACKET] DEVICE step is complete, and a
 * device is known to be present, this function is called.
 * We apply two errata fixups which are specific to Silicon Image,
 * a Seagate and a Maxtor fixup.
 *
 * For certain Seagate devices, we must limit the maximum sectors
 * to under 8K.
 *
 * For certain Maxtor devices, we must not program the drive
 * beyond udma5.
 *
 * Both fixups are unfairly pessimistic.  As soon as I get more
 * information on these errata, I will create a more exhaustive
 * list, and apply the fixups to only the specific
 * devices/hosts/firmwares that need it.
 *
 * 20040111 - Seagate drives affected by the Mod15Write bug are blacklisted
 * The Maxtor quirk is in the blacklist, but I'm keeping the original
 * pessimistic fix for the following reasons...
 * - There seems to be less info on it, only one device gleaned off the
 * Windows driver, maybe only one is affected.  More info would be greatly
 * appreciated.
 * - But then again UDMA5 is hardly anything to complain about

} sil_blacklist [] = {
 { "ST320012AS",  SIL_QUIRK_MOD15WRITE },
 { "ST330013AS",  SIL_QUIRK_MOD15WRITE },
 { "ST340017AS",  SIL_QUIRK_MOD15WRITE },
 { "ST360015AS",  SIL_QUIRK_MOD15WRITE },
 { "ST380013AS",  SIL_QUIRK_MOD15WRITE },
 { "ST380023AS",  SIL_QUIRK_MOD15WRITE },
 { "ST3120023AS", SIL_QUIRK_MOD15WRITE },
 { "ST3160023AS", SIL_QUIRK_MOD15WRITE },
 { "ST3120026AS", SIL_QUIRK_MOD15WRITE },
 { "ST3200822AS", SIL_QUIRK_MOD15WRITE },
 { "ST340014ASL", SIL_QUIRK_MOD15WRITE },
 { "ST360014ASL", SIL_QUIRK_MOD15WRITE },
 { "ST380011ASL", SIL_QUIRK_MOD15WRITE },
 { "ST3120022ASL", SIL_QUIRK_MOD15WRITE },
 { "ST3160021ASL", SIL_QUIRK_MOD15WRITE },
 { "Maxtor 4D060H3", SIL_QUIRK_UDMA5MAX },

---

### Post by greyhound4334 on 2005-08-11
Guru,

Thanks for the reply.  Sorry, but you're just a bit over my head.  I am not trying to set up a raid configuration -- I just want fast, cheap, reliable storage, which is what lead me to the barracuda.

I'm looking at an ASUS A8N-E motherboard, which is nvidia nForce4 based.  I can't tell from the specs, or anything I've been able to search for, if it has the Silicon Image based SATA controller.  Are you saying that any nForce4 chipset is going to have the Sil controller?

Sorry, I'm a bit new to all of this.  Just want to build a simple, fast, cheap, stable system.

---

### Post by aveline on 2005-08-11
I have one of the seagates listed... so its blacklisted...which means what precisely???

installing ubuntu on it would be a bad idea ?? i ask b/c i tried it but some things happened & windows wasn't bootable b/c it made (ubuntu i assume) removed the bootable flag from the xp partiton on the same drive.

aveline

---

### Post by ganja_guru on 2005-08-11
greyhound4334 -Most motherboards these days use the nforce or the silicon image chipset as their sata/raid controllers, and both are poorly supported under linux. Anyway you maybe able to do ok with a Silicon Image controller and a hard disk not listed in thr black list. (like a WD/Hitachi/Samsung)

aveline - The blacklist means that the kernel is not letting you run your SATA drive at full speed for whatever reason. when the blacklist was on, I would get speeds of only 19MB/s, but when i commented out the blacklist in the kernel i got speeds of 56 MB/s from the hard disk. Unfortunately, doing that fried my disk. Just use that drive as a Ubuntu storage drive.(note: this also depends on what controller you have. google for it.)

---

### Post by aveline on 2005-08-12
[QUOTE=ganja_guru]greyhound4334 -Most motherboards these days use the nforce or the silicon image chipset as their sata/raid controllers, and both are poorly supported under linux. Anyway you maybe able to do ok with a Silicon Image controller and a hard disk not listed in thr black list. (like a WD/Hitachi/Samsung)

aveline - The blacklist means that the kernel is not letting you run your SATA drive at full speed for whatever reason. when the blacklist was on, I would get speeds of only 19MB/s, but when i commented out the blacklist in the kernel i got speeds of 56 MB/s from the hard disk. Unfortunately, doing that fried my disk. Just use that drive as a Ubuntu storage drive.(note: this also depends on what controller you have. google for it.)[/QUOTE]
 why would that fry the hard drivejust b/c its goin at normal speed??? and then why does windows do ok w/it?? i don't understand that.

ok google for my controllers type...um then what am i looking for after that?  I mean would i be looking tosee how compatible it is??? if it iscompatible, will commenting out the line still be dangerous?

aveline

---

