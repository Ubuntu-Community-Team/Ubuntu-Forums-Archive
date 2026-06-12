---
title: "kickstart installation of Ubuntu 8.04"
date: 2009-06-25
forum: Installation &amp; Upgrades
---

### Post by krowa on 2009-06-25
Welcome Everyone,

I am trying kickstart installation of Ubuntu8.04-desktop-LTS. I have generated the ks.cfg file in  

system-config-kickstart

and edited the isolinux.cfg file and given the path of ks.cfg: 

      kernel /casper/vmlinuz 
      append  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz ks=cdrom:ubuntu.ks.cfg quiet splash --

Can somebody tell me wher I make mistake? or tell me how exactly I must boot instalation with kickstart file?

Thanks

krowa

---

### Post by krowa on 2009-06-26
Ok, now I known what I mast do:

"After saving the file, create a boot diskette from boot.img for CD-ROM installations or bootnet.img for network installations. Copy the kickstart file (ks.cfg) on the boot diskette. Boot from the diskette and type linux ks=floppy to start the kickstart installation."

But I do not know for where I have boot.img for Ubuntu 8.04 LTS. How
 I can find it?

---

