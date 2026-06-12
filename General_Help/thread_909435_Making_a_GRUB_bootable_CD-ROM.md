---
title: "Making a GRUB bootable CD-ROM"
date: 2008-09-03
forum: General Help
---

### Post by silvagroup on 2008-09-03
I have always kept a bootable grub cd handy (just in case). 

This used to be a very easy process with mkisofs which was part of all *buntus in the past.

For some crazy reason that's no longer an option with Hardy.
Now that I have my 8.04 running as I like I would like to make a new grub boot cd (just in case).

I have not found any information which helps with doing this with genisoimage.

I know that I can boot into any live cd os and do a grub install but it's so much simpler with the grub iso cd and I have full access to my system with the boot cd.

Any help would be greatly appreciated.

Thanks in advance.

---

### Post by Titan8990 on 2008-09-03
I think this is what you are looking for: [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by silvagroup on 2008-09-03
Thanks Titan8990, but that's very similar to the livecd method what I want would actually just be a mirror of my current mbr with grub and i could run my full sysyetm by botting off the boot cd in case my mbr or grub gets messed up.

Like I said it was a very easy thing to do with mkisofs.

I still have my 7.10 install so I may need to login to it again and do it from there for my 8.04 system, not sure if that's possible but worth a try.

But that still does not solve how to do a grub boot cd from Hardy.

---

### Post by silvagroup on 2008-09-03
Well after some more searching I found that the command for genisoimage is not much different from the mkisofs.

this is the genisoimage command:genisoimage -R -b boot/grub/stage2_eltorito \
-input-charset iso8859-1 \ -V "iso" \ -no-emul-boot \ -boot-load-size 4 -boot-info-table -o grub.iso iso 

Worked great. I now have a grub boot disk !!!!

---

### Post by bisan on 2009-03-21
> **silvagroup said:**
> Well after some more searching I found that the command for genisoimage is not much different from the mkisofs.

this is the genisoimage command:genisoimage -R -b boot/grub/stage2_eltorito \
-input-charset iso8859-1 \ -V "iso" \ -no-emul-boot \ -boot-load-size 4 -boot-info-table -o grub.iso iso 

Worked great. I now have a grub boot disk !!!!

I followed the instructions for creating a GRUB Bootable CD-Rom found at ([http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html](http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html))

I tried both the mkisofs command in the GRUB mannual and the genisoimage command in the post above.  Both times I got the following error message:

I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage: No such file or directory. Invalid node - ' -input-charset'.

I am using Ubuntu 8.10

Any suggestions on what I could be doing wrong?

---

### Post by silvagroup on 2009-03-25
Sorry it took so long for a response,
but you need to install genisoimage and it should work.

---

