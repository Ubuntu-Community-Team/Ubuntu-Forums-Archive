---
title: "Dual Boot: Ubuntu + Win2008"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by westerdaled on 2009-03-19
Yes, another dual boot issue :o but this time I want to boot up  via grub then either select Ubuntu 8.10 or Windows 2008(or vista). in this case the NTFS partition I  want to sit at the end of my 750Gb hard disk.
Is this possible.?


I have now repartition the extended partition as a NTFS primary partition.

> Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60807   488432196   83  Linux
/dev/sda2           60808       61305     4000185   82  Linux swap / Solaris
/dev/sda3           61306       91201   240139620    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12345678

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    7  HPFS/NTFS


My grub item looks like this now
```
title		Windows 2008
root		(hd0,2)
#map (hd0,0) (hd0,2)
#map (hd0,2) (hd0,0)
# rootnoverify (hd0,0)
makeactive
chainloader	+1
```

On selection I now get the error: 
> BOOTMRG Missing press any key to reboot
If this is valid  I guess I now want the bootloader to try to install from my win2008 dvd. How can I make this happen? Any help would be appreciated.


Daniel

---

### Post by meierfra. on 2009-03-19
> If this is valid 
It is.

> I now want the bootloader to try to install from my win2008 dvd. 
I don't understand your question.  Why don't you set your bios to boot from the cdrom drive,  boot from Win2008 dvd and install win2008 to the ntfs partition?

After installing win2008 you will have to reinstall grub:

Boot from the Ubuntu Live CD, open a terminal and type

```
sudo grub
root (hd0,0)
setup (hd0)
quit
```

---

### Post by westerdaled on 2009-03-24
Thanks for your help. I followed your advice and I can boot up using either win2008 x32 or x64 dvds however I seem to end up in the same place. Namely, once the setup loads a few files I am presented with a grey screen and a  working mouse but the setup seems to stall at this point. I say stall as I waited about 10 mins in which time there was no visible disk activity before hitting the reset button and booting into Ubuntu. 

Is the setup stalling on detecting grub on an EXT3 partition?
Should I try booting with Vista or XP and see if that fairs better.

cheers


Daniel

---

### Post by meierfra. on 2009-03-24
> Is the setup stalling on detecting grub on an EXT3 partition?

I don't think so.  Sometimes grub or an ext3 partition prevent Windows from detected a suitable partition for installation.  But I never have seen a case where grub/ext3 caused a problem after the installation has  begun.

> I say stall as I waited about 10 mins in which time there was no visible disk activity before hitting the reset button 

You might wait a  little longer.
Anyway, this seems to be  a plain Windows problem. I would guess that its related to some settings in your bios, but i really don't know. 
If you haven't done so, I suggest to a consult a Windows forum.


> Should I try booting with Vista or XP and see if that fairs better.

Can't hurt.

---

### Post by westerdaled on 2009-03-27
> **meierfra. said:**
> 
You might wait a  little longer.
Anyway, this seems to be  a plain Windows problem. I would guess that its related to some settings in your bios, but i really don't know. 
If you haven't done so, I suggest to a consult a Windows forum.
Can't hurt.

Well I did wait a little longer and yes, I now have win2008 x64 Enterprise running on the tail end of my disk. Interestingly, the install hasn't detected my network card whereas Ubuntu breezed through this. A problem for another day I think

It took two attempts to get my ubuntu back - the find command below was just to confirm my boot location (hd0)

  ```
  sudo grub

    > find /boot/grub/stage1

    > root (hd0,0)  
    

    > setup (hd0)

    > exit

```

Thanks again... :)

---

### Post by meierfra. on 2009-03-28
> Well I did wait a little longer and yes, I now have win2008 x64 Enterprise running on the tail end of my disk. 

Great. Have fun with win2008 and Ubuntu

---

