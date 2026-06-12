---
title: "netbook mod help"
date: 2009-08-11
forum: Hardware
---

### Post by chubbs1981 on 2009-08-11
ok i've never tried modding as such a spray paint here and there but nothing like this. i have an advent 4212 netbook. its ok for my needs, however its heavy for what it is mainly due to the 80gb HDD. 

i want to remove the HDD and run it on the sd card. or if possible to tap a line off the usb drive and fix a stripped down drive into the chassis somewhere to act as a small HDD. if i run the stystem of the card and i remove the HDD should it just work?

as for the usb drive would it just be easier to plug one into the side.

---

### Post by Chronon on 2009-08-11
> **chubbs1981 said:**
> ok i've never tried modding as such a spray paint here and there but nothing like this. i have an advent 4212 netbook. its ok for my needs, however its heavy for what it is mainly due to the 80gb HDD. 

i want to remove the HDD and run it on the sd card. or if possible to tap a line off the usb drive and fix a stripped down drive into the chassis somewhere to act as a small HDD. if i run the stystem of the card and i remove the HDD should it just work?

as for the usb drive would it just be easier to plug one into the side.

The BIOS should proceed through the boot chain and attempt to boot off of each device in the order you specify.  It should work just fine without any HD attached.  I ran Knoppix for several months on a box that only had a CD-ROM drive -- no HD at all.  It ran just fine.

So, you're planning to take the HD out of the netbook and then carry around a USB drive instead?  Sounds heavier to me.  Isn't the HD inside of the netbook a 1.8" drive?  They aren't that heavy, actually (I just checked one and found it to be 45 grams [about 2 oz.]).  Most of the weight is likely to be due to the battery and screen, I would think.  You probably won't save as much weight as you're imagining.

---

### Post by chubbs1981 on 2009-08-11
when i was saying usb drive i mean the pen drive.not an actual external usb drive.

---

### Post by paulisdead on 2009-08-11
Even a 2.5" drive has negligible weight.  Keep in mind you'll likely take a big hit in speed using an SD card or a thumb drive to run your OS on.

Also, think about how awkward it would be having a USB drive hanging out the side constantly, as well.

It might be technically possible to wire up a USB drive internally, especially if there's an unused header, or header you can unplug something you don't use from it.  I doubt it would be that easy, since I'm sure everything USB inside is packed together and soldered in place.

This operation just doesn't seem worth while at all to me.

As Chronon said, most of the weight is in the battery and screen.  I'm not familiar with the netbook you've got, but perhaps it has a smaller battery you can purchase and swap out.

---

### Post by Tickler on 2009-08-20
Hey, I just installed UNR(Ubuntu 9.04) on my advent 4212 recently. The only issue I'm left with which I cant deal with is that the integrated webcam is not recognised. Tried running $lspci but it didn't appear in the output. Also tried the Msi Wind wikis and several other resources, but can't seem to find a solution. Opening Cheese and clicking video gives me te "No Camera Found" message. Were you able to set this up properly? If so, HOW?!!

Much appreciated,
A newbie

---

