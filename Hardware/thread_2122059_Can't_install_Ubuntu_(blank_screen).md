---
title: "Can't install Ubuntu (blank screen)"
date: 2013-03-04
forum: Hardware
---

### Post by ShadowVegan on 2013-03-04
Edit: I got my first problem fixed. I switched to 64 bit and now I can boot from CD and get 'Install Ubuntu' as an option. However, when I select that option, it goes to a black screen, and stays completely blank. I tried from both a CD and a USB drive, and I tried leaving it for a few minutes, and it just stays black. Any ideas?

Original message below (this has all been solved, I just have issues with the black screen now):

Sorry if this is the wrong forum.

I just bought a new laptop and I  want to put Ubuntu on it. I put the Ubuntu installation CD in the CD  drive and went into the BIOS, but in the boot device priority, there is  no option for CD. I tried another (identical CD) in case it's a problem  with the CD, and also tried one of the CDs on my other computer to make  sure it works, so I know the problem is not the CD. I also booted  Windows on my new laptop to verify that the CD drive works, which it  does. It seems to be an issue in the BIOS.

I also tried booting  from an Ubuntu installation USB drive. Unlike with the CD, it actually  gives me the option to boot from the USB drive. However, it won't load  it, so even if I put USB drive as first priority it just skips over it  and loads Windows.

[This]("http://www.bestbuy.com/site/Asus+-+15.6%22+Laptop+-+4GB+Memory+-+500GB+Hard+Drive+-+Black/7688053.p;jsessionid=306DEA9CB9DA7EE279D1CDCB4ED0B953.bbolsp-app04-70?id=1218858193067&skuId=7688053") is the model.

I  do have the option to 'Add New Boot Option' in BIOS at which point I am  prompted to 'Add boot option' (I type it) 'Select Filesystem' (have to  select one from a list), and 'Path for boot option' (I type it), after  which I can click 'Create'. I tried creating one but I just guessed on  what to enter in those fields and it didn't work. The options for  'Select Filesystem' are:
PCI(14|0)\USB(2,0)\HD(Part1,Sig0009E7AB)
PCI(1F|2)\DevicePath(Type 3, SubType 12)HD(Part1,Sig2825be3c-a830-413a-b913-334f17389c83)


Also,  not sure if this is of any use, but under 'SATA Configuration' I found  some details on the CD drive. Everything under SATA Configuration:

SATA Mode Selection [AHCI] (I can also choose [IDE])

Serial ATA Port 0
Device Type: Hard Disk
Model Name: TOSHIBA MQ01ABD050
Serial Number: Y2ABC19JT

Serial ATA Port 2
Device Type: ATAPI CDROM
Model Name: PIONEER DVD-RW DVRTD11R
Serial Number: SMC2711919


If  any other information can be of use, please let me know. Any ideas on  how to install Ubuntu (via CD, USB, or any other method) will be very  much appreciated. Thank you.

---

### Post by sanderj on 2013-03-04
I'm not expert in this, so just some remarks:

The USB-stick: have you check it does work in another computer?

the Windows in the computer: is it Windows 8? If so, it maybe is a UEFI problem. For UEFI, you must use 64-bit Ubuntu. Do you that? 
Furthermore, see [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

HTH

---

### Post by ShadowVegan on 2013-03-04
I didn't try the USB stick in another computer but I didn't realize UEFI requires 64 bit, I actually didn't even know what UEFI was until tonight. (Yes my laptop is Windows 8 and UEFI) I am going to try downloading the 64 bit version of Ubuntu and will update you whether or not it works. Thanks!

---

### Post by ShadowVegan on 2013-03-04
I got the CD made and now it lets me boot from the CD, but I still can't install. The CD is 64 bit 12.04 LTS. When I boot I get black screen with white text:

GNU GRUB version 1.99-21ubuntu3.9

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub> _




Edit: Nevermind, somehow I got it to work! I enabled CSE or CSM or  something like that in the BIOS (UEFI?) menu, because I saw something  about that elsewhere when I was looking for a fix. So through a  combination of using the 64 bit version and changing settings I got it  to work. Loading slow but I just clicked Install Ubuntu so I'm almost  positive it's working.

Thank you very much! [IMG]http://ubuntuforums.org/images/smilies/icon_biggrin.gif[/IMG]

---

### Post by ShadowVegan on 2013-03-04
Now I'm having another issue... whenever I select Install Ubuntu I am taken to a blank black screen and nothing happens. I tried installing 64 bit Ubuntu 12.04 from both CD and USB drive. Both cases I am given the option to Install Ubuntu, Try Ubuntu, and Check Disk For Errors (don't remember the exact wording, but that's basically what they said). Any ideas? Thanks.

---

### Post by sanderj on 2013-03-04
> **ShadowVegan said:**
> Now I'm having another issue... whenever I select Install Ubuntu I am taken to a blank black screen and nothing happens. I tried installing 64 bit Ubuntu 12.04 from both CD and USB drive. Both cases I am given the option to Install Ubuntu, Try Ubuntu, and Check Disk For Errors (don't remember the exact wording, but that's basically what they said). Any ideas? Thanks.

As [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) says: You should choose "Try Ubuntu" (not "Install ubuntu").

---

### Post by ShadowVegan on 2013-03-04
I believe that was giving me a black screen before too, but I got Install Ubuntu to work, finally, after like 5-6 hours. Through a combination of a friend's suggestions and [this page](https://help.ubuntu.com/community/UEFI) I changed a bunch of BIOS settings (I changed a lot, can't say exactly what all I changed, but it definitely did the trick) so now I've successfully gotten it to show up. I think it was mainly about disabling thins like FastBoot and some other UEFI/Win8 things.

Thanks for the suggestions.

---

### Post by justincarter on 2013-03-04
There are many way to install ubuntu. Install from Pd's , install within windows.
Many Ubuntu expert will suggest that for ideal installation  quit Windows entirely, but that’s not completely necessary: Windows and  Ubuntu can co-exist quite peacefully.
In fact, if you want, you can install Ubuntu directly from inside  Wubi. If you have an Ubuntu CD go ahead and insert it in Windows; you’ll  be asked if you want to install Ubuntu. This is possible because of a  program called Wubi.

---

