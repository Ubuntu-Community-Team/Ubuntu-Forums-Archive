---
title: "Can't boot from device after ubuntu install"
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by k1llu4 on 2009-01-03
Hi, this is my first time installing ubuntu with vista installed first onto my lenovo notebook.
The installation was completed successfully and restarting, but after that my notebook can't boot from anything. It's just rebooting again and again, so I can only access BIOS. I'm also trying one key recovery from lenovo but it didn't work either. 
How I can get this fixed? Is there a way to recover it? 

Thanks

---

### Post by tommcd on 2009-01-03
1) How did you install Ubuntu? Did you install using Wubi? Or did you partition the hard drive and do a real install to a dedicated partition?

2) Can you boot from the Ubuntu live CD and open a terminal (applications > accessories > terminal) and run this command:
```
sudo fdisk -l
```
This will list your hard drive partitions and tell us where Ubuntu was installed to if you created a separate partition.

3) Do you see the grub boot menu on boot up?

Please answer those 3 questions. 

And welcome to the Ubuntu forums!

---

### Post by k1llu4 on 2009-01-03
Hi, thanks for reply...
1) I didn't know about Wubi, so it's the 2nd way i guess :p..Since I did created and allocated a partition for root and swap partition..
2 & 3) When I'm restarting my notebook with live cd (also trying cd recovery from lenovo),I can't get anywhere from my first booting screen, it always restart after trying to boot from device..So I can't see the grub boot menu too..

---

### Post by pastalavista on 2009-01-03
In the BIOS settings make sure it is set to boot from the CD first, before trying to boot from the HD. Then reboot with the Ubuntu CD and run the commands **tommcd** suggested and copy/paste the output here.

---

### Post by k1llu4 on 2009-01-03
Yes, I'm sure that my first boot device is my dvd rom and 2nd is my HDD..But my notebook always restarted before the boot up menu appear, making that BIOS is the only one I can access..

---

### Post by utnubuuser on 2009-01-03
Some Thinkpads have a hidden partition where the "Restore to factory settings script lives". Did you make this partition visible before installing?

---

### Post by k1llu4 on 2009-01-03
I wonder if I was installed ubuntu to that hidden partition..Before installed ubuntu, I had created 4 partition on my 160G HD (can't remember how big size for each partition).When I checked my HD from disk management on vista I was just realize that there was another partition about 12G size which is didn't have any label or name and cannot be formatted.As far as I can remember, I have ubuntu installed to that partition..
So, if I just installed it to hidden partition is there any way to fix my booting?

Thanks very much utnubuuser

---

### Post by tommcd on 2009-01-04
As the computer boots go into the BIOS. Then make sure the computer is set to boot from the CDROM as the 1st boot device. Pop in the Ubuntu live CD and hit F10 and exit. It should boot to the Ubuntu live CD. Then open a terminal and post the output of:
```
sudo fdisk -l
```
That should show all your Windows and linux partitions.

---

### Post by k1llu4 on 2009-01-04
I already have tried another live cd like lenovo mbr repair, recovery for vista and gparted live cd..I Also have tried to boot from live usb drive as well..But the results still the same, stuck in initial Lenovo splash screen, then my notebook keep restarting before I can do anything...
It's time to call Lenovo support I think :)

---

