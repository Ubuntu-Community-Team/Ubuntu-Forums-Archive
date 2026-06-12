---
title: "Building new PC with Ubuntu"
date: 2008-07-11
forum: Hardware
---

### Post by colsandurz on 2008-07-11
Hello,

I'm planning on building a new PC in the next fews weeks and after some experiences with poor hardware compatibility (an ati video card) I'm looking for some suggestions/things to avoid.  

One of my larger concerns is my NIC, I know to avoid atheros chipsets and realtek isn't that great either... does any one have any good suggestions for a nic. 

I'm sure I'll be buying an nVidia, probably an 8000 series.

Also, for memory DDR2 vs DDR3?  I remember reading an article on Tom's Hardware about (early) DDR3 not being so great

Are there any motherboards I should avoid?? I'm planning on buying a brandname here like ASUS, MSI, gigabyte.  are there any motherboards that are particularly compatible with linux??

Finally, for CPU I plan on getting an intel core 2 duo, which I don't anticipate any problems with.

Thanks, for any help.

---

### Post by ChameleonDave on 2008-07-11
Try [http://www.linuxhardware.org/](http://www.linuxhardware.org/)

I attach a file containing my system information, obtained with "sudo lshw -sanitize" and "sysinfo".

---

### Post by colsandurz on 2008-07-11
I do have one additionally question -- if I do go with the core duo, 32 bit processor, how is memory support as I get closer to 4GB?  I know intel developed Physical Address Extention so, I believe, up to 8 GB of memory can be used on a 32 bit system, but I have only seen this implemented in Windows (it's changed in the boot.ini)  Is PAE available for desktop linux?  If not what is the maximum memory I can use? (it could be lower than since there are devices other than memory that need addresses, I believe in windows you can use around 3.37 GB, it might vary from system to system)

---

### Post by ChameleonDave on 2008-07-11
> **colsandurz said:**
> I do have one additionally question -- if I do go with the core duo, 32 bit processor, how is memory support as I get closer to 4GB?  I know intel developed Physical Address Extention so, I believe, up to 8 GB of memory can be used on a 32 bit system, but I have only seen this implemented in Windows (it's changed in the boot.ini)  Is PAE available for desktop linux?  If not what is the maximum memory I can use? (it could be lower than since there are devices other than memory that need addresses, I believe in windows you can use around 3.37 GB, it might vary from system to system)
See [http://ubuntuforums.org/showthread.php?t=855511](http://ubuntuforums.org/showthread.php?t=855511)

---

### Post by MasterNetra on 2008-07-11
All i can say is to remember to stick to common brands and types of parts to help ensure that Ubuntu will recognize the stuff. But i guess acording to the thread posted, Ubuntu (32bit) does not support 4GB plus at least not out of the box. Ubuntu (64bit) apparently does with maybe some enabling of this and that MIGHT be required.

---

### Post by silkstone on 2008-07-11
I put this machine together recently with an Abit Fatality motherboard, Intel E4600 processor, 2GB DDR2 RAM and Nvidia 8400GS graphics card. I'm not a gamer so the card is fine for 1680x1050 including desktop effects, although I turned these off once I'd had a play.

Everything worked straight out of the box. I'd not recommend that setup for 3-D games, but for everything else it works well and is quite inexpensive. There's really no need for more than 2GB RAM. Ubuntu 32-bit will recognise just over 3GB (same as XP). I have heard of people having problems if there's 4GB installed, because the OS cannot resolve the extra RAM, but I can't confirm that.

---

### Post by colsandurz on 2008-07-11
So I put together this initial list... does anyone have any experience with any of these not working with linux (or not working with each other for that matter)

CPU
Intel Core 2 Duo E7200

Motherboard
GIGABYTE GA-EP45-DS3L LGA 775 Intel P45

Memory
Crucial Ballistix PC2-6400

Video
GIGABYTE GV-NX88T512HPV1

HD
320 GB, SATA 3Gb/s, seagate

---

### Post by MasterNetra on 2008-07-11
Also i should there is generally no reason you should need more then 4GB at this time. But should you want to get 8GB go with using Ubuntu's 64 bit version (which i use for my Intel Core 2 Duo processors anyway and it runs pretty well.)

But you could run your part names through the forum to see if ppl have had problems or something. Just a thought though.

---

