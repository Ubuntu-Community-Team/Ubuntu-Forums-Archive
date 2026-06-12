---
title: "clone hdd to ssd"
date: 2014-08-21
forum: Hardware
---

### Post by stan-saraczewski-yahoo on 2014-08-21
I'd like to clone a 500gb hdd in a laptop running 12.02 to a 500gb ssd. I have a 1tb portable usb-attached drive to copy the 500gb to, then would copy the image from the 1tb to the ssd after swapping it with the hdd.

The question is what software would be simplest ? Clonezilla has a same-to-same (or larger) limitation so I could not go 1tb to 500gb... and reviewing numerous posts I see that some work with the boot sector would be involved. 

If I purchased an external drive enclosure and installed the ssd in it I could use Clonezilla to copy the hdd directly to it, then move it to the laptop. 

Advice anyone ? Thank you...

---

### Post by weatherman2 on 2014-08-21
No "work with the boot sector" should be needed.  The newest versions of Clonezilla seem pretty reliable.  You should be able to "clone" in this way by imaging as you describe.  But understand that you won't be using the *entire *1TB drive for the Clonezilla image;  it will save the image in a directory containing all the files need to restore it.  You could save multiple Clonezilla images on the same 1TB drive.

There's a very slight chance the SSD is in fact slightly smaller than the original HDD, even though both are technically 500GB.  If so, Clonezilla may fail when trying to restore the image to the SSD.  Without a way to connect the SSD and plug it in to check its size, you may have trouble finding out its exact size.  To be safe, you could shrink one of your partitions on the HDD just a little - probably your swap partition is easiest.  You can do this with Gparted.  You can disable swap temporarily in Gparted, then shrink the swap slightly, maybe by 50MB.  Then boot up Clonezilla and save the image to your 1TB, swap your 500GB HDD for the SSD, and then restore the image with Clonezilla.  Chances are it will boot right up.  Then start Gparted again, find the swap and grow it back to the full size left, then choose "Swap On" again and you should be good.

---

### Post by stan-saraczewski-yahoo on 2014-08-21
Thank you weatherman2 for your thoughts. When my ssd arrives in a few days I will use your suggestion.

---

### Post by weatherman2 on 2014-08-21
You may wish to purchase a cheap USB SATA adapter anyway.  It will make cloning easier/faster, because you can attach both drives at the same time (one via USB).  If you buy an enclosure (an adapter that includes a little case around the drive), you can also use your old HDD as a portable hard drive in the future, if you wish.  You may find a 2.5" SATA USB enclosure for around $5 USD on eBay or Amazon if you look.

---

### Post by stan-saraczewski-yahoo on 2014-08-21
Weatherman2 - thanks for the advice - that's just what I intended on doing and have ordered the enclosure.

---

