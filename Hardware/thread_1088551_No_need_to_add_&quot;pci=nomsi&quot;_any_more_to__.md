---
title: "No need to add &quot;pci=nomsi&quot; any more to  A8V-VM mb"
date: 2009-03-06
forum: Hardware
---

### Post by Fenris_rising on 2009-03-06
Hi all

I hope the following makes sense. I first installed HH 8.04 10 months ago with minimal issues and am now a firm believer in the ethos and benefits of the open source community. 

My main PC died due to PSU failure and has been offline for 2 months. Happily I have got it up and running again and over the past few days I have been familiarizing myself with where I put all my files etc etc.

Anyway amidst all this I decided I would clean the whole thing down and reinstall from the ground up. This is mainly down to my having played around with 'this, that and the other' during my learning how to get the best out of Ubuntu.

Now one of the pre-requisites I had to perform for my PC to boot up to the desktop was to add the code 'pci=nomsi' to the boot string of my menu.lst . A small thing to do though if the kernel was ever updated I would have to redo the addition of the pci=nomsi to the menu.lst .

The other thing I had to do was download and use the 'diskmounter'. My PC has 1 sata HDD which has the main OS. A further 2 IDE HDD's are used as storage. These 2 HDD's never mounted from a fresh install hence the need for the diskmounter one shot 'cure' for this. 

OK if thats all I ever had to do I have had it easy compared to some of you who have to jump through more hoops than Danny the dolphin :D But one small change in my BIOS settings seems to have cured both issues and at first glance improved the speed and response of my system.

My Motherboard is an ASUS A8V-VM quite old in computer terms but it works well for me. The change made in the bios was under the POWER tab and involved enabling the 'ACPI 2.0 Support' Simple and for me just a why not try it moment even though it means little to me :D But I don't have to edit the menu.lst or use diskmounter anymore :)

Whether this will help anyone else I don't know I just thought it may be interesting for those who may have the same MB or if the option is available in other flavours and you have similar issues. Perhaps it would even cure other issues?

regards

Fenris

---

### Post by =CrAzYG33K= on 2009-03-06
Isn't the motherboard based off the AMD socket 939?
I believe I too have the same mobo.
Thanks for the heads-up! :)

---

### Post by Fenris_rising on 2009-03-06
Hi there

yes it is. However just a quick edit. The mounting of the disks aren't added to the fstab file though they show in the places menu. I forgot this was because with them plugged in at install time Ubuntu ignored the sata drive (as in gone without a trace). I had to unplug the 2 IDE drives so the sata would appear as a candidate for the install to go on. 

Hence the drives don't get added. I cant remember why this was important to me (old age is taking it's toll I fear)

But miracle of miracles I have manually added them to my fstab!!! This is quite a feat for me. Especially as diskmounter seems to be unobtainable now. I remember now! it was so that the relevant 'how full' indicator bars in conky would work for each IDE drive.

But the pci=nomsi ain't needed by me anymore and it certainly seems nippier. Even my wireless card seems to be working much better. The speed issue may be perceived of course but it does seem much better.

It would be interesting to know if I have just been lucky or the simple bios change is of 'real' worth. Worst case is I am talking out of my behind, or it needs to be done before the install?? or would it be effective with an existing install??

I have also installed remastersys to create a backup ISO of my setup. I did this with my EEEPC and it's fantastic. If say the HDD died I can fit a new one and then just install a working, set up by me copy of my OS. This in conjunction with backup data files is a killer :D

regards

Fenris

---

