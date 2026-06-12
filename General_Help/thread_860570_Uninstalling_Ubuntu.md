---
title: "Uninstalling Ubuntu"
date: 2008-07-15
forum: General Help
---

### Post by Drayx9293 on 2008-07-15
I have ubuntu installed accross my whole hard drive with no partitions, meaning I cannot uninstall from windows.  Grub will not let me boot from a live cd. Is there a way to remove grub so I can boot from a windows or linux live cd and delete the partition.  Or is there another way to delete linux from inside linux? Thanks in advance.

---

### Post by PixelSmack on 2008-07-15
Try having a look at your BIOS settings, there will probably be a way to set that to boot from a CD prior to grub even being loaded.

---

### Post by coffeecat on 2008-07-15
> **Drayx9293 said:**
> Grub will not let me boot from a live cd.

I think you're misunderstanding something here. If you want to boot from a CD, just put the CD in the drive and bootup. If the CD won't boot, that's nothing to do with Grub. You'll need to change the BIOS settings.

However, what may be happening is that you are not able to put the CD in quick enough and Grub starts the bootup process from the HD. Do you get a grub menu? If so, just tap the down arrow key to stop it booting, put the CD in and the do the good old three-fingered salute - ctrl-alt-del. That will start a reboot and if your BIOS settings are correct, you will boot from the CD.

Alternatively, if you are already in the Ubuntu desktop, just put the CD in, ignore the window that pops up and do System > Quit > Restart.

---

### Post by Drayx9293 on 2008-07-15
I have my bios configured to boot from cd drive first, I know my cd drive works.  Ive tryed to disable booting from hard drive (I still boot into ubuntu). Ive tryed pulling the plug on my hard drive and all i get is please insert system disk and press enter (the disk is already in).  I installed linux using this cd drive so I know it boots live disks fine.

---

### Post by coffeecat on 2008-07-15
> **Drayx9293 said:**
> all i get is please insert system disk and press enter

That's not a grub message. That's a BIOS message. Do you get this with the Windows install disc or the Ubuntu CD or both? I've seen another thread where the OP could boot OK from an Ubuntu CD but not from his Windows CD, even though he could browse the contents of his Windows CD. Seems that the Windows CD may have been faulty.

Also I've heard of this happening when a fault develops in the CD/DVD drive. It still seems to work but you can't boot from it. I don't know why. Assuming this is a desktop, not a laptop, have you got another optical drive (or can you borrow one) that you could put into your computer to replace the one that is there - even if only to see if you can boot from that.

---

### Post by Drayx9293 on 2008-07-15
I put the cd in my laptop and it worked fine.  And my friend just used the cd drive to install the same disk the other day.  (he built a new computer and the store forgot to bag his cd drive).  Im fairly sure my drive is working since when I put in the cd with ubuntu up the cd reads just fine.  I find it odd that bios still tries to boot from the hard drive even though i have that sort of booting disabled for testing purposes.

---

### Post by Drayx9293 on 2008-07-15
Ok i figured out why it was booting from the hard drive.  My bios has a boot from another device option that it uses when it cant find what its looking for.  I turned that off and it got a cant find system disk error again.

---

### Post by jimv on 2008-07-15
Your CD drive is likely messed up then, if an XP disk or Ubuntu disk won't load, and the disks work in other machines.  You could try getting one of those CD drive cleaning kits and running it through the machine.

---

### Post by brnetonboy on 2008-07-15
there should be a place in your bios that will let you set the boot order. usually it's hard drive first, then CD, then floppy...

figure out which one is your CD drive and make that one first. If you have more than one hard drive make sure that the correct one is in front of the other ones. 

the state of the hard drive doesn't matter when installing a new OS. you can wipe it completely clean during an install, no matter what it looked like before.

---

### Post by Drayx9293 on 2008-07-16
I know my computer boots from live cds because I installed linux using one about a month ago.  I know both my linux and vista cds work because I have placed them in other computers and they worked.  I believe the cd drive works since my friend just used it to install vista on his new computer... I have tryed replugging in the cd drive and It can read cds when my computer is on.  Why cant I boot from them? I never even recieve the message that says Press any key to boot from cd.  Any ideas on how to fix?

---

### Post by brnetonboy on 2008-07-17
you might want to check the jumper on the CD drive to make sure it is set up correctly (master or slave--probably you should just set it to Cable Select)...

---

### Post by Drayx9293 on 2008-07-24
Ive tryed plugging the cd drive into another SATA port, i know cd drive works, just burned an iso yesterday.  Everything works except for booting from live cds.  Booting from live cds worked fine until I installed linux about a month ago.

---

