---
title: "help with Grub Error 17"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by lionlion on 2009-01-23
I have ubuntu and windows xp on my dell vostro 1400.

At beginning, I was screwed by windows but ubuntu was fine. I even could not boot from windows installation CD and always got blue screen include

```

Plug and Play detected an error most likely caused by a faulty driver.

Technical information:
*** STOP: 0x000000CA (0x00000001,0x82ED2E30,0x82FCDC08,0x00000000)
```

I fixed it through testdisk

```

sudo apt-get install testdisk
sudo testdisk

```


I tried "fdisk /mbr" and grub installation. Now I got my windows back, but my ubuntu was screwed. I got 
"Error 17: Cannot mount selected partition"

If I used ubuntu live CD, I saw a mirror as /dev/sda4 and /dev/sda5 through command sudo fdisk -l

```

/dev/sda4     13992   14593    4835565   f W95 Ext'd (LBA)
/dev/sda5     13992   14267    2216907  82 Linux swap / Solaris (LBA)

```


Any suggestions?

---

### Post by caljohnsmith on 2009-01-24
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by lionlion on 2009-01-25
Thanks for your reply

As I run "fdisk -l", I get the following:

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+   6  FAT16
/dev/sda2   *          11        7659    61440592+   7  HPFS/NTFS
/dev/sda3            7660       13991    50861790   83  Linux
/dev/sda4           13992       14593     4835565    f  W95 Ext'd (LBA)
/dev/sda5           13992       14267     2216907   82  Linux swap / Solaris
/dev/sda6           14268       14593     2618563+   c  W95 FAT32 (LBA)


```
As I run "bash ~/Desktop/boot_info_script*.sh", I attach output file. 

Please take a look and help me.

Thank you very much

---

### Post by caljohnsmith on 2009-01-25
OK, from your Live CD try:
```
sudo mount /dev/sda3 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
And then change all your Ubuntu entries to use (hd0,2) similar to:
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		[COLOR="Blue"](hd0,2)[/COLOR]
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=641a35d3-e9db-4171-ba94-fdf0e819fbc6 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```
Also change the "# groot=(hd0,3)" line:
```
# groot=[COLOR="Blue"](hd0,2)[/COLOR]
```
And lastly, change your last Windows entry to:
```
title		Microsoft Windows XP Embedded
rootnoverify	(hd0,5)
chainloader	+1
```
Then reboot, try booting Ubuntu from Grub, and let me know what happens. Also, try booting your "XP Embedded" entry in the Grub menu and let me know if that works or not. We can work from there.

---

### Post by lionlion on 2009-01-29
HI, caljohnsmith

Thank you so much. 

My window and ubuntu are up after following your suggestion.

I never entered "XP Embedded" before and don't know what it is for and what would be happen when it was normal.

This time I tried. I got 

```
Error 12: Invalid device requested.

Press any key to continue...
```

Anyway, thank you so much. Any suggestion on avoiding this issue?

---

### Post by caljohnsmith on 2009-01-29
Great, I'm glad to hear Windows and Ubuntu are booting OK now. As long as you're not concerned with whatever it is you have installed to sda6, then don't worry about the "XP Embedded" Grub entry (you can delete it if you want). Cheers and have fun with your OSes. :)

---

