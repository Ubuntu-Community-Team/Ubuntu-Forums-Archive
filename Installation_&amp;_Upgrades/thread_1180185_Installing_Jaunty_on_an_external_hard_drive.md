---
title: "Installing Jaunty on an external hard drive"
date: 2009-06-06
forum: Installation &amp; Upgrades
---

### Post by johnconnor on 2009-06-06
Hi everyone!

I'm running Hardy on my laptop and would like to give Jaunty a real try (I mean more than just trying the live CD). But my internal HDD is a mess and I did not find the time to save everything right now. So to avoid loosing my data, I would like to install Jaunty on my external HDD. I've read that it's pretty simple and that I just need to disconnect my internal HDD to make sure its not altered. The problem is that, as you can guess, I can hardly disconnect my laptop's internal HDD... How can I can sure that it wont be altered during the install even though its still connected?

---

### Post by logos34 on 2009-06-06
change the location of the bootloader, so it won't overwrite hardy's grub on the internal mbr.

WHen you get to "Ready to Install" screen (step 7), press 'Advanced" button lower right.  Change the default grub location from '(hd0)' to **(hd1)**, or **/dev/sdb**. 

When you finish reboot, go into the Bios and change the hard disk boot priority so the USB is first.  

If you want you can also add a [configfile Jaunty boot entry]("http://members.iinet.net.au/%7Eherman546/p15.html#1._Configfile") to Hardy grub memnu.lst.

Hope that helps

---

### Post by johnconnor on 2009-06-06
Thank you for your help!

There's just one last problem. I would like to try ext4 as well so I use the advanced partition editor. At the "Ready to install" screen, the installer tells me he's gonna format my internal HDD's swap partition... I guess I have to tell the partitioner not to use the internal swap. Just to be sure.

---

### Post by logos34 on 2009-06-06
> **johnconnor said:**
> Thank you for your help!

There's just one last problem. I would like to try ext4 as well so I use the advanced partition editor. At the "Ready to install" screen, the installer tells me he's gonna format my internal HDD's swap partition... I guess I have to tell the partitioner not to use the internal swap. Just to be sure.

well, you can either let it format the internal one (but you'll have to edit hardy /etc/fstab), or just make a new one on the external (hey, it's only a gig or so).

Note: if you opt for ext4, I'm not entirely sure if hardy grub (ext3) will be able to chainload jaunty grub...so you may be limited to toggling the bios boot disk in the Bios for desired OS

---

### Post by johnconnor on 2009-06-06
I made a new swap on the external HDD. I don't understand why by default it wants to use the internal swap... I thus modified the internal swap to "don't use this partition". At the "Ready to install" screen, it no long tells it's gonna format the internal swap, only the external ext4 and swap partitions. But on the other hand, it tells me it will modify the partition tables on both the internal and external HDD. Will Hardy still boot after this?

---

### Post by logos34 on 2009-06-06
> **johnconnor said:**
> But on the other hand, it tells me it will modify the partition tables on both the internal and external HDD. Will Hardy still boot after this?

from my post above:

> **logos34 said:**
> 
WHen you get to "Ready to Install" screen (step 7), press [COLOR="Red"]'Advanced" button[/COLOR] lower right.  Change the default grub location from '(hd0)' to **(hd1)**, or **/dev/sdb**. 


---

### Post by johnconnor on 2009-06-06
This is what understood. But the fact that the installer wants to modify the partition tables on both HDDs does not seem to be related to the bootloader, but to the fact that I had to modify the internal swap partition (so that it won't be used) in the advanced partitioner. If I don't launch the advanced partitioner, the "Ready to install" screen doesn't tell the internal HDD's partition table's gonna be modified. If I use the advanced partitioner, the final screen says both HDD's partition tables will be modified. I have to use the advanced tool if I want an ext4 partition. So I have to modify the internal swap to tell the advanced partitioner not to use it. So the final screen tells me both HDD's partition tables will be modified. My question is: If I run the installation anyway (with both partition tables being modified), will Hardy still run afterwards?

Sorry if my previous message was confusing

---

### Post by logos34 on 2009-06-06
> **johnconnor said:**
> This is what understood. But the fact that the installer wants to modify the partition tables on both HDDs does not seem to be related to the bootloader, but to the fact that I had to modify the internal swap partition (so that it won't be used) in the advanced partitioner. If I don't launch the advanced partitioner, the "Ready to install" screen doesn't tell the internal HDD's partition table's gonna be modified. If I use the advanced partitioner, the final screen says both HDD's partition tables will be modified. I have to use the advanced tool if I want an ext4 partition. So I have to modify the internal swap to tell the advanced partitioner not to use it. So the final screen tells me both HDD's partition tables will be modified. My question is: If I run the installation anyway (with both partition tables being modified), will Hardy still run afterwards?


I can't see how it would screw up hardy, although I haven't done a 9.04 install (and it's been a year since I did 8.04)...The partition table is a actually located right after the bootloader on the MBR (446 + [COLOR="Red"]46[/COLOR] bytes)...What exactly it means by 'modified' (how?) I'm not sure, since you clearly told it not to use the internal swap...

You want a sure way to do this and have peace of mind too?  Open up the bottom of the lappy, disconnect the hard disk, then boot with the USB attached and install that way.  Nothing on the internal hdd will be touched, and nothing to manually configure or partition.  Afterward add a 9.04 boot entry to hardy grub, and a hardy entry to jaunty /etc/fstab if you want to mount and access it. 

Done.

---

### Post by johnconnor on 2009-06-07
> **logos34 said:**
> You want a sure way to do this and have peace of mind too?  Open up the bottom of the lappy, disconnect the hard disk, then boot with the USB attached and install that way.  Nothing on the internal hdd will be touched, and nothing to manually configure or partition.

This is what I ended up doing, the installer was behaving too strangely to take the risk... Thank you for your help!

---

