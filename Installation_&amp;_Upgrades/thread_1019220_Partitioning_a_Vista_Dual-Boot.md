---
title: "Partitioning a Vista Dual-Boot"
date: 2008-12-22
forum: Installation &amp; Upgrades
---

### Post by xalfor on 2008-12-22
I tried setting up a dual-boot on my system with Vista, but I got stuck at partitioning. It defaulted into manual partitioning, and then in manual, the only options were to configure a logical volume or configure software RAID. 

Any help would be appreciated!

---

### Post by tommcd on 2008-12-23
Vista has it's own partitioning tool that you can use to shrink the Vista partition and create some free space:
[http://lifehacker.com/software/vista/screenshot-tour--repartition-your-hard-drive-in-windows-vista-231613.php](http://lifehacker.com/software/vista/screenshot-tour--repartition-your-hard-drive-in-windows-vista-231613.php)
[http://articles.techrepublic.com.com/5100-10878_11-6170510.html](http://articles.techrepublic.com.com/5100-10878_11-6170510.html)
Use that to create some free space, then boot up the Ubuntu CD and install Ubuntu onto the newly allocated free space. Be sure to defragment Windows before partitioning. 

A 10GB partition would be enough if you just want to try Ubuntu without using up too much space. If you are committed to dual booting, then use more space or split the drive 50% Vista and 50% Ubuntu.

And welcome to the Ubuntu forums!

---

### Post by xalfor on 2008-12-23
> **tommcd said:**
> Vista has it's own partitioning tool that you can use to shrink the Vista partition and create some free space:
[http://lifehacker.com/software/vista/screenshot-tour--repartition-your-hard-drive-in-windows-vista-231613.php](http://lifehacker.com/software/vista/screenshot-tour--repartition-your-hard-drive-in-windows-vista-231613.php)
[http://articles.techrepublic.com.com/5100-10878_11-6170510.html](http://articles.techrepublic.com.com/5100-10878_11-6170510.html)
Use that to create some free space, then boot up the Ubuntu CD and install Ubuntu onto the newly allocated free space. Be sure to defragment Windows before partitioning. 

A 10GB partition would be enough if you just want to try Ubuntu without using up too much space. If you are committed to dual booting, then use more space or split the drive 50% Vista and 50% Ubuntu.

And welcome to the Ubuntu forums!

Thanks for the help and the welcome. I'm still having trouble though. I was able to clear off the space, and have about 15GB free now. I still can't figure out how to set them up, though. When I go into the installer again, I still only have the options to configure software RAID and the Logical Volume Manager. If I try to just finish partitioning, it tells me I need a root partition (which makes sense).

---

### Post by caljohnsmith on 2008-12-23
Is your Vista currently using a RAID configuration? In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and hopefully what your problem might be.

---

