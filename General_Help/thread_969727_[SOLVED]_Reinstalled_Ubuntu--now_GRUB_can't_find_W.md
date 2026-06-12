---
title: "[SOLVED] Reinstalled Ubuntu--now GRUB can't find Windows"
date: 2008-11-03
forum: General Help
---

### Post by fiddler616 on 2008-11-03
Hello,
The other month Windows crashed, and I didn't do a thing about it since I didn't have a recovery CD.

The other day I managed to get a recovery CD, and after double-checking here on the forums, I installed Windows.

That overwrote GRUB, of course, but I found a tutorial on the main Ubuntu site describing how to get it back--involving using a terminal off a Live CD....which brought GRUB back. However, GRUB couldn't mount the Ubuntu partition, and Windows wouldn't load.

After some tomfoolery with the Super GRUB Disk, I decided that to maintain sanity, I would just back up my documents and reinstall Ubuntu. Which I did.

The Ubuntu install works great, except GRUB won't even *list* Windows, and I have no idea why.

**A brief history of my hard drives:**
First, I had C:\ , D:\ , / and swap. C:\ had Windows, D:\ had a few random Windows programs/documents, / had Ubuntu, and swap--well, it was swap.

When I installed Windows, I put it on D:\ , leaving a 'dead' Windows installation (the previous one, which didn't work) on C:\

When I installed Ubuntu, I used the partition manager to erase C:\ --I had backups, and it really wasn't doing anything. / and swap were converted into / /home and swap, and D:\ wasn't touched.

Is getting rid of C:\ (which was labeled as 'boot', I believe) the cause of the problem?


Thanks in advance.

---

### Post by elbarto_87 on 2008-11-03
Maybe try the Super Grub boot disk to see if you can access your partitions.

 [Link]("http://supergrub.forjamari.linex.org/")

Im pretty sure this is the file I downloaded when I had some issues after a fresh xp install. Its a small iso file (only a few MB I think) that runs as a live cd. Just boot into it on startup and it should tell you all of the available OS's to boot. Might be worth a shot...

Elbarto

---

### Post by caljohnsmith on 2008-11-03
So you are getting the Grub menu on start up OK, and can boot into Ubuntu, but you just don't have an option to boot Windows? If that's the case, when you get into Ubuntu, just open a terminal (applications > accessories > terminal), and do:
```
sudo fdisk -lu
```
Find your Windows partition as type "NTFS" or possibly "FAT32", and once you know it, then do:
```
gksudo gedit /boot/grub/menu.lst
```
And at the very end of the document, add an entry like:
```
title Windows XP
root (hd0,X)
chainloader +1
```
But replace the "X" with your Windows partition number minus one:
```
sda1 = (hd0,0)
sda2 = (hd0,1)
sda3 = (hd0,2)
...etc.
```
That should be all it takes; but if you run into problems, then post the output of the fdisk command above, and we can work from there. :)

---

### Post by fiddler616 on 2008-11-04
> **caljohnsmith said:**
> So you are getting the Grub menu on start up OK, and can boot into Ubuntu, but you just don't have an option to boot Windows?[/QUTOE]
Yes.
[QUOTE
That should be all it takes; but if you run into problems, then post the output of the fdisk command above, and we can work from there. :)
OK, so I did as instructed, and Windows XP did indeed appear on the GRUB menu (though I had to press Esc to enter it (?)), but when I tried to boot off of it, it gave me something along the lines of
> Error 13: Invalid or unexecutable something-or-other

(I can get the precise wording if you want.)

Here's my fdisk:
```

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5827c934

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1        77079870    78140159      530145    5  Extended
/dev/sda2        56050785    65818304     4883760   83  Linux
/dev/sda3   *    65818305    77079869     5630782+   7  HPFS/NTFS
/dev/sda4              63    19535039     9767488+  83  Linux
/dev/sda5        77079933    78140159      530113+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   234436544   117218241    c  W95 FAT32 (LBA)

```

I tried the SGD before I reinstalled Ubuntu--and even though it gave me a GRUB menu, nothing would boot off of it. There seems to be some more specific tutorials on their wiki, but the menu.lst method seems a bit easier (IMHO)

Thanks!

---

### Post by caljohnsmith on 2008-11-04
It looks like Windows is on sda3, so have you tried the following in your menu.lst:
```
title Windows XP
root (hd0,2)
chainloader +1
```
If not, give it a shot and let me know what happens when you choose it from the Grub menu.

---

### Post by NoVista on 2008-11-04
deleted

---

### Post by fiddler616 on 2008-11-04
> **caljohnsmith said:**
> It looks like Windows is on sda3, so have you tried the following in your menu.lst:
```
title Windows XP
root (hd0,2)
chainloader +1
```
If not, give it a shot and let me know what happens when you choose it from the Grub menu.
Wow...I'm an idiot...I put (hd0,3) not 2. So I go into gksu gedit to fix it, and:
```
timmy@Stanway01:~$ gksudo gedit /boot/grub/menu.lst
 
** (gedit:6185): WARNING **: Could not write gedit state file: Failed to create file '/root/.gnome2/gedit-2.VRQ7JU': No such file or directory

I/O error : No such file or directory
I/O error : No such file or directory
timmy@Stanway01:~$ 

```
I booted anyway though, and it gave me <edit>the error I had before I reinstalled Ubuntu:
>  NTLDR is missing, press Ctrl-Alt-Del.
</edit>
Going back into gedit, I see that the 2 was indeed written, but even closing gedit with no changes causes the same error message.
Edit: The Ctrl-Alt-Del makes me think it's a Windows thing--not a GRUB thing....(?)

---

### Post by caljohnsmith on 2008-11-04
OK, what might have happened is that Windows put its boot files on some other NTFS/FAT32 partition when you installed Windows, and you either deleted that partition or deleted the boot files since then. How about posting:
```
sudo mount /dev/sda3 /mnt
ls -l /mnt
```
And we can work from there.

---

### Post by fiddler616 on 2008-11-04
Edit:Never mind

---

### Post by fiddler616 on 2008-11-04
Here it is:
```
timmy@Stanway01:~$ ls -l /mnt
total 774200
drwxrwxrwx 1 root root      4096 2008-11-02 16:04 Documents and Settings
-rwxrwxrwx 1 root root 792723456 2008-11-02 17:28 pagefile.sys
drwxrwxrwx 1 root root      4096 2008-11-02 19:16 Program Files
drwxrwxrwx 1 root root         0 2008-11-02 17:13 RECYCLER
drwxrwxrwx 1 root root         0 2008-11-02 16:03 System Volume Information
drwxrwxrwx 1 root root     49152 2008-11-02 19:30 WINDOWS

```

---

### Post by caljohnsmith on 2008-11-04
OK, it unfortunately looks like you are missing all three of your Windows boot files. I've attached to this post the three files that you need, and I modified the boot.ini file so it should work with your sda3 partition. How about downloading the zipped files to your desktop and doing the following:
```
sudo mount /dev/sda3 /mnt
cd ~/Desktop
tar xvf "Windows_boot_files.tar.gz"
sudo mv boot.ini ntldr NTDETECT.COM /mnt
```
Reboot, select Windows from Grub, and let me know how far you get this time. :)

---

### Post by fiddler616 on 2008-11-04
> **caljohnsmith said:**
> OK, it unfortunately looks like you are missing all three of your Windows boot files. I've attached to this post the three files that you need, and I modified the boot.ini file so it should work with your sda3 partition. How about downloading the zipped files to your desktop and doing the following:
```
sudo mount /dev/sda3 /mnt
cd ~/Desktop
tar xvf "Windows_boot_files.tar.gz"
sudo mv boot.ini ntldr NTDETECT.COM /mnt
```
Reboot, select Windows from Grub, and let me know how far you get this time. :)
Wow! Thank you very much! Everything's working great now. I really appreciate your walking me through this--from start to finish.
(The last post was especially well engineered, as well)

Solved!

---

### Post by caljohnsmith on 2008-11-04
That's great news, I'm glad that missing boot files was the only problem with Windows. Cheers and have fun. :)

---

