---
title: "creating 5th partition for GRUB"
date: 2009-04-13
forum: Installation &amp; Upgrades
---

### Post by dijxtra on 2009-04-13
I have 4 primary partitions: 3 OSes (Kbuntu/Xubuntu/Arch) and swap. Now I want to create a separate partition for GRUB. So, I'd like to ask:

0. why can't I have more than 4 primary partitions
1. does GRUB have to be installed on a primary partition
2. does Ubuntu have to be installed on a primary partition if I want to use it's GRUB (as I do it now, before I have created separate partition for GRUB)
3. does Ubuntu have to be installed on a primary partition if I don't want to use it's GRUB (I'll use GRUB on separate partition)
4. do Windows XP have to be installed on a primary partition
5. what primary/logical configuration do you propose if I wan to have saaaay, 5 linuxes, 1 windows, swap and separate GRUB partition? Which one should I put on primary and which one on logical partition?
6. how dangerous is ti to resize ext3 partitions with gparted? Am I reasonably safe from data loss?

Thanks in advance.

---

### Post by Aubergines on 2009-04-13
**0. why can't I have more than 4 primary partitions?**
The reason why you can't have more than 4 primary partitions is due to the limitations of the partition table. The partition table on current drives occupies 64 bytes. Each partition uses 16 bytes and therefore you can only have 4 partitions. More info [here](http://www.viralpatel.net/taj/tutorial/partition_table.php).

**1. does GRUB have to be installed on a primary partition?**
Grub is installed into the MBR which isn't on any partition, it's the first 446 bytes of a hard drive. The grub configurations and the application that writes to the MBR however can be on any partition.

**2. does Ubuntu have to be installed on a primary partition if I want to use it's GRUB**
Ubuntu can be installed on any partition. Grub is simply an application, the application is controlled by a configuration file (menu.lst). The app with the config writes the bootloader with your specified settings to the MBR. It doesn't matter which distro you use to write to the MBR. 

**3. does Ubuntu have to be installed on a primary partition if I don't want to use it's GRUB (I'll use GRUB on separate partition)**
See above

**4. do Windows XP have to be installed on a primary partition**
No, Windows can be installed on any partition. In fact windows is installed within a logical partition as default.

**5. what primary/logical configuration do you propose if I wan to have saaaay, 5 linuxes, 1 windows, swap and separate GRUB partition? Which one should I put on primary and which one on logical partition?**
If you want a shared /boot partition for all your linux distos (I'm not even sure that's safe with various distro possibility using different versions of grub but sharing the same configs) you can put /boot and swap on a primary. The rest of the drive can be a logical partition which holds all your distros.

**6. how dangerous is ti to resize ext3 partitions with gparted? Am I reasonably safe from data loss?**
No idea, the gparted faq can be found [here](http://gparted.sourceforge.net/faq.php)

---

### Post by dijxtra on 2009-04-13
Excellent! Thanks for all your answers, you were most helpful.

> **Aubergines said:**
> **0. why can't I have more than 4 primary partitions?**
**5. what primary/logical configuration do you propose if I wan to have saaaay, 5 linuxes, 1 windows, swap and separate GRUB partition? Which one should I put on primary and which one on logical partition?**
If you want a shared /boot partition for all your linux distos (I'm not even sure that's safe with various distro possibility using different versions of grub but sharing the same configs) you can put /boot and swap on a primary. The rest of the drive can be a logical partition which holds all your distros.
No, not shared /boot partition, but a partition that has only /boot/grub in it, and to which MBR is pointing. That is much simpler than shared /boot.

---

### Post by meierfra. on 2009-04-13
> 4. do Windows XP have to be installed on a primary partition
No, Windows can be installed on any partition. In fact windows is installed within a logical partition as default.

Incomplete answer. You will not be able to install Windows unless you have a primary fat or ntfs partition on the boot drive. So it will be best to install Windows on a primary partition.

I suggest to make Windows and your grub partition primary, the rest logical
(or if you want to have Windows on logical partition, you can format the grub partition as fat32 and use it also  as the Windows System partition)

> how dangerous is ti to resize ext3 partitions with gparted? Am I reasonably safe from data loss?
gparted is very safe, but in rare cases data loss can occur.  So  you should  backup all your value data.

---

### Post by dijxtra on 2009-04-14
meierfra., thanks for the tip.

Now, can anyone tell me how can I figure out to which GRUB does my MBR point to (in a scenario I have GRUB on saaay: hd0,0, hd0,1 and hd0,3 and they all have identical menu.lst)?

---

### Post by meierfra. on 2009-04-14
> Now, can anyone tell me how can I figure out to which GRUB does my MBR point to 

Well, you could just add  something like this to your menu.lst:

title  Menu.lst from /dev/sda1
root


Or download the Boot Info Script to your desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and type:


> sudo bash ~/Desktop/boot_info_script*.sh

That will create the file "RESULTS.txt"  on your desktop
The first few lines of RESULTS.txt will answer your question.

---

### Post by dijxtra on 2009-04-14
Interesting. So, there's no way I can find that out from grub shell?

---

### Post by meierfra. on 2009-04-14
> So, there's no way I can find that out from grub shell?

No. Actually the boot_info_script was originally invented to provide an answer to your question. Namely look at all the MBRs, determine whether grub is installed and if yes, determine  where grub is pointing to. 

Here is on  more way to answer your question.
Say grub is installed in the mbr of /dev/sda. 
Then type 

```
sudo xxd -s 1049 -l 2 /dev/sda 
```

If it returns

0X8Y

it means grub looks for menu.lst on

(hdY,X)

So for example if it returns

0382

then grub looks for menu.lst on 

(hd2,3)


Also "0XFF" has the same meaning as "0X80", that is grub looks for menu.lst on (hd0,X)"

---

### Post by dijxtra on 2009-04-15
> **meierfra. said:**
> Here is on  more way to answer your question.
Say grub is installed in the mbr of /dev/sda. 
Then type 

```
sudo xxd -s 1049 -l 2 /dev/sda 
```

If it returns

0X8Y

it means grub looks for menu.lst on

(hdY,X)

So for example if it returns

0382

then grub looks for menu.lst on 

(hd2,3)


Also "0XFF" has the same meaning as "0X80", that is grub looks for menu.lst on (hd0,X)"

Now, that's an answer I was looking for! :-D Thanks a bunch! Now I'll go dissect xxd and have fun. :-)

---

