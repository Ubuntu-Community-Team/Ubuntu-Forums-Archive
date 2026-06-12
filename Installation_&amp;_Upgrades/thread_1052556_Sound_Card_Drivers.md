---
title: "Sound Card Drivers"
date: 2009-01-27
forum: Installation &amp; Upgrades
---

### Post by NuttyMonk on 2009-01-27
Hi all,

i've just installed Ubuntu for the first time.  I have some drivers of some sort on the disc i got with my motherboard which has onboard sound and graphics but i'm not sure what they are and how to use them in Ubuntu.

Ubuntu automatically installed the Graphic Card drivers for me and i can see them in the "**System -> Administration -> Hardware Drivers**" section.  But i'm having problems with flickering video in VLC and the Movie Player which is installed with Ubuntu and i am also having problems with jumping audio in both of those progs as well.

I've tried using different output methods in VLC for the audio and video but nothign i do seems to fix the problems so i decided i wanted to use whatever drivers i got on my motherboards install CD in Ubuntu.

This is the files and folders i have in the "**boot**" folder on the CD.

bzImage (program)
initrd.gz (Gzip Archive)
-> isolinux (folder
   isolinux.bin
   isolinux.cfg
   txtmsg (program)

Can anyone tell me what i should do with this stuff to install it?

The **"isolinux.cfg**" file has this text inside it which seems to be video boot options for the kernel...
> 
default XPR2

label XPR2

	kernel /boot/bzImage

	append initrd=/boot/initrd.gz root=/dev/ram0 rw init=linuxrc ramdisk_size=16384 vga=785 video=vesa:ywrap,mtrr console=/dev/tty1 splash=silent boot=cdrom user acpi=off noapic

implicit	0

#gfxboot	bootlogo

#display	txtmsg

prompt		0

timeout		0

#readinfo	2

#framebuffer	0

Linux is quite confusing for someone who has only used Windows for the last 20 years.

If any of this stuff is drivers for the graphics or sound card and i can get it installed i'd be grateful.

Cheers

NM

---

### Post by Mark Phelps on 2009-01-28
You can't use the CD that came with your PC.  It most probably has Windows drivers on it -- which will NOT work in Linux.

The files in the /boot folder are just that -- files needed to boot.  They're not drivers; leave them alone.

As to the flickering, you need to go into the multimedia apps and select "X11" for the video.  That should stop the flickering.

---

