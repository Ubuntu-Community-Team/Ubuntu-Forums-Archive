---
title: "Dell BIOS update"
date: 2015-06-02
forum: Hardware
---

### Post by Daniel_Harvey on 2015-06-02
Hello,

I am a new Ubuntu user, we have an old Dell Dimension 3000 which I installed the latest Ubuntu on a couple of weeks ago so that my 11 year old son could spend every waking moment building Minecraft worlds and watch Stampy videos. At the moment it only has 512mb of RAM but I have purchased 2gb of Crucial memory but it doesn't recognise it I have been told this is most probably due to it needing a BIOS update.

So far I have spent 3 evenings trawling through various suggestions on how to update the BIOS (I know I should have done this before uninstalling XP) and seem to be hitting a dead end everything I do. 

Please could someone explain to me in really simple terms how I could do this as I am pulling my grey hair out, the wife has started talking about divorce if quote "I spend anymore time on that old bloody computer" and if my son once more says is it sorted I could be put in an asylum.

Thank you for your help, I know this is an issue that has been debated elsewhere but I just can't seem to get it to work.

---

### Post by mörgæs on 2015-06-02
Hi, welcome to the fora.

Does the present BIOS support booting from USB?

---

### Post by Daniel_Harvey on 2015-06-02
I don't think so although I have read somewhere that you can, when I F12 the boot options don't give USB/

Obviously it will boot from CD.

---

### Post by mörgæs on 2015-06-02
If the USB stick is attached during boot and you press F12, is the option still missing?

---

### Post by weatherman2 on 2015-06-02
You may be chasing a red herring.  I've worked on a few Dells of that vintage.  You can't automatically plug in any RAM that fits in the DIMM slot and expect it to work.  Before going through all the trouble of updating the BIOS, I would confirm the RAM really is going to work in there even with the latest BIOS.  I'm not sure I've ever seen a BIOS update add RAM compatibility, though I'm sure it has happened.

I'm lucky that I have plenty of old Dell Windows CDs laying around and can easily install XP on a spare hard drive just to do a BIOS update, if need be.  You may find some tricks to do it using FreeDOS or something on a USB boot, but I'd be cautious - it's easy to "brick" a computer by messing up a BIOS flash.  Then again, that old Dell isn't worth much anyway at this point...

---

### Post by grahammechanical on 2015-06-02
I would not explain to anyone how to flash the BIOS even if we had exactly the same machines. There should be motherboard user guide that explains it. And then there is this.

[http://www.dell.com/support/home/us/en/04/Drivers/DriversDetails?driverId=R115211](http://www.dell.com/support/home/us/en/04/Drivers/DriversDetails?driverId=R115211)

[http://www.freedos.org/](http://www.freedos.org/)

[http://en.community.dell.com/support-forums/desktop/f/3514/t/19259277](http://en.community.dell.com/support-forums/desktop/f/3514/t/19259277)

Regards.

---

### Post by tgalati4 on 2015-06-03
Dell has some PC Utilities that you can burn to a CD.  Search the Dell website. One of those options is to flash BIOS.  I have flashed older Dell machines using a freedos CD and a floppy (with the BIOS files), or by creating a freedos-bootable USB stick with the BIOS files on it.  There are some tutorials on the web.  

Will the machine boot with 1 GB?  1.5 GB?  If so, then go ahead and install.  Make a swap partition on your hard disk of 2.5 GB ahead of time, that will make the installation easier if RAM is low because the Live image will detect swap and use it during installation.

The other method is to put the hard disk in a newer PC and install, then swap the hard disks.  You may have to perform some tweaks, but it generally works OK.  Make sure it is the only drive in the system so that it is detected as /dev/sda.

---

### Post by Yellow Pasque on 2015-06-03
What are the specs of the memory you bought? Have you tried just running 1 stick of memory in the connector labeled DIMM3? (the memory slot closest to the CPU) as tgalati4 suggested?

Note: the updated BIOS versions that Dell offers for your system only mention support for newer CPU's. They should not be necessary for supporting 2GB of RAM.

---

