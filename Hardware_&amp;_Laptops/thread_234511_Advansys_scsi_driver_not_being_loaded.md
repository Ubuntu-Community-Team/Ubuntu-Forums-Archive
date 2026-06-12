---
title: "Advansys scsi driver not being loaded"
date: 2006-08-11
forum: Hardware &amp; Laptops
---

### Post by bluegecko73 on 2006-08-11
I'm trying to get Ubuntu 6.06 LAMP server installed on an old pc which has an old Advansys scsi controller card (ABP5140?) controlling the only hard drive, but I'm not having much luck.

I finally realised during the install procedure (which stuck on a blank blue screen with a grey bar for many hours) that it hadn't found any hard drive at all, or recognised it to load the driver.
I managed to get it installed by running a 'modprobe advansys' at a point that meant the installation could progress and I seemed to get everything installed.

The problem I'm left with now though is that after rebooting the machine, it cannot find /dev/sda1 again for much of the same reasons as before - no advansys driver is being loaded.

I've picked apart the initrd image (which I believe is what should have the driver), and it does contain the advansys module.
I've also added an 'alias scsi_hostadapter advansys' line into the /etc/modprobe.d/aliases file after reading that could help, and repackaged the initrd image, but no luck.

I'm totally lost for ideas as to why its not being loaded or anything else to try to make it load.

Anyone have any ideas?

Thanks

---

### Post by bluegecko73 on 2006-08-15
I finally found a solution that worked which involved a tweak to the initrd.

I found the initrd did actually contain my driver, the advansys.ko, but it wasn't loading it. I eventually found out that all I needed to do was to add the line 'advansys' into the /conf/modules file contained in the initrd.
After repacking the details into a new initrd, being v.careful as to how thats down (see below) to avoid problems, it all worked.

For the exact steps (if it'll help anyone else). I've simplified the name of the initrd.img, just for clarity:

1) boot your machine with a version of linux that'll let you tweak and access your initrd. I used a copy of knoppix I had lying around, and going to runlevel 2 ('knoppix 2' at the boot prompt in my case) to get a shell to work from.

2) mount my hard drive so it can be accessed:

mount /dev/sda1 /mnt/sda1

3) gunzip the existing intrd into a temp directory:

gunzip < /mnt/sda1/boot/src-initrd.img > /tmp/working-initrd.img

4) create a working directory:

cd /tmp 
mkdir initrd
cd initrd

5) uncompress the file which should now have the full initrd structure in your current directory:

cpio -id < ../working-initrd.img

6) edit the conf/modules file to add in your missing module and save it

7) re-archive the contents:

[from the initrd dir]
find . | cpio -o -H newc > ../new-initrd.img

This should now leave you with an archive file in your /tmp directory.

Note: I found it was v.important to include the -H newc bit in the above command. Without it, I found that information was being dumped when rearchived and the block size was smaller than that shown when extracting the contents. I also got a Kernel panic when testing with one of my earlier attempts as a result of missing this out.

8) re-zip the contents:

gzip -9 new-initrd.img

This leaves you with a new-initrd.img.gz file. 

9) move the new archive into your boot area. If you want to preserve what you already have, tweak your grub menu to include a new boot menu option for this new initrd file, or just amend the default instead.

Reboot and hopefully you'll get a working system.

---

