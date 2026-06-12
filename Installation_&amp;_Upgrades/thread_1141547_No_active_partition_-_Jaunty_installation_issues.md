---
title: "No active partition - Jaunty installation issues"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by Jeconti on 2009-04-28
I'm trying to install jaunty on my Mini 9. I downloaded the iso and ran an integrity check to make sure it's okay then used image writer to write it to an external. When I attempt to boot, it simply complains that there is no active partition and then cycles again only to the same outcome.

When I tried to use Lilo to active the partition using sudo lilo.real -A /dev/sdb it responded No active partition found on /dev/sdb

---

### Post by tahnok on 2009-04-28
you have to set the partion you created to active by using some sort of partion manager. I recommend using gparted.

---

### Post by shatterblast on 2009-04-28
The root partition's mount point should be set to /.  This is also assuming it has a swap partition.  It might be easier to use the Install option while running the ISO image's software.  Virtual Box may support this concept if you don't want to burn the image into some bootable format.

---

### Post by Jeconti on 2009-04-28
to tahnok, That would work, but when I use image writer to write the ISO to the external, gparted then reads the disk as unallocated. Writing a partition destroys the ISO data written to the disk.

to shatterblast, I'm unfamiliar with the program you speak of, but unless it would run completely on my external, I'm unsure how I would run a program while installing a new operating system.

---

### Post by Jeconti on 2009-04-28
So I went to play with virtual box, except my Mini 9 is the SSD one. I don't have enough space to create a virtual machine to run Jaunty. So...still looking for some help on this one.

---

### Post by shatterblast on 2009-04-28
Some Mini 9s have the option of an external CD burner, though I think sold separately at times.  That's assuming you might have the option to burn the ISO to CD or even DVD.  Otherwise, I think you could use GParted to first format one partition as a SWAP of about 2 to 4 GB and then format another larger partition as EXT3 where the primary files would go.  The EXT3 partition would need to be set as root by /.

The difficult part would be installing GRUB and the rest of the files from the ISO image onto the partition.  Also to my understanding, the image writer method is for the Intrepid version still.  I'm not sure if Jaunty supports that particularly yet.

---

### Post by Jeconti on 2009-04-28
I'm pretty sure it's supported. I was running Netbook Remix off a pen drive the day after it came out. I'm going to set it up again then use a tool from pendrivelinux.com to force it to be bootable. I'll let you know how it goes.

---

### Post by Jeconti on 2009-04-29
Solved. Screw usb-imagewriter. The create startup disk app works way better.

---

