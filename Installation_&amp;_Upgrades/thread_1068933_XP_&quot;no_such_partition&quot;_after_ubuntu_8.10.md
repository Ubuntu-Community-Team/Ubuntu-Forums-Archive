---
title: "XP &quot;no such partition&quot; after ubuntu 8.10 installation, HELP PLEASE!"
date: 2009-02-13
forum: Installation &amp; Upgrades
---

### Post by DARKAD on 2009-02-13
Before I installed the ubuntu 8.10 version, I had win2000 on one partition and win xp on another one. 
With some other ntfs partitions to store some data.

I installed ubuntu 8.10 on primary partition, the windows 2000 partition, adding a swap partition also.

After ubuntu installation hith sudo fdisk -l i see this:
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1083     8699166   83  Linux
/dev/sda2            1084        4866    30386947+   f  W95 Ext'd (LBA)
/dev/sda5            1218        1412     1566306    7  HPFS/NTFS
/dev/sda6            1413        2433     8201151    7  HPFS/NTFS
/dev/sda7            2434        3649     9767488+   7  HPFS/NTFS
/dev/sda8            3650        4866     9775521    7  HPFS/NTFS
/dev/sda9            1084        1217     1076292   82  Linux swap / Solaris

Now I see the WINNT (xp directory) mounting one of the ntfs partitions but I can't tell which one it is (watching the above list).

So I edited the menu.lst file and I rebooted my pc for five times changing the below text lines by the * symbol with (1,2,3,4,5)

...
...
...
### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows XP
root (hd0,*)
savedefault
makeactive
chainloader +1

the result was error 22 "no such partition error" and another error was about ....device.... with code 12.

Any suggestion would be very appreciated, it's a necessary needing indeed.

Thank you in advance.

---

### Post by caljohnsmith on 2009-02-13
Since your only remaining NTFS partitions are all logical partitions, that means Windows is most likely missing its boot files; whenever you install Windows to a logical partition, it puts its boot files in a primary NTFS/FAT partition. Since you deleted your only primary NTFS partition (Windows 2000) when you installed Ubuntu, probably Windows XP is now missing its boot files. It would help to get more information about your setup related to booting Windows, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your Windows booting problem might be.

---

### Post by DARKAD on 2009-02-13
Oh really thank you!
On monday I'll go back at work and then I'll try this script.

At the moment I'll search information on it to try to resolve all the problems in early monday morning!

Anyway I'll post the script results.

Thanks.

---

