---
title: "Where's Grub - some confusion regarding boot drive"
date: 2009-03-28
forum: Installation &amp; Upgrades
---

### Post by mooncaptain on 2009-03-28
Hi all,

I have XP on one drive in my system. I installed a 2nd drive and install 8.04 on it. After the reboot I went into the BIOS and set the boot drive to be the drive where I installed ubuntu. The boot failed (I don't remember the error - sorry). 

I immediately reset the boot drive to the disk with XP. The system booted to a Grub menu. I did not expect this. The grub menu had an "Other OS" section with my XP install listed. 

Does this mean that grub is on my XP drive? What if I blow away (format) the ubuntu drive? Do I still have grub? Not that I mind so much but how did this happen? I have installed various Ubuntu systems on this machine and this hasn't happened before. If I wanted to boot to the grub and have a choice of OS to load I set the boot drive to the one with the ubuntu on it.

If it comes to it how would I remove grub?

---

### Post by meierfra. on 2009-03-28
By default Grub is installed to the MBR of the  boot drive.

The following will installed Grub to the MBR of the Ubuntu drive and  restore the MBR of the Windows drive:

Open a terminal in Ubuntu (Applications->Accessories->Terminal

** Step 1 Install Grub to the MBR of the Ubuntu drive.**


```

sudo grub

```

and at the "grub>" prompt.


```

 find /boot/grub/stage2

```

This will return (hdX,Y), where X and Y are some numbers, like (hd1,0)
(if it returned 'file not found', try  'find /grub/stage2' and  'find /stage2' )

Still at the "grub>" prompt:

```

root (hdX,Y)
setup (hdX)
quit

```

(here X and Y need to be replaced by the numbers you got from "find /boot/grub/stage2")


** Step 2) Install a Windows Style MBR to the Windows drive: **


```

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

```

(Here "/dev/sda" needs to be the device name of your Windwos drive. It probably is "/dev/sda" but you should double check via "sudo fdisk -lu")


**Step 3 Edit Menu.lst so that you can boot to Windows from the Grub menu.**

Open the file "menu.lst" via 

```
gksudo gedit /boot/grub/menu.lst
```


Look for  the  item which looks  something like

title XP
root (hd0,?)
savedefault
chainloader +1

Replace the line

root (hd0,?)


by the the three lines

root (hd1,?)
map (hd0) (hd1)
map (hd1) (hd0)

Save the file and reboot. If you boot from the Windows drive, you should boot directly into XP. If you boot from the Ubuntu drive, you should get the Grub menu, which lets you boot into XP and Ubuntu


Or if you want, you can just keep your current setup, and use "Step 2" if you ever need to remove Grub from the MBR of  Windows drive to boot directly into XP.

---

### Post by mooncaptain on 2009-03-28
Thanks I am up and running with my new configuration.

If I set the boot drive to the XP drive the system boots straight to XP.

If I set the boot drive to the ubuntu drive I get grub and choices that all currently work.

I did one additional change. For the Ubuntu options I had to change hd1 to hd0. Fortunately the "live" grub editor let me edit the boot configuration after it failed to initially mount the partition.

Thanks again - I had no idea about lilo or how to put grub on a specific drive.

---

### Post by meierfra. on 2009-03-28
> Ihad to change hd1 to hd0. 

Sorry. I should have warned you. I have gotten so used to UUIDs (which are used by Ubuntu 8.10 and higher) that I forgot that Ubuntu 8.04 often still uses "root (hd?,?)"

> I had no idea about lilo 
"lilo" is just one of many ways to fix the MBR. Most people recommend running "fixmbr" from the XP CD. But "lilo" from Ubuntu is much faster and does the job  just as well.


> Thanks I am up and running with my new configuration.
Great. Have fun with XP and Ubuntu.

---

